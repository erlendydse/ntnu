### Begreper og oppgaver

- **Forwarding table**  
- **Generalized forwarding**  
- **Match plus action**  
  - Hva er det?  
    - I tillegg til forwarding kan en ruter også utføre handlinger som `modify`, `drop` og `send-to-controller`.

- **Destination-based forwarding**  
- **Longest prefix matching (LPM)**  
  - Hvorfor brukes LPM?  
    - For å velge den mest presise og effektive ruten i store nettverk.  
  - Brukes i:  
    - Begge forwarding-typer, men særlig i Destination-based forwarding.

- **Switching fabric**  
- **Interconnection networks**  
- **Head-of-line blocking (HOL)**  
  - Hvordan fungerer det?  
    - En pakke A blokkeres fordi en pakke foran den i køen venter på en annen utgangsport.

- **Buffer management**  
  - Hva er marking?  
    - Pakker kan prioriteres ulikt, f.eks. for å sikre QoS.

- **Ulike typer scheduling**  
- **Interface**  
  - Hva er det?  
    - Fysisk grensesnitt som lar enheten koble til nettet, f.eks. en Ethernet-port. IP-adresser knyttes til interface, ikke enheten selv.  
  - Flere interfaces = flere IP-adresser.

- **DHCP (Dynamic Host Configuration Protocol)**  
  - Hvordan fungerer det?  
    - **Discover** → **Offer** → **Request** → **ACK**  
    - Alternativt kan man sende `Request` direkte hvis man husker IP-en.  
  - Formål (3):  
    - Tildele IP-adresse  
    - Gi info om første ruter (gateway)  
    - Gi info om DNS-server

- **Subnet**  
  - Hvordan beregnes antall host-adresser?  
    - `2^antall host-bits - 2` (én for nett-ID, én for broadcast)  
  - Eksempel /24:  
    - `2^8 - 2 = 254` brukbare adresser

- **CIDR (Classless Inter-Domain Routing)**  

- **IPv4 vs IPv6**  
  - Headerforskjeller:  
    - IPv6 har **ikke**: fragmentering, checksum eller options  
    - IPv6 har fast headerstørrelse: 40 bytes  
    - IPv4 har variabel header: 20–60 bytes

- **Tunneling**  
  - Hva er det?  
    - Å sende IPv6 datagrammer innkapslet i IPv4 datagrammer for å kunne bruke IPv4-rutere.

- **NAT (Network Address Translation)**  
  - Hvorfor brukes det?  
    - For å spare på begrensede IPv4-adresser  
  - Hvordan fungerer det?  
    - Ruter oversetter mellom private og offentlige IP-er  
    - Endrer også portnummer for å skille kommunikasjon mellom ulike interne enheter

- **Quality of Service (QoS)**  
  - Hva er det?  
    - Et “trafikkpoliti” som prioriterer viktig trafikk som video og tale, og nedprioriterer mindre viktig trafikk som nedlastinger og e-post

---

### Relasjoner mellom begreper

- **Dataplan vs Kontrollplan**  
  - Dataplan = forwarding  
  - Kontrollplan = routing

- **Destination-based vs Generalized forwarding**  
  - Destination-based: Kun IP-basert  
  - Generalized: Kan bruke flere felt og utføre flere handlinger (match plus action)

- **Tunneling og NAT**  
  - Felles: Jobber med overgangen mellom IPv4 og IPv6  
  - Tunneling: Sender IPv6 gjennom IPv4  
  - NAT: Reduserer behovet for mange offentlige IPv4-adresser

- **To måter å bruke DHCP på**  
  - Full prosess (`Discover` → `Offer` → `Request` → `ACK`): når host ikke husker IP  
  - Kun `Request` og `ACK`: når host husker og vil gjenbruke IP-adressen