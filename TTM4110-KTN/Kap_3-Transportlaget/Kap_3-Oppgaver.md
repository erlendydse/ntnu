### Begreper og oppgaver

- **TCP**  
  - Hva betyr det at TCP er byte-stream-orientert?  
    - Det ser på data fra applikasjonslaget som en kontinuerlig strøm av bytes, og segmenterer det før sending.

- **3-Way Handshake**  

- **TCP-sender vs TCP-mottaker**  

- **Multiplexing**  
- **Demultiplexing**  
  - Hvordan skjer demultiplexing i transportlaget?  
    - Transportlaget får pakker fra nettverkslaget, sjekker header og gir dataen videre til riktig socket.

- **Connectionless vs Connection-oriented demultiplexing**

- **ACK**  
  - Hva betyr nummeret som følger med en ACK?  
    - Det er sekvensnummeret til neste forventede byte.

- **Sekvensnummer**  
  - Hva betyr et segments sekvensnummer?  
    - Det er bytenummeret til den første byten som sendes i segmentet (ikke antall segmenter!).

- **Kumulativ ACK**  
  - Hva er det?  
    - En ACK(n) bekrefter at alle bytes frem til n er mottatt korrekt.

- **Selective Repeat vs Go-Back-N**  
  - Go-Back-N:  
    - Vinduet kan være én mindre enn sekvensnummerstørrelsen.  
    - Sender ACK kun for neste forventede pakke.  
  - Selective Repeat:  
    - Sender ACKs for alle mottatte pakker, selv om de er ute av rekkefølge.

- **QUIC**  
  - Hva er det og hvorfor brukes det?  
    - Transportprotokoll basert på UDP, gir pålitelighet og congestion control. Kan etableres raskere (1 RTT).

- **Flow Control**  
  - Hvordan fungerer det?  
    - Mottakeren oppgir bufferplass i headeren. Sender begrenser hvor mye **unACKed** data som sendes.

- **Congestion Control**  
  - Hvorfor brukes det?  
    - Hindre overbelastning i nettverket → mindre tap og bedre flyt.  
    - Fordeler båndbredde rettferdig.

  - Hvordan fungerer det?  
    - **Slow start:**  
      - Starter med CWND = 1 MSS, dobles for hver ACK.  
    - **Congestion Avoidance:**  
      - Når threshold nås → øk CWND lineært. Timeout → tilbake til slow start.  
      - 3 DupACKs → Fast Recovery.  
    - **Fast Recovery:**  
      - Gå ikke helt tilbake til start etter 3 duplikate ACKs.  

  - Hvordan vet klienten at det er congestion?  
    - Mottar ikke ACKs (pakker tapt).  

  - Hva er TCP Cubic?  
    - Forbedring på congestion control – CWND vokser raskere før threshold.  
    - *(Bilde referanse: `Pasted image 20240402141540.png` – legg inn separat om ønskelig)*

  - Hva er CWND?  
    - "Congestion Window" – hvor mye **unACKed** data senderen kan ha i nettverket samtidig.

- **Checksum**  
  - Hvis checksum er riktig, betyr det at pakken er feilfri?  
    - Nei. Den kan likevel være feil (f.eks. to flipped bits kan kansellere hverandre).

---

### Relasjoner mellom begreper

- **Flow-Control vs Congestion-Control**  
  - Flow-Control: mellom **host og host**  
  - Congestion-Control: i **selve nettverket**

- **End-to-end vs Network-assisted Congestion Control**  
  - End-to-end: sender/mottaker oppdager og reagerer på congestion  
  - Network-assisted: rutere hjelper til (f.eks. ECN-bit, eksplisitt feedback)

- **Hvordan er TCP en blanding av Selective Repeat og Go-Back-N?**  
  - TCP kaster ikke out-of-order pakker (Selective Repeat)  
  - TCP bruker Duplicate ACKs (Go-Back-N)  
  - Har sender-vindu som begrenser antall u-acknowledged segmenter (Go-Back-N)

- **TCP vs UDP – Komplett sammenligning**  

  | Egenskap | TCP | UDP |
  |----------|-----|-----|
  | Pålitelighet | ✅ Ja (ACK, re-sending) | ❌ Nei (best-effort) |
  | Flow control | ✅ | ❌ |
  | Congestion control | ✅ | ❌ |
  | Tjenester ikke støttet | ❌ Delay garanti, ❌ Båndbredde garanti |
  | Demultiplexing | 4-tuple (IP+Port fra begge sider) | 2-tuple (Dest IP + Port) |
  | Kommunikasjonstype | Byte-strøm | Pakker |
  | Returvei | Bruker etablert kobling | Leses fra header |
  | Oppsett | 3-Way Handshake | Ingen |
  | Socket-definisjon | 4 felt (src IP, src port, dest IP, dest port) | 2 felt (dest IP, dest port) |
  | Flere forbindelser til samme port | Ja – skiller på IP/port | Nei – samme socket brukes |
  | Analogier | TCP = telefonsamtale, UDP = postkort |
  | Checksum | ✅ | ✅ |
  | Ekstra headerfelt | Sekvensnr, ACK, vindustørrelse | Ikke til stede i UDP |