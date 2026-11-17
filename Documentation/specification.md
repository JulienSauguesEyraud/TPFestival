# CreateArtist

### 1. Informations générales

- **Méthode HTTP :** POST
- **URL :** `/api/artists`
- **Description :** Permet de créer un artiste 

### 2. Paramètres

**Paramètres URL :** aucun

**Paramètres Query :** aucun

### 3. Corps de la requête

Format JSON :

```json
{
  "nom_artiste": "Hakai"
}
```

| Champ | Type | Obligatoire | 
|---|---|---|
| nom_artiste | string | oui |

### 4. Réponse en cas de succès

- **Code HTTP :** 200 / 201 / 204
- **Description :** L'artiste a été créé avec succès.

Exemple JSON :

```json
{
  "type": "artiste",
  "id": 1,
  "nom_artiste": "Hakai"
}
```

### 5. Réponses en cas d'erreur

| Code HTTP | Signification | Cas |
|---|---|---|
| 400 | Bad Request | Nom d'artiste manquant ou invalide |
| 409 | Conflict | Identifiant déjà utilisé |
| 500 | Internal Server Error | Erreur interne du serveur |

### 6. Règles de gestion

- Le nom de l'artiste est obligatoire.
- L'identifiant est généré automatiquement.
- Le champ type est automatiquement défini à artiste.
- L'artiste est enregistré dans la collection festival.
- Tous les champs obligatoires doivent être renseignés.