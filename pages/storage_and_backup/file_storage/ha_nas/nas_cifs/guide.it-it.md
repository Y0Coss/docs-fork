---
title: Montare un NAS-HA tramite condivisione CIFS
excerpt: Configurare e montare un NAS-HA tramite il protocollo CIFS
updated: 2025-10-09
---

## Obiettivo

**Questa guida ti mostra come configurare e montare il tuo spazio di archiviazione NAS-HA OVHcloud tramite il protocollo CIFS.**

## Prerequisiti

- Un [server dedicato](/links/bare-metal/bare-metal) **o** un [VPS](/links/bare-metal/vps) **o** un'[istanza Public Cloud](/links/public-cloud/public-cloud).
- Un'offerta [NAS-HA](/links/storage/nas-ha).

## Procedura

### Configurazione per Windows

- **Windows Server 2008** : clicca sul menu `Start`{.action} > `All the programs`{.action} > `Accessories`{.action} > `Command prompt`{.action}.
- **Windows Server 2012** : clicca sull'icona `Windows PowerShell`{.action} nella barra dei task.
- **Windows Server 2016** : clicca sul menu `Start`{.action} e poi sull'icona del `Windows PowerShell`{.action}.
- **Windows Server 2019** : clicca sul menu `Start`{.action} e poi sull'icona del `Windows PowerShell`{.action}.

Esegui questo comando:

```bash
net use z: \\CIFS_SERVER_IP\CIFS_PATH
```

#### Esempi

- Montaggio CIFS per un NAS-HA:

```bash
net use z: \\10.16.101.8\zpool-000206_PARTITION_NAME_1
```

> [!alert]
>
> L'utente SMB/CIFS è `nobody`, qualsiasi modifica dei diritti effettuata da questo utente può generare conflitti con i diritti NFS esistenti.
> 

Potrebbe essere visualizzato il seguente messaggio di errore:

```console
System error 1272 has occurred.

You can't access this shared folder because your organization's security policies block unauthenticated guest access. These policies help protect your PC from unsafe or malicious devices on the network.
```

> [!primary]
>
> Per correggere questo errore, è necessario modificare il registro di sistema di Windows. A tal fine, aprire l'editor del registro (regedit), quindi accedere alla chiave `HKLM\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters`.<br>
> Assegnare il valore "1" al parametro `AllowInsecureGuestAuth`.<br>
> Trova ulteriori informazioni su questo argomento sulle [pagine di supporto Microsoft](https://learn.microsoft.com/it-it/windows-server/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3).

### Configurazione per Linux

Connettiti tramite SSH al tuo server e digita il seguente comando:

```sh
mount -t cifs -o uid=root,gid=100,dir_mode=0700,username=root,password= //IP_SERVEUR_CIFS/CHEMIN_CIFS /mnt/FolderMount
```

> [!warning]
> 
> Per montare le condivisioni tramite nome host (anziché indirizzo IP), è necessario l'utilità `mount.cifs`. Di solito è inclusa nel pacchetto `cifs-utils`.
>
> `mount.cifs` è un wrapper che risolve i nomi host e aggiunge il parametro `ip=` ai parametri di montaggio trasmessi al kernel.
> 
> Senza `mount.cifs`, i tentativi di montaggio tramite nome host genereranno il seguente errore:
>
> ```text
> mount: /mnt/FolderMount: mount(2) system call failed: No route to host.
>        dmesg(1) may have more information after failed mount system call.
> ```
>

## Per saperne di più

[Domande frequenti sul NAS](/pages/storage_and_backup/file_storage/ha_nas/nas_faq)

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra [Community di utenti](/links/community).