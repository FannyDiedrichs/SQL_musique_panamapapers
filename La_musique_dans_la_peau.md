##  Récupérer tous les albums

SELECT Title FROM albums;

## Récupérer tous les albums dont le titre contient "Great"

SELECT * FROM albums WHERE Title LIKE "%Great %";

## Donner le nombre total d'albums contenus dans la base (sans regarder les id bien sûr)

SELECT COUNT(Title) FROM albums;

## Supprimer tous les albums dont le nom contient "music"

# 🤷‍♀️

## Récupérer tous les albums écrits par AC/DC

SELECT * FROM albums, artists WHERE albums.ArtistId = artists.ArtistId AND Name LIKE "%AC/DC%";

## Récupérer tous les titres des albums de AC/DC

SELECT tracks.Name, Title
FROM artists
INNER JOIN albums
ON albums.ArtistId = artists.ArtistId
INNER JOIN tracks
ON tracks.AlbumId = albums.AlbumId
WHERE artists.Name LIKE "%AC/DC%";

## Récupérer la liste des titres de l'album "Let There Be Rock"

SELECT Title, Name FROM albums, tracks WHERE albums.AlbumId = tracks.AlbumId AND Title LIKE "Let There Be Rock";

## Afficher le prix de cet album ainsi que sa durée totale

### Prix

SELECT SUM(UnitPrice) FROM albums, tracks WHERE albums.AlbumId = tracks.AlbumId AND Title LIKE "Let There Be Rock";

### Durée totale

SELECT SUM(Milliseconds) FROM albums, tracks WHERE albums.AlbumId = tracks.AlbumId AND Title LIKE "Let There Be Rock";

## Afficher le coût de l'intégralité de la discographie de "Deep Purple"

SELECT SUM(UnitPrice)
FROM artists
INNER JOIN albums
ON albums.ArtistId = artists.ArtistId
INNER JOIN tracks
ON tracks.AlbumId = albums.AlbumId
WHERE artists.Name LIKE "%Deep Purple%";

## Créer l'album de ton artiste favori en base, en renseignant correctement les trois tables albums, artists et tracks

Artists :
INSERT INTO artists (ArtistId, Name)
VALUES (2222, "Kids United")

Album :
INSERT INTO albums (AlbumId, Title, ArtistId)
VALUES (1111, "Un monde meilleur", 2222)

Tracks :
INSERT INTO tracks (TrackId, Name, AlbumId, MediaTypeId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
VALUES (1112, "On écrit sur les murs", 1111, 12345, 12345, "Alphonse", 1233, 12, 0.99)
--->Error while executing SQL query on database 'chinook': UNIQUE constraint failed: tracks.TrackId


```python

```
