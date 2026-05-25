# Pointeuse — Guide d'installation et d'utilisation

## 📱 Installation sur votre téléphone

### Étape 1 — Héberger l'application

L'application doit être accessible via une URL `https://` pour fonctionner en mode PWA.

**Option A — GitHub Pages (gratuit, recommandé)**
1. Créez un compte sur https://github.com si vous n'en avez pas
2. Créez un nouveau dépôt public (ex : `pointeuse`)
3. Téléversez tous les fichiers de ce dossier dans le dépôt
4. Allez dans *Settings → Pages → Source* : sélectionnez `main` / `root`
5. Votre URL sera : `https://VOTRE-NOM.github.io/pointeuse/`

**Option B — Serveur local (réseau domestique)**
Si vous avez un NAS ou un serveur local :
```
# Python (si installé)
cd /chemin/vers/pointeuse
python3 -m http.server 8080
```
Accédez via `http://IP-DU-SERVEUR:8080`  
⚠️ Sans HTTPS, le service worker (mode hors-ligne) ne fonctionnera pas.

---

### Étape 2 — Ajouter à l'écran d'accueil

**Sur iPhone (Safari)**
1. Ouvrez l'URL dans Safari
2. Tapez l'icône de partage (carré avec flèche ↑)
3. Choisissez **« Sur l'écran d'accueil »**
4. Donnez le nom `Pointeuse` et appuyez sur **Ajouter**

**Sur Android (Chrome)**
1. Ouvrez l'URL dans Chrome
2. Tapez les ⋮ (trois points) en haut à droite
3. Choisissez **« Ajouter à l'écran d'accueil »** ou **« Installer »**
4. Appuyez sur **Installer**

L'application s'ouvre désormais en plein écran comme une app native.

---

## ☁️ Connexion OneDrive (optionnel)

La synchronisation OneDrive nécessite la création d'une **application Azure gratuite**.

### Créer l'application Azure (5 minutes)

1. Rendez-vous sur https://portal.azure.com (connectez-vous avec votre compte Microsoft)
2. Cherchez **« Azure Active Directory »** ou **« Microsoft Entra ID »**
3. Cliquez sur **« Inscriptions d'applications »** → **« Nouvelle inscription »**
4. Remplissez :
   - **Nom** : `Pointeuse`
   - **Types de comptes pris en charge** : *Comptes dans un annuaire organisationnel et comptes personnels Microsoft*
   - **URI de redirection** : sélectionnez `SPA (application monopage)` et entrez votre URL (ex : `https://VOTRE-NOM.github.io/pointeuse/index.html`)
5. Cliquez **S'inscrire**
6. Copiez l'**ID d'application (client)** — c'est une chaîne de type `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`

### Configurer dans l'application

1. Ouvrez l'onglet **Réglages**
2. Dans la section **OneDrive**, collez votre **Client ID** dans le champ prévu
3. Cliquez **Connecter OneDrive**
4. Connectez-vous avec votre compte Microsoft dans la fenêtre qui s'ouvre
5. L'application est maintenant liée à OneDrive

Le fichier `pointeuse_data.json` sera créé à la racine de votre OneDrive.  
La synchronisation se fait automatiquement à chaque badgeage.

---

## 🔧 Utilisation

### Badgeage
- **Arrivée** → en arrivant le matin
- **Début pause** → en quittant pour déjeuner
- **Fin pause** → en revenant du déjeuner
- **Départ** → en quittant le soir

Les boutons se débloquent dans l'ordre. Une alerte apparaît si vous sortez des plages horaires ou si la pause est trop courte.

### Historique
Consultez vos heures par **semaine**, **mois** ou **année**.  
Le bilan affiche le total travaillé et le cumul des heures supplémentaires/déficitaires.

### Absences
Enregistrez vos **CP, RTT, maladies, formations**…  
Les jours d'absence sont exclus du calcul des heures supplémentaires.

### Réglages
- **Planning hebdomadaire** : modifiez les horaires et activer/désactiver chaque jour
- **Plages horaires** : personnalisez les alertes d'arrivée/départ
- **Jours fériés** : affichés automatiquement pour l'année en cours (France)
- **Données** : export CSV (Excel), export/import JSON, réinitialisation

---

## 📂 Structure des fichiers

```
pointeuse/
├── index.html      ← Application principale
├── manifest.json   ← Manifest PWA
├── sw.js           ← Service Worker (mode hors-ligne)
├── icon-192.png    ← Icône 192×192
├── icon-512.png    ← Icône 512×512
├── icon-apple.png  ← Icône Apple Touch (180×180)
└── README.md       ← Ce fichier
```

---

## 🔄 Sauvegarde sans OneDrive

Sans OneDrive, utilisez l'export/import manuel :
1. **Réglages → Exporter JSON** → sauvegardez le fichier dans votre OneDrive manuellement
2. Pour restaurer : **Réglages → Importer JSON**

---

*Version 2.0 — Contrat 39 h/semaine — France*
