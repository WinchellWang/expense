# 💳 Guide d'enregistrement automatique des dépenses avec Apple Pay

> Suivez automatiquement vos dépenses en temps réel lors de vos paiements avec Apple Pay grâce aux automatisations de l'application Raccourcis iOS. 100 % privé, en local et sans aucune saisie manuelle.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Présentation

Grâce aux automatisations personnelles d'iOS, vous pouvez enregistrer automatiquement vos achats dans **Expense** dès que vous approchez votre iPhone ou Apple Watch pour payer via Apple Pay.

### Avantages de l'automatisation
- ⚡ **Zéro effort** : Dès que votre carte est validée, la dépense est enregistrée en arrière-plan sans aucune action de votre part.
- 🏷️ **Catégorisation intelligente** : Associez les catégories intégrées d'Apple Pay (Alimentation et boissons, Achats, Transports, etc.) directement à vos catégories Expense.
- 🏪 **Nom du commerçant inclus** : Le nom de la boutique ou du restaurant est automatiquement ajouté aux notes de la dépense.
- 🔒 **100 % privé et sécurisé** : Tout fonctionne directement sur votre iPhone. Aucun compte bancaire à connecter, aucun serveur distant, aucune donnée financière ne quitte votre appareil.

---

## 🛠️ Prérequis

- Un **iPhone** sous iOS 17.0 ou version ultérieure (iOS 17.6+ / iOS 18+ recommandé).
- **Apple Pay** configuré avec au moins une carte dans l'application Cartes (Wallet).
- L'application **Expense** installée sur votre iPhone.
- L'application native **Raccourcis**.

---

## 🚀 Guide de configuration pas à pas

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

```text
┌──────────────────────────────────────────────────────────┐
│  Quand une carte est touchée                             │
│  Catégorie : Food & Drinks  |  Commerçants : Tous        │
│  Exécution : Immédiate      |  Notification : Non        │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────┐
│  #  Obtenir les nombres de [Montant]                     │
└────────────────────────────┬─────────────────────────────┘
                             │ (Variable : # Nombres)
                             ▼
┌──────────────────────────────────────────────────────────┐
│  📈 Add Expense (Ajouter une dépense)                    │
│     Montant :   # Nombres                                │
│     Catégorie : 🍱 Food & Drinks                         │
│     Note :      Pay Commerçant                          │
│     Afficher lors de l'exécution : Désactivé             │
└────────────────────────────┬─────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────┐
│  ⏹  Arrêter ce raccourci                                 │
└──────────────────────────────────────────────────────────┘
```

---

## 💡 Recommandation : Configuration multi-catégories

Répétez ces étapes pour créer une automatisation dédiée à chacune de vos dépenses fréquentes :

| Catégorie du déclencheur | Catégorie Expense correspondante | Exemples de dépenses |
| :--- | :--- | :--- |
| **Alimentation et boissons** | `🍱 Food & Drinks` | Restaurants, boulangeries, supermarchés, livraisons |
| **Achats** | `🛍️ Shopping` | Vêtements, magasins de détail, électronique |
| **Transports** | `🚗 Transportation` | Carburant, métro, bus, taxi, parking |
| **Voyages** | `🏖️ Travel` | Billets d'avion, hôtels, billets de train |
| **Services** | `🛠️ Services` | Coiffeur, réparations, pressing |
| **Divertissement** | `🎠 Entertainment` | Cinéma, musées, concerts |
| **Santé** | `💊 Health` | Pharmacie, consultations médicales, fitness |

### 🌟 Automatisation globale de secours
Créez une dernière automatisation avec :
- **Catégorie** : **Toutes les catégories**
- **Catégorie Expense** : **`🏷️ General`**

> Elle servira de filet de sécurité pour enregistrer automatiquement toutes les dépenses non catégorisées !

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
**Non.** Tout fonctionne localement sur votre iPhone grâce au framework App Intents d'Apple. Aucun compte n'est nécessaire et aucune donnée financière ne quitte votre appareil.
