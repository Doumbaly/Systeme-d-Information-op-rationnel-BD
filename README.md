# Systeme-d-Information-op-rationnel-BD
La gestion du Systeme d'information d'un centre hospitalier
Explication des choix du diagramme de cas

•	Cas et scénarios

•	Transmettre DMA <include> Ressortir DMA: car le patient doit être suivi pendant tout son séjour par son DMA. Ainsi, le DMA doit etre transmis au service compétent dès le debut de son  séjour.
•	Ressortir DMA <include> Controle d'accès : car ressortir le DMA de n'importe quel patient necessite que le système vérifie si celui qui essai d'y avoir accès en à le droit. 
•	Ressortir DMA <extend> Création DMA: car si le patient n’a pas de dossier médical administratif (DMA) , on se doit de le lui en créer. 
•	Premiers soins <extend> Admissions SC : car un patient après être admis aux urgences reçois les premiers soins et au besoin est affecté à un service clinique compétent pour une hospitalisation. 
•	Ressortir DM <include> Controle d'Accès: car l'accès au DM d'un patient necessite que le système vérifie si celui qui essai d'y avoir accès en à le droit. 
•	Ressortir DM <extend> Création DM: car si le patient n’a pas de dossier médical (DM), on se doit de le lui en créer. 
•	Clôture DM <include> Envoi lettre de sortie : car pour clôturer le DM il faut impérativement que le PH référant envoi la lettre de sortie du patient.
•	Confirmation opération <include> réalisation opération : en effet, il est primordial que le système soit alerté. Ainsi, pour confirmer une opération il faut que le personnel qui réalise au préalable l’opération.
•	Réalisation opération <include> scan du bracelet : car en effet, pour réaliser n'importe qu'elle opération il faut que le personnel infirmier puisse identifier le patient à travers la lecture de son bracelet. 
•	Réalisation opération <include> consultations prescription : car il faut impérativement que le personnel infirmier sache ce qu'il doit faire au patient comme intervention mais aussi suivant quel procédure (méthodes, dosage, .....etc)



•	Acteurs 
•	Nous avons décider de regrouper les divers services (urgences, médico-techniques, clinique) en <services> car ils sont tous des services du CH et qu’ils interviennent dans le séjour du patient.
•	Nous avons décidé de regrouper les acteurs tels que praticiens hospitaliers, secrétaires médicales, les infirmiers en <personel> car ce sont tous des membres du personnel de l’hôpital qui interviennent dans le séjour du patient.
•	Les admissions : nous avons gardé cet acteur car il intervient de façon administrative aussi bien dans la création que la clôture du DMA mais aussi dans la clôture du dossier temporaire.
•	Patient: c’est le principal sujet du CH celui dont le séjour ou parcours est scruté par ce système. 

Explication des choix du diagramme de classe

    1-Classe <séjour> pour résumer le parcours (ensemble des consultations, hospitalisations) d’un patient depuis son entrée (date d’entrée), jusqu’à sa sortie (date de sortie) du Centre Hospitalier (CH).  
    2-Classe <personnel> pour résumer l’ensemble des différentes personnes médicales en interaction avec le patient lors de son séjour au CH.   
  3- Classe <services> pour regrouper l’ensemble des différents services offert par le centre hospitalier. 
 4- Classe <patient> pour résumer l’ensemble des informations d’identité et d’identification relatives à un patient. 
 5- Classe <prestation> pour faire cas des différents analyses et test réalisé par les services médico-techniques à la demande du service clinique. 
6- Classe <observation médicale> pour résumer l’ensemble des observations médicales faites par les différents PH sur le patient. 
7-Classe <prescriptions> pour résumer l’ensemble des différentes prescriptions effectué par les PH à faire exécuter par le personnel infirmier. 
8- Classe <opération> pour résumer les informations relatives aux opération (date prévue, date exécution, et la signature du PH ayant réalisé l’opération) subit par le patient lors de son séjour au CH. 
9- Classe<secteur> relatif à la position géographique du patient rattaché à une <spécialité> 
10- Classe <action> relatif à l'action effectué par le personnel du CH sur le patient. Est-ce uniquement une consultation ? une Hospitalisation ou si le patient à été sujet aux deux.  
11-Classe<médecin> relatif au médecin traitant du patient qui peut l’envoyer au CH 
12-Classe <Dossier_patient> regroupe l'ensemble DM et DMA lié au patient 
13-Classe<DM> relatif aux informations médicales relatif à un patient donné relativement à un séjour 
14-Classe<DMA> regroupe l'ensemble des consultations et hospitalisations subit par le patient lors de ces différents séjours mais aussi les informations d'identifications du patient. 
Base SQL Relationnel

•	Triggers et procédures
- Nous avons simplement traduit les méthodes des diagrammes de classe en triggers et procédures.
Nous avons par exemple créer un Trigger qui permet de determiner le nombre de chambre utilisé qui s'actualise à chaque fois après un "after insert"  ou un "after delete" lorsqu'un patient est mis ou sort d'une chambre. 
•	Tables
- table_prescription_personnel est une table de liaison entre table_personnel et table_prescription car un personnel et plus précisement un PH  peut effectuer une ou plusieurs prescriptions et les prescriptions relatif à un client lors de son séjour au CH peut etre effectuer par un ou plusieurs PH
- table_prescription_operation est une table de liaison entre table_operation et table_prescription car une prescription peut etre lié à une ou plusieurs opération sur un patient et une opération peut etre lié à plusieurs prescriptions. 
-table_personnel_operation est une table de liaison entre table_operation et table_personnel car un personnel peut etre lié à une ou plusieurs opération et une opération peut faire intervenir plusieurs personnel

Base SQL Objet-Relationnel

•	Procédures
•	Ce sont les mêmes procédures que la partie relationnelle, adaptées à de l’objet-relationnel
Par exemple nous avons créer une procédure qui permet d 'afficher le DMA, Afficher le nombre de patient, modifier les informations personnel sur le patient.  
