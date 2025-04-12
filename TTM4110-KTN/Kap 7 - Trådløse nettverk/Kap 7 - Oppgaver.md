### Begreper

- **Wireless hosts**  
- **Wireless links**  
- **Base stations**  
- **Infrastructure mode**  
- **Ad Hoc mode**  

- **Handover**  
  - Hva er handover?  
    - En enhet bytter fra en basestasjon til en annen  

- **SNR**  
  - Hva brukes SNR til?  
    - Måler forholdet mellom ønsket signal og bakgrunnsstøy  
    - Jo høyere SNR, desto bedre signal i forhold til støy  

- **BER**  
  - Hva brukes bit error rate til?  
    - Måler hvor mange bitfeil som oppstår ved trådløs kommunikasjon  

- **802.11 Wireless LAN (WiFi)**  
- **Basic Service Set (BSS)**  
  - Hva består et BSS av?  
    - Et access point (AP) og tilkoblede enheter  

- **Association**  
  - Hvorfor er kanaler viktig?  
    - WiFi bruker ulike frekvenskanaler for å unngå interferens mellom AP-er  

- **Passiv scanning**  
  - Hvordan fungerer det?  
    - AP sender beacon frames  
    - Host oppdager AP-er og sender **request**  
    - Får **response** fra valgt AP  

- **Aktiv scanning**  
  - Hvordan fungerer det?  
    - Host sender **probe signal**  
    - AP svarer med forslag  
    - Host sender **request**, får **response**  

- **Beacon frames**  
- **Probe signal**  

- **SSID**  
  - Hvorfor brukes SSID?  
    - Navn som identifiserer et trådløst nettverk  
  - Hører SSID til AP?  
    - Nei, det identifiserer nettverket (WLAN), ikke AP direkte  

- **WiFi CSMA/CA**  
  - Hvordan fungerer CSMA/CA?  
    - **Sender:**  
      - Sjekker om kanalen er ledig (venter DIFS)  
      - Hvis ledig → send  
      - Hvis ikke → binary backoff, teller ned mens kanalen er ledig  
      - Hvis ACK mottas → send neste pakke  
      - Hvis ikke ACK → send samme pakke med lengre backoff  
    - **Mottaker:**  
      - Mottar pakke → venter SIFS → sender ACK  

  - Hvorfor har ikke CSMA collision detection?  
    - Vanskelig å oppdage kollisjoner i trådløs – prøver heller å unngå dem  

  - Hva er forskjellen på om en ACK blir mottatt eller ikke?  
    - **Mottatt:** neste pakke, samme backoff  
    - **Ikke mottatt:** samme pakke, økt backoff  

  - Hvordan hjelper ACK-er i trådløse nettverk?  
    - Bekrefter mottak i tilfelle bitfeil eller **hidden terminal problem**  

- **DIFS og SIFS**  
  - Hvorfor vente DIFS?  
    - Sjekke om kanalen er ledig  
  - Hva er lengst av DIFS og SIFS?  
    - DIFS er lengre  
  - Når brukes de?  
    - **Uten RTS/CTS:**  
      - DIFS før sending, SIFS før ACK  
    - **Med RTS/CTS:**  
      - DIFS før RTS, SIFS mellom:  
        - RTS → CTS  
        - CTS → DATA  
        - DATA → ACK  

- **RTS og CTS**  
  - Hvordan fungerer det?  
    - Node sender RTS til AP  
    - AP sender CTS til alle  
    - Node sender DATA  
    - AP sender ACK  

- **Hidden terminal**  
  - Hvordan hjelper ACK-er?  
    - Hvis A og B ikke hører hverandre, men begge når C, kan kollisjoner skje.  
    - ACK fra C bekrefter hvilken som ble mottatt.  

- **Adressering**  
  - Hvorfor trenger vi 4 adressefelt?  
    - Source, destination, mellomstasjon og en ekstra for Ad-Hoc-nettverk  

- **Handover (samme subnet)**  
  - Hvordan fungerer det?  
    - Ved AP-bytte sender nytt AP en broadcast  
    - Switch oppdaterer MAC-tabellen for den nye tilkoblingen  

- **Cellular**  
- **Roaming**  
  - Hvorfor er inter-carrier settlements viktig?  
    - Fordeler inntektene mellom hjemmenettverk og besøkt nett  

- **IMSI**  
  - Hva er det?  
    - Unik identifikator for mobilnett, lagres på SIM-kort  

- **Home Subscriber Service (HSS)**  
  - Hvorfor trenger vi det?  
    - Inneholder data om brukere, abonnement og autentisering  

- **Mobility Management Entity (MME)**  
  - Hvorfor trenger vi MME?  
    - Autentisering og sporing av enheter  

- **PDN Gateway**  
  - Hva gjør den?  
    - Hjelper med NAT og IP-håndtering  

- **LTE**  
  - Hva er det?  
    - Standard for mobil datakommunikasjon (f.eks. 4G)  
  - Hvorfor tunneling?  
    - Enheten kan beholde IP-adresse selv ved bytte av område  

---

### Relasjoner

- **Infrastructure vs Ad-Hoc mode**  
  - Ad-Hoc har ingen AP – direkte kommunikasjon  

- **Ad-Hoc vs P2P**  
  - Likhet: direkte enhet-til-enhet  
  - Forskjell:  
    - Ad-Hoc = midlertidig, uten infrastruktur  
    - P2P = større system, brukes til deling, distribusjon  

- **Trådløs link vs vanlig link**  
  - Trådløs: svakere signal, mer interferens  

- **BSS og WLAN**  
  - Et WLAN består av flere BSS koblet via switch  

- **SNR og BER**  
  - Høy SNR = lav BER  
  - SNR beskriver kvaliteten på signalet, som påvirker feilrate  

- **Passiv vs Aktiv skanning**  
  - Passiv: AP sender beacon → host scanner  
  - Aktiv: Host sender probe → AP svarer  

- **WiFi CSMA/CA vs Ethernet CSMA/CD**  
  - WiFi: Collision Avoidance (unngår)  
  - Ethernet: Collision Detection (oppdager)  
  - Begge lytter før de sender  

- **WiFi vs Cellular**  
  - WiFi: Lokalt, enkel infrastruktur, 802.11  
  - Cellular: Dekker større område, bruker LTE, mer komplekst system  

- **Basestasjoner i Cellular vs WiFi**  
  - Cellular: Koordinerer for mobilitet og belastningsfordeling (load management)  