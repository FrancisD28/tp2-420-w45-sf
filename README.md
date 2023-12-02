# tp2-420-w45-sf

Date: 02/12/23

# SECTION 1 - Étape1 :


  ## Vérification docker

  
![image](https://github.com/FrancisD28/tp2-420-w45-sf/assets/122577270/00479872-4988-46d8-a182-c0f3bb1c80f0)



# Étape2 : 
## commade utilisé :

la création du réseau virtuel  :  
  - docker network create mon_reseau

la création de vos conteneurs :
  -  docker container run -d -p 80:80 --name conteneur_apache --network mon_reseau httpd:alpine
  -  docker container run -d  --name conteneur_mongodb --network mon_reseau -e MONGO_INITDB_ROOT_USERNAME=adminmongo -e MONGO_INITDB_ROOT_PASSWORD=EncoreUneAutreBD -v $(pwd)/mongodb:/data/db mongo
        
bien reliés au réseau virtuel privé mon_reseau :
  - docker network inspect mon_reseau
      
             "Containers": {
            "436156d4bc1de38bdf561a9a5c42f630ffe038921b9945c436e3a71d07dff4cc": {
                "Name": "conteneur_apache",
                "EndpointID": "15a30fae75c186637e5a2cd0f06b1c41ba3d2848851fe4da914ca330d269f80c",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
            "b8241f3d0f9da6ae180bf9fa4b5032a9d0e544e2eb7c5d876f96bf7fc8b93a03": {
                "Name": "conteneur_mongodb",
                "EndpointID": "885caba8ba12168a854f4f37c9277964d1d950622ccea1a35581804fc3e9c303",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            }

les journaux de apache :

   - docker logs conteneur_apache
     
[Fri Dec 01 20:23:00.490068 2023] [mpm_event:notice] [pid 1:tid 139821476100936] AH00489: Apache/2.4.58 (Unix) configured -- resuming normal operations
[Fri Dec 01 20:23:00.490282 2023] [core:notice] [pid 1:tid 139821476100936] AH00094: Command line: 'httpd -D FOREGROUND'
