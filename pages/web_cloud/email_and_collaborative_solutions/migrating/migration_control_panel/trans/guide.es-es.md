---
title: 'Migrar una dirección de correo electrónico MX Plan a una cuenta de correo electrónico profesional, Exchange o Zimbra'
excerpt: 'Descubra cómo migrar una dirección de correo electrónico MX Plan a una cuenta de correo electrónico profesional, Exchange o Zimbra'
updated: 2025-12-22
---

## Objetivo

OVHcloud ofrece varias soluciones de correo electrónico: MX Plan (vendido por separado o incluido en una oferta de alojamiento web), correo electrónico profesional, Exchange y Zimbra. Cada una de ellas dispone de funcionalidades propias y puede adaptarse a distintos usos. ¿Sus necesidades han evolucionado? OVHcloud pone a su disposición una herramienta de migración que le permite pasar de una solución a otra.

**Descubra cómo migrar una dirección de correo electrónico MX Plan a una cuenta de correo electrónico profesional o Exchange.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) permite migrar sus mensajes de un servidor de correo electrónico a otro.<br>
> Si sus correos electrónicos están almacenados únicamente de forma local (configuración en POP o archivo local), puede realizar un [export desde su software de correo electrónico](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), y luego [importar su archivo PST a través de OMM](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) o [importar directamente desde su software de correo electrónico](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Requisitos

- Tener una dirección de correo electrónico MX Plan (a través de la oferta MX Plan o incluida en una oferta de [alojamiento web OVHcloud](/links/web/hosting)).
- Tener un servicio [Exchange](/links/web/emails-hosted-exchange), [Correo electrónico profesional](/links/web/email-pro) con al menos una cuenta no configurada (que aparecerá en la forma « @configureme.me ») o [Zimbra](/links/web/zimbra).
- **No haber configurado ninguna redirección en la dirección de correo electrónico MX Plan que desee migrar**.
- Estar conectado a su [espacio cliente OVHcloud](/links/manager).

## Procedimiento

### Etapa 1: delimitar su proyecto

Las soluciones de correo profesional y Exchange comparten una base común de funcionalidades. No obstante, existen diferencias según los casos de uso. Al elegir una dirección Exchange, dispone de todas las funciones colaborativas, como la sincronización del calendario y de los contactos. La solución de correo profesional, por su parte, ofrece algunas de estas funciones, pero únicamente para su uso a través de un webmail.

Antes de continuar, es importante saber a qué oferta desea migrar sus direcciones de correo MX Plan. Para ayudarle en esta elección, consulte la página de [soluciones de correo profesional de OVHcloud](/links/web/emails), que ofrece un comparativo detallado de las ofertas. Tiene la posibilidad de combinar soluciones y, por tanto, utilizar para el mismo nombre de dominio una o varias cuentas de correo profesional y Exchange. Además, si debe migrar varias cuentas, le recomendamos que establezca un plan de migración.

### Etapa 2: pedir sus cuentas de correo profesional o Exchange

Este paso es opcional si ya dispone de un servicio Exchange o de correo profesional al que realizar esta migración.

En caso contrario, inicie sesión en su [espacio cliente OVHcloud](/links/manager), y pida el servicio de correo profesional o Exchange que desee. Siga los distintos pasos y espere hasta la instalación del servicio. Se le enviará un correo electrónico al finalizar este proceso.

> [!primary]
>
> Una vez que el correo esté pedido, déjelo en la forma « @configureme.me » al principio. De hecho, se renombrará durante la migración.
>

### Etapa 3: Realizar la migración

Antes de comenzar su migración, deberá identificar la versión del MX Plan desde la que migra.

> [!primary]
>
> La tecnología de correo de su oferta MX Plan puede variar según la fecha de activación de su oferta o si ha tenido lugar recientemente una migración. Esta tecnología se distingue especialmente por la interfaz de su webmail. Para identificarla desde su espacio cliente, siga estos pasos :
>
> 1. Inicie sesión en su [espacio cliente OVHcloud](/links/manager).
> 1. Vaya a la sección `Web Cloud`{.action}.
> 1. Haga clic en `MX Plan`{.action}.
> 1. Seleccione el dominio correspondiente.
> 1. El apartado `Información general`{.action} se selecciona por defecto.
> 1. Anote la tecnología utilizada bajo la mención **Webmail** en el recuadro `Suscripción`.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Migración manual de una oferta MX Plan a Exchange, correo profesional o Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> Esta sección se aplica a todos los servicios MX Plan que utilizan la tecnología de webmail Rouncube, Zimbra u OWA.
>
> Sin embargo, si desea migrar un servicio MX Plan que utilice el webmail Roundcube a una plataforma Email Pro o Exchange OVHcloud, siga la sección « [Migración automática de una oferta MX Plan Roundcube a Exchange o Email Pro](#roundcube-mxplan) » de este guía.

> [!warning]
>
> Si acaba de pedir su nueva oferta de correo, añada primero el nombre de dominio a su plataforma de correo, antes de comenzar su migración. <br> - *Por ejemplo, para migrar la cuenta « myemail@mydomain.ovh », debe añadir el nombre de dominio « mydomain.ovh » a su plataforma.*
>
> Seleccione la pestaña `Dominios asociados`{.action} o `Dominio`{.action} en su plataforma, y haga clic en `Añadir un dominio`{.action}. Una vez que el nombre de dominio esté añadido, asegúrese de que la mención `OK` o `Activo`{.action} esté presente en la columna `Estado`.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Para más detalles sobre la adición de un nombre de dominio, siga [el guía de correo profesional](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [el guía de Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) o [el guía de Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

La migración de su MX Plan se realizará en 3 grandes etapas, **Renombrar**, **Crear** y **Migrar**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Renombre** la cuenta MX Plan a migrar con un nombre provisional ( ejemplo: para migrar la cuenta MX plan *john.smith@mydomain.ovh*, renómbrela en *john.smith01@mydomain.ovh*).

En la pestaña `Cuentas de correo`{.action} de su plataforma MX Plan, haga clic en el botón `...`{.action} y luego en `Modificar`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> La modificación de la cuenta no es inmediata, espere hasta que termine la operación antes de pasar al siguiente paso.

2\. **Cree** su dirección de correo en la nueva cuenta de su plataforma de correo profesional o Exchange (tomando el ejemplo anterior, creará *john.smith@mydomain.ovh* en su nueva plataforma).

En la pestaña `Cuentas de correo`{.action} de su plataforma de correo profesional o Exchange, haga clic en el botón `...`{.action} y luego en `Modificar`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migre** la cuenta MX Plan a la cuenta de su nueva plataforma mediante nuestra herramienta [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Para más información sobre OMM, consulte nuestro guía [Migrar cuentas de correo mediante OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

El plazo de migración depende de la cantidad de contenido a migrar a su nueva cuenta. Puede variar desde unos minutos hasta varias horas.

Compruebe, después de la migración, que puede acceder a sus elementos conectándose al webmail en la dirección [Webmail](/links/web/email)

Puede conservar o eliminar la cuenta de origen con el nombre provisional después de esta migración.

Si desea eliminarla, vaya a la pestaña `Cuentas de correo`{.action} de su MX Plan, haga clic en el botón `...`{.action} y luego en `Reiniciar esta cuenta`{.action}.

#### 3.2 Migración automática de una oferta MX Plan Roundcube a Exchange o Email Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> Esta sección se aplica únicamente a los servicios MX Plan que utilizan la tecnología de webmail Rouncube.

> [!primary]
>
> Su cuenta OVHcloud debe ser previamente contacto administrador **y** contacto técnico del servicio MX plan a migrar, **así como** del servicio de correo profesional o Exchange al que migra.
>
> Para más información sobre los cambios de contactos, consulte nuestro guía para [gestionar los contactos de sus servicios](/pages/account_and_service_management/account_information/managing_contacts).
>

La migración puede realizarse desde dos interfaces:<br>

- **la del asistente de configuración de Exchange alojado**, únicamente si acaba de pedir un servicio de Exchange alojado y no ha configurado nada en este último;
- **la del MX Plan**, desde que disponga de un servicio de correo profesional o Exchange (ya configurado o no) y de una dirección MX Plan que desee migrar.

> Para recordar, antes de comenzar la migración, asegúrese de que no esté configurada ninguna **redirección** ni ningún **contestador** en su MX Plan.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Una vez que esté preparado, continúe leyendo esta documentación según la interfaz seleccionada. Le recordamos que el plazo de migración depende de la cantidad de contenido a migrar a su nueva cuenta. Puede variar desde unos minutos hasta varias horas.

> [!warning]
>
> Una vez confirmada la migración, ya no podrá acceder a su dirección de correo MX Plan anterior ni cancelar el proceso de migración. Le recomendamos encarecidamente realizar esta operación en un horario adecuado.
>
> Aunque ya no podrá acceder a su dirección de correo actual, los mensajes ya recibidos así como los que se reciban no se perderán. Todos estarán inmediatamente accesibles desde su nueva cuenta.
>

##### **Migración desde el asistente de configuración de Exchange**

Para acceder a él, seleccione en el [espacio cliente OVHcloud](/links/manager) el servicio correspondiente. El asistente debería aparecer para ayudarle a configurar su nuevo servicio Exchange. Durante este proceso, podrá seleccionar las cuentas de correo MX Plan a migrar.

Si el asistente de configuración no aparece, aparecerán las informaciones generales del servicio Exchange. En este caso, deberá realizar la migración de sus cuentas a través de la interfaz MX Plan.

##### **Migración desde la interfaz MX Plan**

Para realizar la migración desde esta interfaz, vaya a la sección `Correos`{.action} de su espacio cliente OVHcloud. Elija entonces el servicio que lleva el nombre de dominio de sus direcciones de correo. Haga clic en el logotipo con forma de engranaje en la línea de la cuenta de correo afectada (también llamada cuenta de origen) y luego en `Migrar la cuenta`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

En la ventana que aparece, seleccione el servicio de destino (al que desea migrar la dirección) y haga clic en `Siguiente`{.action}. Si dispone de al menos una cuenta « libre » (es decir, aún no configurada), la migración se realizará en una de estas cuentas. Una vez hecho esto, lea la información que aparece, confírmela y haga clic en `Siguiente`{.action} para continuar la operación.

Si no dispone de ninguna cuenta « libre », aparecerá un botón `Pedir cuentas`{.action}. Siga los pasos y espere a que las cuentas estén instaladas para realizar de nuevo la operación.

Confirme finalmente la contraseña de la dirección de correo de origen (la que desea migrar) y haga clic en `Migrar`{.action}. Esta operación deberá repetirse tantas veces como sea necesario para migrar otras cuentas.

![exchange](images/account_migration_steps.png){.thumbnail}

### Etapa 4: verificar o modificar la configuración de su dominio

En este paso, sus direcciones de correo ya deberían estar migradas y funcionales. Por seguridad, le invitamos a asegurarse de que la configuración de su dominio es correcta consultando su espacio cliente.

Para ello, seleccione el servicio de correo profesional, Exchange o Zimbra correspondiente, y vaya a la pestaña `Dominios asociados`{.action} o `Dominio`{.action} en su plataforma. Compruebe la sección o la columna `Diagnóstico`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Si acaba de realizar la migración o de modificar un registro DNS de su dominio, es posible que la visualización en el [espacio cliente OVHcloud](/links/manager) necesite algunas horas para actualizarse.
>

Para modificar la configuración, haga clic en el botón rojo y realice la operación solicitada. Esta última necesita un tiempo de propagación de 4 a 24 horas como máximo antes de ser plenamente efectiva.

### Etapa 5: utilizar sus direcciones de correo migradas

Le queda solamente utilizar sus direcciones de correo migradas. Para ello, OVHcloud pone a disposición una aplicación en línea (_web app_) accesible en la dirección [Webmail](/links/web/email). Deberá introducir allí las identificaciones relativas a su dirección de correo.

Si ha configurado uno de los correos migrados en un cliente de correo (como Outlook), deberá configurarlo de nuevo. Las informaciones de conexión al servidor OVHcloud han cambiado tras la migración. Para ayudarle en sus operaciones, consulte nuestra documentación desde las secciones de los guías dedicadas a [correo profesional](/products/web-cloud-email-collaborative-solutions-email-pro) y [Exchange alojado](/products/web-cloud-email-collaborative-solutions-mx-plan). Si no puede reconfigurar la cuenta inmediatamente, el acceso mediante la aplicación en línea sigue siendo posible.

### Organización del contenido de sus direcciones de correo tras una migración <a name="content-after-migration"></a>

Cuando se conecte por primera vez a su nueva cuenta de correo, el contenido migrado puede estar parcialmente oculto. Para mostrar todos los elementos, desde el webmail, haga clic en la flecha junto a la `Bandeja de entrada` para revelar los subdirectorios. El contenido migrado de su antigua cuenta de correo debería aparecer.

![exchange](images/owa_migrate_content.png){.thumbnail}

Los directorios por defecto, como « elementos enviados » o « papelera » aparecen en inglés (« Sent items » y « Trash »), a excepción de los directorios que haya creado.

Después de una migración, no dude en explorar todos los directorios y subdirectorios de su cuenta para verificar que todos los elementos están presentes.

### Migrar Manualmente

También puede migrar manualmente sus direcciones de correo a su nueva oferta de correo OVHcloud utilizando únicamente su software de correo. Apóyese en nuestro guía [Migrar manualmente su dirección de correo](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). Le recomendamos encarecidamente utilizar este método únicamente cuando los métodos principales no sean posibles.

## Más información

[Gestionar los contactos de sus servicios](/pages/account_and_service_management/account_information/managing_contacts).

[Primeros pasos con la oferta de correo profesional](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Primeros pasos con la oferta de Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Primeros pasos con la oferta de Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Interactúe con nuestra [comunidad de usuarios](/links/community).