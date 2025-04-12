
<h3 style="color:#7190c9">Begreper</h3>
- CBR og VBR   
	- Hva er bitrate?   
		- Hvor mye data som blir overført hvert sekund
	- Hva er forskjellen på CBR og VBR?   
		- I CBR blir overført data sendt med konstant hastighet. Vi får altså like mye data per sekund hvert sekund. I VBR blir data sendt med varierende hastighet. 
		- I VBR kan vi altså ha en film med ulike scener der noen scener blir sendt med veldig høy kvalitet, mens andre scener har lavere kvalitet. Dette optimerer båndbredden da vi hele tiden ser hvor mye som kan sendes
		- CBR er bedre for live-streaming eller konferanser som krever en konstant strøm av data. VBR er bedre for fleksibilitet og optimal bruk av båndbredde. Gjerne for filmer der innholdet varierer i kompleksitet
- Jitter   
	- Hva er jitter og hvordan løses dette   
		- Jitter er at det oppstår en **variasjon** i delay mellom når bits sendes fra en server og når de mottas hos en klient. Løses med buffer på klientsiden
	- Hvordan løses jitter   
		- Buffer 
- VoIP   
	- Hva er det? 
		- Teknologien som muliggjør å sanntidsoverføre lyd og bilde over internett
	- Hvordan fungerer lydoverføring?   
		- Pakker genereres bare når man snakker. De sendes ned i sockets hver 20 ms. Vi tolererer tap på mellom 1-10%. Vi har jitter som ved video. Løses med buffer med **q-verdi**
	- Hvordan fungerer **q** verdien i avspilling?   
		- Mottaker prøver å spille av pakke akkurat tid **q** etter at den ble opprettet. Dersom klippet ikke blir mottatt før **q** kastes det. 
		- **Q** velges. Dersom den er for stor gir det dårlig opplevelse. Dersom den er for liten kan det føre til at mange klipp ikke blir spilt
	- Hvordan håndteres pakketap?   
		- Interleaving og Forward error correction
- Forward error correction   
	- Hva er det?   
		- Sender med ekstra informasjon slik at man kan rekonstruere tapte pakker uten at pakker må sendes på nytt
	- To måter? 
		- Etter at n pakker har blitt sendt sender man med en ekstra pakke som lages ved å utføre XOR på de originale pakkene. Dersom en av de n pakkene går tapt kan man rekonstruere hele den tapte pakken
		- For hver pakke som sendes sendes det med en kopi av en tidligere pakke som er kodet med en lavere bitrate. På denne måten vil man kunne unngå å sende pakken på nytt
- Interleaving   
	- Hva er interleaving?   
		- ![[Pasted image 20240427200453.png|400]]
		- De originale pakkene brytes opp i mindre biter og sendes i en annen sammensetning. Deretter settes de sammen igjen hos mottaker. Dette gjør at hvert pakketap merkes mindre da man kun mister en liten del av pakken, men det øker buffer som trengs for avspillingen
- RTP    
	- Hva er det?   
		- Real-time Protocol (RTP) er en protokoll som brukes for overføring av lyd- og video-streams
	- Hvilke headerfelt er spesielt for RTP?    
		- Payload type - Hvilken type enkoding - klient kan endre dette i løpet av sesjonen 
		- Sekvensnummer - for å detektere pakketap
		- Tidspunkt - sikre at pakkene blir spilt av i riktig rekkefølge. Dette hjelper også med synkronisere lyd og bilde ved live overføring
		- SSRC - skille mellom lyd/bilde fra forskjellige kilder (f.eks i en videokonferanse der flere snakker samtidig) slik at man kan spille de av på riktig måte


<h3 style="color:#F4B9B2">Relasjoner</h3>
- Hva er relasjonen mellom VoIP og RTP?   
	- RTP er protokollen som brukes dersom en applikasjon trenger sanntidsoverføring av data f.eks VoIP
- Hva brukes FEC og Interleaving til?   
	- Begrense pakketap i VoIP. Rette opp feil uten at man må sende pakker på nytt
- Hva er forskjellen på FEC og Interleaving?   
	- FEC er å legge til ekstra (unødvendig) informasjon slik at dersom det skjer et pakketap vil man kunne klare å bruke noe av den ekstra informasjonen til å rekonstruere de tapte pakkene. Dette øker størrelsen på pakkene som må sendes. 
	- Interleaving er å dele opp pakkene og sende de på en sammenflettet måte. Mottakeren setter på sammen delene slik de skal avspilles. Dersom det skjer et pakketap vil vi tape litt av alle pakkene istedenfor å tape en hel
- Hva er relasjonen mellom jitter og CBR?   
	- Dersom det er mye jitter i nettverket kan en stabil overføringshastighet forbedre overføringen. Dette fordi det blir mer forutsigbart når man sender. VBR er mindre forutsigbart og mye jitter sammen med VBR kan gi store forsinkelser

