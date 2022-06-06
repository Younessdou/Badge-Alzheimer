# Badge-Alzheimer
Projet électronique du semestre 5
![image](https://user-images.githubusercontent.com/102952196/172234339-7a247ab0-70ba-4eca-8208-53b98c0cd811.png)

# Sommaire 
### Introdcution
### I) Cahier des charges
### II) Gantt et diagramme d'architecture
### III) Choix des composants
##### A) Module GPS
##### B) Module Lora
##### C) Microprocesseur
### IV) Réalisation du PCB
##### A) Choix des pins du microP
##### B) Schématic & board
##### C) Soudage des composants sur la carte
### V) Codage du module GPS 
### VI) LoRa
### VII) Alimentation
### Conclusion

# Remerciement
Nous remercions nos tuteurs durant ce projet mr.Papazoglou et mme.Giannini pour leurs conseils et astuces qui nous ont permis de découvrir de nouvelles choses et acquérir de nouvelles compétences tout en appliquant ce que nous avions vu durant cette année d'étude, et nous tenons aussi à remercier mme.Kittel du bureau technique qui nous a aidé pour notre PCB.
# Introduction
Dans le cadre des projets tutorés du semestre 6, nous avons été amenés à travailler sur la conception d’un badge Alzheimer qu’on a choisi de le nommer «TrackNanny».
TrackNanny est tout simplement un outil de localisation et de prévention, destiné aux personnes atteintes d’Alzheimer ou aux personnes qu’on ne souhaiterait pas perdre à l’extérieur. Ce badge permet d’envoyer une alerte à la personne qui prend en charge l’utilisateur dès que ce dernier dépasse un rayon prédéfini par rapport à un épicentre qui est aussi prédéfini. Ce badge contient aussi un bouton SOS qui permet d’envoyer un autre message d’alerte avec la position exacte de l’utilisateur  si quelqu’un l’a trouvé.
Pour notre projet on a pris l'adresse de l'ENSEA comme épicentre et on a défini un rayon de 700m.       
    <p align="center">
  ![image](https://user-images.githubusercontent.com/102952196/172074814-38775fe0-8dbf-4ab3-8878-b09c5b6b4a9d.png)
### Gantt & diagramme d’architecture
Durant ces 11 séances de projets, nous avons commencé par répartir les tâches entres nous en remplissant notre diagramme de gantt oú on a placé nos missions par ordre de priorité.

 ![Gantt](https://user-images.githubusercontent.com/102952196/172154765-9482008e-096a-402d-be36-c48180985edc.PNG)
Et on a structuré notre projet selon le diagramme d'architecture suivant:
  
  ![image](https://user-images.githubusercontent.com/102952196/172156091-67155b6f-def1-421c-9388-7977e902d51d.png)

# I) Cahier des charges
Pendant la première séance nous avons commencé par établir un cahier des charges sur lequel on s'est basé pour la suite du projet:
    <p align="center">
  ![image](https://user-images.githubusercontent.com/102952196/172075574-5d03239c-d805-4c50-b37f-956eaed6fcdc.png)
      
    Budget: 50€
# III) Choix des composants
### A) Module GPS
      Module GPS : SKU:TEL0132

![image](https://user-images.githubusercontent.com/102952196/172147944-7357abd9-92e7-49d9-a8ec-b08142006ed8.png)

![image](https://user-images.githubusercontent.com/102952196/172147791-6351b35b-64fb-4b0b-8131-e2e65e2c84ce.png)
  
 ### B) Module LORA
   Module LoRa-E5 Grove 113020091\
      
![image](https://user-images.githubusercontent.com/102952196/172148474-36a117b4-fe20-4d85-b3fd-29dd695f7b92.png)
      
On a choisi le module LoRa-E5 Grove 113020091 puisque c'était le moins cher et le plus compacte oar rapport aux autres.
  
 ### C) Microprocesseur
     STM32L412KBT6
![image](https://user-images.githubusercontent.com/102952196/172150014-ca028def-238b-4bf8-8710-70fc0b0e8092.png)
![image](https://user-images.githubusercontent.com/102952196/172150266-ec14c010-cb16-4491-b7c4-82fd3c122440.png)
      
tableau des microprocesseurs proposés:


![image](https://user-images.githubusercontent.com/102952196/172151214-44fe0de1-d569-4e52-a10d-49f4bdb16874.png)


  Au début on avait le choix entre 4 microprocesseurs, et puisqu’on va utiliser 2 UART et 1 GPIO; 1 pour le module GPS et 1 pour le LoRa, donc il nous restait 2 choix et puisque le STM32L021K4T6 n'est pas tounours fiable , on a opté pour le 4ème vu son prix qui est presque la moitié du 3ème et aussi puisqu’il a le même package que les autres donc on aura la possibilité de le changer sur notre PCB et aussi puisqu’il contient que 32 pin et ça reste plus simple et facile à souder et manipuler que celui avec 64 pins.

# IV) Réalisation du PCB
        
 ### A) Choix des pins du microP
Nous avons fait bon usage du Logiciel STM32CubeIDE afin de voir les pins associés à l’UART, leurs numéros ainsi que leurs disposition lors de la création de la carte Pcb.
Après ajout des pins pour notre bouton SOS et RESET, on se retrouve avec une Pin view comme ci-contre :

![image](https://user-images.githubusercontent.com/102952196/172151907-238130cc-69c4-47ab-830a-4e99ce5c4768.png)
- Pin PA2-3 : Module GPS
- Pin PA5 : Bouton SOS
- Pin PA14-15 : RESET 
- Pin PA9-10 : Module LoRaWan   
        
 ### B) Schematic et board
 
 Nous avons commencé par créer notre PCB sur eagle en telechargeant les librairies contenant nos composants, puis on a créé notre schématic qui conteint la partie microP, l'alimentation les connecteurs pour le module GPS et LoRa ainsi que nos deux boutons reset et SOS.
        
 ![image](https://user-images.githubusercontent.com/102952196/172228188-170e0d4e-d2f7-470b-ac41-4c7d0b681883.png)

  À partir de ce schématic on a généré notre board pour relier les composants entre eux en top ou en buttom.
        
 ![image](https://user-images.githubusercontent.com/102952196/172246452-4f0cc083-9cef-4c66-bd3f-23c5b033cdee.png)

   
  Aprés le routage de ce dernier, on a bien respecter notre objectif qui est de réduire l'espace entre les composants et mettre un grand nombre de liaison en top afin d'obtenir une carte adéquate avec la forme de notre badge, ensuite on l'a imprimé et on a soudé les composants dessus à l'aide de mr.Papazouglou et mme.Kittel.
 
 Voici le format final de notre PCB:
        
![image](https://user-images.githubusercontent.com/102952196/172250104-db166c38-a251-456d-bc1c-b1ed38cc40ca.png)
        
        
 # V) Codage du module GPS
 Cette partie a été faite par deux autres étudiants; Alexis Regnault et Valérian PRIOU qui se sont occupés de la partie software de plusieurs projets dont le notre, veuillez trouvez leurs rapport pour notre projet ci-joint avec les fichiers, il est intitulé «Rapport_Alzheimer_PRIOU_REGNAULT.pdf» ainsi que le git du codage du module GPS via le lien ci-dessous.
https://github.com/ValerianPRIOU/Alzheimer
        
 # VI) LoRa or LoRaWAN?
 Cette partie a été géré par deux autres étudiants; Mohamed Amine Bouhyat Oliver BELLIARD ABREU, ils ont aussi travaillé sur la partie LoRawan des autres projets. Veuillez trouver le lien de leurs git ci-dessous.
        
  https://github.com/OliverBELLIARD/LoRaWAN     
             

 # VII) Alimentation:
 Cette partie a été géré par deux étudiantes; Inass Rachidi Manon COTTAR qui s'ocuppaient de l'alimentation de plusuieurs projets en même temps, vous trouverez le liens ci-dessous du travail détaillé qui a été fait en parallèle avec nous.

https://github.com/inassra/batterie

# Conclusion
Pour le moment, nous n'avons toujours pas terminé notre projet, il nous reste dans la partie software l'assemblage du code du module GPS et le module LoRa dans un seul code qui doit être implementer par la suite dans le microprocesseur, lors du test de notre carte on a eu un problème avec le régulateur qui délivre les 5V par contre on obtient bien nos 6V à l'entrée ainsi que nos 3,3V à la sortie de l'autre régulateur. Ce premier projet a été trés intéressant puisqu'on pu mettre à disposition la plupart des connaissances et compétences vu durant cette année. L'idée du projet est trés intéressante et on peut poursuivre le travail sur ce projet aprés en essayant de le compléter et de l'améliorer en modifiant notre cahier des charges et en ajoutant d'autres missions comme un accéleromètre pour detectrer la chutte de l'utilisateur.

