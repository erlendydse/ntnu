### Begreper og oppgaver

- **Error detection/correction**

- **Cyclic Redundancy Check (CRC)**  
  - Kan CRC rette opp feil?  
    - Nei  
  - Hvordan fungerer sender og mottaker i CRC?  
    - **Sender:** Tar data `D` og generator `G`, bruker XOR for å finne remainder `r`  
    - **Mottaker:** Tar `D + r` og utfører XOR med `G`  
      - Remainder = 0 → ✅ suksess  
      - Remainder ≠ 0 → ❌ det har skjedd en feil  

- **Parity Check**

- **Single Bit Parity**  
  - Hvordan fungerer det?  
    - Legger til en ekstra bit slik at antallet 1-ere blir partall  

- **Two-D Parity**  
  - Fordel:  
    - Kan både detektere og rette bit-feil  

- **Point-to-point vs Broadcast**  
  - Forskjell:  
    - Antall enheter som deler linken  

- **MAC-protokoll**  
  - Hvorfor trengs det ikke for point-to-point?  
    - Ingen deler linken  
  - Tre grupper:  
    - Random Access  
    - Channel Partitioning  
    - Taking Turns  

- **Random Access**  
  - Kjennetegn:  
    - Noder konkurrerer om båndbredden (f.eks. som en nattklubb – tilfeldig hvem som får slippe inn)

- **Slotted ALOHA**  
  - Hvordan fungerer det?  
    - Alle sender når de vil  
    - Ved kollisjon: For hver slottid flipper noden "mynt/kron" for å bestemme om den prøver å sende  
  - Slotted vs Unslotted:  
    - Slotted → færre kollisjoner, men vanskeligere å synkronisere  
    - Unslotted → flere kollisjoner, enklere implementasjon  

- **CSMA/CD**  
  - Hvordan fungerer det?  
    - Noden sjekker om kanalen er ledig før sending  
    - Ved kollisjon → Binary Exponential Backoff  
  - Hvorfor regnes det som Random Access?  
    - Det er fortsatt konkurranse om tilgang – uten tidsplan eller garantert plass  
  - Betydning:  
    - **Carrier Sense:** Lytter før man sender  
    - **Multiple Access:** Flere noder bruker samme link  

- **Binary Exponential Backoff**  
  - Hvordan fungerer det?  
    - Etter `n` kollisjoner: Velger tilfeldig K innen `0–2ⁿ⁻¹` → multipliserer med tidsintervall  
  - Hvorfor eksponentiell venting?  
    - Få kollisjoner = kortere ventetid  
    - Mange kollisjoner = større intervall og lengre ventetid  

- **Ethernet CSMA/CD**  
  - MAC-protokoll:  
    - Unslotted CSMA/CD med binary backoff  
  - Slotted vs Unslotted:  
    - Unslotted sender når ledig, uten å vente på faste slottider  

- **TDMA / FDMA**  
  *(ingen detaljer gitt – legg til hvis ønsket)*

- **Polling**  
  - Sentral kontroller spør nodene om de har data å sende  

- **Token Passing**  
  - En token sirkulerer – den som har token får sende  

- **MAC-adresse**  
  - Hvorfor trengs de?  
    - For lokal kommunikasjon (Layer 2), raskere enn IP  
  - Hva brukes de til?  
    - Link-lag kommunikasjon  
  - Alternativt navn:  
    - Ethernet-adresse  

- **ARP**  
  - Hvordan fungerer det?  
    - Enhet sender ARP-request (broadcast)  
    - Mottaker svarer med MAC-adresse  
  - Når brukes det?  
    - Ved sending til enheter i samme subnet  
  - Hvorfor oversette mellom MAC og IP?  
    - De hører til forskjellige lag i OSI-modellen  
  - Hvorfor har ARP-tabell verdier med TTL?  
    - Informasjonen kan endres – må oppdateres jevnlig  
  - Hvem har ARP-tabell?  
    - Alle nettverks-tilkoblede enheter  
  - Hvordan vet man IP-en til ruteren ved annet subnet?  
    - Ved hjelp av subnettmaske og konfigurasjon → enheten sender til default gateway (ruteren)  

- **Broadcasting**  
  - Hva er en broadcast-link?  
    - Link som brukes av flere enheter – meldinger går til alle  
  - Hva brukes det til?  
    - F.eks. ARP og DHCP  

- **Ethernet-switch**  
  - Hva er flooding og hvorfor brukes det?  
    - Ukjent MAC-adresse → send til alle porter  
  - Hvordan lærer switchen adressene?  
    - Ser på source MAC og lagrer hvilken port den kom fra  

- **Cable Access Network (CAN)**  
  - MAC-protokoller:  
    - Downstream → FDM  
    - Upstream → TDM + Random Access  

---

### Relasjoner mellom begrep

- **Slotted ALOHA vs CSMA**  
  - ALOHA: Alle sender når de vil  
  - CSMA: Høflig – venter til kanalen er ledig  
  - Backoff:  
    - CSMA → Binary Exponential  
    - ALOHA → mynt/kron per slottid  

- **Cyclic Redundancy vs Parity Check**  
  - CRC: Mer avansert, bedre deteksjon  
  - Parity: Enklere, sørger for partall 1-ere  

- **Trenger vi MAC når vi har IP?**  
  - Ja – MAC er raskere og brukes på lokalnett  

- **Channel Partitioning vs Random Access**  
  - CP: Bra ved høy last, ineffektiv ved lav last  
  - RA: Bra ved lav last, ineffektiv ved høy last  

- **Polling vs Token Passing**  
  - Polling: Sentral kontroller spør  
  - Token: Ingen kontroller, token sendes rundt  

- **Finne MAC i samme vs annet subnet**  
  - Samme subnet: ARP-request  
  - Annet subnet: ARP til gateway/ruter → videre ARP i neste nett