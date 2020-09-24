# WEB3.0_TP05 - Web sémantique et données interconnectées (Linked Data)

### ANTELME Mathis

## Le format **RDFa**
Comme nous l'avons vu en cours, le format **RDFa** permet d'insérer des triplets **RDF** au sein d'un code **HTML** sans devoir saisir plusieurs fois les mêmes informations.

Observer le code source de la page https://www.w3.org/ns/entailment/data/RDFS.html et identifiez les annotations **RDFa**.
En utilisant l'outil `RDFa Play` découvrez les triplets **RDF** présents dans la page en sélectionnant l'onglet Raw Data.

L'exemple précédent a été réalisé à titre d'exemple mais beaucoup de sites commerciaux commencent à utiliser le format **RDFa**. Vous pouvez réaliser la même opération avec les pages suivantes (en copiant collant le code source de la page) :

- https://www.walmart.com/ip/Lenovo-ideapad-S145-15-6-Laptop-Intel-Core-i3-1005G1-Dual-Core-Processor-4GB-Memory-128GB-Solid-State-Drive-Windows-10-Dark-Orchid-81W800K3US-Google-/497938228?findingMethod=wpa
- https://www.yelp.com/biz/fog-harbor-fish-house-san-francisco-2?osq=Restaurants
- http://www.rottentomatoes.com/m/interstellar_2014/

Maintenant nous allons créer un fichier HTML avec des annotations **RDFa**.

Pour cela nous allons d'abord créer des données RDF décrivant votre profil en utilisant l'outil FOAF-a-matic.
Les données RDF produites seront insérées dans une page HTML sous la forme d'annotations RDFa.
Vous vérifierez avec l'outil `RDFa Play` que les triplets **RDF** originaux se retrouvent bien dans la page **HTML**.

---

## Création de données interconnectées

*Dans cet exercice nous allons voir qu'à l'aide d'un outil adapté, il est relativement aisé d'enrichir des données au format **CSV** pour produire un graphe **RDF** sans nécessairement passer par l'écriture d'un programme de traitement.*

- Installer l'outil `LODRefine`
- Récuperer sur le site OpenData de La Rochelle le fichier décrivant les événements à venir au format **CSV**.
- Puis configurez l'extension **RDF** de `LODRefine` (en haut à droite) en définissant un modèle de graphe **RDF** (menu `Edit RDF skeleton`) pour pouvoir produire (menu Export en haut également à droite) un graphe **RDF** de la forme suivante (format **RDF**/**XML**) :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rdf:RDF
    xmlns:schema="http://schema.org/"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns:owl="http://www.w3.org/2002/07/owl#"
    xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#">

<rdf:Description rdf:about="https://opendata.larochelle.fr/0">
    <rdf:type rdf:resource="http://schema.org/Event"/>
    <schema:identifier>25444</schema:identifier>
    <schema:startDate>06-09-2018</schema:startDate>
    <schema:endDate>06-09-2018</schema:endDate>
    <schema:description>▬ Le Service Civique Dating, késako ? C'est l'opportunité de : - rencontrer des organismes d'accueil de volontaires - d'échanger sur les missions qu'ils proposent (environnement, culture, loisirs, sport, solidarité, éducation pour tous ...). - de passer un entretien en direct ou par Skype ‼ ▬ "Mais... le service civique, c'est quoi ?" Pour répondre à toutes vos questions, RDV le 04 septembre, à la Belle du Gabut, de 14h00 à 16h00 (+ possibilité de faire des simulations d'entretiens pour vous préparer au mieux le jour J !) + d'infos: cdij17@yahoo.fr // 05.46.41.16.36 12 rue Fleuriau - La Rochelle Lieu : La Belle du Gabut Site internet : http://www.infojeunesse17.com</schema:description>
</rdf:Description>

<rdf:Description rdf:about="https://opendata.larochelle.fr/1">
    <rdf:type rdf:resource="http://schema.org/Event"/>
    <schema:identifier>25443</schema:identifier>
    <schema:startDate>10-09-2018</schema:startDate>
    <schema:endDate>16-09-2018</schema:endDate>
    <schema:description>Une semaine consacrée aux sports féminins avec des animations sportives de découverte gratuites pour les femmes dans tous les quartiers de la Ville. INFORMATIONS PRATIQUESToutes les activités sont réservées aux féminines de + de 16 ans sauf le skateboard à partir de 8 ans.Respecter les horaires de l’emploi du temps.Savoir nager pour les activités aquatiques .À NE PAS OUBLIERVenir en tenue de sport.Prévoir sa bouteille d’eau et une tenue de rechangeTÉLÉCHARGEZ LE PROGRAMME</schema:description>
</rdf:Description>
```

### Quelques conseils:

Le vocabulaire de Schema.org n'est pas présent par défaut, il faut l'installer lorsqu'on définit le squelette **RDF** (**RDF** skeleton).
La description de l'évenement nécessite quelques traitements comme l'élimination des balises **HTML** et des espaces (cf. documentation de l'outil).

---

### ANTELME Mathis