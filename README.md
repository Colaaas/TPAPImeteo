## Technologies utilisées  
Les principales dépendances ajoutées au projet :  
1. **Spring Web** : Permet de développer des applications web (RESTful API et front-end).  
2. **Spring Data JPA** : Facilite l'accès et la manipulation des bases de données en utilisant JPA.  
3. **Hibernate** : Implémentation de JPA pour gérer les entités et les bases de données.  
4. **H2 Database** : Base de données légère et en mémoire pour le développement et les tests.  
5. **Spring Boot DevTools** : Outils pour améliorer l'expérience de développement (rechargement automatique, etc.).  
6. **Thymeleaf** : Moteur de template pour créer des pages HTML dynamiques.  

## Reponses aux questions:

**1. Avec quelle partie du code avons-nous paramétré l'url d'appel /greeting ?**  

   @GetMapping("/greeting")  
   public String greeting(@RequestParam(name="nameGET", required=false, defaultValue="World") String  
   nameGET, Model model) {  
   model.addAttribute("nomTemplate", nameGET);  
   return "greeting";  
   }  

**2. Avec quelle partie du code avons-nous choisi le fichier HTML à afficher ?**  

Le fichier HTML à afficher est choisi par :  
return "greeting";  
Cela correspond au fichier greeting.html situé dans le dossier templates.  

**3. Comment envoyons-nous le nom à qui nous disons bonjour avec le second lien ?**  

Le nom est envoyé via le paramètre de requête nameGET dans l'URL   
Ce paramètre est capturé par @RequestParam   
Ensuite, il est ajouté au modèle    
Ce modèle est utilisé dans le fichier greeting.html pour afficher le message avec la variable ${nomTemplate}. 

**Avez- vous remarqué une différence ?**  
la table ADDRESS est apparue


**Expliquez l'apparition de la nouvelle table en vous aidant de vos cours sur Hibernate, et de la
dépendance Hibernate de Spring.**  
La classe `Address` est une entité JPA, mappée à une table `address` dans la base de données grâce à Hibernate.

**@Entity** indique à Hibernate que cette classe est une entité à persister.  
**@Id** marque le champ `id` comme clé primaire.  
**@GeneratedValue** permet de générer automatiquement l'ID.  
Spring, avec Spring Data JPA et Hibernate, gère automatiquement la création de la table `address` lors du démarrage.  
Une fois la table créée, Spring permet de manipuler les entités via des repositories, et la page web peut afficher les données de la table via les services.  

**Voyez-vous tout le contenu de data.sql**  
Non je n'ai pas réussi à afficher tout le contenu, je n'ai pas trouvé de solution

**A quoi sert l'annotation @Autowired**  
**@Autowired** sert à injecter automatiquement des dépendances dans les classes gérées par Spring  

**Expliquez la méthode que vous avez utilisé pour ajouter Bootstrap dans le README.**  
Pour ajouter Bootstrap à mon projet, j'ai utilisé une CDN (Content Delivery Network).  
J'ai mis le lien vers le fichier CSS de Bootstrap dans la balise <head> de mes pages HTML pour appliquer les styles.
J'ai également ajouté le lien vers le fichier JavaScript de Bootstrap juste avant la fin de la balise <body> pour activer les fonctionnalités interactives  

**Faut-il une clé API pour appeler MeteoConcept ?**  
Oui, on a besoin d'une clé pour appeler l'API MeteoConcept.  

**Quelle URL appeler ?**  
https://api.meteo-concept.com/api/forecast/daily?lat={latitude}&lon={longitude}&token={e16392e61525ffa8ad06914e1fc2efc0df44e341da46af29dc60bbaf9aa43b64}  

**Quelle méthode HTTP utiliser ?**  
Méthode HTTP GET  

**Comment passer les paramètres d'appels ?**  
Les paramètres lat, lon  et token sont passés par l'URL.  

**Où est l'information dont j'ai besoin dans la réponse :**  

**Pour afficher la température du lieu visé par les coordonnées GPS :**  
Dans le champ temperatureMin et temperatureMax dans la réponse JSON  

**Pour afficher la prévision de météo du lieu visé par les coordonnées GPS :**  
Dans le champ description de l'objet de prévision correspondant à la date demandée  
