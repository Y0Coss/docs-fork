60 - Haber contratado una de las ofertas de correo electrónico siguientes:
    - MX Plan OVHcloud (disponible a través de una [oferta de alojamiento Web Cloud](/links/web/hosting)), un [alojamiento gratuito 100M](/links/web/domains-free-hosting) o una oferta MX Plan adquirida por separado.
    - [Exchange](/links/web/emails-hosted-exchange) o [Private Exchange](/links/web/emails-hosted-exchange).
    - [E-mail Pro](/links/web/email-pro).
    - [Zimbra](/links/web/zimbra).
    - Una oferta de correo electrónico fuera de OVHcloud que disponga de DKIM.

85 - [Configurar el DKIM automáticamente para una oferta de correo electrónico de OVHcloud](#auto-dkim)
- [Configurar el DKIM mediante API para una oferta de correo electrónico de OVHcloud](#internal-dkim)
    - [API - Configuración completa del DKIM](#firststep)
        - [Para MX Plan y Zimbra](#confemail)
        - [Para Exchange](#confex)
        - [Para E-mail Pro](#confemp)
    - [API - Los distintos estados del DKIM](#dkim-status)
    - [API - Activar o cambiar un selector DKIM](#enable-switch)
    - [API - Desactivar y eliminar el DKIM](#disable-delete)

106 Para comprender bien por qué el DKIM permite proteger sus intercambios de correo electrónico, es necesario entender cómo funciona. El DKIM utiliza el «**hashing**» y el «**cifrado asimétrico**» para crear una firma segura. La **plataforma de correo electrónico** y la **zona DNS** de su nombre de dominio ayudarán a transmitir la información del DKIM a sus destinatarios.

108 /// details | El hashing <a name="hash"></a>

118 ///

120 /// details | El cifrado asimétrico <a name="encrypt"></a>

136 ///

138 /// details | ¿Cómo se utilizan el hashing y el cifrado asimétrico para el DKIM? <a name="encrypt-and-hash"></a>

144 ///

146 /// details | ¿Por qué es necesario configurar los servidores DNS? <a name="dns-and-dkim"></a>

150 ///

152 /// details | ¿Qué es un selector DKIM? <a name="selector"></a>

165 ///

167 /// details | Ejemplo de un correo electrónico enviado utilizando DKIM <a name="example"></a>

177 ///

179 ### Configurar el DKIM automáticamente para una oferta de correo electrónico de OVHcloud <a name="auto-dkim"></a>

La configuración automática del DKIM está disponible para todas nuestras ofertas de correo electrónico:

- MX Plan incluida con un [alojamiento Web Cloud](/links/web/hosting), un [alojamiento gratuito 100M](/links/web/domains-free-hosting) o adquirida por separado.
- [Exchange](/links/web/emails).
- [E-mail Pro](/links/web/email-pro).
- [Zimbra](/links/web/zimbra).

Cuando configure su nombre de dominio en una solución de correo electrónico de OVHcloud, la configuración automática del DKIM se propone y se realiza por defecto si no la desactiva.

Si el DKIM no se ha activado cuando ha añadido un nombre de dominio a su plataforma de correo electrónico, deberá iniciar el proceso de configuración automática a través del área de cliente.

Haga clic en la pestaña inferior correspondiente a su oferta.

> [!tabs]
> **MX Plan**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. Haga clic en `MX Plan`{.action}.
>> 1. Seleccione el dominio correspondiente.
>> 1. Finalmente, vaya a la pestaña `Información general`{.action}.
>>
>> En el bloque **Información general**, puede observar que el indicador `DKIM` es rojo bajo la mención **Diagnóstico**.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Para activar el DKIM, simplemente haga clic en el indicador `DKIM` rojo y luego en `Validar`{.action} desde la ventana de activación que aparece.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> En el caso de que su nombre de dominio no esté gestionado en el mismo área de cliente de OVHcloud que su plataforma de correo electrónico o esté registrado fuera de OVHcloud, obtendrá la ventana siguiente:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> Esta le invita a introducir dos valores CNAME en la zona DNS del nombre de dominio, lo que permite vincular este nombre de dominio a los selectores DKIM de su servicio de correo electrónico. Es necesario introducir estos valores y asegurarse de que se hayan propagado antes de hacer clic en `Activar`{.action}.
>>
> **Exchange**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. En la sección `MICROSOFT`, haga clic en `Exchange`{.action}.
>> 1. Seleccione la plataforma correspondiente.
>> 1. Finalmente, vaya a la pestaña `Dominios asociados`{.action}.
>>
>> A la derecha del nombre de dominio correspondiente, puede observar que el indicador `DKIM` es rojo.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Para activar el DKIM, simplemente haga clic en el indicador `DKIM` rojo y luego en `Validar`{.action} desde la ventana de activación que aparece.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. Haga clic en `Email Pro`{.action}.
>> 1. Seleccione la plataforma correspondiente.
>> 1. Finalmente, vaya a la pestaña `Dominios asociados`{.action}.
>>
>> A la derecha del nombre de dominio correspondiente, puede observar que el indicador `DKIM` es rojo.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Para activar el DKIM, simplemente haga clic en el indicador `DKIM` rojo y luego en `Validar`{.action} desde la ventana de activación que aparece.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **Zimbra**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. Haga clic en `Zimbra Mail`{.action}.
>> 1. Finalmente, vaya a la pestaña `Dominio`{.action}.
>> 1. A la derecha del dominio correspondiente, haga clic en `⁝`{.action}, y luego en `Diagnóstico`{.action}.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/access.png){.thumbnail .w-400 .h-600}
>>
>> A la derecha de la mención `DKIM` en la pestaña correspondiente, debería observar una advertencia indicando que el DKIM no está configurado correctamente. Haga clic en la pestaña `DKIM`{.action} para acceder al estado de la configuración DKIM. Para corregir el error, debe añadir o modificar dos entradas DNS de tipo CNAME en la zona DNS del nombre de dominio asociado, según las informaciones visibles desde esta pestaña.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/dkim-cname-conf.png){.thumbnail .w-400 .h-600}
>>
>> > [!primary]
>> > **Consejo para crear un registro CNAME**
>> >
>> > Desde el [área de cliente de OVHcloud](/links/manager) donde se aloja el nombre de dominio de su servicio de correo electrónico, en la sección `Web Cloud`{.action}, haga clic en `Nombres de dominio`{.action} en la columna de la izquierda y seleccione el nombre de dominio correspondiente.<br>
>> > Seleccione la pestaña `Zona DNS`{.action} y haga clic en `Añadir una entrada`{.action} en la ventana que aparece. Elija `CNAME` y complete según los valores que haya anotado.

Para activar el DKIM, simplemente haga clic en el indicador `DKIM` rojo y luego en `Validar`{.action} desde la ventana de activación que aparece.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}

La activación automática del DKIM dura entre 30 minutos y 24 horas como máximo. Para verificar que su DKIM funciona correctamente, simplemente vaya a la sección de gestión del dominio mencionada en las pestañas anteriores y verifique que el indicador `DKIM` es verde o, para una oferta Zimbra, que la pestaña `DKIM` no muestra más el icono de advertencia.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto03.png){.thumbnail .w-400 .h-600}

Si han pasado más de 24 horas y su indicador `DKIM` sigue siendo rojo, consulte la sección [« ¿Por qué el DKIM no funciona y aparece en rojo en el área de cliente? »](#reddkim) de este guía.

### Configurar el DKIM mediante API para un correo electrónico de OVHcloud <a name="internal-dkim"></a>

Para una plataforma Exchange o E-mail Pro, debe recuperar primero la referencia de su plataforma para configurar su DKIM.

Haga clic en la pestaña inferior correspondiente a su oferta.

> [!tabs]
> **Exchange**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. En la sección `MICROSOFT`, haga clic en `Exchange`{.action}.
>> 1. Seleccione la plataforma correspondiente.
>>
>> Por defecto, el nombre de su plataforma corresponde a su referencia o será visible bajo el nombre que le haya asignado (ver imagen de abajo).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/general-information/dns-dkim-platform-exchange.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. Haga clic en `Email Pro`{.action}.
>> 1. Seleccione la plataforma correspondiente.
>>
>> Por defecto, el nombre de su plataforma corresponde a su referencia o será visible bajo el nombre que le haya asignado (ver imagen de abajo).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/email-pro/general-information/dns-dkim-platform-emailpro.png){.thumbnail .w-400 .h-600}

Asegúrese también de que el nombre de dominio que desea utilizar para sus correos electrónicos esté activo en la sección `Dominios asociados`{.action}.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dns-dkim-domain.png){.thumbnail .w-400 .h-600}

#### API - Configuración completa del DKIM <a name="firststep"></a>

Para configurar el DKIM, vaya a la [página de las API de OVHcloud](/links/console) y inicie sesión:

1. Haga clic en `Authentication`{.action} en la esquina superior izquierda.
1. Haga clic a continuación en `Login with OVHcloud SSO`{.action}.
1. Introduzca sus identificadores de OVHcloud.
1. Haga clic en el botón `Authorize`{.action} para autorizar las llamadas a las API desde este sitio.

> [!primary]
>
> Consulte nuestro guía « [Primeros pasos con las API de OVHcloud](/pages/manage_and_operate/api/first-steps) » si nunca ha utilizado las API.

Vaya a la sección `/email/domain/` (ofertas MX Plan y Zimbra), `/email/exchange` (oferta Exchange) o `/email/pro` (oferta E-mail Pro) de las API y escriba « dkim » en el campo `Filter` para mostrar únicamente las funciones API relacionadas con el DKIM.

Haga clic en la pestaña correspondiente a su oferta:

> [!tabs]
> **MX Plan y Zimbra**
>>
>> ![email](/pages/assets/screens/api/get-email-domain-domain-dkim.png){.thumbnail .w-400 .h-600}
>>
> **Exchange**
>>
>> ![email](/pages/assets/screens/api/get-email-exchange-organizationname-service-exchangeservice-domain-domainname-dkim.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> ![email](/pages/assets/screens/api/get-email-pro-service-domain-domainname-dkim.png){.thumbnail .w-400 .h-600}
>>

##### **Para MX Plan y Zimbra** <a name="confemail"></a>

Siga las **5 etapas** haciendo clic sucesivamente en cada una de las 5 pestañas siguientes:

> [!tabs]
> **1. Activar DKIM en su nombre de dominio**
>> Para activar DKIM en su nombre de dominio, utilice la llamada a la API siguiente: <br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : escriba el nombre de dominio asociado a su servicio de correo electrónico en el que desea activar DKIM.
>>
>> Pulse en `EXECUTE`{.action} para iniciar la activación.<br>
>>
>> *Ejemplo de resultado:*
>>
>> ```console
>> {
>>  "domain": "mydomain.ovh",
>>  "id": 123455789,
>>  "function": "domain/enableDKIM",
>>  "status": "todo"
>> }
>> ```
>>
>> Debería obtener un resultado similar al del ejemplo anterior con la mención `"status": "todo"` indicando que DKIM se va a instalar.
>>
> **2. Comprobar el estado de la operación DKIM**
>> Después de iniciar el proceso de activación de DKIM, siga el estado de la instalación para asegurarse de que la instalación se complete o para recuperar los registros DNS si su zona DNS se gestiona fuera de su área de cliente de OVHcloud.<br>
>>.
>> <br>
>> Para ello, utilice la llamada a la API siguiente:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : escriba el nombre de dominio asociado a su servicio de correo electrónico.<br>
>> <br>
>> Pulse en `EXECUTE`{.action} para visualizar el resultado.<br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> {
>>  "activeSelector": null,
>>  "autoconfig": true,
>>  "selectors": [
>>    {
>>      "selectorName": "ovhmo3456789-selector2",
>>      "status": "set",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net."
>>    },
>>    {
>>      "selectorName": "ovhmo3456789-selector1",
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "status": "set"
>>    }
>>  ],
>>  "status": "modifying"
>> }
>> ```
>> <br>
>> En el ejemplo anterior, la última línea de estado `"status": "modifying"` significa que la configuración está en curso. Espere aproximadamente **10 minutos** y vuelva a lanzar la llamada a la API.
>>
>> - si el valor es `"status": "enabled"`, su configuración está terminada y funcional.
>> - si el valor es `"status": "disabled"`, su configuración debe completarse manualmente, pase a la etapa siguiente.
>>
> **3. Recuperar el registro DNS**
>> Debe configurar manualmente la zona DNS de su nombre de dominio **en los siguientes casos** :
>>
>> - su servicio de correo electrónico está vinculado a un nombre de dominio que se gestiona en otra cuenta de cliente OVHcloud;
>> - su servicio de correo electrónico está vinculado a un nombre de dominio que se gestiona en otro registrador.
>>
>> Para configurar su zona DNS, debe recuperar los valores del registro DNS **de los dos selectores**. Para ello, utilice el resultado de la llamada a la API del paso anterior :
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : escriba el nombre de dominio asociado a su servicio de correo electrónico.
>>
>> Pulse en `EXECUTE`{.action} para visualizar el resultado.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> {
>>  "activeSelector": null,
>>  "status": "disabled",
>>  "autoconfig": false,
>>  "selectors": [
>>    {
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "status": "toSet",
>>      "selectorName": "ovhmo4287928-selector1"
>>    },
>>    {
>>      "selectorName": "ovhmo4287928-selector2",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net.",
>>      "status": "toSet"
>>    }
>>  ]
>> }
>> ```
>>
>> Los valores `"status": "toSet"` y `"status": "disabled"` significan que los registros CNAME deben configurarse. Recupere las 2 valores `cname` en un archivo de texto y pase a la etapa siguiente.
>>
> **4. Configurar el registro DNS**
>> Desde [el área de cliente de OVHcloud](/links/manager) donde se aloja el nombre de dominio de su servicio de correo electrónico, en la pestaña `Web Cloud`{.action}, pulse en `Noms de domaine`{.action} en la columna de la izquierda y seleccione el nombre de dominio correspondiente.<br>
>> Vaya a la pestaña `Zone DNS`{.action} y pulse en `Ajouter une entrée`{.action} en la ventana que aparece. Elija `CNAME` y complete según los valores que ha recogido.
>>
>> Si descomponemos los valores del ejemplo en la etapa "**3. Recuperar el registro DNS**" :
>>
>> - `ovhmo3456789-selector1._domainkey.mydomain.ovh` corresponde al subdominio del registro CNAME. Solo conservamos `ovhmo3456789-selector1._domainkey` porque el `.mydomain.ovh` ya está prellenado. <br>
>> - `ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net."` corresponde a la diana del registro. Hay que conservar bien el punto al final para puntuar el valor.<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api022.png){.thumbnail .w-400 .h-600}
>>
>> Una vez introducidos los valores, pulse en `Suivant`{.action} y luego en `Valider`{.action}.
>>
>> > [!primary]
>> >
>> > **Repita esta operación para el segundo selector.**
>>
>> Si configura su zona DNS en una interfaz externa fuera de OVHcloud, su registro CNAME debe tener la siguiente forma :
>>
>> ```console
>> ovhmo3456789-selector1._domainkey IN CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > No olvide que una modificación en una zona DNS está sujeta a un retraso de propagación. Es generalmente corto pero puede prolongarse hasta 24 horas.
>>
> **5. Activación del DKIM**
>>
>> Después de la propagación de su configuración DNS, utilice de nuevo la llamada a la API siguiente para activar el DKIM :<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : escriba el nombre de dominio asociado a su servicio de correo electrónico en el que desea activar DKIM.
>>
>> Pulse en `EXECUTE`{.action} para iniciar la activación.<br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> {
>>  "selectors": [
>>    {
>>      "selectorName": "ovhmo3465680-selector2",
>>      "cname": "ovhmo3456789-selector2._domainkey.mydomain.ovh CNAME ovhmo3456789-selector2._domainkey.123402.aj.dkim.mail.ovh.net.",
>>      "status": "set"
>>    },
>>    {
>>      "status": "set",
>>      "cname": "ovhmo3456789-selector1._domainkey.mydomain.ovh CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.",
>>      "selectorName": "ovhmo3465680-selector1"
>>    }
>>  ],
>>  "activeSelector": "ovhmo3465680-selector1",
>>  "autoconfig": true,
>>  "status": "enabled"
>> }
>> ```
>>
>> - Si observa bien los valores `"status": "set"` en los 2 selectores, esto significa que están bien configurados.
>> - Si observa los valores `"status": "toSet"` en los 2 selectores, esto significa que sus modificaciones DNS no son visibles. Vuelva a la pestaña « **4. Configurar el registro DNS** ».
>> - Si observa bien los valores `"status": "toFix"` en los 2 selectores, esto significa que los registros CNAME han sido bien detectados en la zona DNS de su nombre de dominio pero que los valores son incorrectos. Vuelva a la pestaña « **4. Configurar el registro DNS** ».
>>
>> > [!success]
>> >
>> > Ahora ha realizado todas las manipulaciones para activar el DKIM. Para asegurarse de que está bien activado, verifique su estado volviendo a la pestaña de la etapa « **2. Comprobar el estado de la operación DKIM** » para verificar que el valor `status:` esté bien en `enabled`. Si es así, su DKIM está ahora activo.
>>

##### **Para Exchange** <a name="confex"></a>

Siga las **5 etapas** siguientes pulsando en cada una de las pestañas.

> [!tabs]
> **1. Lista de selectores**
>> Antes de crear uno de los selectores para su nombre de dominio, debe recuperar el nombre que se les asigna automáticamente en la plataforma Exchange.<br>
>> <br>
>> Para ello, utilice la llamada a la API siguiente:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkimSelector
>> >
>> <br>
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que desea activar DKIM. <br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> "ovhex123456-selector1"
>> "ovhex123456-selector2"
>> ```
>>
> **2. Crear un selector**
>> Ahora va a crear un selector, generar su par de claves y el registro DNS asociado al nombre de dominio.<br>
>> <br>
>> Para ello, utilice la llamada a la API siguiente:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que desea activar el DKIM.
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `"selectorName"` : en la pestaña **EJEMPLO** de la sección **CUERPO DE LA SOLICITUD**, introduzca el nombre de un selector que haya obtenido en el paso anterior (ejemplo: « ovhex123456-selector1 »).
>>
>> *Ejemplo de entrada :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhex123456-selector1"
>> }
>> ```
>>
>> Pulse en `EJECUTAR`{.action} para iniciar la creación del selector.<br>
>>
>> > [!primary]
>> >
>> > Le recomendamos que realice esta operación dos veces para cada uno de los selectores mencionados anteriormente. El segundo selector le permitirá cambiar el par de claves cuando sea necesario. Le invitamos a consultar nuestro caso de uso [« Cómo cambiar su par de claves DKIM »](#2selectors) cuando desee cambiar al segundo selector.
>> <br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> status: "todo",
>> function: "addExchangeDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Recuperar el registro DNS**
>> Debe configurar manualmente la zona DNS de su nombre de dominio **en los siguientes casos** :
>>
>> - su plataforma Exchange está vinculada a un nombre de dominio que se gestiona en otro cliente OVHcloud ;<br>
>> - su plataforma Exchange está vinculada a un nombre de dominio que se gestiona en otro registrador ;<br>
>>
>> Para configurar su zona DNS, debe recuperar los valores del registro DNS **para cada selector si ha creado dos**. Para ello, utilice la llamada a la API siguiente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que desea configurar el DKIM.
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `selectorName` : introduzca el nombre del selector que ha creado en el paso anterior.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> targetRecord: "ovhex123456-selector1._domainkey.1675.ac.dkim.mail.ovh.net"
>> recordType: "CNAME"
>> header: "from;to;subject;date"
>> taskPendingId: 108712689
>> status: "waitingRecord"
>> cnameIsValid: false
>> lastUpdate: "1970-01-01T00:00:00+01:00"
>> customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"
>> selectorName: "ovhex1234565-selector1"
>> ```
>>
>> Recupere los valores `customerRecord` y `targetRecord` en un archivo de texto. Pase al paso siguiente.
>>
>> > [!primary]
>> >
>> > Es posible que el `status:` esté en `todo`, esto no tiene ninguna incidencia en la configuración de su zona DNS.
>>
> **4. Configurar el registro DNS**
>> Desde el [área de cliente de OVHcloud](/links/manager) donde se aloja el nombre de dominio de su plataforma Exchange, en la pestaña `Web Cloud`{.action}, pulse en `Nombres de dominio`{.action} en la columna de la izquierda y seleccione el nombre de dominio correspondiente.<br>
>> Vaya a la pestaña `Zona DNS`{.action} y pulse en `Añadir una entrada`{.action} en la ventana que aparece. Elija `CNAME` y complete según los valores que haya obtenido.<br>
>>
>> Si tomamos los valores del ejemplo en el paso "**3.Recuperar el registro DNS**":
>>
>> - `customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"` corresponde al subdominio del registro CNAME. Solo conservamos `ovhex123456-selector1._domainkey` porque el `.mydomain.ovh` ya está prellenado. <br>
>> - `targetRecord: "ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corresponde a la diana del registro. Añadimos un punto al final para delimitar el valor. Esto da `ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Una vez introducidos los valores, pulse en `Siguiente`{.action} y luego en `Validar`{.action}.<br>
>>
>> **Repita esta operación para el segundo selector si lo ha creado.**<br>
>>
>> Si configura su zona DNS en una interfaz externa a OVHcloud, su registro CNAME debe tener la forma siguiente :
>>
>> ```console
>> ovhex123456-selector1._domainkey IN CNAME ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > No olvide que una modificación en una zona DNS está sujeta a un tiempo de propagación. Es generalmente corto pero puede llegar hasta 24 horas.
>>
> **5. Activación del DKIM**
>> > [!warning]
>> >
>> > Desde la sección « [API - Los diferentes estados del DKIM](#dkim-status) » de este guía, verifique que el valor `status:` esté bien en `ready` antes de poder activar el DKIM.
>>
>> Para activar el DKIM, utilice la llamada a la API siguiente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que desea activar el DKIM.
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ».
>> - `selectorName` : introduzca el nombre del selector que ha creado.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> id: 108716876
>> todoDate: "2023-05-05T11:30:11+02:00"
>> finishDate: null
>> status: "todo"
>> function: "enableExchangeDKIM"
>> ```
>>
>> > [!success]
>> >
>> > Ahora ha realizado todas las operaciones necesarias para activar el DKIM. Para asegurarse de que está activo, consulte la sección « [API - Los diferentes estados del DKIM](#dkim-status) » de este guía para verificar que el valor `status:` esté bien en `inProduction`. Si es así, su DKIM está ahora activo.<br><br> **Si ha creado dos selectores**, el segundo selector debería estar en `status: "ready"`.
>>

##### **Para Email Pro** <a name="confemp"></a>

Siga las **5 etapas** siguientes pulsando en cada una de las pestañas.

> [!tabs]
> **1. Lista de selectores**
>> Antes de crear uno de los selectores para su nombre de dominio, debe recuperar el nombre que se les asigna automáticamente por la plataforma Email Pro.<br>
>> <br>
>> Para ello, utilice la siguiente llamada a la API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim
>> <br>
>>
>> - `service` : introduzca el nombre de su plataforma Email Pro que tiene la forma "emailpro-zz111111-1". <br>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Email Pro en el que desea activar DKIM. <br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> "ovhemp123456-selector1"
>> "ovhemp123456-selector2"
>> ```
>>
> **2. Crear un selector**
>> Ahora creará un selector, generará su par de claves y el registro DNS asociado al nombre de dominio.<br>
>>
>> > [!primary]
>> >
>> > Le recomendamos realizar esta operación dos veces para cada uno de los selectores mencionados anteriormente. El segundo selector le permitirá cambiar de par de claves cuando sea necesario. Le invitamos a consultar nuestro caso de uso [« Cómo cambiar su par de claves DKIM »](#2selectors).
>> <br>
>> Para ello, utilice la siguiente llamada a la API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Email Pro en el que desea activar DKIM.
>> - `service` : introduzca el nombre de su plataforma Email Pro que tiene la forma "emailpro-zz111111-1". <br>
>> - `"selectorName"` : En la pestaña **EXAMPLE** de la sección **REQUEST BODY**, introduzca el nombre de un selector que haya anotado en el paso anterior. (ejemplo: "ovhemp123456-selector1").
>>
>> *Ejemplo de entrada :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhemp123456-selector1"
>> }
>> ```
>>
>> Haga clic en `EXECUTE`{.action} para iniciar la creación del selector.<br>
>>
>> > [!primary]
>> >
>> > Le recomendamos realizar esta operación dos veces para cada uno de los selectores mencionados anteriormente. El segundo selector le permitirá cambiar de par de claves cuando sea necesario. Le invitamos a consultar nuestro caso de uso [« Cómo cambiar su par de claves DKIM »](#2selectors) cuando desee cambiar al segundo selector.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> status: "todo",
>> function: "addDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Recuperar el registro DNS**
>> Debe configurar manualmente la zona DNS de su nombre de dominio **en los siguientes casos** :
>>
>> - su plataforma Email Pro está vinculada a un nombre de dominio que se gestiona en otro cliente OVHcloud ;<br>
>> - su plataforma Email Pro está vinculada a un nombre de dominio que se gestiona en otro registrador ;<br>
>>
>> Para configurar su zona DNS, debe recuperar los valores del registro DNS **para cada selector si ha creado dos**. Para ello, utilice la siguiente llamada a la API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : introduzca el nombre de su plataforma Email Pro que tiene la forma "emailpro-zz111111-1" .
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Email Pro en el que desea configurar el DKIM.
>> - `selectorName` : introduzca el nombre del selector que ha creado en el paso anterior.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> targetRecord: "ovhemp123456-selector1._domainkey.1675.ac.dkim.mail.ovh.net"
>> recordType: "CNAME"
>> header: "from;to;subject;date"
>> taskPendingId: 108712689
>> status: "waitingRecord"
>> cnameIsValid: false
>> lastUpdate: "1970-01-01T00:00:00+01:00"
>> customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"
>> selectorName: "ovhemp1234565-selector1"
>> ```
>>
>> Recupere los valores `customerRecord` y `targetRecord` en un archivo de texto. Pase al paso siguiente.
>>
>> > [!primary]
>> >
>> > Es posible que el `status:` esté en `todo`, esto no tiene incidencia en la configuración de su zona DNS.
>>
> **4. Configurar el registro DNS**
>> Desde el [área de cliente de OVHcloud](/links/manager) donde se aloja el nombre de dominio de su plataforma Email Pro, en la pestaña `Web Cloud`{.action}, haga clic en `Noms de domaine`{.action} en la columna de la izquierda y seleccione el nombre de dominio correspondiente.<br>
>> Vaya a la pestaña `Zone DNS`{.action} y haga clic en `Ajouter une entrée`{.action} en la ventana que aparece. Elija `CNAME` y complete según los valores que haya anotado.<br>
>>
>> Si tomamos los valores del ejemplo en el paso "**3.Recuperar el registro DNS**":
>>
>> - `customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"` corresponde al subdominio del registro CNAME. Solo conservamos `ovhemp123456-selector1._domainkey` porque el `.mydomain.ovh` ya está prefijado. <br>
>> - `targetRecord: "ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corresponde a la diana del registro. Añadimos un punto al final para finalizar el valor. Esto da `ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Una vez introducidos los valores, haga clic en `Suivant`{.action} y luego en `Valider`{.action}.<br>
>>
>> **Repita esta operación para el segundo selector si lo ha creado.**<br>
>>
>> Si configura su zona DNS en una interfaz externa a OVHcloud, su registro CNAME debe tener la siguiente forma :
>>
>> ```console
>> ovhemp123456-selector1._domainkey IN CNAME ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > No olvide que una modificación en una zona DNS está sujeta a un tiempo de propagación. Es generalmente corto, pero puede llegar hasta 24 horas.
>>
> **5. Activación del DKIM**
>> > [!warning]
>> >
>> > Desde la sección « [API - Los distintos estados del DKIM](#dkim-status) » de este guía, verifique que el valor `status:` esté bien en `ready` antes de poder activar el DKIM.
>>
>> Para activar el DKIM, utilice la siguiente llamada a la API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : introduzca el nombre de su plataforma Email Pro que tiene la forma "emailpro-zz111111-1" .
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Email Pro en el que desea activar el DKIM.
>> - `selectorName` : introduzca el nombre del selector que ha creado.
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> id: 108716876
>> todoDate: "2023-05-05T11:30:11+02:00"
>> finishDate: null
>> status: "todo"
>> function: "enableDKIM"
>> ```
>>
>> > [!success]
>> >
>> > Usted ha realizado ahora todas las operaciones para activar el DKIM. Para asegurarse de que está bien activado, consulte la sección « [API - Los distintos estados del DKIM](#dkim-status) » de este guía para verificar que el valor `status:` esté bien en `inProduction`. Si es así, su DKIM está ahora activo.<br><br> **Si ha creado dos selectores**, el segundo selector debería estar en `status: "ready"`.
>>

#### API - Los distintos estados del DKIM <a name="dkim-status"></a>

Seleccione la oferta de correo electrónico correspondiente en las pestañas siguientes :

> [!tabs]
> **MX Plan y Zimbra**
>> Durante sus operaciones sobre el DKIM de su plataforma de correo electrónico, utilice la llamada a la API siguiente para verificar el estado actual del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>>
>> - `domain` : introduzca el nombre de dominio asociado a su servicio de correo electrónico en el que debe estar presente el DKIM.
>>
>> Mire después el valor `status:` general en el resultado :
>>
>> - `disabled` : el DKIM está desactivado, no ha sido aún configurado o ha sido desactivado por API. <br>
>> - `modifying` : la configuración del DKIM está en curso, es necesario esperar hasta el final del proceso.<br>
>> - `toConfigure` : la configuración del DKIM está pendiente de los parámetros DNS del nombre de dominio. Debe introducir manualmente los registros DNS en la zona del nombre de dominio. Para ello, consulte [el paso 4 de « la configuración completa del DKIM » para MX Plan y Zimbra](#confemail).<br>
>> - `enabled` : el DKIM está configurado y funcional.<br>
>> - `error` : El proceso de instalación ha encontrado un error. Le invitamos a abrir un [ticket con el soporte](https://help.ovhcloud.com/csm?id=csm_get_help) especificando el nombre de dominio afectado.<br>
>>
>> A nivel de los selectores, también tiene 3 estados posibles:
>>
>> - `set` : el selector está bien configurado y activo.
>> - `toSet` : el selector no está configurado en la zona DNS del nombre de dominio. Consulte [el paso 4 de « la configuración completa del DKIM » para MX Plan y Zimbra](#confemail).
>> - `toFix` : el selector ha sido bien configurado en la zona DNS del nombre de dominio pero los valores son incorrectos. Consulte [el paso 4 de « la configuración completa del DKIM » para MX Plan y Zimbra](#confemail).
>>
> **Exchange**
>> Durante sus operaciones sobre el DKIM de su plataforma Exchange, utilice la llamada a la API siguiente para verificar el estado actual del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que debe estar presente el DKIM. <br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma "hosted-zz111111-1" o "private-zz111111-1". <br>
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma "hosted-zz111111-1" o "private-zz111111-1". <br>
>> - `selectorName` : introduzca el nombre del selector que ha creado. <br>
>>
>> Mire después el valor `status:` en el resultado :
>>
>> - `todo` : la tarea ha sido inicializada, va a comenzar. <br>
>> - `WaitingRecord` : los registros DNS están pendientes de configuración o en proceso de validación en la zona DNS del nombre de dominio. Se realiza una verificación automática periódica para comprobar si el registro DNS está presente y correctamente rellenado.
>> - `ready` : los registros DNS están presentes en la zona. El DKIM puede ahora ser activado. <br>
>> - `inProduction` : el DKIM está bien configurado y activado, por lo tanto, está plenamente operativo. <br>
>> - `disabling` : el DKIM está en proceso de desactivación. <br>
>> - `deleting` : el DKIM está en proceso de eliminación. <br>
>>
>> Si se encuentra el siguiente error al lanzar la llamada a la API, significa que el selector no existe o ha sido eliminado. Deberá crearlo.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>
> **Email Pro**
>> Durante sus operaciones sobre el DKIM de su plataforma Email Pro, utilice la llamada a la API siguiente para verificar el estado actual del DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : introduzca el nombre de su plataforma Email Pro que tiene la forma "emailpro-zz111111-1" . <br>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Email Pro en el que debe estar presente el DKIM. <br>
>> - `selectorName` : introduzca el nombre del selector que ha creado . <br>
>>
>> Mire después el valor `status:` en el resultado :
>>
>> - `todo` : la tarea ha sido inicializada, va a comenzar. <br>
>> - `WaitingRecord` : los registros DNS están pendientes de configuración o en proceso de validación en la zona DNS del nombre de dominio. Se realiza una verificación automática periódica para comprobar si el registro DNS está presente y correctamente rellenado. <br>
>> - `ready` : los registros DNS están presentes en la zona. El DKIM puede ahora ser activado. <br>
>> - `inProduction` : el DKIM está bien configurado y activado, por lo tanto, está plenamente operativo. <br>
>> - `disabling` : el DKIM está en proceso de desactivación. <br>
>> - `deleting` : el DKIM está en proceso de eliminación. <br>
>>
>> Si se encuentra el siguiente error al lanzar la llamada a la API, significa que el selector no existe o ha sido eliminado. Deberá crearlo.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>

#### API - Activar o cambiar un selector DKIM <a name="enable-switch"></a>

> [!warning]
>
> El selector DKIM debe estar en estado `ready` antes de poder ser activado.

Seleccione la oferta de correo electrónico afectada entre las siguientes pestañas :

> [!tabs]
> **Exchange**
>> Para activar el DKIM en un selector, utilice la siguiente llamada a la API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange en el que desea activar el DKIM.<br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma "hosted-zz111111-1" o "private-zz111111-1".<br>
>> - `organizationName

> [!primary]
>
> Durante una rotación del selector DKIM, puede activar directamente el segundo selector que ha creado para cambiar a él, manteniendo activo el primer selector durante el tiempo necesario para que todos los correos electrónicos enviados con este sean correctamente analizados por su destinatario.

#### API - Desactivar y eliminar el DKIM <a name="enable-switch"></a>

> [!warning]
>
> **Para las ofertas Exchange y E-mail Pro** <br>
>
> El selector DKIM debe estar en estado `inProduction` o `ready` antes de poder desactivarse.

Seleccione la oferta de correo electrónico afectada entre las pestañas siguientes:

> [!tabs]
> **MX Plan y Zimbra**
>> Si desea desactivar el DKIM sin eliminar los selectores y su par de claves, utilice la llamada a la API siguiente:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/disable
>> <br>
>>
>> - `domain` : introduzca el nombre de dominio asociado a su servicio de correo electrónico en el que debe estar presente el DKIM. <br>
>>
>> *Ejemplo de resultado :*
>>
>> ```console
>> {
>>  "domain": "guidesteam.ovh",
>>  "id": 174219594,
>>  "function": "domain/disableDKIM",
>>  "status": "todo"
>> }
>> ```
>>
> **Exchange**
>> Si desea desactivar el DKIM sin eliminar el selector y su par de claves, utilice la llamada a la API siguiente:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange. <br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : introduzca el nombre del selector que desea desactivar. <br>
>>
>> Si desea eliminar el selector DKIM y su par de claves, utilice la llamada a la API siguiente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange DELETE /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange. <br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : introduzca el nombre del selector que desea eliminar. <br>
>>
> **E-mail Pro**
>> Si desea desactivar el DKIM sin eliminar el selector y su par de claves, utilice la llamada a la API siguiente :
>> 
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma E-mail Pro. <br>
>> - `selectorName` : introduzca el nombre del selector que desea desactivar. <br>
>> - `service` : introduzca el nombre de su plataforma E-mail Pro que tiene la forma « emailpro-zz111111-1 ». <br>
>>
>> Si desea eliminar el selector DKIM y su par de claves, utilice la llamada a la API siguiente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro DELETE /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma E-mail Pro. <br>
>> - `selectorName` : introduzca el nombre del selector que desea eliminar. <br>
>> - `service` : introduzca el nombre de su plataforma E-mail Pro que tiene la forma « emailpro-zz111111-1 ». <br>
>>

### Configurar el DKIM para una oferta de correo electrónico fuera de su cuenta OVHcloud <a name="external-dkim"></a>

Si desea configurar su zona DNS para añadir un registro DKIM para su oferta, siga las instrucciones siguientes.

Desde [el área de cliente de OVHcloud](/links/manager), haga clic en la pestaña `Web Cloud`{.action} y luego en `Noms de domaine`{.action} en la columna de la izquierda y seleccione el nombre de dominio correspondiente.

Haga clic en la pestaña `Zone DNS`{.action} y luego en `Ajouter une entrée`{.action}. Existen 3 maneras de añadir un registro para configurar el DKIM en su zona DNS:

- [un registro DKIM](#dkim-record) : configuración que permite visualizar todos los parámetros de un registro DKIM.
- [un registro TXT](#txt-record) : registro a utilizar cuando se le hayan proporcionado todos los parámetros DKIM.
- [un registro CNAME](#cname-record) : registro utilizado para una oferta de correo electrónico OVHcloud o un servidor de correo Microsoft.

#### Registro DKIM <a name="dkim-record"></a>

Este registro se llama DKIM en la interfaz, pero en realidad es un registro TXT de salida. El registro DKIM tiene como objetivo facilitar la lectura de los distintos elementos de configuración del DKIM presentándolos en forma de casillas independientes.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-add.png){.thumbnail .w-400 .h-600}

- **Subdominio** : introduzca el nombre del selector DKIM y añada `._domainkey` como sufijo, su nombre de dominio se añadirá automáticamente al final.

*ejemplo:*

```console
  selector-name._domainkey.mydomain.ovh.
```

- **Versión (v=)** : sirve para indicar la versión del DKIM. Se recomienda utilizarla y su valor por defecto es `DKIM1`.<br>
Si se especifica, esta etiqueta debe colocarse en primer lugar en el registro y debe ser igual a "DKIM1" (sin comillas). Los registros que comiencen con una etiqueta "v=" con otro valor deben ignorarse.

- **Granularidad (g=)** : permite especificar la parte « local-part » de una dirección de correo electrónico, es decir, la parte situada antes del « @ ».<br>
Permite especificar la dirección de correo electrónico o las direcciones de correo electrónico que están autorizadas a firmar un mensaje electrónico con la clave DKIM del selector.<br>
El valor por defecto de "g=" es "\*", lo que significa que todas las direcciones de correo electrónico están autorizadas a utilizar la clave de firma DKIM.<br>
Al indicar un valor específico para "g=", se puede limitar el uso de la clave a una parte local de dirección de correo electrónico específica o a un rango de direcciones de correo electrónico específicas utilizando caracteres genéricos (por ejemplo: "\*-group").

- **Algoritmo (hash) (h=)** : permite especificar los algoritmos de hash utilizados para firmar los encabezados de correo electrónico. Esta etiqueta permite definir una lista de algoritmos de hash que se utilizarán para generar una firma DKIM para un mensaje dado.

- **Tipo de clave (k=)** : especifica el algoritmo de firma utilizado para firmar los mensajes de correo electrónico salientes. Permite a los destinatarios saber cómo se ha firmado el mensaje y cuál es el método utilizado para verificar su autenticidad.<br>
Los valores posibles para la etiqueta "k=" incluyen "rsa" para el algoritmo de firma RSA y "ed25519" para el algoritmo de firma Ed25519. La elección del algoritmo depende de la política de seguridad del remitente y de la compatibilidad del destinatario.

- **Notas (n=)** : sirve para incluir notas de interés para los administradores que gestionan el sistema de claves DKIM.<br>
Estas notas pueden ser útiles para motivos de documentación o para ayudar a los administradores a comprender o gestionar el funcionamiento del DKIM. Las notas incluidas en n= no son interpretadas por los programas y no afectan al funcionamiento del DKIM.

- **Clave pública (base64) (p=)** : se utiliza para introducir los datos de la clave pública DKIM, que están codificados en base64.<br>
Esta etiqueta es obligatoria en la firma DKIM y permite a los destinatarios de la firma recuperar la clave pública necesaria para verificar la autenticidad del mensaje firmado.

- **Revocar la clave pública** : si una clave pública DKIM ha sido revocada (por ejemplo, en caso de compromiso de la clave privada), se debe utilizar un valor vacío para la etiqueta "p=", indicando que esta clave pública ya no es válida. Los destinatarios deben devolver un error para cualquier firma DKIM que haga referencia a una clave revocada.

- **Tipo de servicio (s=)**: La etiqueta "s=" (Service Type) es opcional y no está presente por defecto. Permite especificar el o los tipos de servicios a los que se aplica este registro DKIM.<br>
Los tipos de servicios se definen utilizando una lista de palabras clave separadas por dos puntos ":".<br>
El destinatario debe ignorar este registro si el tipo de servicio apropiado no está incluido.<br>
La etiqueta "s=" está destinada a restringir el uso de las claves para otros fines, en caso de que el uso del DKIM se defina para otros servicios en el futuro.<br>
Los tipos de servicios actualmente definidos son "\*" (todos los tipos de servicios), "email" (correo electrónico).

- **Modo de prueba (t=y)** : permite a los propietarios del nombre de dominio probar la implementación del DKIM sin correr el riesgo de que los mensajes se rechacen o se marquen como SPAM si la verificación de la firma DKIM falla.<br>
Cuando se utiliza la marca "t=y", el destinatario no debe tratar de forma diferente los mensajes firmados en modo de prueba y los mensajes no firmados. Sin embargo, el destinatario puede seguir el resultado del modo de prueba para ayudar a los firmantes.

- **Subdominios (t=s)** : permite restringir el uso de la firma DKIM al nombre de dominio únicamente (por ejemplo: @mydomain.ovh) o permitir el envío desde el nombre de dominio y sus subdominios (por ejemplo: @mydomain.ovh, @test.mydomain.ovh, @other.mydomain.ovh, etc.).

#### Registro TXT <a name="txt-record"></a>

Este es el tipo de registro nativo utilizado para configurar el DKIM en la zona DNS de su nombre de dominio. Es necesario dominar bien su sintaxis para completarlo.

Este tipo de configuración DKIM se recomienda cuando las informaciones a introducir le han sido comunicadas por el proveedor del servicio de correo electrónico.

Para comprender bien la composición del registro DKIM, consulte la parte anterior de este guía titulada « [Registro DKIM](#dkim-record) ».

**Ejemplo de un registro DKIM**

- subdominio :

```console
selector-name._domainkey.mydomain.ovh.
```

- objetivo :

```console
v=DKIM1;t=s;p= MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA77VDAIfyhjtoF0DIE5V7 rev1EKk4L0nxdBpD5O/jPrM4KP0kukeuB6IMpVplkkq52MSDeRcjoO50h0DmwZOr RUkyGjQwOnAh0VhY3fqkuwBYftEX7vWo8C2E1ylzimABkwPpSL62jZ1DheoXcil9 1M35wWBKtlYdXVedKjCQKOEnwTo+0hdNe38rU9NMgq6nbTIMjDntvxoVI+yF3kcx q/VpAY8BIYbcAXkVFvUyfUBABnnKpf0SfblsfcLW0Koy/FRxPDFOvnjNxXeOxMFR UI6K6PaW2WvtbJG2v+gHLY5M4tB0+/FNJU9emZfkPOk3DmRhZ8ENi7+oZa2ivUDj OQIDAQAB
```

#### Registro CNAME <a name="cname-record"></a>

El registro CNAME es un alias. Esto significa que el valor objetivo apunta a una URL que proporcionará ella misma el registro DKIM al servidor que consulte el registro CNAME. Este tipo de registro CNAME para configurar el DKIM es frecuente en el marco del uso de un servidor de correo Microsoft.

Se trata precisamente del tipo de registro utilizado para activar el DKIM en un nombre de dominio declarado para una oferta Exchange OVHcloud. Este procedimiento permite que su proveedor de solución de correo electrónico gestione por usted la seguridad y la actualización del DKIM.

### Probar su DKIM <a name="test-dkim"></a>

Le recomendamos enviar un correo electrónico desde una cuenta de su plataforma Exchange a una dirección de correo electrónico que verifique la firma DKIM al recibirlo.

Esto es lo que podrá encontrar en el encabezado del correo electrónico recibido :

<pre class="bgwhite"><code>ARC-Authentication-Results: i=1; mx.example.com;
       dkim=pass header.i=@mydomain.ovh header.s=ovhex123456-selector1 header.b=KUdGjiMs;
       spf=pass (example.com: domain of test-dkim@mydomain.ovh designates 54.36.141.6 as permitted sender) smtp.mailfrom=test-dkim@mydomain.ovh
Return-Path: &lt;test-dkim@mydomain.ovh&gt;
</code></pre>

Para recuperar el encabezado de un correo electrónico, consulte nuestro guía « [Recuperar el encabezado de un correo electrónico](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_headers) ».

### Casos de uso <a name="usecases"></a>

#### ¿Cómo y por qué cambiar el par de claves DKIM en mi oferta? <a name="2selectors"></a>

> [!warning]
>
> Esta pregunta concierne únicamente a las ofertas Exchange y E-mail Pro.

Cuando active por primera vez el DKIM en su servicio de correo electrónico, es posible crear 2 selectores que contienen cada uno un par de claves. El segundo selector sirve como sucesor del que está en uso actualmente.

Para evitar intentos de descifrado de la clave DKIM, se recomienda cambiar regularmente el par de claves. Para ello, asegúrese de haber configurado correctamente sus 2 selectores verificando que el primero está en estado `inProduction` y el segundo en estado `ready`. Puede verificar este estado refiriéndose a la sección « [API - Los diferentes estados del DKIM](#dkim-status) ».

Haga clic en la pestaña siguiente correspondiente a su oferta.

> [!tabs]
> **Exchange**
>> Para cambiar al segundo selector, utilice la llamada a la API siguiente :
>> 
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>>
>> - `domainName` : introduzca el nombre de dominio asociado a su plataforma Exchange. <br>
>> - `exchangeService` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `organizationName` : introduzca el nombre de su plataforma Exchange que tiene la forma « hosted-zz111111-1 » o « private-zz111111-1 ». <br>
>> - `selectorName` : introduzca el nombre del selector al que desea cambiar. <br>
>>
> **E-mail Pro**
>> Para cambiar al segundo selector, utilice la llamada a la API siguiente :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/enable

Usted observa que sus correos electrónicos no están firmados con DKIM, a pesar de su activación o configuración. En primer lugar, inicie sesión en su área de cliente para verificar el estado del DKIM.

Haga clic en la pestaña inferior correspondiente a su oferta, para comprobar el estado del DKIM en su plataforma de correo electrónico.

> [!tabs]
> **Exchange**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. En la sección `MICROSOFT`, haga clic en `Exchange`{.action}.
>> 1. Seleccione la plataforma afectada.
>>
>> En la sección `Dominios asociados`{.action}, compruebe el color del icono `DKIM` a la derecha del nombre de dominio afectado (ver imagen de abajo).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>
> **Email Pro**
>>
>> 1. Inicie sesión en su [área de cliente de OVHcloud](/links/manager).
>> 1. Vaya a la sección `Web Cloud`{.action}.
>> 1. Haga clic en `Email Pro`{.action}.
>> 1. Seleccione la plataforma afectada.
>> 1. Finalmente, vaya a la pestaña `Dominios asociados`{.action}.
>>
>> En la sección `Dominios asociados`{.action}, compruebe el color del icono `DKIM` a la derecha del nombre de dominio afectado (ver imagen de abajo).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>

A continuación se detallan los 4 estados que pueden provocar que el icono DKIM aparezca en rojo en su área de cliente. Haga clic en la pestaña correspondiente a su código de error:

> [!tabs]
> **501**
>>
>> "Only one dkim selector has been initialized"<br><br>
>> Solo hay un selector DKIM presente en su configuración. Para permitirnos el cambio a una nueva clave cuando sea necesario, es necesario configurar ambos selectores proporcionados por el servicio.<br><br>
>> Para corregir este error:
>>
>> - Compruebe el estado de los selectores DKIM para identificar cuál debe configurarse. Para ello, consulte la sección « [API - Los diferentes estados del DKIM](#dkim-status) » de este guía.
>> - Una vez que haya identificado el selector a configurar, siga los pasos de la sección « [API - Configuración completa del DKIM](#firststep) » de este guía, según su oferta (Exchange o Email Pro), aplicándola únicamente al selector afectado.
>> Espere como máximo 24 horas después de configurar el selector.
>>
> **502**
>>
>> "One DKIM configuration task is in error"<br><br>
>> Se ha producido un error durante la configuración del DKIM. Si después de 24 horas su configuración sigue en este estado, le recomendamos que abra un [ticket con el soporte](https://help.ovhcloud.com/csm?id=csm_get_help).
>>
> **503**
>>
>> "CNAME record is wrong"<br><br>
>> El valor del registro CNAME necesario para la configuración del DKIM no se ha introducido correctamente. Debe configurar correctamente la zona DNS del nombre de dominio asociado.
>> Para configurar su zona DNS, recupere los valores del registro CNAME que aparece:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Tomando como ejemplo la captura de pantalla anterior, el nombre de dominio es « **mydomain.ovh** » y se solicita configurar el selector « **2** ». Aquí, debe añadir un registro CNAME cuyo subdominio tenga el valor `ovhex1234567-selector2.domainkey.mydomain.ovh` y cuya diana sea `ovhex1234567-selector2.domainkey.7890.dkim.mail.ovh.net`.<br><br>
>> Una vez que su zona DNS esté configurada, espere el tiempo de propagación DNS (máximo 24 horas)
>>
> **504**
>>
>> "One CNAME record is missing"<br><br>
>> El valor del registro CNAME necesario para la configuración del DKIM está ausente. Debe configurar la zona DNS del nombre de dominio asociado.
>> Para configurar su zona DNS, recupere los valores del registro CNAME que aparece:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Tomando como ejemplo la captura de pantalla anterior, el nombre de dominio es « **mydomain.ovh** » y se solicita configurar el selector « **2** ». Aquí, debe añadir un registro CNAME cuyo subdominio tenga el valor `ovhex1234567-selector2.domainkey.mydomain.ovh` y cuya diana sea `ovhex1234567-selector2.domainkey.890123.dkim.mail.ovh.net`.<br><br>
>> Una vez que su zona DNS esté configurada, espere el tiempo de propagación DNS (máximo 24 horas)
>>

#### Desde la interfaz de API de OVHcloud, ¿cómo entender el estado del DKIM que no funciona? <a name="api-error"></a>

Si utiliza las API de OVHcloud para configurar su DKIM y este no funciona, consulte la sección « [API - Los diferentes estados del DKIM](#dkim-status) » de este guía para identificar el estado de sus selectores.

A continuación se detallan los estados que pueden bloquear el funcionamiento de su DKIM y la solución adecuada para cada situación.

> [!tabs]
> **Exchange y Email Pro**
>> - `WaitingRecord` : Los registros DNS están pendientes de configuración o en proceso de validación en la zona DNS del nombre de dominio. Se realiza una verificación automática periódica para comprobar si el registro DNS está presente y correctamente rellenado. Según su oferta, siga **el paso 5** en la sección « [API - Configuración completa del DKIM](#firststep) » para configurar correctamente la zona DNS del nombre de dominio afectado.
>> - `ready` : Los registros DNS están presentes en la zona. El DKIM puede activarse ahora. Solo tendrá que activar el selector siguiendo la sección « [API - Activar o cambiar un selector DKIM](#enable-switch) ».
>> - `deleting` : El DKIM está en proceso de eliminación. Una vez eliminado, deberá seguir la sección « [API - Configuración completa del DKIM](#firststep) ».
>> - `disabling` : El DKIM está en proceso de desactivación. Una vez finalizada esta operación, podrá activar el selector siguiendo la sección « [API - Activar o cambiar un selector DKIM](#enable-switch) ».
>> - `todo` : La tarea ha sido inicializada, debe comenzar. Si después de 24 horas su selector sigue en este estado, le recomendamos que abra un [ticket con el soporte](https://help.ovhcloud.com/csm?id=csm_get_help) especificando el número del selector afectado.
> **MX Plan y Zimbra**
>> - `disabled` : El DKIM está desactivado, no ha sido configurado aún o ha sido desactivado mediante API. <br>
>> - `modifying` : La configuración del DKIM está en curso, es necesario esperar hasta que finalice el proceso.<br>
>> - `toConfigure` : La configuración del DKIM está pendiente de los parámetros DNS del nombre de dominio. Debe rellenar manualmente los registros DNS en la zona del nombre de dominio. Para ello, consulte el paso « [Configuración completa del DKIM](#confemail) » de este guía. <br>
>> - `error` : El proceso de instalación ha encontrado un error. Le recomendamos que abra un [ticket con el soporte](https://help.ovhcloud.com/csm?id=csm_get_help) especificando el nombre de dominio afectado.
>>
>> En cuanto a los selectores, también tiene 2 estados relacionados con un error:
>>
>> - `toSet` : El selector no está configurado en la zona DNS del nombre de dominio. Consulte [el paso 4 de « la configuración completa del DKIM » para MX Plan y Zimbra](#confemail).
>> - `toFix` : El selector sí está configurado en la zona DNS del nombre de dominio, pero los valores son incorrectos. Consulte [el paso 4 de « la configuración completa del DKIM » para MX Plan y Zimbra](#confemail).

## Más información
Interactúe con nuestra [comunidad de usuarios](/links/community).

En el marco de la implementación de un registro DNS dinámico (DynHost), el uso de un comodín (carácter `*`) en el campo `subdominio`{.action} del formulario de un registro DNS no está disponible.