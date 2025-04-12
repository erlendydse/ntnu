### Begreper og oppgaver

- **HTTP**  
  - Hva er forskjellen på persistent og non-persistent connection?  
    - **Persistent:** Alle forespørsler og svar sendes over samme forbindelse.  
    - **Non-persistent:** Klienten må opprette en ny kobling for hver forespørsel.  
  - Hvilken brukes?  
    - HTTP bruker persistent fra versjon 1.1 og spesielt i HTTP/2.0 og videre.

- **GET**  
- **Conditional-GET**  
  - Får man tak i en nettside hvis man sender en Conditional-GET?  
    - Nei, man får bare beskjed om nettsiden er endret.  
  - Hvordan kjenner man igjen en Conditional-GET?  
    - Den har et `If-Modified-Since`-felt.  
  - Hvem sender Conditional-GET?  
    - Webcachen sender den til serveren. Hvis serveren svarer med **304 Not Modified**, sendes den cachede versjonen til brukeren.

- **Webcaches**  
- **Cookies**  
  - Hvordan fungerer cookies?  
    - *(Bilde referanse: `Pasted image 20240330172642.png`) – du kan legge til bildet manuelt eller beskrive det her)*  

- **Buffer**  
- **Encoding**  
- **DASH (Dynamic Adaptive Streaming over HTTP)**  
- **Manifestfil**  
  - Hvor ligger den?  
    - I CDN-nettverk  

- **CDN (Content Delivery Network)**  
- **DNS**  
  - Hva gjør DNS?  
    - Oversetter domenenavn til IP-adresser  

- **Socket**  
  - What is the purpose of a socket?  
    - Å etablere en forbindelse slik at enheter kan sende og motta data – som en telefonsamtale, man må først "ringe opp".

---

### Relasjoner mellom begreper

- **Hva er forskjellen på TCP og HTTP?**  
  - **TCP** er som posten: sørger for at brevet kommer frem.  
  - **HTTP** er innholdet i brevet: hva som etterspørres og leveres.

- **Hva er forskjellen på GET og Conditional-GET?**  
  - **GET**: Henter en nettside uansett.  
  - **Conditional-GET**: Spør kun om innholdet er endret siden sist.

- **Hva er sammenhengen mellom Webcaches og Conditional-GET?**  
  - Bruker spør om en nettside → Webcachen sender Conditional-GET til serveren  
  - Hvis server svarer med **304 Not Modified**, sender cachen sin versjon  
  - Hvis endret, caches ny versjon og sendes videre  

- **Hva er forskjellen på temporal og spatial encoding?**  
  - **Temporal encoding:** Ser på hva som endrer seg mellom bilder (bevegelse).  
  - **Spatial encoding:** Ser på bildeinformasjon som ligger etter hverandre i samme bilde (romlig kompresjon).