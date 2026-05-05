## Étape 1 : Configuration de l’environnement

Mettre en place un environnement Android avec Drozer pour l’analyse de la surface d’attaque.

### 1. Lancement de l’émulateur Android

L’émulateur Android a été lancé depuis Android Studio :

<img width="566" height="504" alt="image" src="https://github.com/user-attachments/assets/6feb173a-fb76-44c6-b1e0-a4fc7455e7b1" />

### 2. Installation de Drozer Agent

L’agent Drozer a été installé sur l’émulateur à l’aide de la commande :

<img width="289" height="47" alt="image" src="https://github.com/user-attachments/assets/8dda88f2-5027-4935-b15b-7dd4656ce7f2" />

### 3. Installation de l’application vulnérable

Une application de test volontairement vulnérable a été installée :

<img width="296" height="44" alt="image" src="https://github.com/user-attachments/assets/acb03c32-1ca9-4b63-b81d-d9d3f35723b0" />

### 4. Activation du serveur Drozer

<img width="323" height="439" alt="image" src="https://github.com/user-attachments/assets/e7ccd6d8-7e06-497e-a6f7-09d45adae933" />

<img width="190" height="343" alt="image" src="https://github.com/user-attachments/assets/65912821-3caa-4435-bda1-54e4361f5771" />

### 5. Configuration du port forwarding

Le port forwarding a été configuré pour permettre la communication avec Drozer :

<img width="307" height="31" alt="image" src="https://github.com/user-attachments/assets/d26df198-104b-49a9-8ea8-891b6c85af8e" />

## Étape 2 : Connexion Drozer

### Connexion à la console

<img width="472" height="251" alt="image" src="https://github.com/user-attachments/assets/4fc09b78-df50-404c-bc5e-b1b0e62f3973" />

La connexion avec l’émulateur est établie avec succès.

### Listez les modules disponibles pour vous familiariser avec Drozer :

<img width="824" height="500" alt="image" src="https://github.com/user-attachments/assets/a4adfc6d-3521-43cd-b18f-7177b6d666eb" />

## Étape 3 : Cartographie des composants Android exposés

Identifiez toutes les applications installées sur l'émulateur :
dz> run app.package.list
Localisez l'application vulnérable dans la liste (com.example.vulnerableapp) :
dz> run app.package.list -f vulnerable
Obtenez des informations détaillées sur l'application :
dz> run app.package.info -a com.example.vulnerableapp
Identifiez les activités exportées :
dz> run app.activity.info -a com.example.vulnerableapp
Identifiez les services exportés :
dz> run app.service.info -a com.example.vulnerableapp
Identifiez les broadcast receivers exportés :
dz> run app.broadcast.info -a com.example.vulnerableapp
Identifiez les content providers exportés :
dz> run app.provider.info -a com.example.vulnerableapp
Créez un tableau récapitulatif des composants exposés :
<col><col><col><col>
Type de composant
Nom
Exporté
Protection
Activity
LoginActivity
Oui
Aucune
Activity
UserProfileActivity
Oui
Permission
Service
DataSyncService
Oui
Aucune
Receiver
BootReceiver
Oui
Aucune
Provider
UserDataProvider
Oui
Lecture/Écriture
