﻿---
title: 'Lync Server 2013: Bypass multimediale e controllo di ammissione di chiamata'
TOCTitle: Bypass multimediale e controllo di ammissione di chiamata
ms:assetid: 120b2a2b-5f97-4735-a2ee-0f849feb8c1d
ms:mtpsurl: https://technet.microsoft.com/it-it/library/Gg398203(v=OCS.15)
ms:contentKeyID: 49299733
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Bypass multimediale e controllo di ammissione di chiamata in Lync Server 2013

 

_**Ultima modifica dell'argomento:** 2012-10-05_

Il bypass multimediale (o Media Bypass, ovvero la possibilità di ignorare il Mediation Server) e il servizio Controllo di ammissione di chiamata interagiscono per gestire il controllo della larghezza di banda per i supporti di chiamata. Il bypass multimediale facilita il flusso multimediale su buoni collegamenti. Il servizio Controllo di ammissione di chiamata gestisce il traffico sui collegamenti con vincoli di larghezza di banda. Poiché le due funzionalità si escludono a vicenda, è necessario ricordarsi dell'una quando si pianifica l'altra. Sono supportate le combinazioni seguenti:

  - Il controllo di ammissione di chiamata e il bypass multimediale sono entrambi abilitati. Il secondo deve essere impostato su **Utilizza configurazione siti e aree** . Tali informazioni sui siti e sulle aree sono le stesse utilizzate per il controllo di ammissione di chiamata.
    
    Se si abilita il controllo di ammissione di chiamata, non sarà possibile selezionare **Ignora sempre** e viceversa perché le due configurazioni si escludono reciprocamente. In altri termini, solo una delle due funzionalità verrà applicata a una determinata chiamata PSTN. Viene innanzitutto effettuata una verifica per determinare se il bypass multimediale sia applicabile alla chiamata. In caso affermativo, non viene utilizzato il controllo di ammissione di chiamata. Questo comportamento è logico in quanto, se una chiamata è idonea per il bypass, utilizza per definizione una connessione su cui il controllo di ammissione di chiamata non è necessario. Se il bypass non è applicabile alla chiamata, ovvero se gli ID bypass del client e del gateway non corrispondono, viene utilizzato il controllo di ammissione di chiamata.

  - Il controllo di ammissione di chiamata non è abilitato e il bypass multimediale è impostato su **Ignora sempre** .
    
    In questa configurazione le subnet di client e trunk sono mappate a un solo ID bypass, che viene calcolato dal sistema.

  - Il controllo di ammissione di chiamata non è abilitato e il bypass multimediale è impostato su **Utilizza configurazione siti e aree** .
    
    Quando è abilitata l'impostazione **Utilizza configurazione siti e aree** , la determinazione della possibilità di applicare il bypass funziona essenzialmente nello stesso modo, indipendentemente dal fatto che il controllo di ammissione di chiamata sia abilitato o meno. In altri termini, per una determinata chiamata PSTN, la subnet del client è mappata a un particolare sito e viene estratto l'ID bypass di tale subnet. Analogamente, la subnet del gateway è mappata a un particolare sito e viene estratto l'ID bypass di quella subnet. Il bypass verrà applicato per la chiamata solo se i due ID bypass sono identici, altrimenti non verrà utilizzato.
    
    Anche se il controllo di ammissione di chiamata è disabilitato a livello globale, è necessario definire criteri di larghezza di banda per ogni sito e collegamento se si desidera utilizzare la configurazione dei siti e delle aree per controllare la decisione di applicare o meno il bypass. Il valore effettivo del vincolo di larghezza di banda o la relativa modalità non è importante. Lo scopo finale è avere il sistema che calcola automaticamente ID bypass diversi da associare a impostazioni locali diverse non connesse perfettamente. Se si stabilisce un vincolo di larghezza di banda, significa per definizione che un collegamento non è ben connesso.

  - Il controllo di ammissione di chiamata è abilitato e il bypass multimediale non è abilitato. Questa situazione si verifica esclusivamente se tutti i gateway e i sistemi IP-PBX non sono ben connessi o non soddisfano altri requisiti per il bypass multimediale. Per informazioni dettagliate su tali requisiti, vedere [Requisiti tecnici per il bypass multimediale in Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md).

## Vedere anche

#### Concetti

[Panoramica del bypass multimediale in Lync Server 2013](lync-server-2013-overview-of-media-bypass.md)  
[Modalità di bypass multimediale in Lync Server 2013](lync-server-2013-media-bypass-modes.md)  
[Requisiti tecnici per il bypass multimediale in Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md)

