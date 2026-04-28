# Routage-dynamique-OSPF
<img width="945" height="455" alt="image" src="https://github.com/user-attachments/assets/0d42b7a2-aeb7-444e-a20f-eeab493e891b" />

	Interface	
R1	Gig0/0	10.0.41.253
	Gig0/1	10.0.12.253
	Gig0/2	
R2	Gig0/0	10.0.23.254
	Gig0/1	10.0.12.254
	Gig0/2	
R3	Gig0/0	10.0.23.253
	Gig0/1	10.0.34.253
	Gig0/2	
R4	Gig0/0	10.0.41.254
	Gig0/1	10.0.34.254
	Gig0/2	
Mise en œuvre d'une topologie routée multi-zones (OSPF Area 0/1)

1.	IP fixe pour les serveurs   serveur0  192.168.10.2  ,serveur1 192.168.40.2
2.	Configurer sur les switch les port de vlan et les switchports
3.	Configurer DHCP pools  avec 192.168.XX.1 comme passerelle par défaut, adresses commençant par 192.168.XX.10  (XX signifie  le numéro de VLAN, ex : pour VLAN 10 ,   192.168.10.10 ) 
4.	Configurer des sous-interface en 192.168.XX.1 , et IP de serveur en  IP helper-address
 

Plan d'adressage













Serveur DHCP	Ip helper-address	Nom de VLAN	Gateway	Adresse réseau	Area 

Server0 	
192.168.10.2	Vlan 10	192.168.10.1	192.168.20.0/24	Area 1
		Vlan 30	192.168.30.1	192.168.40.0/24	Area 1
		Vlan 50	192.168.50.1	192.168.60.0/24	Area 1
		Vlan 70	192.168.70.1	192.168.80.0/24	Area 1

Serveur DHCP	Ip helper-address 	Nom de VLAN	Gateway	Adresse réseau	Area

Server1 	
192.168.40.2	Vlan 20	192.168.20.1	192.168.20.0/24	Area 1
		Vlan 40	192.168.40.1	192.168.40.0/24	Area 1
		Vlan 60	192.168.60.1	192.168.60.0/24	Area 1
		Vlan 80	192.168.80.1	192.168.80.0/24	Area 1

	Adresse réseau	
R1 – R2	10.0.12.0/30	
Area 0
R2 – R3	10.0.23.0/30	
R3 – R4	10.0.34.0/30	
R4 – R1	10.0.41.0/30	



Configuration du protocole OSPF sur le routeur4
Router(config)#router ospf 4
Router(config)#network 10.0.41.254  0.0.0.3 area 0
Router(config)#network 10.0.34.254  0.0.0.3 area 0
Router(config)#network 192.168.10.1  0.0.0.255 area 1
Router(config)#network 192.168.20.1  0.0.0.255 area 1


Après la commande show ip route 

 

O IA : Routes apprises via OSPF provenant d'autres zones (Inter-Area)

