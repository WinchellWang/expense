# 💳 Guide d'enregistrement automatique des dépenses avec Apple Pay

> Enregistrez les paiements sans contact Apple Pay avec Raccourcis : catégorie fixe, classement dans General à revoir plus tard, ou classification par IA sur l’appareil.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Présentation

Grâce aux automatisations personnelles d'iOS, vous pouvez enregistrer automatiquement vos achats dans **Expense** dès que vous approchez votre iPhone ou Apple Watch pour payer via Apple Pay.

### Avantages de l'automatisation
- ⚡ **Zéro effort** : Dès que votre carte est validée, la dépense est enregistrée en arrière-plan sans aucune action de votre part.
- 🏷️ **Choix du classement** : Associez une catégorie du déclencheur à Expense, utilisez General ou laissez l’IA estimer la catégorie.
- 🏪 **Nom du commerçant inclus** : Le nom de la boutique ou du restaurant est automatiquement ajouté aux notes de la dépense.
- 🔒 **Traitement local** : L’enregistrement classique utilise App Intents sur votre iPhone. Pour l’IA, choisissez On-Device. Aucun accès bancaire n’est nécessaire.

---

## 🛠️ Prérequis

- Un **iPhone** sous iOS 18.0 ou version ultérieure.
- **Apple Pay** configuré avec au moins une carte dans l'application Cartes (Wallet).
- L'application **Expense** installée sur votre iPhone.
- L'application native **Raccourcis**.

---

## 🚀 Raccourci classique : configuration pas à pas

Ce guide prend pour exemple la catégorie **« Alimentation et boissons (Food & Drinks) »** (la procédure est identique pour toutes les autres catégories) :

### Étape 1 : Créer une nouvelle automatisation
1. Ouvrez l'application **Raccourcis** sur votre iPhone.
2. Touchez l'onglet **Automatisation** en bas de l'écran.
3. Touchez le bouton **`+`** en haut à droite.
4. Faites défiler vers le bas et sélectionnez **Transaction** (ou **Cartes** selon les versions d'iOS).

---

### Étape 2 : Configurer le déclencheur
Sur l'écran de configuration du déclencheur :

1. **Carte** : Choisissez **N'importe quelle carte** (ou sélectionnez des cartes spécifiques).
2. **Catégories** :
   - Touchez **Catégories**.
   - Cochez **Alimentation et boissons** (Food & Drinks).
   - Validez en touchant la coche bleue `✓` en haut à droite.
3. **Commerçants** : Laissez sur **Tous les commerçants**.
4. **Mode d'exécution** :
   - Cochez **Exécuter immédiatement** (le bouton passe au **vert**).
   - Désactivez **M'avertir lors de l'exécution** (pour éviter les notifications à chaque paiement).
5. Touchez **Suivant** en haut à droite.

---

### Étape 3 : Créer les actions de l'automatisation
Sélectionnez **Nouvelle automatisation vide**, puis ajoutez les 3 actions suivantes :

#### Action 1 : Extraire la valeur numérique
Apple Pay transmet les montants avec des symboles monétaires (ex. `15,50 €`, `$9.21`). L'extraction de la valeur numérique garantit un enregistrement parfait :
1. Touchez **Ajouter une action**.
2. Recherchez **« Obtenir les nombres du texte »** (ou `Get numbers from`) et sélectionnez-la.
3. Touchez le paramètre d'entrée et choisissez **Entrée de raccourci** (ou `Transaction > Montant`).
   - L'action affiche alors : `Obtenir les nombres de [Montant]`.
   - La variable produite est **`Nombres`** (`# Numbers`).

#### Action 2 : Enregistrer la dépense dans Expense
1. Dans la barre de recherche en bas, tapez **Expense**.
2. Sélectionnez l'action **Add Expense** (Ajouter une dépense).
3. Configurez les trois champs :
   - **Amount (Montant)** : Touchez le champ, puis sélectionnez la variable **`Nombres`** issue de l'action 1.
   - **Category (Catégorie)** : Touchez le champ et sélectionnez **`🍱 Food & Drinks`** (ou Alimentation).
   - **Note** : Touchez le champ, sélectionnez **Entrée de raccourci**, touchez la pastille bleue insérée et choisissez **Commerçant** (`Pay Merchant`).
4. Touchez la flèche `>` de la vignette **Add Expense** pour ouvrir les options avancées :
   - Désactivez **Afficher lors de l'exécution** (Show When Run) pour garantir l'exécution silencieuse en arrière-plan.

#### Action 3 : Arrêter le raccourci proprement
1. Dans la barre de recherche, cherchez et ajoutez **« Arrêter ce raccourci »** (Stop this shortcut).
2. Touchez **OK** en haut à droite pour enregistrer l'automatisation.

---

## 📸 Schéma du flux de travail

Votre automatisation finale se présente ainsi :

![shortcuts](./shortcuts.jpg)

---

## 💡 Recommandation : Configuration multi-catégories

Répétez les étapes pour les catégories disponibles dans le déclencheur. Ce tableau donne des exemples de correspondances, sans couvrir tous les paiements Apple Pay :

| Catégorie du déclencheur | Catégorie Expense correspondante |
| :--- | :--- |
| **Alimentation et boissons** | `🍱 Food & Drinks` |
| **Achats** | `🛍️ Shopping` |
| **Transports** | `🚗 Transportation` |
| **Voyages** | `🏖️ Travel` |
| **Services** | `🛠️ Services` |
| **Divertissement** | `🎠 Entertainment` |
| **Santé** | `💊 Health` |

---

## ⚠️ Limites du raccourci classique et solution General

L’automatisation Transaction d’Apple permet de filtrer par catégorie, mais l’entrée transmise au raccourci **ne contient pas de champ Category**. Un raccourci classique ne peut donc pas lire la catégorie d’origine d’Apple Pay. Cette limite vient de la conception de Raccourcis dans iOS et ne peut pas être corrigée par Expense.

- **Correspondance individuelle** : Sélectionnez une catégorie dans le déclencheur, puis indiquez explicitement la catégorie Expense correspondante dans **Add Expense**. Créez une automatisation par correspondance. Certaines catégories Apple Pay ne figurent pas dans la liste du déclencheur : les paiements qui ne correspondent pas aux catégories sélectionnées ne seront pas enregistrés.
- **Enregistrer toutes les catégories** : Choisissez **Any Category** (toutes les catégories), **Any Card** (n’importe quelle carte) et **Any Merchant** (tous les commerçants), puis fixez **Add Expense → Category** à **General** (général). Cela évite les omissions dues au filtre de catégorie, même sans catégorie correspondante dans la liste. Modifiez ensuite manuellement les catégories dans Expense. Le raccourci ne peut toujours pas identifier la catégorie d’origine.

Utilisez une seule méthode pour les mêmes paiements. Lorsque vous activez **Any Category**, désactivez les automatisations par catégorie qui couvrent ces paiements pour éviter les doublons. « Tous » désigne ici les paiements sans contact Apple Pay transmis par iOS au déclencheur Transaction.

---

## 🤖 Raccourci avec IA : toutes les catégories et classement automatique

> **L’IA comble le manque de classification automatique :** Any Category inclut toutes les catégories, puis le nom du commerçant permet d’estimer le classement. Vous réduisez le tri manuel sans devoir enregistrer systématiquement chaque dépense dans General.

Gardez le déclencheur **Any Category** pour éviter le filtrage, puis laissez Apple Intelligence estimer la catégorie Expense à partir du nom du commerçant. L’IA ne récupère pas le champ Category manquant d’Apple Pay. Dans le flux fourni, le classement a lieu **avant Add Expense**, avec un seul enregistrement par paiement.

### Conditions requises

- **iOS 26 ou ultérieur**, sur un iPhone compatible avec **Apple Intelligence**, activé et disponible dans votre langue et votre région.
- L’action **Utiliser le modèle (Use Model)** de Raccourcis, réglée sur **Sur l’appareil (On-Device)**. Une mise à jour iOS ne suffit pas sur un appareil incompatible. Consultez le [guide de démarrage Apple Intelligence d’Apple](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios).

---

## 📥 Télécharger le raccourci IA

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="Ajouter le raccourci IA" width="64" height="64">
</a>

[Ajouter le raccourci IA](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ Configurer le raccourci IA

1. Ajoutez le raccourci IA partagé depuis la section de téléchargement dédiée ci-dessus.
2. Créez une automatisation **Transaction** avec **Any Card → Any Category → Any Merchant**, activez **Exécuter immédiatement** et désactivez **M’avertir lors de l’exécution**.
3. Exécutez le raccourci importé depuis l’automatisation, en lui transmettant **Transaction / Entrée de raccourci** pour accéder à **Amount** (montant) et **Merchant** (commerçant).
4. Vérifiez que **Use Model** utilise **On-Device** et reçoit le nom du commerçant. Le modèle renvoie un numéro de catégorie ; la branche **If** correspondante exécute **Add Expense** avec le montant extrait, la catégorie associée et le commerçant en note. Vérifiez les catégories de chaque branche dans Expense et désactivez **Afficher lors de l’exécution**.
5. Désactivez les autres automatisations qui enregistrent les mêmes paiements. Vérifiez le montant, la note et la catégorie après le premier paiement.

### Prompt de classification et réglages du modèle

Copiez le prompt anglais ci-dessous dans **Use Model**. À la dernière ligne, remplacez `Transaction (Merchant)` par la véritable variable **Transaction → Merchant** de l’entrée du raccourci, et non du texte littéral. Toutes les versions linguistiques utilisent ce même prompt pour conserver les mêmes numéros de catégorie.

Comme dans la capture, réglez **Model → On-Device**, **Output → Number** (nombre) et désactivez **Follow Up**. Dans les branches If, comparez la **Response** numérique aux valeurs de `1` à `8` ; `8` correspond à General.

```text
You are a transaction classification assistant.

Your task is to classify the given merchant/business name into exactly one of the following 8 categories:

1: Food & Drinks (e.g., restaurants, cafes, bars, supermarkets, food delivery)

2: Shopping (e.g., clothing, electronics, home goods, general retail)

3: Transportation (e.g., public transit, gas stations, ride-hailing/Uber/Lyft, tolls, parking)

4: Travel (e.g., airlines, hotels, Airbnb, car rentals, booking agencies)

5: Services (e.g., utilities, phone bills, insurance, subscriptions, repairs, professional services)

6: Entertainment (e.g., movies, streaming, gaming, concerts, museums, clubs)

7: Health (e.g., pharmacies, doctors, dentists, gyms, wellness)

8: General (other expense that is hard to classify into the above 7 categories)

Rules:
- Output ONLY the single category number (from 1 to 8).
- Do not include any explanations, punctuation, spaces, or extra text.

Here is Merchant Name: Transaction (Merchant)
```

### Flux et limites

La capture a été réalisée sous **iOS 27**, avec les réglages détaillés du modèle ouverts. Les conditions ci-dessus restent **iOS 26 ou ultérieur** sur un appareil compatible.

![Flux du raccourci avec IA](./iOS_27_AI_Shortcuts.jpg)

L’IA estime la catégorie à partir du nom du commerçant et peut se tromper, notamment pour les magasins vendant des produits variés. Vérifiez et corrigez les enregistrements dans Expense si nécessaire. Utilisez **General** en cas d’incertitude. La capture montre des branches numérotées : si vous adaptez le raccourci, dirigez aussi les réponses vides ou inattendues vers General pour éviter qu’une réponse sans correspondance empêche l’enregistrement. Un échec d’exécution du modèle peut encore nécessiter une saisie manuelle.

Le traitement local suppose le choix **On-Device**. Sélectionner Private Cloud Compute ou ChatGPT change le lieu de traitement de la classification.

---

## ❓ Foire aux questions & Résolution des problèmes

### Q1 : Le montant enregistré est vide ou affiche 0.00 ?
**Cause** : Les montants transmis contiennent souvent des symboles de devises (`€`, `$`) qui peuvent bloquer la conversion numérique directe.  
**Solution** : Assurez-vous d'avoir inséré l'action **« Obtenir les nombres du texte »** avant de lier la variable **`# Nombres`** au montant d'Add Expense.

### Q2 : Une boîte de dialogue de confirmation s'affiche à chaque paiement ?
**Solution** :
1. Dans les réglages du déclencheur, vérifiez qu'**Exécuter immédiatement** est bien coché et que **M'avertir lors de l'exécution** est désactivé.
2. Dans les actions, développez l'action `Add Expense` et assurez-vous qu'**Afficher lors de l'exécution** est désactivé.

### Q3 : Puis-je modifier la catégorie ou la note plus tard ?
**Oui !** Toutes les dépenses enregistrées apparaissent instantanément dans l'application Expense. Vous pouvez toucher n'importe quelle entrée pour la modifier à tout moment.

### Q4 : Expense transmet-il mes données bancaires à des serveurs tiers ?
Le raccourci classique enregistre les dépenses localement via App Intents d’iOS. La version IA traite aussi la classification localement si **On-Device** est sélectionné ; Private Cloud Compute et ChatGPT utilisent un traitement distant. La synchronisation et la sauvegarde iCloud facultatives d’Expense sont des réglages distincts.
