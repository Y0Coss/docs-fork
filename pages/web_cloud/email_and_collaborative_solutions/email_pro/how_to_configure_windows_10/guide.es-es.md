---
title: "E-mail Pro - Configurar su cuenta de E-mail Pro en el nuevo Outlook para Windows"
excerpt: "Descubra cómo configurar su dirección de E-mail Pro en el Nuevo Outlook para Windows"
updated: 2025-09-02
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
</style>

## Objetivo

Las direcciones de correo electrónico de la oferta [E-mail Pro](/links/web/email-pro) se pueden configurar en un cliente de mensajería compatible. Esto le permite enviar y recibir mensajes desde la aplicación de su elección.

El **Nuevo Outlook** reemplaza desde el 1 de enero de 2025 la aplicación **Correo** en Windows. Para obtener más información sobre este tema, consulte la página oficial de Microsoft: "[Outlook para Windows: El futuro del correo, calendario y Personas en Windows 11](https://support.microsoft.com/office/outlook-pour-windows-l-avenir-du-courrier-du-calendrier-et-des-personnes-sur-windows-11-715fc27c-e0f4-4652-9174-47faa751b199)".

**Descubra cómo configurar su dirección de E-mail Pro en el Nuevo Outlook para Windows.**

## Requisitos

- Tener una dirección [E-mail Pro](/links/web/email-pro).
- Tener el [Nuevo Outlook](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) para Windows.
- Poseer las credenciales relacionadas con la dirección de correo electrónico que desea configurar.

> [!warning]
>
> Esta documentación se aplica únicamente al **Nuevo Outlook** y no al "[Outlook Clásico](https://support.microsoft.com/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5)" disponible en la suite Microsoft 365 o instalado previamente en su computadora.

/// details | Información relacionada con la gestión y configuración de los servicios OVHcloud

OVHcloud pone a su disposición servicios cuya configuración, gestión y responsabilidad recaen en usted. Por lo tanto, es su responsabilidad asegurar su correcto funcionamiento.

Le proporcionamos esta guía para acompañarlo en las tareas más comunes. Sin embargo, le recomendamos contactar a un [socio especializado](https://marketplace.ovhcloud.com/c/support-collaboration) y/o al proveedor del servicio si encuentra dificultades. Tenga en cuenta que no podremos proporcionar asistencia. Para obtener más información, consulte la sección "Más información" de esta guía.

///

## Procedimiento

### Agregar la cuenta <a name="add-account"></a>

> [!warning]
>
> En nuestro ejemplo, usamos el nombre del servidor: pro?.mail.ovh.net. Debe reemplazar el "?" con el número correspondiente al servidor de su servicio E-mail Pro.
> 
> Encuentre este número en su [Panel de Control OVHcloud](/links/manager), en la sección `Web Cloud`{.action} y luego `E-mail Pro`{.action}. El nombre del servidor es visible en el marco **Conexión** de la pestaña `Información General`{.action}.

> [!tabs]
> **Etapa 1**
>> - Abra Outlook. En el panel izquierdo, haga clic en `Agregar una cuenta`{.action} para iniciar la configuración.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-400}
>>
> **Etapa 2**
>> - Introduzca su dirección de correo electrónico y haga clic en `Continuar`{.action}.
>> - Introduzca su contraseña y haga clic en el botón `Mostrar más`{.action}.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-400}
>>
> **Etapa 3**
>> - Introduzca los siguientes parámetros:
>>    - **Servidor de entrada IMAP**: pro?.mail.ovh.net
>>    - **Puerto**: 993
>>    - **Tipo de conexión segura**: SSL/TLS
>>    - **Nombre de usuario SMTP**: la dirección de correo electrónico que está agregando.
>>    - **Servidor de salida SMTP**: pro?.mail.ovh.net
>>    - **Puerto**: 587
>>    - **Tipo de conexión segura**: STARTTLS
>>    - **Contraseña**: no introduzca nada; se utilizará la contraseña ingresada anteriormente.
>> - Haga clic en `Continuar`{.action} para finalizar la configuración.
>>
>> ![outlook](images/configuration-newoutlook-windows-emp-03.png){.thumbnail .w-400}

### Utilizar la dirección de correo electrónico <a name="use-account"></a>

Una vez configurada la dirección de correo electrónico, ya puede usarla. Ahora puede enviar y recibir mensajes.

OVHcloud también ofrece una aplicación web que le permite acceder a su dirección de correo electrónico desde su navegador mediante la dirección [Webmail](/links/web/email). Puede iniciar sesión utilizando las credenciales de su dirección de correo electrónico.

### Modificar los ajustes existentes <a name="modify-settings"></a>

La aplicación Outlook no permite modificar los ajustes del servidor de su cuenta de correo electrónico.

Si su cuenta de correo electrónico ya está configurada y desea volver a configurarla, deberá eliminarla y recrearla:

- Haga clic en el icono de ajustes "⋮" en la parte inferior del panel izquierdo.
- En la sección "Tus cuentas", haga clic en `Gestionar`{.action} a la derecha de la dirección de correo electrónico correspondiente.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-400}

- Desplácese hacia abajo en la página.
- Haga clic en `Eliminar`{.action} para iniciar el proceso de eliminación.
- Determine si desea eliminar solo en este dispositivo o en todos los dispositivos que utilicen Outlook.

![outlook](images/configuration-newoutlook-windows-emp-05.png){.thumbnail .w-400}

> [!success]
>
> Una vez que haya eliminado su cuenta de correo electrónico, siga las instrucciones de la sección "[Agregar la cuenta](#add-account)" de esta documentación.

### Ajustes generales de envío y recepción <a name="settings-account"></a>

#### Ajustes de recepción IMAP y POP <a name="imap-pop"></a>

Para la recepción de correos electrónicos, al elegir el tipo de cuenta, le recomendamos usar **IMAP**. Sin embargo, también puede seleccionar **POP**.

Seleccione la pestaña correspondiente a su tipo de configuración:

> [!tabs]
> **Configuración IMAP**
>>
>> - **Nombre de usuario**: Introduzca la dirección de correo electrónico **completa**.
>> - **Contraseña**: Introduzca la contraseña de la dirección de correo electrónico.
>> - **Servidor de entrada**: pro?.mail.ovh.net (reemplace bien el "?" con el número de su servidor).
>> - **Puerto**: 993.
>> - **Tipo de seguridad**: SSL/TLS.
>>
> **Configuración POP**
>>
>> - **Nombre de usuario**: Introduzca la dirección de correo electrónico **completa**.
>> - **Contraseña**: Introduzca la contraseña de la dirección de correo electrónico.
>> - **Servidor de entrada**: pro?.mail.ovh.net (reemplace bien el "?" con el número de su servidor).
>> - **Puerto**: 995.
>> - **Tipo de seguridad**: SSL/TLS.

#### Ajustes de envío SMTP <a name="smtp"></a>

Para el envío de correos electrónicos, encuentre a continuación los parámetros **SMTP** que debe utilizar:

**Configuración SMTP**

- **Nombre de usuario**: Introduzca la dirección de correo electrónico **completa**.
- **Contraseña**: Introduzca la contraseña de la dirección de correo electrónico.
- **Servidor de salida**: pro?.mail.ovh.net (reemplace bien el "?" con el número de su servidor).
- **Puerto**: 587.
- **Tipo de seguridad**: STARTTLS.

## Más información

> [!primary]
>
> Para obtener más información sobre la configuración de una dirección de correo electrónico desde el cliente de mensajería Nuevo Outlook en Windows, consulte [el centro de ayuda de Microsoft](https://support.microsoft.com/office/start-using-new-outlook-for-windows-4395454d-cb2f-4c16-bb24-fa4bb36650ae).

[Primeros pasos con la solución E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)

Para servicios especializados (SEO, desarrollo, etc.), contacte con los [socios de OVHcloud](/links/partner).

Si desea recibir asistencia para usar y configurar sus soluciones OVHcloud, le recomendamos consultar nuestras diferentes [ofertas de soporte](/links/support).

Únase a nuestra [comunidad de usuarios](/links/community).