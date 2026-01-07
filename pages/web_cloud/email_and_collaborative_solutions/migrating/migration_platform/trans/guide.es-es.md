---
title: "Migrar direcciones de correo electrónico de una plataforma de correo electrónico OVHcloud a otra"
excerpt: "Descubra cómo migrar direcciones de correo electrónico de una plataforma Exchange o E-mail Pro a otra plataforma Exchange, E-mail Pro, MX Plan o Zimbra"
updated: 2025-12-22
---

## Objetivo

Desea migrar sus direcciones de correo electrónico de una plataforma Exchange o E-mail Pro a otra plataforma Exchange, E-mail Pro o MX Plan. Encontrará en esta guía un proceso de migración en dos fases:

1. **Configurar la plataforma de destino**.
2. **Migrar las cuentas de correo electrónico** de su plataforma actual a la nueva.

![email-migration](images/migration_platform01.gif){.thumbnail}

> [!primary]
>
> Para migrar una solución MX Plan a una plataforma Exchange o E-mail Pro, le invitamos a seguir nuestra guía [Migrar una dirección de correo electrónico MX Plan a una cuenta E-mail Pro o Exchange](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel).
>

**Descubra cómo migrar direcciones de correo electrónico de una plataforma Exchange o E-mail Pro a otra plataforma Exchange o E-mail Pro.**

## Requisitos

- Disponer de una plataforma **"fuente"** con cuentas configuradas de [Exchange](/links/web/emails-hosted-exchange) o [E-mail Pro](/links/web/email-pro) o [Zimbra](/links/web/zimbra).
- Disponer de una plataforma de **"destino"** con cuentas de [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) o MX Plan (a través de la oferta MX Plan o incluida en una oferta de [alojamiento web OVHcloud](/links/web/hosting)). Esta plataforma debe disponer de cuentas no configuradas o disponibles para acoger las direcciones de correo electrónico que deben migrarse.
- Estar conectado a su [espacio cliente OVHcloud](/links/manager).

## Procedimiento

### Configurar la plataforma de destino

> [!warning]
>
> Antes de comenzar su migración, si acaba de pedir su nueva oferta de correo electrónico, primero agregue el nombre de dominio a su plataforma de correo electrónico. Si migra a una plataforma MX Plan, el nombre de dominio asociado siendo "fijo", puede pasar directamente a la [siguiente etapa](#accountsmigration).
>
> Seleccione la pestaña `Domaines associés`{.action} o `Domaine`{.action} en su plataforma, y haga clic en `Ajouter un domaine`{.action}. Una vez que el nombre de dominio se haya agregado, asegúrese de que la mención `OK` o `Actif`{.action} esté bien presente en la columna `Statut`.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Para más detalles sobre la adición de un nombre de dominio, siga [la guía E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [la guía Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) o [la guía Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### Migrar las cuentas de correo electrónico <a name="accountsmigration"></a>

La migración de sus cuentas de correo electrónico se realizará en 3 grandes etapas: **Renombrar** la cuenta de correo electrónico de origen, **crear** la nueva cuenta de correo electrónico y **migrar** de la plataforma de origen a la nueva.

![email-migration](images/migration_platform03.gif){.thumbnail}

> [!warning]
>
> Caso particular:
>
> - Si debe migrar **una cuenta Exchange o Zimbra PRO** a una cuenta **E-mail Pro** o **Zimbra STARTER**, debe asegurarse de que sus cuentas de correo electrónico no excedan los 10 Go (E-mail Pro) o 15 Go (Zimbra STARTER). Las funciones colaborativas, la sincronización de calendarios y contactos no están presentes en E-mail Pro o Zimbra STARTER y no pueden migrarse.
> - Si debe migrar **una cuenta Exchange, E-mail Pro o Zimbra** a una cuenta **MX Plan**, debe asegurarse de que su cuenta de correo electrónico no exceda los 5 Go. Las funciones colaborativas, la sincronización de calendarios y contactos no están presentes en MX Plan y no pueden migrarse.

#### Renombrar

Renombre la cuenta de correo electrónico a migrar con un nombre provisional (ejemplo: para migrar la cuenta de correo *john.smith@mydomain.ovh*, renómbrela en *john.smith01@mydomain.ovh*).

En la pestaña `Comptes e-mail`{.action} de su plataforma de correo electrónico, haga clic en el botón `...`{.action} y luego en `Modifier`{.action}.

![email-migration](images/migration_platform04.png){.thumbnail}

#### Crear

Cree su dirección de correo electrónico en la nueva cuenta de su plataforma E-mail Pro, Exchange o MX Plan (tomando el ejemplo anterior, creará *john.smith@mydomain.ovh* en su nueva plataforma).

En la pestaña `Comptes e-mail`{.action} de su plataforma, haga clic en el botón `...`{.action}, a la derecha de la cuenta de correo electrónico de destino, y luego en `Modifier`{.action}.

![email-migration](images/migration_platform05.png){.thumbnail}

#### Migrar

> [!warning]
> 
> Solo los datos de sus cuentas de correo electrónico se migrarán (correos, contactos, calendarios, reglas de bandeja de entrada, etc.). Las funcionalidades vinculadas a su plataforma deberán ser recreadas en la nueva plataforma :
>
> - [Alias](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/feature_redirections) 
> - [Delegaciones de derechos](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_delegation) 
> - [Grupos](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_groups)
> - Contactos externos
> - [Pie de página](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_footers)

Migre la cuenta de correo electrónico "fuente" a la cuenta de su nueva plataforma utilizando nuestra herramienta [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Para más información sobre OMM, consulte nuestra guía [Migrar cuentas de correo electrónico mediante OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![email-migration](images/migration_platform06.png){.thumbnail}

El tiempo de migración depende de la cantidad de datos a migrar hacia su nueva cuenta. Puede variar desde unos minutos hasta varias horas.

Compruebe, después de la migración, que puede recuperar todos sus elementos conectándose al webmail en la dirección [Webmail](/links/web/email).

Una vez realizada la migración, puede conservar o eliminar la cuenta de origen con el nombre provisional.

Si desea eliminarla, diríjase a la pestaña `Comptes e-mail`{.action} de su plataforma de correo electrónico de origen, haga clic en el botón `...`{.action} y luego en `Réinitialiser ce compte`{.action}.

### Verificar o modificar la configuración de su dominio

En esta etapa, sus direcciones de correo electrónico deben ya estar migradas y funcionales. Por seguridad, le invitamos a asegurarse de que la configuración de su dominio es correcta consultando su espacio cliente.

Para ello, seleccione el servicio E-mail Pro, Exchange o Zimbra concernido, y diríjase a la pestaña `Domaines associés`{.action} o `Domaine`{.action} en su plataforma. Verifique la sección o la columna `Diagnostic`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Si acaba de realizar la migración o de modificar un registro DNS de su dominio, es posible que la visualización en el [espacio cliente OVHcloud](/links/manager) necesite algunas horas para actualizarse.
>

Para modificar la configuración, haga clic en el punto rojo y realice la manipulación solicitada. Esta última necesita un tiempo de propagación de 4 a 24 horas máximo antes de ser plenamente efectiva.

![email-migración](images/check_the_dns_records_associated_domains.png){.thumbnail}

### Utilizar sus direcciones de correo electrónico migradas

Solo le queda utilizar sus direcciones de correo electrónico migradas. Para ello, OVHcloud pone a disposición una aplicación en línea (_web app_) accesible en la dirección [Webmail](/links/web/email). Debe introducir allí las identificaciones relativas a su dirección de correo electrónico.

Si ha configurado uno de los cuentas migradas en un cliente de correo (ejemplo: Outlook, Thunderbird), debe configurarlo de nuevo. Las informaciones de conexión al servidor OVHcloud han cambiado tras la migración.

> [!primary]
>
> También puede migrar manualmente direcciones de correo electrónico a OVHcloud utilizando nuestra herramienta [OVHcloud Mail Migrator (OMM)](/links/web/omm). Para ello, debe disponer de las informaciones (usuario, contraseña, servidores) del correo electrónico de origen y del correo electrónico de destino.
>

## Más información

[Gestionar los contactos de sus servicios](/pages/account_and_service_management/account_information/managing_contacts).

[Primeros pasos con la oferta E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Primeros pasos con la oferta Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Primeros pasos con la oferta Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Interactúe con nuestra [comunidad de usuarios](/links/community).