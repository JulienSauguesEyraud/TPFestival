**Fonctionnalités** : 
1. Créer, modifier, supprimer et consulter les artistes, les scènes et les concerts.
2. Rechercher des concerts selon plusieurs critères : genre musical, scène, période (avant/après
une date), statut du concert, tarif maximum, et recherche texte libre sur l'artiste ; trier les
résultats (par date, tarif…) dans l'ordre croissant ou décroissant.
3. Vendre un billet pour un concert (avec un acheteur identifié) et vérifier un billet à l'entrée de
la scène (par son code).
4. Prévenir la vente de billets au-delà de la capacité de la scène.
5. Afficher un tableau de bord : recettes par jour et par scène, taux de remplissage, artistes
ayant vendu le plus de billets.

**Fonctionnalités bonus** (rajouter certains champs dans les entités) : 
- Statistiques élaborées par agrégation (recettes par catégorie de billet, âge de la programmation, tendances de vente jour par jour…).
- Gestion fine des « sold out » et de la capacité des scènes.
- Historique des modifications d'un concert, design soigné de l'interface, tests de vos routes, tout raffinement documenté.

**Liste de entités** :
- artiste (id, nom_artiste)
- scène (id, nom_scene, adresse, capacité)
- concert (id, genre_musical, date_début, date_fin, statut, scene_id (référence), artiste_id (référence))
- billet (code, prix, date_achat, consomme, concert_id (référence),  acheteur {nom, prenom, mail})

**Justification référencé/embarqué**
Acheteur est embarqué dans billet car même si un acheteur vient à changer de mail ce n'est pas dérengeant de garder le mail du moment de l'achat
Le reste est référencé car sinon lors d'une modification de l'un d'eux tous les billets associés (et les concerts dans le cas de scène et artiste) devraient être modifiés et cela ferait de nombreuses requêtes 

**contraintes**
- id : type : integer
- nom_artiste : type string
- nom_scene : type string
- adresse : type string
- capacité : type integer / minimum = 1
- genre_musical : type string
- date_début : type string / format : date
- date_fin : type string / format : date
- statut : type string / enum [termine, en_cours, annule, a_venir]
- code : type string avec 12 chiffres entre 0 et 9 / unique
- prix : type number / minimum = 0 / maximum tarif max du concert en code en code
- date_achat : type string / format : date / se remplit automatiquement en code
- consomme : type : boolean
- acheteur : type : object
    - nom : type string
    - prenom : type string
    - mail : type string / format : email


tous les champs en required

**choix des index**
- id pour artiste
- id pour scène
- id pour concert
- code pour billet