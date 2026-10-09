# Amiibo Dock, app Android

## Compiler l'APK avec GitHub (rien à installer)
1. Crée un dépôt GitHub (privé, c'est mieux) et envoie-y tout le contenu de ce dossier,
   y compris le dossier caché `.github`.
2. Onglet **Actions** : la compilation part toute seule (environ 5 minutes).
3. Ouvre la compilation terminée, section **Artifacts**, télécharge `amiibo-dock-apk`.
4. Dézippe, envoie `app-debug.apk` sur ton téléphone et installe-le
   (Android va demander d'autoriser l'installation d'apps inconnues).

## Compiler sur ton PC (Android Studio installé)
    npm install
    npm run build
    npx cap add android
    npx cap sync android
    cd android && gradlew assembleDebug
L'APK sort dans `android/app/build/outputs/apk/debug/app-debug.apk`.

## Utilisation
- Connexion par Bluetooth seulement. Accepte les permissions Bluetooth et position.
  Si Android demande un code d'appairage, celui du Chameleon Ultra est 123456 par défaut.
- Pour garder tes sous-dossiers, zippe ton dossier d'amiibo et choisis le .zip dans l'app.
- La clé retail se charge pareil que sur ordi.
- Barre du bas : ◀ précédent, Nouvel UID, ▶ suivant.
