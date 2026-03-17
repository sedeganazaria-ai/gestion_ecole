# Tâches Backend — Gestion École

Document des tâches à réaliser par le **développeur Backend** (Laravel).  
À mettre à jour au fil du projet.

---

## Légende statut

- [ ] À faire
- [x] Fait
- [~] En cours / partiel

---

## 1. Modèles, migrations et rôles

- [ ] **Utilisateurs et rôles** : table `roles`, pivot `user_role` ou champ `role` sur `users`
- [ ] Rôles : `admin`, `directeur`, `censeur`, `secretaire`, `comptable`, `enseignant`, `parent`
- [ ] **Année scolaire** : modèle + migration (début, fin, courante)
- [ ] **Classes, séries, matières** : modèles + migrations + relations
- [ ] **Élèves** : modèle `Student` (ou `Eleve`) lié à `User` si besoin, classe, année
- [ ] **Enseignants** : lien User ↔ matières, affectations aux classes
- [ ] **Frais / tranches** : modèles (FraisScolarite, Tranche, etc.)
- [ ] **Paiements, reçus** : modèles (Payment, Receipt, etc.)
- [ ] **Notes, compositions, bulletins** : modèles (Exam, Grade, Bulletin, etc.)
- [ ] **Emplois du temps** : modèle (Schedule, créneaux, etc.)
- [ ] **Parents** (optionnel) : modèle Parent, lien parent ↔ élèves

---

## 2. Autorisation (Policies / Gates)

- [ ] Politiques par ressource : qui peut créer/modifier/supprimer/voir
- [ ] **Admin** : accès total (Gate ou policy globale)
- [ ] **Directeur** : lecture globale + validation selon règles métier
- [ ] **Censeur** : académie (classes, notes, emplois du temps, bulletins)
- [ ] **Secrétaire** : élèves (inscription, dossiers, cartes, transferts) — pas paiements
- [ ] **Comptable** : paiements, tranches, reçus, rapports financiers
- [ ] **Enseignant** : uniquement ses classes/matières (scope sur les requêtes)
- [ ] **Parent** : uniquement les données de ses enfants (filtrer par parent_id / élèves liés)
- [ ] Middleware ou Inertia shared data pour exposer le rôle et les permissions au front

---

## 3. Administrateur Principal

- [ ] CRUD comptes utilisateurs (secrétaire, comptable, censeur, etc.) + attribution rôles
- [ ] CRUD rôles et permissions (si système de permissions granulaires)
- [ ] Config année scolaire : store/update, définir année courante
- [ ] CRUD classes, séries, matières
- [ ] CRUD paramétrage des frais de scolarité
- [ ] Endpoints ou contrôleurs Inertia pour **statistiques globales**
- [ ] Sauvegardes / paramètres système (si requis : commandes, config)

---

## 4. Directeur

- [ ] Routes et contrôleurs **lecture seule** : stats, rapports financiers, bulletins
- [ ] Endpoints pour **validation** des décisions (ex. valider une décision censeur/comptable)
- [ ] Liste élèves + personnel (avec autorisation Directeur)

---

## 5. Censeur

- [ ] CRUD classes, affectation élèves aux classes
- [ ] Affectation enseignants ↔ matières (et éventuellement classes)
- [ ] CRUD emplois du temps (créneaux, salles, etc.)
- [ ] CRUD examens / compositions
- [ ] Saisie et **validation des notes** (workflow : brouillon → validé)
- [ ] Génération des **bulletins** (calcul des moyennes, PDF ou données pour le front)
- [ ] Contrôle d’accès : uniquement censeur (et admin)

---

## 6. Secrétaire

- [ ] **Inscription élèves** : validation, création élève (+ user si besoin), affectation classe
- [ ] **Mise à jour infos élèves** : autorisation secrétaire, règles de validation
- [ ] **Dossiers scolaires** : stockage pièces (files), association à l’élève
- [ ] **Cartes scolaires** : génération (PDF ou données) + contrôle d’accès
- [ ] **Transferts** : enregistrement entrant/sortant, historique
- [ ] Ne pas exposer les routes/actions de paiement au rôle Secrétaire

---

## 7. Comptable

- [ ] **Enregistrement paiements** : création Payment, lien élève/tranche, montant, type
- [ ] **Tranches** : CRUD ou lecture + calcul des échéances / soldes
- [ ] **Reçus** : génération (numéro, PDF)
- [ ] **Élèves débiteurs** : requête (solde > 0), liste + détail
- [ ] **Rapports financiers** : agrégations (par période, par classe, etc.), export si besoin
- [ ] **Historique des transactions** : liste filtrée, pagination
- [ ] Autorisation : seul Comptable (et Admin/Directeur en lecture si prévu)

---

## 8. Enseignant

- [ ] **Mes classes** : requête filtrée par `user_id` (affectations enseignant)
- [ ] **Saisie des notes** : uniquement pour ses matières/classes (policy + scope)
- [ ] **Liste élèves** : par classe, limitée aux classes de l’enseignant
- [ ] **Emploi du temps** : lecture seule, filtré par enseignant
- [ ] S’assurer qu’aucune donnée d’autres matières/enseignants n’est exposée

---

## 9. Parent (optionnel)

- [ ] Modèle Parent / liaison parent–élève(s)
- [ ] Authentification parent (guard ou rôle)
- [ ] **Notes de l’enfant** : lecture seule, filtrées par élève(s) du parent
- [ ] **Paiements** : lecture seule, pour les élèves liés
- [ ] **Notifications** : table notifications (bulletins, alertes), envoi + liste pour le parent

---

## 10. API / Réponses Inertia

- [ ] Toutes les pages sensibles en **Inertia** avec `middleware(['auth', 'role:...'])` (ou équivalent)
- [ ] Retour des **données structurées** (statistiques, listes, bulletins) pour le front
- [ ] **Validation** : Form Requests pour chaque formulaire important
- [ ] Gestion des **erreurs** (404, 403, 422) et messages cohérents pour le front

---

## 11. Données de test et sécurisation

- [ ] Seeders : rôles, année scolaire, classes, séries, matières, utilisateurs par rôle
- [ ] Données de démo (élèves, notes, paiements) pour tests
- [ ] Pas de fuite de données entre rôles (tests feature par rôle)
- [ ] Sauvegardes (config, commandes) si demandé par le cahier des charges

---

**Dernière mise à jour** : à renseigner par le dev backend.
