# Tri de CV – Service RH CHIFFON

Outil d’aide au tri de CV pour le service RH de CHIFFON (450 salariés, textile, Auvergne-Rhône-Alpes).
Il compare chaque CV aux fiches de poste et donne pour chacun :

- les **critères éliminatoires** (✓ rempli / ✗ non rempli / ? à vérifier) ;
- les **mots-clés reconnus**, surlignés dans le CV ;
- un **verdict avec pourcentage** : *Entretien conseillé* (≥ 65 %), *À approfondir* (45–64 %), *Non prioritaire* (< 45 % ou critère éliminatoire non rempli) ;
- des **questions d’entretien suggérées**, adaptées aux manques et aux points de vigilance du CV.

L’outil propose, **l’humain décide** : chaque fiche a un champ « Décision RH ».

---

## 1. Mettre l’outil en ligne avec GitHub Pages (10 minutes)

1. Créez un compte sur github.com (gratuit).
2. Cliquez sur **New repository** → nom : `chiffon-tri-cv` → **Private** conseillé → *Create*.
3. Cliquez sur **Add file → Upload files** et déposez `index.html`, `README.md` et `.gitignore` → *Commit changes*.
4. Allez dans **Settings → Pages** → *Source* : `Deploy from a branch` → branche `main`, dossier `/ (root)` → *Save*.
5. Après 1 à 2 minutes, l’adresse du site s’affiche (ex. `https://votre-compte.github.io/chiffon-tri-cv/`).

> GitHub Pages sur un dépôt privé demande une offre payante (GitHub Pro / Team). Avec un compte gratuit, le dépôt doit être public :
> ce n’est pas grave, car **le dépôt ne contient que le code, jamais les CV**.

## 2. Utilisation

| Onglet | Ce qu’on y fait |
|---|---|
| **Classement** | Matrice candidats × postes, puis fiches détaillées (critères, mots-clés, score, questions, décision RH). |
| **Ajouter des CV** | Coller le texte ou importer un `.pdf`, `.docx`, `.txt` (plusieurs à la fois possible). E-mails et téléphones sont masqués. |
| **Postes & critères** | Modifier les fiches : expérience minimum, compétence indispensable, diplôme, mots-clés pondérés, questions. |
| **Conservation (1 an)** | Voir la prochaine suppression, faire une sauvegarde chiffrée, importer, tout effacer. |

Les 15 candidatures de l’annexe 2 sont chargées au premier lancement pour l’exemple.

## 3. Comment le score est calculé

```
Score = mots-clés (60 pts) + expérience (25 pts) + diplôme (15 pts) − 5 pts par point de vigilance
```

- **Mots-clés** : chaque compétence a un poids de 1 à 3 et des synonymes (accents et majuscules ignorés). 55 % du poids total trouvé = 60 pts.
- **Expérience** : années détectées ÷ expérience idéale du poste (plafonné à 25 pts).
- **Diplôme** : niveau atteint = 15 pts ; en cours ou non précisé = 8 pts.
- **Vigilance** (diplôme en cours, projet tourné vers le conseil externe, management directif, etc.) : jamais éliminatoire, mais génère une question d’entretien.

**Règle d’équité** : si une information manque dans le CV, le critère passe en « à vérifier » et n’élimine pas le candidat.
Un CV « Entretien conseillé » avec un critère à vérifier ou 2 vigilances est rétrogradé en « À approfondir ».

### Les 4 fiches de poste fournies

| Poste | Pourquoi chez CHIFFON |
|---|---|
| Chargé(e) SIRH & digitalisation RH | Paie et dossiers sur papier, aucun indicateur RH. |
| Chargé(e) de recrutement & onboarding | 110 000 € de recrutement 2024, surtout via cabinets ; onboarding inexistant. |
| Chargé(e) QVCT & prévention | Obligations QVCT non respectées ; 95 000 € d’avantages sans impact mesuré. |
| Gestionnaire paie & administration | Paie sur supports papier, convention du textile. |

## 4. Conserver les CV 1 an : les options

| Option | Coût | Suppression à 1 an | Pour qui |
|---|---|---|---|
| **A. Navigateur + sauvegarde chiffrée** (intégré) | 0 € | Automatique à chaque ouverture | Test, 1 utilisateur |
| **B. Stockage objet européen** (Scaleway, OVHcloud) | quelques €/mois | Règle de cycle de vie « expirer après 365 jours » | **Équipe RH (recommandé)** |
| **C. Base de données UE** (Supabase région UE + tâche planifiée) | 0 à 25 €/mois | Purge quotidienne programmée | Équipe, avec comptes et journal d’accès |
| **D. ATS / SIRH du marché** | abonnement | Paramètre de l’outil | Cible long terme |

**À ne pas faire** : déposer les CV dans le dépôt GitHub. Git garde tout l’historique : un CV supprimé reste récupérable, et un dépôt public est visible par tous.

### Ce que dit la règle (RGPD / CNIL)

- La CNIL recommande de garder le dossier d’un candidat non retenu **2 ans maximum après le dernier contact**. **1 an** est donc dans les clous.
- Il faut **informer le candidat** (durée de conservation, droits d’accès et d’effacement) : la case à cocher dans « Ajouter des CV » le rappelle.
- Un candidat retenu passe dans le dossier du personnel : supprimez son CV de l’outil après l’embauche.
- Pas de rejet **100 % automatique** (RGPD art. 22) : une personne valide toujours.
- Le tri de CV par IA est classé « haut risque » par le règlement européen sur l’IA (AI Act). Les obligations correspondantes s’appliquent à partir du **2 décembre 2027** (report voté en 2026) : transparence, contrôle humain, absence de biais. Cet outil est conçu pour être explicable : chaque point du score est affiché.

## 5. Pistes d’évolution

- Brancher un modèle d’IA (Claude, Mistral…) pour lire des CV très libres et affiner les questions, en gardant la grille actuelle comme base et la décision humaine.
- Ajouter une grille d’entretien notée (pour comparer les candidats après entretien).
- Suivre les indicateurs : délai de recrutement, coût par recrutement, part des recrutements faits en interne vs cabinets.

## Fichiers

```
index.html   l’outil complet (code + fiches de poste + exemples), aucun serveur nécessaire
README.md    ce document
.gitignore   empêche d’envoyer des sauvegardes de CV sur GitHub par erreur
```
