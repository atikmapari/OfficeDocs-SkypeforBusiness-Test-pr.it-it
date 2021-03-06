﻿---
title: Verificare le impostazioni di configurazione
TOCTitle: Verificare le impostazioni di configurazione
ms:assetid: 41dbf91c-f2e1-4b9a-88cf-959575558cf2
ms:mtpsurl: https://technet.microsoft.com/it-it/library/JJ204848(v=OCS.15)
ms:contentKeyID: 49300332
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificare le impostazioni di configurazione

 

_**Ultima modifica dell'argomento:** 2015-03-09_

Dopo aver unito la topologia e aver eseguito il cmdlet **Import-CsLegacyConfiguration** , verificare che i criteri e le impostazioni di Office Communications Server 2007 R2 siano stati importati in Lync Server 2013. Nella tabella seguente sono elencati i criteri e le impostazioni da verificare.

## Criteri e impostazioni da verificare dopo la migrazione


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Se si usa il carico di lavoro seguente:</th>
<th>Verificare i criteri e le impostazioni seguenti:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servizi di messaggistica istantanea e conferenza</p></td>
<td><p>Criteri di presenza</p>
<p>Criteri conferenza</p></td>
</tr>
<tr class="even">
<td><p>Conferenza telefonica con accesso esterno</p></td>
<td><p>Numeri di accesso esterno</p>
<p>Dial plan</p></td>
</tr>
<tr class="odd">
<td><p>VoIP aziendale</p></td>
<td><p>Criteri vocali</p>
<p>Route vocali</p>
<p>Dial plan</p>
<p>Impostazioni di utilizzo PSTN</p></td>
</tr>
<tr class="even">
<td><p>Communicator Web Access</p></td>
<td><p>URL semplici</p></td>
</tr>
<tr class="odd">
<td><p>Utenti esterni</p></td>
<td><p>Criteri di accesso esterno</p></td>
</tr>
<tr class="even">
<td><p>Archiviazione</p></td>
<td><p>Criteri di archiviazione</p></td>
</tr>
</tbody>
</table>


## Per verificare i criteri e le impostazioni

1.  Nell'ambiente Office Communications Server 2007 R2 prendere nota dei nomi dei dial plan (inizialmente noti come profili località), dei numeri di accesso esterno (aree e numeri di telefono di Operatore Conferenza), delle route vocali e dei criteri elencati nella tabella precedente, oltre agli URL utilizzati per Communicator Web Access.

2.  Nel server Front End Lync Server 2013 aprire Pannello di controllo di Lync Server.

3.  Per verificare i criteri conferenza importati, nel riquadro a sinistra fare clic su **Servizi di conferenza** , su **Criteri conferenza** e quindi verificare che tutti i criteri conferenza dell'ambiente Office Communications Server 2007 R2 siano inclusi nell'elenco.
    

    > [!NOTE]
    > I criteri <STRONG>Riunione</STRONG> delle versioni precedenti di Office Communications Server sono ora noti come criteri conferenza in Lync Server 2013. Inoltre, l'impostazione <STRONG>Partecipanti anonimi</STRONG> delle versioni precedenti di Office Communications Server è ora un'impostazione dei criteri conferenza di Lync Server 2013.

    

    > [!NOTE]
    > In Office Communications Server 2007 R2, se i criteri conferenza non sono impostati su <STRONG>utilizzo per utente</STRONG> , vengono importate solo le impostazioni dei criteri globali. In questa situazione non vengono importati altri criteri conferenza.

    

    > [!NOTE]
    > Se <STRONG>Partecipanti anonimi</STRONG> è impostato su <STRONG>Applica per utente</STRONG> nei criteri conferenza di Office Communications Server 2007 R2, vengono creati due criteri conferenza durante la migrazione: uno con <STRONG>AllowAnonymousParticipantsInMeetings</STRONG> impostato su <STRONG>True</STRONG> e uno con <STRONG>AllowAnonymousParticipantsInMeetings</STRONG> impostato su <STRONG>False</STRONG> .



4.  Per verificare i dial plan importati, fare clic su **Routing vocale** , su **Dial Plan** e quindi verificare che tutti i dial plan dell'ambiente Office Communicator 2007 R2 siano inclusi nell'elenco.
    

    > [!NOTE]
    > In Lync Server 2013 i <STRONG>profili località</STRONG> sono ora denominati <STRONG>dial plan</STRONG> .



5.  Per verificare i criteri vocali importati, fare clic su **Routing vocale** , su **Criteri vocali** e quindi verificare che tutti i criteri vocali dell'ambiente Office Communicator 2007 R2 siano inclusi nell'elenco.
    

    > [!NOTE]
    > Se i criteri vocali non sono impostati su <STRONG>utilizzo per utente</STRONG> nell'ambiente Office Communications Server 2007 R2, vengono importati solo i criteri vocali globali. In questa situazione non vengono importati altri criteri vocali.



6.  Per verificare le route vocali importate, fare clic su **Routing vocale** , su **Route** e quindi verificare che tutte le route vocali dell'ambiente Office Communicator 2007 R2 siano incluse nell'elenco.

7.  Per verificare le impostazioni di utilizzo PSTN importate, fare clic su **Routing vocale** , su **Utilizzo PSTN** e quindi verificare che le impostazioni di utilizzo PSTN dell'ambiente Office Communicator 2007 R2 siano incluse nell'elenco.

8.  Per verificare i criteri di accesso esterno importati, fare clic su **Federazione e accesso esterno** , su **Criteri di accesso esterno** e quindi verificare che tutti i criteri di accesso esterno dell'ambiente Office Communicator 2007 R2 siano inclusi nell'elenco.

9.  Per verificare i criteri di archiviazione, fare clic su **Monitoraggio e archiviazione** , su **Criteri di archiviazione** e quindi verificare che tutti i criteri di archiviazione dell'ambiente Office Communications Server 2007 R2 siano inclusi nell'elenco.

10. Aprire Lync Server Management Shell.

11. Per verificare i criteri di presenza, alla riga di comando digitare quanto segue.
    
        Get-CsPresencePolicy
    
    Esaminando il nome nel parametro **Identity** verificare che tutti i criteri di presenza dell'ambiente Office Communications Server 2007 R2 siano stati importati.

## Per verificare i criteri e le impostazioni utilizzando i cmdlet

1.  Aprire Lync Server Management Shell.

2.  Eseguire i cmdlet nella tabella seguente per verificare i criteri e le impostazioni.
    
    La sintassi di tali cmdlet è simile all'esempio seguente:
    
        Get-CsConferencingPolicy
    
    Per informazioni dettagliate su tali cmdlet, eseguire:
    
        Get-Help <cmdlet name> -Detailed


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Per i criteri o le impostazioni seguenti:</th>
<th>Usare il cmdlet seguente:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Criteri di presenza</p></td>
<td><p><strong>Get-CsPresencePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Criteri conferenza</p></td>
<td><p><strong>Get-CsConferencingPolicy</strong></p></td>
</tr>
<tr class="odd">
<td><p>Numeri di accesso esterno</p></td>
<td><p><strong>Get-CsDialInConferencingAccessNumber</strong></p></td>
</tr>
<tr class="even">
<td><p>Dial plan</p></td>
<td><p><strong>Get-CsDialPlan</strong></p></td>
</tr>
<tr class="odd">
<td><p>Criteri vocali</p></td>
<td><p><strong>Get-CsVoicePolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Route vocali</p></td>
<td><p><strong>Get-CsVoiceRoute</strong></p></td>
</tr>
<tr class="odd">
<td><p>Utilizzo PSTN</p></td>
<td><p><strong>Get-CsPstnUsage</strong></p></td>
</tr>
<tr class="even">
<td><p>URL</p></td>
<td><p><strong>Get-CsSimpleUrlConfiguration</strong></p></td>
</tr>
<tr class="odd">
<td><p>Criteri di accesso esterno</p></td>
<td><p><strong>Get-CsExternalAccessPolicy</strong></p></td>
</tr>
<tr class="even">
<td><p>Criteri di archiviazione</p></td>
<td><p><strong>Get-CsArchivingPolicy</strong></p></td>
</tr>
</tbody>
</table>

