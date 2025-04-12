### Begreper

- **CBR og VBR**  
  - Hva er bitrate?  
    - Hvor mye data som blir overført hvert sekund  
  - Hva er forskjellen på CBR og VBR?  
    - I CBR blir data sendt med konstant hastighet – like mye data per sekund.  
    - I VBR varierer hastigheten basert på innholdet. Høy kvalitet ved komplekse scener, lavere ved enkle.  
    - CBR er best for live-streaming/konferanser.  
    - VBR er best for filmer med variert innhold – optimerer båndbreddebruk.

- **Jitter**  
  - Hva er jitter og hvordan løses det?  
    - Variasjon i delay mellom når bits sendes og mottas.  
    - Løses med buffer på klientsiden.  

- **VoIP**  
  - Hva er det?  
    - Teknologi for å sanntidsoverføre lyd og bilde over internett  
  - Hvordan fungerer lydoverføring?  
    - Pakker sendes kun når man snakker.  
    - Sendes i sockets hvert 20 ms.  
    - Tolererer 1–10 % pakketap.  
    - Har jitter → løses med buffer og q-verdi.  
  - Hvordan fungerer **q**-verdien i avspilling?  
    - Pakker spilles av **q** millisekunder etter opprettelse.  
    - Kommer pakken for sent → kastes.  
    - For høy q gir dårlig respons. For lav q gir tapt data.  
  - Hvordan håndteres pakketap?  
    - Interleaving og Forward Error Correction (FEC).

- **Forward Error Correction (FEC)**  
  - Hva er det?  
    - Ekstra data sendes for å kunne rekonstruere tapte pakker uten retransmisjon.  
  - To metoder:  
    - XOR av n pakker → kan gjenoppbygge én tapt pakke.  
    - Hver pakke inkluderer kopi av tidligere pakke i lavere kvalitet.  

- **Interleaving**  
  - Hva er interleaving?  
    - Data brytes opp i biter og sendes i omorganisert rekkefølge.  
    - Reduserer konsekvensene av pakketap (man mister bare smådeler).  
    - Krever mer buffer for korrekt rekonstruksjon.  
    - ![interleaving bilde](Pasted%20image%2020240427200453.png)

- **RTP – Real-time Transport Protocol**  
  - Hva er det?  
    - Protokoll for lyd- og video-strømmer i sanntid.  
  - Hvilke headerfelt er viktige?  
    - **Payload type:** hvilken enkoding som brukes  
    - **Sekvensnummer:** detekterer pakketap  
    - **Tidsstempel:** sørger for riktig rekkefølge, synkroniserer lyd/bilde  
    - **SSRC:** skiller kilder i f.eks. videokonferanser  

---

### Relasjoner

- **VoIP og RTP**  
  - RTP er protokollen som brukes for sanntidsoverføring, f.eks. VoIP.

- **FEC og Interleaving – hva brukes de til?**  
  - Begrense pakketap og forbedre kvalitet i VoIP.  
  - Rette opp tap uten retransmisjon.

- **Forskjellen mellom FEC og Interleaving**  
  - **FEC:** ekstra data sendes → mulig å gjenopprette hele pakker. Øker pakkestørrelse.  
  - **Interleaving:** bryter opp og sammenfletter pakker. Mister deler, men ikke hele. Mindre synlig tap.

- **Jitter og CBR**  
  - Ved høy jitter gir CBR (stabil bitrate) bedre forutsigbarhet enn VBR.  
  - VBR + jitter = større risiko for forsinkelse og dårlig brukeropplevelse.