---
title: "Zimbra Pro - Configurar su cuenta de correo electrónico mediante ActiveSync en Outlook clásico para Windows"
excerpt: "Descubra cómo configurar su dirección de correo electrónico Zimbra Pro en Outlook para Windows mediante el protocolo ActiveSync"
updated: 2025-12-17
---

<style>
details>summary {
    color:rgb(255,165,0) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
.w-600 {
  max-width:600px !important;
}
.h-500 {
  max-width:500px !important;
}
</style>

## Objetivo

Las cuentas Zimbra Pro pueden configurarse en Windows utilizando el protocolo ActiveSync, lo que le permite configurar todas las funcionalidades colaborativas de su dirección de correo electrónico de una sola vez. La aplicación Outlook para Windows permite consultar su cuenta de correo electrónico Zimbra Pro mediante el protocolo ActiveSync.

**Descubra cómo configurar su dirección de correo electrónico Zimbra Pro en Outlook para Windows mediante el protocolo ActiveSync.**

## Requisitos

- Disponer de una dirección de correo electrónico [Zimbra Pro](/links/web/emails-zimbra).
- Disponer de la aplicación [Outlook clásico](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) en Windows.
- Disponer de las credenciales relativas a la dirección de correo electrónico que desea configurar.

/// details | Información relativa a la gestión y configuración de los servicios de OVHcloud

OVHcloud pone a su disposición servicios cuya configuración, gestión y responsabilidad son suyas. Por lo tanto, le corresponde garantizar su buen funcionamiento.

Le proporcionamos este guía para ayudarle en las tareas habituales. Sin embargo, le recomendamos encarecidamente que se ponga en contacto con un [socio especializado](/links/transversal/marketplace-support-collaboration) y/o con el editor del servicio si tiene dificultades. De hecho, no podremos proporcionarle asistencia. Más información en la sección « [Más información](go-further) » de este guía.

///

## Procedimiento

> [!warning]
>
> Antes de comenzar su configuración, es importante señalar que la aplicación Outlook incluida gratuitamente con Windows 11 es incompatible con el protocolo ActiveSync, necesario para la configuración de una cuenta Zimbra Pro. Deberá utilizar la versión **Outlook clásico** para beneficiarse del soporte del protocolo ActiveSync.
>
> Para instalar Outlook clásico en su ordenador Windows, descárguelo desde la página de Microsoft « [Instalar o reinstalar Outlook clásico en un PC Windows](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) », e instálelo.
>
> Una vez finalizada la instalación, para distinguir las dos versiones cuando estén instaladas, escriba « Outlook » en la barra de búsqueda de Windows. Podrá entonces constatar la diferencia como se muestra a continuación.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Añadir la cuenta <a name="add-account"></a>

Para añadir una cuenta Zimbra Pro en Outlook clásico, siga los pasos que se indican a continuación pulsando sucesivamente en las pestañas que aparecen a continuación:

> [!tabs]
> **Paso 1**
>>
>> 1. Vaya al **panel de control** de Windows.
>> 2. Haga clic en `Cuentas de usuario`{.action}.
>> 3. Haga clic en `Correo`{.action}.
>> 4. Haga clic en `Cuentas de correo...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Paso 2**
>>
>> - Desde la ventana **Configuración de la cuenta**, en la pestaña `Correo`, haga clic en `Nuevo...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Paso 3**
>>
>> - Desde la ventana **Añadir una cuenta**, seleccione `Configuración manual o tipos de servidores adicionales`{.action}.
>> - Haga clic en `Siguiente`{.action} para continuar.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Paso 4**
>>
>> - Seleccione `Exchange ActiveSync`{.action}.
>> - Haga clic en `Siguiente`{.action} para continuar.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Paso 5**
>>
>> Introduzca las informaciones de conexión a su cuenta:
>>
>> - **Su nombre** : Defina un nombre de visualización.
>> - **Dirección de correo electrónico** : Introduzca su dirección de correo electrónico completa.
>> - **Servidor de correo** : Introduzca « zimbra1.mail.ovh.net ».
>> - **Nombre de usuario** : Introduzca su dirección de correo electrónico completa.
>> - **Contraseña** : Introduzca la contraseña asociada a su dirección de correo electrónico.
>>
>> Haga clic en `Siguiente`{.action} para finalizar la adición de la cuenta.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Paso 6**
>>
>> Su dirección de correo electrónico está ahora configurada para Outlook. Para beneficiarse de una sincronización completa de las funcionalidades de su cuenta Zimbra Pro, **descargue e instale** el módulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) ».
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Paso 7**
>>
>> Una vez instalado el módulo « [Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/) », inicie Outlook clásico.
>> La primera vez, aparecerá la ventana de configuración **Zimbra Server configuration Settings**. Complete las siguientes informaciones:
>>
>> - **Nombre del servidor** : Introduzca « zimbra1.mail.ovh.net ».
>> - **Dirección de correo electrónico** : Introduzca su dirección de correo electrónico completa.
>> - **Contraseña** : Introduzca la contraseña asociada a su dirección de correo electrónico.
>>
>> No es necesario modificar los demás parámetros. Haga clic en `Aplicar`{.action} para validar los parámetros y asegúrese de que sean correctos. Haga clic finalmente en `Aceptar`{.action} para acceder a Outlook y comenzar a utilizar su dirección de correo electrónico.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> Si experimenta un fallo de envío o recepción después de seguir los pasos de configuración anteriores, consulte la sección « [Modificar los parámetros existentes](#modify-settings) » de este guía.

### Utilizar la dirección de correo electrónico

Una vez que la dirección de correo electrónico esté configurada, puede comenzar a utilizarla. Puede enviar y recibir mensajes, así como gestionar sus calendarios y tareas.

OVHcloud también ofrece una aplicación web que permite acceder a su dirección de correo electrónico desde un navegador web. Puede conectarse al [webmail OVHcloud](/links/web/email) con las credenciales de su dirección de correo electrónico. Para cualquier pregunta sobre su uso, consulte nuestro guía « [Utilizar el webmail Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra) ».

### ¿Cómo modificar los parámetros existentes? <a name="modify-settings"></a>

Para modificar los parámetros de una cuenta de correo electrónico ya configurada, siga las instrucciones siguientes:

1. Vaya al **panel de control** de Windows.
1. Haga clic en `Cuentas de usuario`{.action}.
1. Haga clic en `Correo`{.action}.
1. Haga clic en `Cuentas de correo...`{.action}.
1. Seleccione la cuenta de correo electrónico deseada en la lista y haga clic en `Modificar...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Encuentre los parámetros en el **paso 7** del capítulo « [Añadir la cuenta](#add-account) ».

### ¿Cómo eliminar una cuenta de correo electrónico? <a name="delete-account"></a>

Para eliminar su cuenta de correo electrónico, siga las instrucciones siguientes:

1. Vaya al **panel de control** de Windows.
1. Haga clic en `Cuentas de usuario`{.action}.
1. Haga clic en `Correo`{.action}.
1. Haga clic en `Cuentas de correo...`{.action}.
1. Seleccione la cuenta de correo electrónico deseada en la lista y haga clic en `Eliminar`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Para poder eliminar su cuenta de correo electrónico, es necesario que no sea la cuenta de correo electrónico predeterminada.

## Más información <a name="go-further"></a>

> [!primary]
>
> Para obtener más información sobre la configuración de una dirección de correo electrónico desde la aplicación Outlook en Windows, consulte el [centro de ayuda de Microsoft](https://support.microsoft.com/fr-fr/office/ajouter-un-compte-de-messagerie-%C3%A0-outlook-pour-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

Para servicios especializados (posicionamiento, desarrollo, etc.), póngase en contacto con los [socios de OVHcloud](/links/partner).

Si desea beneficiarse de una asistencia en el uso y la configuración de sus soluciones OVHcloud, le proponemos consultar nuestras diferentes [ofertas de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).