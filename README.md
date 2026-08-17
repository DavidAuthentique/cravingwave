# Cravingwave

**L'envie est une vague : elle monte, plafonne, puis retombe. En 10 minutes, tu peux la surfer.**

Cravingwave est un outil de crise pour les personnes en démarche de sobriété, quelle que soit la substance. Quand un craving frappe, l'app guide l'utilisateur pendant 10 minutes, une consigne à la fois : le froid, le mouvement, l'effort, la respiration, puis la connexion avec ses proches via un signal convenu d'avance. La scène de plage vit en temps réel : la marée descend et le soleil se couche pendant que la vague de l'envie retombe.

- **Site cible :** https://cravingwave.app
- **Langues :** français (défaut) et anglais, basculables dans l'app
- **Version actuelle :** 2.0 (visible au bas des Réglages)

## La méthode en trois idées

1. **Une envie intense est une vague.** Elle monte, plafonne et redescend d'elle-même, généralement en 15 à 30 minutes. On ne la combat pas : on la surfe.
2. **Le corps d'abord, la tête ensuite.** Dans la fenêtre de crise, les outils cognitifs ne sont pas fiables. Le protocole est physique : froid, sortie, effort maximal, respiration 4-6 ou 4-8.
3. **La connexion tue la permission.** Le craving attend une permission, et la permission vit dans le secret (« personne ne va le savoir »). Un signal envoyé à ses proches, un seul emoji convenu d'avance, brise le secret en cinq secondes. La honte grandit dans le secret et rétrécit à voix haute.

## Architecture technique

Un **seul fichier HTML autonome** (`cravingwave.html`), sans dépendance externe, sans serveur, sans compte :

- HTML, CSS et JavaScript vanille dans un seul document
- Images (surfeur, palmier, oiseaux, icônes) encodées en base64 dans le fichier
- Fonctionne entièrement hors ligne une fois chargé
- Sauvegarde locale (`localStorage`) : langue, rythme de respiration, contacts, signal, compteur de vagues; aucune donnée ne quitte l'appareil
- Envoi du signal par lien `sms:` de groupe prérempli (1 à 3 numéros); le message part du numéro de l'utilisateur, jamais d'un serveur
- Bilinguisme par dictionnaire JavaScript intégré (`TXT.fr` / `TXT.en`)

## Déploiement sur cravingwave.app

Le fichier étant autonome, l'hébergement est trivial. Trois options gratuites, au choix :

1. **Cloudflare Pages** ou **Netlify** : glisser-déposer un dossier contenant `index.html` (renommer `cravingwave.html`) et `partage.png`, puis pointer le domaine cravingwave.app vers le site dans les réglages DNS.
2. **GitHub Pages** : dépôt public ou privé, activer Pages, ajouter le domaine personnalisé.

Après la mise en ligne, vérifier l'aperçu du lien (image et description de partage) avec l'outil de débogage de partage de Meta, puisque le groupe de soutien vit sur Messenger.

## Ce qui manque pour une mise en marché complète

### Indispensable avant de partager largement

- [ ] **Hébergement sur le domaine** : tant que l'app circule en fichier, chaque mise à jour exige un retéléchargement manuel et la sauvegarde locale est fragile selon la façon d'ouvrir le fichier. L'hébergement règle les deux d'un coup.
- [ ] **Manifest PWA + service worker** : rend l'app réellement installable (icône, plein écran, hors ligne garanti) depuis le navigateur, sans App Store. C'est le chaînon manquant le plus important techniquement.
- [ ] **Page de confidentialité** : une page simple qui dit la vérité, avantageuse ici : aucune donnée collectée, tout reste sur l'appareil. Obligatoire dès qu'on vise le public (Loi 25 au Québec).
- [ ] **Avertissement légal formalisé** : l'app affiche déjà que l'outil ne remplace ni un suivi médical ni une ligne d'aide; une page dédiée (conditions d'utilisation courtes) consolide la protection.
- [ ] **Tests multi-appareils** : iPhone récents et anciens, Android de différentes marques, avec attention au lien SMS de groupe (le séparateur diffère entre plateformes; déjà géré, à valider sur le terrain).

### Fortement recommandé

- [ ] **Icônes maskables et écran de démarrage** (fait partie du manifest PWA)
- [ ] **Retéléchargement des ressources d'aide par région** : le numéro affiché est québécois; une version marché pourrait détecter la langue/région et proposer la bonne ligne d'aide.
- [ ] **Statistiques respectueuses ou aucune** : si mesure il y a, un outil sans témoins ni données personnelles (type Plausible), sinon rien. La promesse « rien ne quitte ton téléphone » est un argument de vente; ne pas la briser.
- [ ] **Accessibilité** : contraste déjà soigné; ajouter la navigation clavier complète et des libellés vocaux sur le cercle de respiration.

### Version 2 (le produit complet)

- [ ] **Comptes et notifications entre proches** : la personne de confiance reçoit une notification et répond en un tap; escalade automatique si personne ne répond en X minutes. C'est la fonctionnalité qui transforme l'outil personnel en filet de sécurité, et elle exige un serveur.
- [ ] **Historique des vagues** : date, intensité avant/après, courbe de progression.
- [ ] **Sons optionnels** : guidage audio de la respiration.

## Modèle de message pour partager le lien

> C'est un outil que j'utilise quand l'envie frappe : 10 minutes guidées, le corps d'abord, pis un signal à envoyer aux proches. Tout reste sur ton téléphone, rien à installer, rien à créer comme compte. Configure ton signal et tes contacts dans les réglages avant d'en avoir besoin. cravingwave.app

## Fichiers du projet

| Fichier | Rôle |
|---|---|
| `cravingwave.html` | L'application complète (à renommer `index.html` pour l'hébergement) |
| `partage.png` | Image d'aperçu quand le lien est partagé (à placer à la racine du site) |
| `README.md` | Ce document |

## Note importante

Cravingwave est un outil d'accompagnement, pas un traitement. Il ne remplace ni un suivi médical, ni un intervenant en dépendance, ni une ligne d'aide. Au Québec : Drogue, aide et référence, 1 800 265-2626, 24 h sur 24.
