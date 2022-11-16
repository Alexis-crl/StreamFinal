# SYMFONY

## NOUVEAU PROJET

- ouvrir un nouveau terminal
- se rendre dans le dosseir où l'on veut créer le projet (ex.: htdocs, www) :
```
cd chemin_vers_le_dossier_htdocs
```
- créer le projet avec composer (pas besoin de créer le dossier du projer) :
```
composer create-project symfony/website-skeleton nom_du_projet
```

## GIT

- créer un dépôt Git sur GitHub
- avec u nterminal, se rendre dans le dossier du projet (cd ... ou VSC)
- initialiser le dépôt local :
```
git init
```
- lier le dépôt local au dépôt distant :
```
git remote add origin https://url_du_depot_github
```
- ajouter tous les fichiers :
```
git add *
```
- donner un messsage au commit :
```
git commit -m "message_du_commit"
```
- récupérer les dernières modifications :
```
git pull origin master
```
- envoyer les modifications :
```
git push origin master
```
- voir la liste des commits :
```
git log
```

## RÉCUPÉRER UN PROJET

- télécharger le zip ou faire un pull
- recréer le fichier .env à la racine du projet (avec ses propres informations)
- les infos importantes sont APP_ENV, APP_SECRET et DATABASE_URL (éventuellement MAILER_URL)
- mettre à jour le projet :
```
composer install (ou composer update)
```
- créer ou mettre à jour la base de données :
```
php bin/console doctrine:migrations:migrate
```

## APACHE-PACK

- barre de débug / routing / .htaccess
```
composer require symfony/apache-pack
```

## CONTROLLER

```
php bin/console make:controller nom_du_controller
```

## BASE DE DONNÉES

- .env :
```
DATABASE_URL="mysql://root:root@127.0.0.1:8889/sublimmo?serverVersion=5.7"
```
- créer la base de données :
```
php bin/console doctrine:database:create
```
- créer (ou modifier) une entité (table) :
```
php bin/console make:entity
```
- migration :
```
php bin/console make:migration
```
```
php bin/console doctrine:migrations:migrate
```

## FIXTURES

- installer le bundle :
```
composer require --dev doctrine/doctrine-fixtures-bundle
```
- compléter le fichier src/DataFixtures/AppFixtures
- persist()
- flush()
- envoyer en base de données (en écrasant) :
```
php bin/console doctrine:fixtures:load
```
- envoyer en base de données (en ajoutant à la suite) :
```
php bin/console doctrine:fixtures:load --append
```
- bundle pour générer de fausses données :
```
composer require fakerphp/faker
```

## FILTRES TWIG

- s'utilisent avec un pipe (|)
- StringExtension :
```
composer require twig/string-extra
```

## EMAIL

- dans les paramètres du compte Google => Sécurité => Connexion à Google : activer la Validation en deux étapes (pour pouvoir accéder aux Mots de passe des applications)
- créer un nouveau mot de passe d'application
- installer SwiftMailer :
```
composer require symfony/swiftmailer-bundle
```
- .env :
```
gmail://username:password@localhost
```
- créer le formulaire de contact
- créer le controller associé
- afficher le formulaire dans une page / vue
- créer le template de mail (contact/emailContact.html.twig)
- voir les mails dans la toolbar (config/packages/dev/web_profiler.yaml) :
```
intercept_redirects: true
```
(un message apparaît ansuite dans la toolbar)
- config/packages/swiftmailer.yaml :
```
swiftmailer:
    delivery_adresses: ['david.hurtrel@gmail.com'] # forcer l'envoi de mail à certaines adresses mail
    disable_delivery: true # désactiver l'envoi de mail
```

## ROUTER

- voir toutes les routes :
```
php bin/console debug:router
```
- vérifier si une route existe (et obtenir ses informations) :
```
php bin/console router:match /url_de_la_route
```

## FORMULAIRE

- créer un formulaire :
```
php bin/console make:form nom_du_formulaire
```
- ajouter un bouton de validation du formulaire (dans le Form) :
```
->add('envoyer', SubmitType::class)
```

## COMMANDES IMPORTANTES

- vider le cache :
```
php bin/console cache:clear
```
