Questa challenge è la seconda parte di AREA7331 (perciò avremo bisgno anche delle conoscenze della challenge precedente del quale al momento non ho pubblicato il writeup quindi le darò per scontate)
<!-->
Iniziamo la challenge esaminando il badge che ci viene fornito in questa foto:

![badge](./pic/badge.jpg)

Utilizzando il link della challenge precedente possiamo loggare con l'account dell'amministratore di rete costruendo la password come per la challenge precende:

    id:
      eid000213@area7331.lab
    password:
      George-Williams-EID000213-AREA7331!
Per accedere dobbiamo prima resettare la password inviando una richiesta all'url:
<!-->
https://ctf-web-3.codeinthedark.dev/forgot
<!-->
inviando l'eid di George per tornare alla password di default.

Una volta fatto questo possiamo loggare attraverso il link utilizzando le credenziali scritte sopra 
<!-->
https://ctf-web-3.codeinthedark.dev/login
<!-->
E vedere i documenti dell'utente.
<!-->
Abbiamo la foto di un cane chiamato Brutus (ci servirà più avanti)
ed un documento dove ci sono informazioni fondamentali per accedere al mainframe.

![info per entrare](./pic/mainframeinfo.png)

seguendo queste info saremo in grado di entrare all'interno del mainframe e muoverci all'interno dei vari livelli
