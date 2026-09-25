# Expense 💳

<p align="center">
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="../icon/light_icon.png" width="128" height="128" alt="Expense App Icon" style="border-radius: 28px;" />
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="https://testflight.apple.com/images/testflight-iOS-400x400_1x_40.png" width="48" height="48" alt="Expense App Icon" />
  </a>
</p>

<p align="center">
  <strong>Un gestionnaire de dépenses iOS léger, respectueux de la vie privée et magnifiquement simple.</strong><br>
  100% hors ligne · Zéro pistage · Saisie instantanée · Enregistrement automatique et fluide via Apple Pay
</p>

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.0-F05138.svg?style=flat&logo=swift" alt="Swift 5.0"></a>
  <a href="https://developer.apple.com/ios/"><img src="https://img.shields.io/badge/iOS-18.0+-007AFF.svg?style=flat&logo=apple" alt="iOS 18.0+"></a>
  <a href="https://github.com/WinchellWang/expense/releases"><img src="https://img.shields.io/badge/Taille-<5_Mo-success.svg?style=flat" alt="Taille de l'application"></a>
  <a href="../LICENSE"><img src="https://img.shields.io/badge/Licence-GPL_v3-blue.svg?style=flat" alt="Licence"></a>
</p>

<p align="center">
  <a href="../README.md">English</a> •
  <a href="README.zh-Hans.md">简体中文</a> •
  <a href="README.zh-Hant.md">繁體中文</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.fr.md"><b>Français</b></a> •
  <a href="README.es.md">Español</a>
</p>

---

## ✨ Pourquoi Expense ?

Aujourd'hui, la plupart des applications de suivi des dépenses sont alourdies par des flux sociaux, des publicités de crédits, des synchronisations bancaires complexes, des abonnements onéreux et des traqueurs de données personnelles.

**Expense** revient à l'essentiel : un carnet de dépenses sans distractions, élégant et ultra-rapide qui respecte votre temps et votre vie privée. Pesant **seulement quelques mégaoctets (< 5 Mo)**, Expense est un outil natif pensé selon la philosophie « petit et soigné », entièrement développé en Swift et SwiftUI.

---

## 🌟 Points Forts

### ⚡ Un flux de saisie ultra-rapide et intuitif
- **Saisie en un clic** : Ouvrez l'application, saisissez le montant sur le pavé numérique tactile, sélectionnez une catégorie et c'est enregistré. Aucune boîte de dialogue superflue.
- **Modes de saisie personnalisables** : Choisissez entre le mode décimal libre ou le mode à deux décimales fixes pour une vitesse de saisie maximale.
- **Tri intelligent des catégories** : Les icônes de catégories se réorganisent dynamiquement selon votre fréquence d'utilisation réelle afin de garder vos catégories préférées à portée de doigt.

### 🎨 Catégories entièrement personnalisables
- Créez une arborescence de dépenses qui reflète fidèlement votre mode de vie.
- Personnalisez le nom et choisissez parmi des centaines d'émojis Apple natifs organisés par thème.
- Réorganisez, modifiez ou supprimez n'importe quelle catégorie. Le changement de nom se répercute automatiquement sur l'historique complet de vos dépenses.

### 🍏 Enregistrement automatique sans friction via Apple Pay
- Chaque paiement devient une entrée enregistrée sans aucun effort.
- Conçu autour des **App Intents** et des **Raccourcis Siri** d'iOS.
- Chaque fois que vous payez avec Apple Pay, une automatisation personnelle s'exécute en arrière-plan pour consigner le commerçant, le montant et la date, sans même devoir ouvrir l'application.
- Consultez notre [Guide de configuration d'automatisation](AUTOMATION_GUIDE.fr.md).

### 🔒 Priorité absolue à la vie privée (100% Local)
- **Zéro pistage** : Aucun kit SDK tiers, aucune publicité, aucun outil analytique, aucune création de compte et aucun serveur distant.
- **Stockage en bac à sable local** : Toutes vos données financières résident exclusivement dans l'espace isolé et sécurisé de votre iPhone.

### ☁️ Maîtrise totale de vos données : Sauvegarde iCloud et exports
- **Vous êtes l'unique propriétaire de vos données**.
- **Sauvegarde iCloud sécurisée** : Sauvegardez et synchronisez vos dépenses via votre compte iCloud privé, avec prise en charge de la sauvegarde automatique quotidienne.
- **Exportation en un geste** : Exportez à tout moment vos données au format tableur **CSV** (compatible Excel et Numbers) ou au format **JSON**.
- **Restauration intelligente** : Récupérez vos sauvegardes depuis l'application Fichiers ou iCloud avec déduplication intelligente et fusion des catégories.

### 🪶 Ultra-léger (« Petit et remarquable »)
- Développé purement en SwiftUI natif, sans aucune bibliothèque tierce superflue.
- Le binaire complet fait **moins de 5 Mo**, préservant votre stockage et garantissant un lancement instantané.

---

## 🚀 Compilation et Exécution

### Prérequis
- macOS 15.0+ (Sequoia) avec Xcode 16.0+ installé
- Appareil iOS 18.0+ ou simulateur

### Instructions
1. Cloner le dépôt :
   ```bash
   git clone https://github.com/WinchellWang/expense.git
   cd expense
   ```
2. Ouvrir le projet dans Xcode :
   ```bash
   open Expense.xcodeproj
   ```
3. Sélectionner votre appareil cible et appuyer sur `Cmd + R` pour compiler et exécuter.

---

## 🤖 Guide d'automatisation Apple Pay

Expense prend en charge les actions de raccourcis natives :

1. Ouvrez l'application **Raccourcis** sur votre iPhone.
2. Accédez à l'onglet **Automatisation** et créez une **Automatisation perso**.
3. Choisissez **Transaction** (Apple Pay) comme déclencheur.
4. Ajoutez l'action Expense **« Ajouter une dépense »**, en renseignant le montant et le commerçant.
5. Sélectionnez **Exécuter immédiatement** sans confirmation.

Pour les instructions détaillées avec captures d'écran, veuillez consulter le [Guide d'automatisation](AUTOMATION_GUIDE.fr.md).

---

## 🌐 Langues supportées

Expense s'adapte automatiquement à la langue de votre système :

- 🇺🇸 **English** (Anglais)
- 🇨🇳 **简体中文** (Chinois simplifié)
- 🇭🇰 / 🇹🇼 **繁體中文** (Chinois traditionnel)
- 🇯🇵 **日本語** (Japonais)
- 🇫🇷 **Français**
- 🇪🇸 **Español** (Espagnol)

---

## 📄 Licence

Ce projet est sous licence GNU General Public License v3.0 (GPL v3) - consultez le fichier [LICENSE](../LICENSE) pour plus d'informations.
