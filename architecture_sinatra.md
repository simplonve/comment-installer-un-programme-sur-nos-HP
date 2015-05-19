Arborescence projet sinatra
				
Fichier	config.ru	Lorsque sinatra se lance, il lit le fichier et se configure lui même
					require './app'	Import de app.rb
					run Sinatra::Application	Démarrer l'application Sinatra
				
Fichier	Gemfile		Le fichier Gemfile sert à définir les bibliothèque nécessaires au fonctionnement de l'application
					Pas d'extension	Gem : Librairies (package) de codes prêt à l'emploi
				
						source 'https://rubygems.org'	Source pour télécharger le gems
						ruby '2.2.1'	Version de ruby
							
						gem 'sinatra'	gems à télécharger pour l'application
						gem 'activerecord'	
						gem 'sinatra-activerecord'	
						gem 'sqlite3'	
				
					Dans la console, après avoir réalisé les fichiers config.ru et Gemfile saisir la ligne de commande
					« bundle install » (lancer la commande dans l'arborescence du Gemfile). Cette commande va installer
					les gems indiqués dans le fichier Gemfile et génère le fichier Gemfile.lock
				
Fichier	Gemfile.lock	Fichier généré automatiquement après avoir lancé la commande « bundle install »
				
				
Fichier	rakefile.rb		Le fichier rakefile sert à faire le lien entre sql et rubis. Il est lu à chaque fois dès 
						que tu lance le serveur. 
			Lu une seule fois au lancement.
				
			require './app'	Import de app.rb
			require 'sinatra/activerecord/rake'	Import de la librairie rake activerecord pour sinatra
				
				
Fichier	app.rb		Fichier contenant les requêtes http (get, post, etc.)
					C'est dans ce fichier que l'on va récupérer et traiter les champs de saisi envoyé au navigateur par le biais du (des) fichier(s) 				index.erb		
						
					require 'sinatra'	Import de la librairie sinatra
					require 'sinatra/activerecord'	Import de la librairie activerecord pour sinatra
						
					ActiveRecord::Base.establish_connection(	Connection à la base de donnée
					:adapter => 'sqlite3',	Configurer la db pour sqlite3
					:database => 'dev.db'	Nommer la db « dev.db »
					)	
						
					ActiveRecord::Base.default_timezone= :local	Utilisation des dates et heures local pour la db
						
					class Article < ActiveRecord::Base	Création de la class article qui hérite des propriétés de base de ActiveRecord
					end	
						
					get '/' do 	Faire lorsque l'on demande au serveur, que l'on accède à un url, à la racine du site
					     @article = Article.order("created_at ASC")	Appel dans l'ordre croissant de la table Article et stockage dans la variable « article »
					     @title = "Article" 	Affecte « Article » à la variable « title »
					     erb :index	Appel et exécution de index.erb
					end	
						
					post '/' do	Faire un envoi de donnée au serveur (formulaire) ou insertion d'une donnée
					     @article = Article.new(params[:articles])	Création d'un nouvelle article avec les paramètres « articles » récupérer de index.erb
					     @article.save	Enregistrement de l'article
					     redirect '/'	Se rediriger à la racine
					end	
						
					put '/' do	Modification d'une donnée dans la base
					end	
						
					delete '/' do	Suppression d'une donnée dans la base
					end	
				
				
	Dans la console, après avoir réalisé les fichiers rakefile.rb et app.rb saisir la ligne de commande
	« rake -T ». Saisir la commande « rake db:create_migration NAME=create_nomauchoix »
	Création automatique de fichier de migration qui donne des instructions de création et de modification à la base de donnée via acitverecord
				
Dossier	db			Dossier généré en automatique où il sera stocké la base de donnée
				
Dossier migrate		Dossier généré en automatique où il sera stocké les données de migration (structure de(s) 
					table(s))
				
		Fichier ……._create_nomauchoix		Fichier généré en automatique qu'il faudra modifier pour insérer la structure de notre table
				
			class CreateArticle < ActiveRecord::Migration	Ligne généré en auto
			     def change	Ligne généré en auto
			          create_table :articles do |t|	Création de la table « articles ». Reprendre le nom de la « class CreateArticle » en minuscule au pluriel
			               t.string :sujet	
			               t.string :name	Création des différentes colonnes de la table avec le type de variable
			               t.string :message	
			               t.timestamps	
			           end	
			     end	
			end	Ligne généré en auto
				
	« rake db:migrate » Cette commande va générer le fichier schema.rb
	Donne de l'information uniquement. Aucune influence avec les autres fichiers et dossiers (juste une info utilisateur)
				
	Fichier schema.rb	Fichier généré en automatique qui va établir la connexion et les authorisations pour l'accés à la base de donnée.
				
				
Dossier	views	Dossier où va stocker toutes les vues
				
	Fichier index.erb	Le fichier index.erb va nous servir à écrire du html pour l'affichage
		Pour insérer du code ruby dans l'html <% pas de paramètre retourné, affiché, mieux pour du code exécutable if, else, etc. %>		
		ou <%= params[:nom] %> pour retourner des paramètres à app.rb		
				
			<% @article.reverse.each do |articles| %>	
			<div class="cadre">	
			     <h1>Sujet: <%= articles.sujet %></h1>	
			     <h2 class="name">Nom: <%= articles.name %></h2>	
			     <div class="article"><%= articles.message %></div>	
			     <div class="date">posté le: <%= articles.created_at %></div>	
			     <div class="date">édité le: <%= articles.updated_at %></div>	
			     <div class="supprimer">	
			          <form action="/<%= articles.id %>" method= "post">	
			               <input type="submit" value="Supprimer">	
			               <input type="hidden" name="_method" value="delete">	
			          </form>	
			       </div>	
			       <div class="editer">	
			            <form action="/<%= articles.id %>" method= "get">	
			                 <input type="submit" value="Editer">	
			            </form>
			       </div>	
			</div>	
			<% end %>	
				
			<form action="/" method="post" accept-charset="utf-8">	
			     <input type="text" name="articles[sujet]" placeholder="Sujet:">	
			     <input type="text" name="articles[name]" placeholder="Nom:">	
			     <textarea name="articles[message]" placeholder="Votre texte ici:"></textarea>	
			     <input type="submit" value="Poster">	
			</form> 	
				
	Fichier layout.erb	Dans le fichier layout on réalise la mise en page général du site et non pas le contenu 
						qui va changer de page en page,
						on insère <%= yield %> signifie que tout le contenu des autres vues va être affiché à ce moment là.		
						Le layout sert donc de modèle qui va être répété sur toute les pages du site.		
				
			<!DOCTYPE html>	
			<html>	
			     <head>	
			          <meta charset="utf_8">	
			          <link rel="stylesheet" type="text/css" href="style.css">	
			          <title>AppliSinatra: création d'articles, idem BLOG</title>	
			     </head>	
				
			     <body>	
			          <header>BIENVENUE sur ce blog</header>	
			          <%= yield %>	
			     </body>	
			</html>	
				
				
	Fichier edit.erb
			<form action="/<%= @article.id %>" method="post" accept-charset="utf-8">	
			     <input type="text" name="articles[sujet]" value="<%= @article.sujet %>">	
			     <input type="text" name="articles[name]" value="<%= @article.name %>">	
			     <textarea name="articles[message]"><%= @article.message %></textarea>	
			     <input type="submit" value="Editer">	
			     <input type="hidden" name="_method" value="put">	
			</form> 	
				
				
Dossier	public		Dans le dossier public, il sera stocké les images le CSS, JS, etc..
				
					class User	Création d'une class Utilisateur
					     attr_accessor :nom, :email	accesseur d'attribut, permet d'obtenir get et d'assigner set les variables @nom et @email
					     def initialize(attributes = {})	Méthode initialize de ruby avec passage d'attribut appelé à l'exécution du code User.new
					           @nom  = attributes[:nom]	
					           @email = attributes[:email]	
					     end	
					     def formatted_email	Méthode formatted_email de ruby permet de construire l'adresse mail à partir de @nom et @email
					           "#{@nom} <#{@email}>"	
					      end	
					end	

