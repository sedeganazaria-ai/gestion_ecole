# Tâches Frontend — Gestion École

Document des tâches à réaliser par le **développeur Frontend** (React / Inertia / TypeScript).  
À mettre à jour au fil du projet.

---

## Légende statut

- [ ] À faire
- [x] Fait
- [~] En cours / partiel

---

## 1. Authentification & layout

- [ ] Pages login / logout déjà présentes — adapter si besoin (rôles, redirections)
- [ ] Layout principal avec sidebar/header selon le **rôle** de l’utilisateur
- [ ] Menu de navigation dynamique : afficher uniquement les entrées autorisées pour le rôle
- [ ] Page « Accès refusé » (403) pour les URLs non autorisées
- [ ] Gestion du parent (si implémenté) : espace dédié ou portail parent

---

## 2. Administrateur Principal

- [ ] **Gestion des comptes** : liste, création, modification, suppression (secrétaire, comptable, etc.)
- [ ] **Gestion des rôles et permissions** : interface d’affectation des rôles
- [ ] **Configuration année scolaire** : sélection/création, dates
- [ ] **Paramétrage** : classes, séries, matières (formulaires + listes)
- [ ] **Paramétrage frais de scolarité** : configuration des frais par niveau/classe
- [ ] **Tableau de bord / statistiques globales** : graphiques, KPIs (à connecter aux APIs backend)
- [ ] **Sauvegardes et paramètres système** : page dédiée (si exposée en front)

---

## 3. Directeur

- [ ] **Tableau de bord** : statistiques globales (lecture seule)
- [ ] **Validation** : interfaces pour valider les décisions importantes (selon specs backend)
- [ ] **Rapports financiers** : consultation (lecture seule)
- [ ] **Bulletins** : consultation des bulletins
- [ ] **Listes** : liste complète des étudiants et du personnel (lecture)

---

## 4. Censeur

- [ ] **Gestion des classes** : CRUD classes, affectation élèves
- [ ] **Affectation enseignants aux matières** : interface d’affectation
- [ ] **Emplois du temps** : création / édition / visualisation (grille hebdomadaire)
- [ ] **Examens / compositions** : création, paramétrage, listes
- [ ] **Validation des notes** : workflow de validation (boutons, états)
- [ ] **Génération des bulletins** : déclenchement + prévisualisation / téléchargement

---

## 5. Secrétaire

- [ ] **Inscription des nouveaux élèves** : formulaire complet (infos perso, classe, etc.)
- [ ] **Mise à jour des informations des élèves** : fiche élève, édition
- [ ] **Dossiers scolaires** : consultation / gestion des pièces (si applicable)
- [ ] **Cartes scolaires** : génération / prévisualisation / impression
- [ ] **Transferts** : formulaire et suivi des transferts (entrants / sortants)
- [ ] Pas de gestion des paiements (ne pas afficher les entrées comptables)

---

## 6. Comptable

- [ ] **Enregistrement des paiements** : formulaire (élève, montant, type, tranche)
- [ ] **Tranches de scolarité** : visualisation / gestion des échéances
- [ ] **Génération des reçus** : impression / PDF
- [ ] **Élèves débiteurs** : liste, filtres, détail des dus
- [ ] **Rapports financiers** : tableaux, graphiques (revenus, encaissements, etc.)
- [ ] **Historique des transactions** : liste, recherche, export

---

## 7. Enseignant

- [ ] **Mes classes** : liste des classes assignées
- [ ] **Saisie des notes** : par matière / classe / composition (uniquement ses matières)
- [ ] **Liste de mes élèves** : par classe
- [ ] **Mon emploi du temps** : vue lecture seule
- [ ] Vérifier que seules **ses** matières sont accessibles (contrôle côté front + backend)

---

## 8. Parent (optionnel)

- [ ] **Espace parent** : authentification dédiée (si implémenté)
- [ ] **Notes de l’enfant** : consultation en lecture seule
- [ ] **Paiements** : historique des paiements de l’enfant
- [ ] **Notifications** : bulletins, alertes (liste + détail)

---

## 9. Composants & UX communs

- [ ] Composants réutilisables : tables (tri, pagination), formulaires, filtres
- [ ] Feedback utilisateur : toasts, messages de succès/erreur
- [ ] Responsive : usage correct sur tablette / mobile si requis
- [ ] Accessibilité de base (labels, focus, contrastes)
- [ ] Gestion du chargement (skeletons, spinners) sur les pages lourdes

---

## 10. Intégration avec le backend

- [ ] Utiliser les routes et réponses Inertia fournies par le backend
- [ ] Gérer les erreurs de validation (422) et les afficher dans les formulaires
- [ ] Adapter les vues si les structures de données (props) changent

---

**Dernière mise à jour** : à renseigner par le dev frontend.
