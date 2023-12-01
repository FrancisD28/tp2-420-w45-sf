# tp2-420-w45-sf

SECTION 1:
Étape1 :
  Docker
![image](https://github.com/FrancisD28/tp2-420-w45-sf/assets/122577270/00479872-4988-46d8-a182-c0f3bb1c80f0)

Étape2 : 

la création du réseau virtuel  :  docker network create mon_reseau

la création de vos conteneurs :
  -  docker container run -d -p 80:80 --name conteneur_apache --network mon_reseau httpd:alpine
  -  docker container run -d  --name conteneur_mongodb --network mon_reseau -e MONGO_INITDB_ROOT_USERNAME=adminmongo -e MONGO_INITDB_ROOT_PASSWORD=EncoreUneAutreBD -v $(pwd)/mongodb:/data/db mongo
        
bien reliés au réseau virtuel privé mon_reseau : 
      - docker network inspect mon_reseau

les journaux de apache :

   - docker logs conteneur_apache
