### Begreper og oppgaver

- **Link State**  
- **Distance Vector**  

- **ICMP**  
  - Hva brukes ICMP til?  
    - Diagnostisere nettverksproblemer  
  - Hvordan fraktes ICMP?  
    - Direkte inne i IP-pakker  

- **Traceroute**  
  - Hvordan fungerer traceroute?  
    - Sender pakker med økende TTL-verdier.  
    - Når en TTL utløper, sender ruteren en ICMP-melding tilbake.  
    - Dette brukes til å kartlegge rutene pakken tar.  
  - Hva er forskjellen på ping og traceroute?  
    - Begge bruker **ICMP echo request**  
    - **Ping:** Sjekker om en host er tilgjengelig og om det er pakketap  
    - **Traceroute:** Viser alle rutere på veien til destinasjonen og hvor feilen ligger hvis forbindelsen feiler  

---

### Relasjoner mellom begreper

- **Forskjellen på Link State og Distance Vector**  
  - Link State: Har kunnskap om hele nettverket  
  - Distance Vector: Kjenner kun til sine naboer  

- **Hvilken er best – Link State eller Distance Vector?**  
  - **Link State:**  
    - Bedre i store nettverk  
    - Mer effektiv ruting  
    - Krever mer minne og beregning  
  - **Distance Vector:**  
    - Enklere  
    - Bedre i små nettverk  
    - Mindre ressurskrevende  