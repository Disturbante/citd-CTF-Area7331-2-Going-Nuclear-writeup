Questa challenge è la seconda parte di AREA7331 (perciò avremo bisogno anche delle conoscenze della challenge precedente del quale al momento non viene pubblicato il writeup quindi verrannò date per scontate)
<!-->
Iniziamo la challenge esaminando il badge che ci viene fornito in questa foto:

![badge](./pic/badge.jpg)

Utilizzando il link della challenge precedente possiamo loggare con l'account dell'amministratore di rete costruendo la password come per la challenge precendente:

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
e poter vedere i documenti dell'utente.
<!-->
Abbiamo la foto di un cane chiamato Brutus (ci servirà più avanti)
ed un documento dove ci sono informazioni fondamentali per accedere al mainframe.

![info per entrare](./pic/mainframeinfo.png)

seguendo queste info saremo in grado di entrare all'interno del mainframe e muoverci all'interno dei vari livelli
<!-->
Accedendo al seguente link:
<!-->
https://ctf-web-5.codeinthedark.dev/
<!-->
potremo vedere questo:
<!-->
![pannello di accesso](./pic/mainframelogin.png)
<!-->
inserendo le seguenti credenziali loggeremo nel primo livello:
    address:
        fw-admin-1.area7331.lab
    user:
        admin
    password:
        brutus
<!-->
Adesso siamo all'interno del primo pannello, perciò dobbiamo disabilitare il firewall(così per tutti i pannelli successivi)

![fw-admin-1-off](./pic/mainframe-fwadmin1.png)

andare sull'healthcheck dove troveremo l'address del secondo indirizzo a cui accedere _"fw-admin-2.area7331.lab"_.
https://github.com/Disturbante/citd-CTF-Area7331-2-Going-Nuclear-writeup/blob/main/pic/
![firewall1off](./pic/mainframe-firewalloff.png)


Accedendo al secondo pannello e seguendo i passi precedenti cioè disattivare il firewall e poi navigare nella sezione healtcheck dove è possibile notare altri indirizzi raggiungibili quali:

![firewall2off](./pic/mainframe-fwfirewalloff2.png)

Ora provando ad accedere all'indirizzo _"cameras.area7331.lab"_ o _"speakers.camera7331.lab"_, le credenziali sarrannò errate però andando a rileggere il documento all'interno dell'account di _"George Williams"_, possiamo apprendere che sta utilizzando una tecnologi molto antiquata per i controlli, quindi l'idea più semplice per bypassare un form  di login è tramite una sqlinjection come in foto:

![cmaerassqlioff](./pic/cameras-accessviaSqli.png)

il risultato ottenuto è l'accesso e la disattivazione delle camere:

![cmaerassqlioff](./pic/camerasoff.png)

Possiamo continuare con lo stesso procedimento andando a disattivare gli speakers:

![speakersoff](./pic/speakersoff.png)

La situazione ora cambia perchè provando la stessa metodologia con i due indirizzi _"reactor-subsystems.area7331.lab"_ e _"reactor-main.area7331.lab"_ non avremmo accesso in quanto l'utente admin non è quello giusto.
<!-->
Per risolvere quest livello basterà andare nel pannello precendente _"fw-admin-2.area7331.lab"_ ed entrare nella sezione logs.
<!-->
![logs](./pic/logs.png)
<!-->
all'interno di questi logs troveremo le azioni di modifica degli speakers e delle telecamere, ma soprattutto un tentativo di login dell'utente jwhite con un typo.
<!-->
attraverso questi logs possiamo facilemente capire le credenziali dell'utente:
<!-->   
    address:
        reactor-subsystems.area7331.lab
    username:
        jwhite
    password:
        iloveyou
<!-->
all'interno di questo pannello dobbiamo disabilitare entrambi i sistemi di raffreddamento così da causare l'esplosione
<!-->
![disabitazione controlli](./pic/subsystems.png)
<!-->
Successivamente possiamo loggare nell'ultimo address con le seguenti credenziali:
<!-->
    address:
        reactor-main.area7331.lab
    username:
        jwhite
    password:
        iloveyou
<!-->
ed attivare l'override:
<!-->
![override](./pic/reactormain.png)
<!-->
così da ottenere questo:
<!-->
![override](./pic/override.png)
<!-->
ed infine la flag!!
<!-->
![flag redactata ovviamente](./pic/flag.png)
<!-->
