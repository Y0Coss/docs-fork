60 - You must have subscribed to one of the following email offers:
    - MX Plan OVHcloud (available via a [Cloud Web Hosting offer](/links/web/hosting)), a [free 100M hosting](/links/web/domains-free-hosting) or a separately ordered MX Plan offer.
    - [Exchange](/links/web/emails-hosted-exchange) or [Private Exchange](/links/web/emails-hosted-exchange).
    - [E-mail Pro](/links/web/email-pro).
    - [Zimbra](/links/web/zimbra).
    - An email offer outside of OVHcloud that has DKIM enabled.

85 - [Automatically configure DKIM for an OVHcloud email offer](#auto-dkim)
- [Configure DKIM via API for an OVHcloud email offer](#internal-dkim)
    - [API - Full DKIM configuration](#firststep)
        - [For MX Plan and Zimbra](#confemail)
        - [For Exchange](#confex)
        - [For E-mail Pro](#confemp)
    - [API - The different DKIM states](#dkim-status)
    - [API - Enable or change a DKIM selector](#enable-switch)
    - [API - Disable and delete DKIM](#disable-delete)

106 To understand why DKIM helps secure your email exchanges, it is necessary to understand how it works. DKIM uses "**hashing**" and "**asymmetric encryption**" to create a secure signature. The **email platform** and the **DNS zone** of your domain name will help transmit the DKIM information to your recipients.

108 /// details | Hashing <a name="hash"></a>

118 ///

120 /// details | Asymmetric encryption <a name="encrypt"></a>

136 ///

138 /// details | How are hashing and asymmetric encryption used for DKIM? <a name="encrypt-and-hash"></a>

144 ///

146 /// details | Why do we need to configure DNS servers? <a name="dns-and-dkim"></a>

150 ///

152 /// details | What is a DKIM selector? <a name="selector"></a>

165 ///

167 /// details | Example of an email sent using DKIM <a name="example"></a>

177 ///

179 ### Automatically configure DKIM for an OVHcloud email offer <a name="auto-dkim"></a>

Automatic DKIM configuration is available for all our email offers:

- MX Plan included with a [Cloud Web Hosting](/links/web/hosting), a [free 100M hosting](/links/web/domains-free-hosting) or ordered separately.
- [Exchange](/links/web/emails).
- [E-mail Pro](/links/web/email-pro).
- [Zimbra](/links/web/zimbra).

When you configure your domain name on an OVHcloud email solution, automatic DKIM configuration is proposed and performed by default if you do not disable it.

If DKIM was not enabled when you added a domain name to your email platform, you will need to launch the automatic configuration process via the Control Panel.

Click on the tab below corresponding to your offer.

> [!tabs]
> **MX Plan**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. Click on `MX Plan`{.action}.
>> 1. Select the relevant domain.
>> 1. Finally, go to the `General information`{.action} tab.
>>
>> In the **General information** section, you can see that the `DKIM` badge is red under the **Diagnostic** label.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> To enable DKIM, simply click on the red `DKIM` badge and then click on `Validate`{.action} from the activation window that appears.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> If your domain name is not managed in the same OVHcloud Control Panel as your email platform or is registered outside OVHcloud, you will see the window below:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> This window asks you to enter two CNAME values in the DNS zone of the domain name, which links this domain name to the DKIM selectors of your email service. You need to enter these values and ensure they are propagated before clicking on `Enable`{.action}.
>>
> **Exchange**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. In the `MICROSOFT` section, click on `Exchange`{.action}.
>> 1. Select the relevant platform.
>> 1. Finally, go to the `Associated domains`{.action} tab.
>>
>> To the right of the relevant domain name, you can see that the `DKIM` badge is red.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> To enable DKIM, simply click on the red `DKIM` badge and then click on `Validate`{.action} from the activation window that appears.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. Click on `Email Pro`{.action}.
>> 1. Select the relevant platform.
>> 1. Finally, go to the `Associated domains`{.action} tab.
>>
>> To the right of the relevant domain name, you can see that the `DKIM` badge is red.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> To enable DKIM, simply click on the red `DKIM` badge and then click on `Validate`{.action} from the activation window that appears.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **Zimbra**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. Click on `Zimbra Mail`{.action}.
>> 1. Finally, go to the `Domain`{.action} tab.
>> 1. To the right of the relevant domain, click on `⁝`{.action}, then on `Diagnostics`{.action}.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/access.png){.thumbnail .w-400 .h-600}
>>
>> To the right of the `DKIM` label on the corresponding tab, you should see a warning indicating that DKIM is not working. Click on the `DKIM`{.action} tab to access the DKIM configuration status. To fix the error, you need to add or modify two DNS entries of type CNAME in the DNS zone of the associated domain name, according to the information visible from this tab.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/dkim-cname-conf.png){.thumbnail .w-400 .h-600}
>>
>> > [!primary]
>> > **Tip for creating a CNAME record**
>> >
>> > From the [OVHcloud Control Panel](/links/manager) where the domain name of your email service is hosted, in the `Web Cloud`{.action} section, click on `Domain names`{.action} in the left column and select the relevant domain name.<br>
>> > Select the `DNS zone`{.action} tab and then click on `Add an entry`{.action} in the window that appears. Choose `CNAME` and complete the fields according to the values you have noted.

To enable DKIM, simply click on the red `DKIM` badge and then click on `Validate`{.action} from the activation window that appears.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}

Automatic DKIM activation takes between 30 minutes and a maximum of 24 hours. To check that your DKIM is working, simply return to the domain management section mentioned in the tabs above and check that the `DKIM` badge is green, or for a Zimbra offer, that the `DKIM` tab no longer displays the warning icon.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto03.png){.thumbnail .w-400 .h-600}

If after 24 hours your `DKIM` badge is still red, refer to the section [« Why is DKIM not working and appears red in the Control Panel? »](#reddkim) of this guide.

### Configure DKIM via API for an OVHcloud email offer <a name="internal-dkim"></a>

For an Exchange or E-mail Pro platform, you must first retrieve your platform's reference to configure your DKIM.

Click on the tab below corresponding to your offer.

> [!tabs]
> **Exchange**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. In the `MICROSOFT` section, click on `Exchange`{.action}.
>> 1. Select the relevant platform.
>>
>> By default, the name of your platform corresponds to its reference or it will be visible under the name you have assigned to it (see the image below).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/general-information/dns-dkim-platform-exchange.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. Click on `Email Pro`{.action}.
>> 1. Select the relevant platform.
>>
>> By default, the name of your platform corresponds to its reference or it will be visible under the name you have assigned to it (see the image below).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/email-pro/general-information/dns-dkim-platform-emailpro.png){.thumbnail .w-400 .h-600}

Also ensure that the domain name you wish to use for your emails is active in the `Associated domains`{.action} section.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dns-dkim-domain.png){.thumbnail .w-400 .h-600}

#### API - Full DKIM configuration <a name="firststep"></a>

To configure DKIM, go to the [OVHcloud API page](/links/console) and log in:

1. Click on `Authentication`{.action} in the top left.
1. Then click on `Login with OVHcloud SSO`{.action}.
1. Enter your OVHcloud credentials.
1. Click on the `Authorize`{.action} button to authorise API calls from this site.

> [!primary]
>
> Refer to our guide « [Getting started with OVHcloud APIs](/pages/manage_and_operate/api/first-steps) » if you have never used APIs before.

Go to the `/email/domain/` (MX Plan and Zimbra offers), `/email/exchange` (Exchange offer) or `/email/pro` (E-mail Pro offer) section of the APIs and enter « dkim » in the `Filter` field to display only the API functions related to DKIM.

Click on the tab corresponding to your offer:

> [!tabs]
> **MX Plan and Zimbra**
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

##### **For MX Plan and Zimbra** <a name="confemail"></a>

Follow the **5 steps** by clicking successively on each of the 5 tabs below:

> [!tabs]
> **1. Enable DKIM on your domain name**
>> To enable DKIM on your domain name, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : enter the domain name attached to your Email service on which you want to enable DKIM.
>>
>> Click on `EXECUTE`{.action} to start the activation.<br>
>>
>> *Example of result:*
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
>> You should get the same result as in the example above with the mention `"status": "todo"` indicating that DKIM will be installed.
>>
> **2. Check the DKIM operation status**
>> After launching the DKIM activation process, follow the installation status to ensure that the installation is completed or to retrieve the DNS records if your DNS zone is managed outside your OVHcloud Control Panel.<br>
>>.
>> <br>
>> For this, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : enter the domain name attached to your Email service.<br>
>> <br>
>> Click on `EXECUTE`{.action} to view the result.<br>
>>
>> *Example of result:*
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
>> In the example above, the last status line `"status": "modifying"` means that the configuration is in progress. Wait approximately **10 minutes** and relaunch the API call.
>>
>> - if the value is `"status": "enabled"`, your configuration is completed and functional.
>> - if the value is `"status": "disabled"`, your configuration must be completed manually, proceed to the next step.
>>
> **3. Retrieve the DNS record**
>> You must manually configure the DNS zone of your domain name **in the following cases** :
>>
>> - your Email service is linked to a domain name managed in another OVHcloud customer account;
>> - your Email service is linked to a domain name managed in another domain registrar.
>>
>> To configure your DNS zone, you must retrieve the values of the DNS record **for both selectors**. For this, use the result of the API call from the previous step:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : enter the domain name attached to your Email service.
>>
>> Click on `EXECUTE`{.action} to view the result.
>>
>> *Example of result:*
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
>> The values `"status": "toSet"` and `"status": "disabled"` mean that the CNAME records must be configured. Retrieve the 2 `cname` values in a text file and proceed to the next step.
>>
> **4. Configure the DNS record**
>> From the [OVHcloud Control Panel](/links/manager) where your Email service's domain name is hosted, in the `Web Cloud`{.action} tab, click on `Domain names`{.action} in the left column and select the concerned domain name.<br>
>> Go to the `DNS Zone`{.action} tab then click on `Add an entry`{.action} in the window that appears. Choose `CNAME` then complete according to the values you have noted.
>>
>> If we break down the values from the example in step "**3. Retrieve the DNS record**" :
>>
>> - `ovhmo3456789-selector1._domainkey.mydomain.ovh` corresponds to the subdomain of the CNAME record. We keep only `ovhmo3456789-selector1._domainkey` as the `.mydomain.ovh` is already pre-filled. <br>
>> - `ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net."` corresponds to the record target. It is important to keep the dot at the end to punctuate the value.<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api022.png){.thumbnail .w-400 .h-600}
>>
>> Once the values are entered, click on `Next`{.action} then on `Validate`{.action}.
>>
>> > [!primary]
>> >
>> > **Repeat this operation for the second selector.**
>>
>> If you configure your DNS zone in a third-party interface outside OVHcloud, your CNAME record must be in the following format:
>>
>> ```console
>> ovhmo3456789-selector1._domainkey IN CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Do not forget that a change in a DNS zone is subject to a propagation delay. It is generally short but can extend up to 24 hours.
>>
> **5. DKIM activation**
>>
>> After the propagation of your DNS configuration, use the following API call again to activate DKIM:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : enter the domain name attached to your Email service on which you want to enable DKIM.
>>
>> Click on `EXECUTE`{.action} to start the activation.<br>
>>
>> *Example of result:*
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
>> - If you observe the values `"status": "set"` on both selectors, this means they are well configured.
>> - If you observe the values `"status": "toSet"` on both selectors, this means that your DNS changes are not visible. Go back to the tab « **4. Configure the DNS record** ».
>> - If you observe the values `"status": "toFix"` on both selectors, this means that the CNAME records have been detected in the DNS zone of your domain name but the values are incorrect. Go back to the tab « **4. Configure the DNS record** ».
>>
>> > [!success]
>> >
>> > You have now completed all the steps to activate DKIM. To ensure that it is active, check its status by returning to the tab of step « **2. Check the DKIM operation status** » to verify that the value `status:` is indeed `enabled`. If this is the case, your DKIM is now active.
>>

##### **For Exchange** <a name="confex"></a>

Follow the **5 steps** below by clicking on each of the tabs.

> [!tabs]
> **1. List of selectors**
>> Before creating any of the selectors for your domain name, you must retrieve the name automatically assigned to them by the Exchange platform.<br>
>> <br>
>> To do this, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkimSelector
>> >
>> <br>
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which you want to enable DKIM. <br>
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>>
>> *Example of result:*
>>
>> ```console
>> "ovhex123456-selector1"
>> "ovhex123456-selector2"
>> ```
>>
> **2. Create a selector**
>> You will now create a selector, generate its key pair and the associated DNS record for the domain name.<br>
>> <br>
>> To do this, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which you want to enable DKIM.
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `"selectorName"` : in the **EXAMPLE** tab of the **REQUEST BODY** section, enter the name of a selector you noted in the previous step (example: "ovhex123456-selector1").
>>
>> *Example of input:*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhex123456-selector1"
>> }
>> ```
>>
>> Click on `EXECUTE`{.action} to start the creation of the selector.<br>
>>
>> > [!primary]
>> >
>> > We recommend that you perform this operation twice for each of the previously listed selectors. The second selector will allow you to change the key pair when necessary. We invite you to consult our use case [« How to change your DKIM key pair »](#2selectors) when you wish to switch to the second selector.
>> <br>
>>
>> *Example of result:*
>>
>> ```console
>> status: "todo",
>> function: "addExchangeDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Retrieve the DNS record**
>> You must manually configure the DNS zone of your domain name **in the following cases** :
>>
>> - your Exchange platform is linked to a domain name managed in another OVHcloud customer account ;<br>
>> - your Exchange platform is linked to a domain name managed in another domain registrar ;<br>
>>
>> To configure your DNS zone, you must retrieve the values of the DNS record **for each selector if you have created two**. To do this, use the following API call :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which you want to configure DKIM.
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `selectorName` : enter the name of the selector you created in the previous step.
>>
>> *Example of result:*
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
>> Retrieve the values `customerRecord` and `targetRecord` in a text file. Move on to the next step.
>>
>> > [!primary]
>> >
>> > It is possible that the `status:` is in `todo`, this has no impact on the configuration of your DNS zone.
>>
> **4. Configure the DNS record**
>> From the [OVHcloud Control Panel](/links/manager) where your Exchange platform's domain name is hosted, click on `Web Cloud`{.action} in the top menu, then click on `Domain names`{.action} in the left column and select the concerned domain name.<br>
>> Go to the `DNS zone`{.action} tab and click on `Add an entry`{.action} in the window that appears. Choose `CNAME` and complete the fields according to the values you noted.<br>
>>
>> If we take the values from the example in step "**3. Retrieve the DNS record**":
>>
>> - `customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"` corresponds to the subdomain of the CNAME record. We keep only `ovhex123456-selector1._domainkey` as the `.mydomain.ovh` is already pre-filled. <br>
>> - `targetRecord: "ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corresponds to the target of the record. Add a dot at the end to punctuate the value. This gives `ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Once the values are entered, click on `Next`{.action} then on `Validate`{.action}.<br>
>>
>> **Repeat this operation for the second selector if you have created it.**<br>
>>
>> If you are configuring your DNS zone in a third-party interface outside of OVHcloud, your CNAME record must be in the following format:
>>
>> ```console
>> ovhex123456-selector1._domainkey IN CNAME ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Do not forget that a change in a DNS zone is subject to a propagation delay. It is generally short but can extend up to 24 hours.
>>
> **5. DKIM activation**
>> > [!warning]
>> >
>> > From the section « [API - DKIM different states](#dkim-status) » of this guide, check that the value `status:` is indeed in `ready` before you can activate DKIM.
>>
>> To activate DKIM, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which you want to enable DKIM.
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1".
>> - `selectorName` : enter the name of the selector you created.
>>
>> *Example of result:*
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
>> > You have now completed all the steps to activate DKIM. To make sure it is active, consult the section « [API - DKIM different states](#dkim-status) » of this guide to check that the value `status:` is indeed in `inProduction`. If this is the case, your DKIM is now active.<br><br> **If you have created two selectors**, the second selector should be in `status: "ready"`.
>>

##### **For Email Pro** <a name="confemp"></a>

Follow the **5 steps** below by clicking on each of the tabs.

> [!tabs]
> **1. List of selectors**
>> Before creating one of the selectors for your domain name, you must retrieve the name automatically assigned to them by the Email Pro platform.<br>
>> <br>
>> To do this, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim
>> <br>
>>
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1". <br>
>> - `domainName` : enter the domain name attached to your Email Pro platform on which you wish to enable DKIM. <br>
>>
>> *Example of result:*
>>
>> ```console
>> "ovhemp123456-selector1"
>> "ovhemp123456-selector2"
>> ```
>>
> **2. Create a selector**
>> You will now create a selector, generate its key pair and the associated DNS record for the domain name.<br>
>>
>> > [!primary]
>> >
>> > We recommend that you perform this operation twice for each of the previously listed selectors. The second selector will allow you to change the key pair when necessary. We invite you to consult our use case [« How to change your DKIM key pair »](#2selectors).
>> <br>
>> To do this, use the following API call:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : enter the domain name attached to your Email Pro platform on which you wish to enable DKIM.
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1". <br>
>> - `"selectorName"` : In the **EXAMPLE** tab of the **REQUEST BODY** section, enter the name of a selector you noted in the previous step. (example: "ovhemp123456-selector1").
>>
>> *Example of input:*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhemp123456-selector1"
>> }
>> ```
>>
>> Click on `EXECUTE`{.action} to start the creation of the selector.<br>
>>
>> > [!primary]
>> >
>> > We recommend that you perform this operation twice for each of the previously listed selectors. The second selector will allow you to change the key pair when necessary. We invite you to consult our use case [« How to change your DKIM key pair »](#2selectors) when you wish to switch to the second selector.
>>
>> *Example of result:*
>>
>> ```console
>> status: "todo",
>> function: "addDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Retrieve the DNS record**
>> You must manually configure the DNS zone of your domain name **in the following cases** :
>>
>> - your Email Pro platform is linked to a domain name that is managed in another OVHcloud customer account ;<br>
>> - your Email Pro platform is linked to a domain name that is managed in another domain name registrar ;<br>
>>
>> To configure your DNS zone, you must retrieve the values of the DNS record **for each selector if you have created two**. To do this, use the following API call :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1" .
>> - `domainName` : enter the domain name attached to your Email Pro platform on which you wish to configure the DKIM.
>> - `selectorName` : enter the name of the selector you created in the previous step.
>>
>> *Example of result:*
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
>> Retrieve the values `customerRecord` and `targetRecord` in a text file. Move on to the next step.
>>
>> > [!primary]
>> >
>> > It is possible that the `status:` is in `todo`, this has no impact on the configuration of your DNS zone.
>>
> **4. Configure the DNS record**
>> From the [OVHcloud Control Panel](/links/manager) where your Email Pro platform's domain name is hosted, click on `Web Cloud`{.action} in the left column and select the concerned domain name.<br>
>> Go to the `DNS Zone`{.action} tab and click on `Add an entry`{.action} in the window that appears. Choose `CNAME` and complete the fields according to the values you have noted.<br>
>>
>> If we take the values from the example in the step "**3. Retrieve the DNS record**":
>>
>> - `customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"` corresponds to the subdomain of the CNAME record. We keep only `ovhemp123456-selector1._domainkey` because the `.mydomain.ovh` is already pre-filled. <br>
>> - `targetRecord: "ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` corresponds to the target of the record. We add a dot at the end to punctuate the value. This gives `ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Once the values are entered, click on `Next`{.action} and then on `Validate`{.action}.<br>
>>
>> **Repeat this operation for the second selector if you have created one.**<br>
>>
>> If you are configuring your DNS zone in a third-party interface outside of OVHcloud, your CNAME record must be in the following format :
>>
>> ```console
>> ovhemp123456-selector1._domainkey IN CNAME ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Do not forget that a change in a DNS zone is subject to a propagation delay. It is generally short but can extend up to 24 hours.
>>
> **5. DKIM activation**
>> > [!warning]
>> >
>> > From the section « [API - DKIM's different states](#dkim-status) » of this guide, check that the value `status:` is indeed in `ready` before you can activate the DKIM.
>>
>> To activate the DKIM, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1" .
>> - `domainName` : enter the domain name attached to your Email Pro platform on which you wish to activate the DKIM.
>> - `selectorName` : enter the name of the selector you have created.
>>
>> *Example of result:*
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
>> > You have now completed all the steps to activate the DKIM. To ensure that it is activated, consult the section « [API - DKIM's different states](#dkim-status) » of this guide to check that the value `status:` is indeed in `inProduction`. If this is the case, your DKIM is now active.<br><br> **If you have created two selectors**, the second selector should be in `status: "ready"`.
>>

#### API - DKIM's different states <a name="dkim-status"></a>

Select the email offer concerned in the following tabs:

> [!tabs]
> **MX Plan and Zimbra**
>> When working on the DKIM of your Email platform, use the API call below to check the current status of the DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>>
>> - `domain` : enter the domain name attached to your Email service on which the DKIM must be present.
>>
>> Then look at the general `status:` value in the result:
>>
>> - `disabled` : the DKIM is disabled, it has not yet been configured or it has been disabled by API. <br>
>> - `modifying` : the DKIM configuration is in progress, you need to wait until the process is complete.<br>
>> - `toConfigure` : the DKIM configuration is waiting for the domain name's DNS parameters. You must manually enter the DNS records in the domain name's zone. For this, refer to [step 4 of « the complete DKIM configuration » for MX Plan and Zimbra](#confemail).<br>
>> - `enabled` : the DKIM is configured and functional.<br>
>> - `error` : The installation process has encountered an error. We invite you to open a [support ticket](https://help.ovhcloud.com/csm?id=csm_get_help) specifying the concerned domain name.<br>
>>
>> At the selector level, you also have 3 possible states:
>>
>> - `set` : the selector is well configured and active.
>> - `toSet` : the selector is not configured in the domain name's DNS zone. Refer to [step 4 of « the complete DKIM configuration » for MX Plan and Zimbra](#confemail).
>> - `toFix` : the selector has been configured in the domain name's DNS zone but the values are incorrect. Refer to [step 4 of « the complete DKIM configuration » for MX Plan and Zimbra](#confemail).
>>
> **Exchange**
>> When working on the DKIM of your Exchange platform, use the API call below to check the current status of the DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which the DKIM must be present. <br>
>> - `exchangeService` : enter the name of your Exchange platform, which appears in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `organizationName` : enter the name of your Exchange platform, which appears in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `selectorName` : enter the name of the selector you have created. <br>
>>
>> Then look at the `status:` value in the result:
>>
>> - `todo` : the task has been initialized, it will start. <br>
>> - `WaitingRecord` : the DNS records are waiting for configuration or are being validated in the domain name's DNS zone. A regular automatic check is made to see if the DNS record is present and correctly filled in.
>> - `ready` : the DNS records are present in the zone. The DKIM can now be activated. <br>
>> - `inProduction` : the DKIM is well configured and activated, it is therefore fully operational. <br>
>> - `disabling` : the DKIM is being disabled. <br>
>> - `deleting` : the DKIM is being deleted. <br>
>>
>> If you encounter the following error when you launch the API call, it means that the selector does not exist or has been deleted. You will need to create it.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>
> **Email Pro**
>> When working on the DKIM of your Email Pro platform, use the API call below to check the current status of the DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1" . <br>
>> - `domainName` : enter the domain name attached to your Email Pro platform on which the DKIM must be present. <br>
>> - `selectorName` : enter the name of the selector you have created . <br>
>>
>> Then look at the `status:` value in the result:
>>
>> - `todo` : the task has been initialized, it will start. <br>
>> - `WaitingRecord` : the DNS records are waiting for configuration or are being validated in the domain name's DNS zone. A regular automatic check is made to see if the DNS record is present and correctly filled in. <br>
>> - `ready` : the DNS records are present in the zone. The DKIM can now be activated. <br>
>> - `inProduction` : the DKIM is well configured and activated, it is therefore fully operational. <br>
>> - `disabling` : the DKIM is being disabled. <br>
>> - `deleting` : the DKIM is being deleted. <br>
>>
>> If you encounter the following error when you launch the API call, it means that the selector does not exist or has been deleted. You will need to create it.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>

#### API - Enable or change a DKIM selector <a name="enable-switch"></a>

> [!warning]
>
> The DKIM selector must be in status `ready` before it can be activated.

Select the email offer concerned among the following tabs:

> [!tabs]
> **Exchange**
>> To activate the DKIM on a selector, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform on which you wish to activate the DKIM.<br>
>> - `exchangeService` : enter the name of your Exchange platform, which appears in the form "hosted-zz111111-1" or "private-zz111111-1".<br>
>> - `organizationName` : enter the name of your Exchange platform, which appears in the form "hosted-zz111111-1" or "private-zz111111-1".<br>
>> - `selectorName` : enter the name of an existing selector.<br>
>>
> **Email Pro**
>> To activate the DKIM on a selector, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : enter the domain name attached to your Email Pro platform on which the DKIM must be present.<br>
>> - `selectorName` : enter the name of the selector you have created .<br>
>> - `service` : enter the name of your Email Pro platform, which appears in the form "emailpro-zz111111-1" . <br>

> [!primary]
>
> When rotating a DKIM selector, you can directly activate the second selector you have created to switch to it, while keeping the first selector active until all emails sent with it are properly analyzed by their recipients.

#### API - Disable and delete the DKIM <a name="enable-switch"></a>

> [!warning]
>
> **For Exchange and Email Pro offers** <br>
>
> The DKIM selector must be in the `inProduction` or `ready` status before it can be disabled.

Select the email offer concerned from the following tabs:

> [!tabs]
> **MX Plan and Zimbra**
>> If you want to disable the DKIM without deleting the selectors and their key pairs, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/disable
>> <br>
>>
>> - `domain` : enter the domain name attached to your Email service on which the DKIM must be present. <br>
>>
>> *Example of result:*
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
>> If you want to disable the DKIM without deleting the selector and its key pair, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform. <br>
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `selectorName` : enter the name of the selector you want to disable. <br>
>>
>> If you want to delete the DKIM selector and its key pair, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange DELETE /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : enter the domain name attached to your Exchange platform. <br>
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `selectorName` : enter the name of the selector you want to delete. <br>
>>
> **Email Pro**
>> If you want to disable the DKIM without deleting the selector and its key pair, use the following API call:
>> 
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : enter the domain name attached to your Email Pro platform. <br>
>> - `selectorName` : enter the name of the selector you want to disable. <br>
>> - `service` : enter the name of your Email Pro platform in the form "emailpro-zz111111-1". <br>
>>
>> If you want to delete the DKIM selector and its key pair, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro DELETE /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : enter the domain name attached to your Email Pro platform. <br>
>> - `selectorName` : enter the name of the selector you want to delete. <br>
>> - `service` : enter the name of your Email Pro platform in the form "emailpro-zz111111-1". <br>
>>

### Configure DKIM for an email offer outside your OVHcloud account <a name="external-dkim"></a>

If you want to configure your DNS zone to add a DKIM record for your offer, follow the instructions below.

From the [OVHcloud Control Panel](/links/manager), click on the `Web Cloud`{.action} tab and then on `Domain names`{.action} in the left column and select the domain name concerned.

Click on the `DNS Zone`{.action} tab and then on `Add an entry`{.action}. There are 3 ways to add a record to configure DKIM in your DNS zone:

- [a DKIM record](#dkim-record) : configuration allowing you to view all the parameters of a DKIM record.
- [a TXT record](#txt-record) : record to use when all DKIM parameters have been provided to you.
- [a CNAME record](#cname-record) : record used for an OVHcloud email offer or a Microsoft email server.

#### DKIM record <a name="dkim-record"></a>

This record is named DKIM on the interface but it is actually a TXT record. The DKIM record aims to facilitate the reading of the different configuration elements of DKIM by presenting them in separate fields.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-add.png){.thumbnail .w-400 .h-600}

- **Sub-domain** : enter the name of the DKIM selector and add `._domainkey` as a suffix, your domain name will be automatically added at the end.

*example:*

```console
  selector-name._domainkey.mydomain.ovh.
```

- **Version (v=)** : is used to indicate the version of DKIM. It is recommended to use it and its default value is `DKIM1`.<br>
If specified, this tag must be placed first in the record and must be equal to "DKIM1" (without the quotes). Records that start with a "v=" tag with another value must be ignored.

- **Granularity (g=)** : allows you to specify the "local-part" of an email address, that is, the part before the "@".<br>
It allows you to specify the email address or email addresses that are allowed to sign an email with the DKIM key of the selector.<br>
The default value of "g=" is "\*", which means that all email addresses are allowed to use the DKIM signature key.<br>
By specifying a specific value for "g=", you can limit the use of the key to a specific local email address or to a range of specific email addresses using wildcard characters (e.g. "\*-group").

- **Hash algorithm (h=)** : allows you to specify the hash algorithms used to sign the email headers. This tag allows you to define a list of hash algorithms that will be used to generate a DKIM signature for a given message.

- **Key type (k=)** : specifies the signature algorithm used to sign outgoing emails. It allows recipients to know how the message was signed and what method was used to verify its authenticity.<br>
Possible values for the "k=" tag include "rsa" for the RSA signature algorithm and "ed25519" for the Ed25519 signature algorithm. The choice of algorithm depends on the sender's security policy and the recipient's support.

- **Notes (n=)** : is used to include notes of interest for administrators who manage the DKIM key system.<br>
These notes can be useful for documentation purposes or to help administrators understand or manage the operation of DKIM. Notes included in n= are not interpreted by programs and do not affect the operation of DKIM.

- **Public key (base64) (p=)** : is used to enter the DKIM public key data, which is encoded in base64.<br>
This tag is mandatory in the DKIM signature and allows recipients to retrieve the public key needed to verify the authenticity of the signed message.

- **Revoke the public key** : if a DKIM public key has been revoked (e.g. in the event of a private key compromise), an empty value must be used for the "p=" tag, indicating that this public key is no longer valid. Recipients must then return an error for any DKIM signature referring to a revoked key.

- **Service type (s=)**: The "s=" (Service Type) tag is optional and is not present by default. It allows you to specify the service or services to which this DKIM record applies.<br>
Service types are defined using a list of keywords separated by colons ":".<br>
The recipient must ignore this record if the appropriate service type is not listed.<br>
The "s=" tag is intended to restrict the use of keys for other purposes, in case the use of DKIM is defined for other services in the future.<br>
The currently defined service types are "\*" (all service types), "email" (email).

- **Test mode (t=y)** : allows domain owners to test the implementation of DKIM without risking messages being rejected or marked as SPAM if the DKIM signature verification fails.<br>
When the "t=y" flag is used, the recipient must not treat messages signed in test mode differently from unsigned messages. However, the recipient may track the test mode results to help signers.

- **Sub-domains (t=s)** : allows you to restrict the use of the DKIM signature to the domain name only (e.g. @mydomain.ovh) or to allow sending from the domain name and its sub-domains (e.g. @mydomain.ovh, @test.mydomain.ovh, @other.mydomain.ovh, etc.).

#### TXT record <a name="txt-record"></a>

This is the native record type used to configure DKIM in the DNS zone of your domain name. It is necessary to master its syntax to complete it correctly.

This type of DKIM configuration is recommended when the information to be entered has been provided to you by the email service provider.

To understand the composition of the DKIM record, refer to the previous section of this guide titled « [DKIM record](#dkim-record) ».

**Example of a DKIM record**

- sub-domain :

```console
selector-name._domainkey.mydomain.ovh.
```

- target :

```console
v=DKIM1;t=s;p= MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA77VDAIfyhjtoF0DIE5V7 rev1EKk4L0nxdBpD5O/jPrM4KP0kukeuB6IMpVplkkq52MSDeRcjoO50h0DmwZOr RUkyGjQwOnAh0VhY3fqkuwBYftEX7vWo8C2E1ylzimABkwPpSL62jZ1DheoXcil9 1M35wWBKtlYdXVedKjCQKOEnwTo+0hdNe38rU9NMgq6nbTIMjDntvxoVI+yF3kcx q/VpAY8BIYbcAXkVFvUyfUBABnnKpf0SfblsfcLW0Koy/FRxPDFOvnjNxXeOxMFR UI6K6PaW2WvtbJG2v+gHLY5M4tB0+/FNJU9emZfkPOk3DmRhZ8ENi7+oZa2ivUDj OQIDAQAB
```

#### CNAME record <a name="cname-record"></a>

The CNAME record is an alias. This means that the target value points to a URL that will itself provide the DKIM record to the server that queries the CNAME record. This type of CNAME record to configure DKIM is common when using a Microsoft email server.

This is precisely the type of record used to activate DKIM on a domain name declared for an OVHcloud Exchange offer. This process allows your email solution provider to manage the security and update of DKIM for you.

### Test your DKIM <a name="test-dkim"></a>

We recommend sending an email from an account on your Exchange platform to an email address that checks the DKIM signature upon receipt.

Here is what you can find in the header of the received email:

<pre class="bgwhite"><code>ARC-Authentication-Results: i=1; mx.example.com;
       dkim=pass header.i=@mydomain.ovh header.s=ovhex123456-selector1 header.b=KUdGjiMs;
       spf=pass (example.com: domain of test-dkim@mydomain.ovh designates 54.36.141.6 as permitted sender) smtp.mailfrom=test-dkim@mydomain.ovh
Return-Path: &lt;test-dkim@mydomain.ovh&gt;
</code></pre>

To retrieve the header of an email, refer to our guide « [Retrieve the header of an email](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_headers) ».

### Use cases <a name="usecases"></a>

#### How and why to change the DKIM key pair on my offer? <a name="2selectors"></a>

> [!warning]
>
> This question concerns only Exchange and Email Pro offers.

When you activate DKIM for the first time on your email service, you can create 2 selectors, each containing a key pair. The second selector serves as a successor to the one currently in use.

To avoid attempts to decrypt the DKIM key, it is recommended to change the key pair regularly. To do this, make sure you have properly configured your 2 selectors by checking that the first is in status `inProduction` and the second in status `ready`. You can check this status by referring to the section « [API - The different states of DKIM](#dkim-status) ».

Click on the tab below corresponding to your offer.

> [!tabs]
> **Exchange**
>> To switch to the second selector, use the following API call:
>> 
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>>
>> - `domainName` : enter the domain name attached to your Exchange platform. <br>
>> - `exchangeService` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `organizationName` : enter the name of your Exchange platform in the form "hosted-zz111111-1" or "private-zz111111-1". <br>
>> - `selectorName` : enter the name of the selector you want to switch to. <br>
>>
> **Email Pro**
>> To switch to the second selector, use the following API call:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : enter the domain name attached to your Email Pro platform on which the DKIM must be present.<br>
>> - `selectorName` : enter the name of the selector you want to switch to. <br>
>> - `service` : enter the name of your Email Pro platform in the form "emailpro-zz111111-1". <br>
>>

After switching to the new selector, keep the old one for 7 days before deleting it and creating a new one.

#### Why is DKIM not working and appears in red in the control panel? <a name="reddkim"></a>

> [!warning]
>
> This question concerns only Exchange and Email Pro offers.

You notice that your emails are not signed by DKIM, despite its activation or configuration. First, log in to your control panel to check the DKIM status.

Click on the tab below corresponding to your offer to check the DKIM status on your email platform.

> [!tabs]
> **Exchange**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. In the `MICROSOFT` section, click on `Exchange`{.action}.
>> 1. Select the concerned platform.
>>
>> In the `Associated Domains`{.action} section, check the color of the `DKIM` icon to the right of the concerned domain name (see the image below).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>
> **Email Pro**
>>
>> 1. Log in to your [OVHcloud Control Panel](/links/manager).
>> 1. Go to the `Web Cloud`{.action} section.
>> 1. Click on `Email Pro`{.action}.
>> 1. Select the concerned platform.
>> 1. Finally, go to the `Associated Domains`{.action} tab.
>>
>> In the `Associated Domains`{.action} section, check the color of the `DKIM` icon to the right of the concerned domain name (see the image below).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>

Here are the 4 states that result in the DKIM icon being red in your control panel. Click on the tab corresponding to your error code:

> [!tabs]
> **501**
>>
>> "Only one dkim selector has been initialized"<br><br>
>> Only one DKIM selector is present in your configuration. To allow us to switch to a new key when necessary, you are required to configure both selectors provided by the service.<br><br>
>> To fix this error:
>>
>> - Check the status of the DKIM selectors to identify the one that needs to be configured. For this, refer to the section « [API - The different DKIM states](#dkim-status) » in this guide.
>> - Once you have identified the selector to configure, follow the steps in the section « [API - Full DKIM configuration](#firststep) » in this guide, according to your offer (Exchange or Email Pro), applying it only to the concerned selector.
>> Wait up to 24 hours after the selector is configured.
>>
> **502**
>>
>> "One DKIM configuration task is in error"<br><br>
>> An error occurred during the DKIM configuration. If, after 24 hours, your configuration is still in this state, we recommend you open a [support ticket](https://help.ovhcloud.com/csm?id=csm_get_help).
>>
> **503**
>>
>> "CNAME record is wrong"<br><br>
>> The value of the CNAME record required for the DKIM configuration has not been entered correctly. You must correctly configure the DNS zone of the attached domain name.
>> To configure your DNS zone, retrieve the values of the CNAME record that is displayed:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Taking the example of the screenshot above, the domain name is "mydomain.ovh" and it is requested to configure the selector "2". Here, you need to add a CNAME record with the subdomain value `ovhex1234567-selector2.domainkey.mydomain.ovh` and the target `ovhex1234567-selector2.domainkey.7890.dkim.mail.ovh.net`.<br><br>
>> Once your DNS zone is configured, wait for the DNS propagation (up to 24 hours).
>>
> **504**
>>
>> "One CNAME record is missing"<br><br>
>> The value of the CNAME record required for the DKIM configuration is missing. You must configure the DNS zone of the attached domain name.
>> To configure your DNS zone, retrieve the values of the CNAME record that is displayed:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Taking the example of the screenshot above, the domain name is "mydomain.ovh" and it is requested to configure the selector "2". Here, you need to add a CNAME record with the subdomain value `ovhex1234567-selector2.domainkey.mydomain.ovh` and the target `ovhex1234567-selector2.domainkey.890123.dkim.mail.ovh.net`.<br><br>
>> Once your DNS zone is configured, wait for the DNS propagation (up to 24 hours).
>>

#### From the OVHcloud API interface, how to understand the state of the DKIM that is not working? <a name="api-error"></a>

If you are using the OVHcloud APIs to configure your DKIM and it is not working, refer to the section « [API - The different DKIM states](#dkim-status) » in this guide to identify the state of your selectors.

Below are the states that can block the operation of your DKIM and the appropriate solution for each situation.

> [!tabs]
> **Exchange and Email Pro**
>> - `WaitingRecord` : The DNS records are waiting for configuration or are being validated in the domain name's DNS zone. An automatic regular check is performed to see if the DNS record is present and correctly filled in. Depending on your offer, follow **step 5** in the section « [API - Full DKIM configuration](#firststep) » to correctly configure the DNS zone of the concerned domain name.
>> - `ready` : The DNS records are present in the zone. The DKIM can now be activated. You will just need to activate the selector by referring to the section « [API - Enable or change a DKIM selector](#enable-switch) ».
>> - `deleting` : The DKIM is being deleted. After deletion, you will need to follow the section « [API - Full DKIM configuration](#firststep) ».
>> - `disabling` : The DKIM is being disabled. After this operation, you will be able to activate the selector by referring to the section « [API - Enable or change a DKIM selector](#enable-switch) ».
>> - `todo` : The task has been initialized, it must be launched. If, after 24 hours, your selector is still in this state, we recommend you open a [support ticket](https://help.ovhcloud.com/csm?id=csm_get_help) specifying the number of the concerned selector.
> **MX Plan and Zimbra**
>> - `disabled` : The DKIM is disabled, it has not yet been configured or it has been disabled by API. <br>
>> - `modifying` : The DKIM configuration is in progress, it is necessary to wait until the process is completed.<br>
>> - `toConfigure` : The DKIM configuration is waiting for the DNS parameters of the domain name. You must manually enter the DNS records in the domain name's zone. For this, refer to the step « [Full DKIM configuration](#confemail) » in this guide. <br>
>> - `error` : The installation process encountered an error. We recommend you open a [support ticket](https://help.ovhcloud.com/csm?id=csm_get_help) specifying the concerned domain name.
>>
>> At the selector level, you also have 2 states related to an error:
>>
>> - `toSet` : The selector is not configured in the domain name's DNS zone. Refer to [step 4 of « the full DKIM configuration » for MX Plan and Zimbra](#confemail).
>> - `toFix` : The selector has been correctly configured in the domain name's DNS zone but the values are incorrect. Refer to [step 4 of « the full DKIM configuration » for MX Plan and Zimbra](#confemail).

## Go further
Join our [community of users](/links/community).

In the context of setting up a dynamic DNS record (DynHost), the use of a wildcard (`*`) in the `subdomain`{.action} field of a DNS record form is not available.