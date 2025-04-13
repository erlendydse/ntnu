### Begreper

- **Konfidensialitet**  
- **Symmetric key**  
- **Public/Private key**  
- **Integritet/Autentisering**  
- **Digital signering**  
  - Hvordan fungerer digital signering?  
    - Bob skriver en melding $m$. Han hasher denne meldingen og legger på sin private key $K^{-}$ for å lage $K^{-}(m)$. Sender $K^{-}(m)$ og $m$  
    - Alice sammenligner to versjoner:  
      1) $m$ som hun hasher = $h(m)$  
      2) bruker Bobs public key for å se om $K^{+}(K^{-}(h(m))) = h(m)$  
- **Digital certificate**  
  - Hva er det?  
    - Et sertifikat som inneholder en person sin public key. Den sertifiseres av CA  
- **Message digest**  
  - Hvorfor?  
    - Lang tid å ta i bruk private/public key på hele meldingen  
  - Kan man få tilbake den originale meldingen etter at den har blitt hashet?  
    - Nei  
- **Sikker epost**  
  - Hvordan sikrer man konfidensialitet på epost?  
    - Bruker asymmetriske nøkler for å utlede en hemmelig symmetrisk nøkkel som brukes for å kryptere datapakkene  
- **TLS**  
  - Hva settes opp først av TCP og TLS?  
    - TCP-kobling settes opp først, og så settes TLS opp etterpå  
  - Hva betyr "Client Hello" og "Server Hello"?  
    - Klienten sender først en "Client Hello"-melding med info om TLS-versjon, krypteringsalgoritmer og tilfeldig tall.  
    - Server svarer med "Server Hello", velger algoritmer, og sender også et tilfeldig tall  
  - Hva brukes det tilfeldige tallet til?  
    - Brukes til å generere nøkler for sesjonen  
    - Sikrer mot "Connection replay"-angrep  
  - Hva er en TLS record?  
    - En lang melding brytes opp i flere små meldinger med hver sin MAC  
- **IPsec**  
  - Hva er hovedtankegangen bak hvordan IPsec fungerer?  
    - Bruke asymmetriske nøkler til å utlede en felles symmetrisk nøkkel  
- **VPN**  
  - Hva er VPN?  
    - Virtuelt privat nettverk som gir en kryptert og sikker tunnel mellom enheter  
- **Brannmur**  
  - Hvorfor bruker man brannmur?  
    - Beskytte nettverk mot uønsket trafikk  
- **Stateless**  
- **Stateful**  
  - Hva kan være et problem med Stateful firewalls?  
    - For aggressive timeout-verdier kan blokkere nyttige pakker  
  - Eksempel på pakker Stateful ikke slipper gjennom:  
    - TCP ACK uten SYN  
    - TCP FIN uten opprettet kobling  
- **Access Control Lists**  
- **Application Gateways**  
  - Eksempel:  
    - Gi enkelte brukere spesialtilgang til tjenester utenfor det interne nettverket  
- **Sikkerhet over WiFi**  
  - Forklaring:  
    - AP oppgir tilgjengelige krypteringsmetoder  
    - Enheten velger metode  
    - De utleder en delt nøkkel via WPA3-handshake og bruker den til å kryptere  
  - Shared symmetric session key derivation:  
    - Begge parter kjenner til en delt hemmelighet $K_{AS-M}$  
    - Brukes til å utlede session key $K_{M-AP}$  
- **Sikkerhet over Cellular**  
  - Man kobler seg til en basestasjon  
  - Autentisering via IMSI på SIM-kort  
  - Enhet og nettverk autentiserer seg mot hverandre  
  - MME sender info til HSS (hjemmenett)

---

### Relasjoner

- **Forskjell på symmetric og public key:**  
  - Symmetric: én felles nøkkel  
  - Public: kryptering med public key, dekryptering med private key  

- **Forskjell og likhet mellom TLS og IPsec:**  
  - Forskjell: TLS = applikasjonslaget, IPsec = nettverkslaget  
  - Likhet: Begge gir konfidensialitet, integritet og autentisering  

- **Relasjon mellom IPsec og VPN:**  
  - IPsec brukes til å lage VPN  

- **Forskjell på IPsec Transport mode og Tunnel mode:**  
  - Transport mode: bare payload kryptert  
  - Tunnel mode: hele datagrammet kryptert  

- **Forskjell på AH og ESP:**  
  - AH: autentisering og integritet  
  - ESP: autentisering, integritet **og** konfidensialitet  
  - Merk:  
    - AH = 2 bokstaver → 2 tjenester  
    - ESP = 3 bokstaver → 3 tjenester  

- **WiFi vs Cellular sikkerhet:**  
  - WiFi: passord/delt hemmelighet  
  - Cellular: SIM-kort med global identitet og nøkler  

- **Stateless vs Stateful:**  
  - Stateless: ser bare på enkeltpakker  
  - Stateful: holder oversikt over tilkoblinger (TCP-stater)  

- **Stateful/Stateless vs Application Gateways:**  
  - Stateful/stateless: lavere nettverkslag  
  - Application Gateway: ser også på applikasjonsdata  

- **Kryptering, integritet og autentisering – kort forklaring:**  
  - **Kryptering:**  
    - Trenger symmetric eller public/private key  
    - Utleder felles symmetrisk nøkkel for kryptering  
  - **Digital signering:**  
    - Trenger public key encryption (privat nøkkel + CA + sertifikat)  
    - Metode: privat nøkkel krypterer → mottaker verifiserer med public key  
  - **Integritet:**  
    - Trenger hash + delt nøkkel  
    - Begge parter lager MAC og sammenligner  

- **Likheter og forskjeller på WPA3, Cellular, TLS og IPsec:**  
  - **Likhet:** bruker delt hemmelighet og nonce for å utlede nøkler  
  - **Forskjell – autentisering:**  
    - TLS: digitalt sertifikat  
    - IPsec: digitalt sertifikat  
    - WiFi: passord  
    - Cellular: SIM-kort  