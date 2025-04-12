<h3 style="color:#93c6c3">Begreper og oppgaver</h3>
- Link state    
- Distance vector   
- ICMP   
	- Hva brukes ICMP til?   
		- Diagnostisere nettverksproblemer
	- Hvordan fraktes ICMP?   
		- Direkte inne i IP pakker
- Traceroute   
	- Hvordan fungerer traceroute?
		- Sender pakker med økende TTL verdier. Når en TTL går ut sender ruteren beskjed tilbake til hosten. På denne måten kartlegger man alle ruterne/switchene på veien. 
	- Hva er forskjellen på ping og traceroute?
	    - Begge brukes **ICMP echo request**
	    - Ping brukes for å finne ut om en host er mulig å nå og om vi har pakketap på veien
	    - Traceroute brukes for å finne alle ruterne på veien og i tilfellet at vi ikke kan nå destinasjonen kan vi finne ut hvor feilen ligger



<h3 style="color:#F4B9B2">Relasjoner mellom begreper</h3>
- Hva er forskjellen på Link State og Distance Vector?   
	- Link State har kunnskap om hele nettet, mens Distance Vector kun har kunnskap om naboene
- Hvilken av Link State og Distance Vector er best?     
	- Generelt kan vi si at for større nettverk er link-state bedre fordi vi kan bestemme effektiv ruting. For mindre nettverk er distance-vector best fordi link-state krever mye minne for å ta vare på informasjon om alle andre rutere og det trengs ikke i mindre nettverk
	- I større nettverk er det mye å hente på å finne en effektiv rute frem til målet. Link state lønner seg derfor. I mindre nettverk er det ikke så mye å hente og å holde oversikt over alle ruter vil derfor ta unødvendig mye plass
