##  Détection des menaces de sécurité AWS

 Ce dépôt contient une solution complète pour la détection, l'analyse et la surveillance des menaces de sécurité web à l'aide des services natifs d'AWS. Il fournit des outils permettant de générer et d'analyser les journaux d'accès, de détecter les comportements suspects ou malveillants et de publier des indicateurs et des alertes de sécurité exploitables. 

 # Caractéristiques

*  Génération automatisée de journaux : simulez des journaux de serveur Web réalistes, incluant les activités légitimes et malveillantes, à des fins de test et de validation.
*  Détection et analyse des menaces : Exécutez des requêtes automatisées pour détecter les schémas d’attaques par déni de service distribué (DDoS), les tentatives d’intrusion, l’activité des bots et les accès suspects aux points de terminaison.
*  Métriques et alertes : publie des métriques de sécurité personnalisées sur AWS CloudWatch et envoie des alertes lorsque l’activité suspecte dépasse les seuils définis.
*  Sans serveur et évolutif : utilise AWS Lambda, Amazon S3, Athena et CloudWatch pour une architecture entièrement sans serveur et évolutive.
*  SQL prêt à l'emploi : Inclut des scripts SQL Athena pour l'analyse et le reporting avancés des menaces.

## Architecture du projet

<img width="431" height="304" alt="image" src="https://github.com/user-attachments/assets/a4e158b8-4878-4836-a77b-d77e78922860" />


### Description du flux de données

1. **Bucket Amazon S3 :** Stockage des journaux bruts (*raw-logs*) et des logs traités (*web-logs-analysis*).
2. **Rôle IAM :** Attribution des permissions d'accès au bucket S3 pour la fonction Lambda.
3. **AWS Lambda :** Traitement et mise en forme des logs bruts au format Apache/Nginx.
4. **Requêtes SQL Athena :** L'ingénieur sécurité exécute des requêtes SQL sur Athena pour interroger la base de données de logs.
5. **Résultats d'analyse SQL :** Extraction des analyses (détection de menaces, performances, erreurs 404/505, adresses IP).
6. **Consultation des résultats :** L'ingénieur sécurité consulte directement le résultat des requêtes.
7. **Amazon CloudWatch & Dashboard :** Génération de métriques sur mesure et affichage sur le tableau de bord CloudWatch.


