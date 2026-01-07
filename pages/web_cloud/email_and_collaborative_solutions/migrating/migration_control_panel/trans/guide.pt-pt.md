---
title: 'Migrar um endereço de e-mail MX Plan para uma conta de E-mail Pro, Exchange ou Zimbra'
excerpt: 'Descubra como migrar um endereço de e-mail MX Plan para uma conta de E-mail Pro, Exchange ou Zimbra'
updated: 2025-12-22
---

## Objetivo

OVHcloud oferece várias soluções de correio eletrónico: MX Plan (vendido sozinho ou incluído numa oferta de alojamento web), E-mail Pro, Exchange e Zimbra. Estas soluções beneficiam de funcionalidades específicas e podem adaptar-se a vários usos. Os seus requisitos evoluem? A OVHcloud coloca à sua disposição uma ferramenta de migração que lhe permite passar de uma solução para outra.

**Descubra como migrar um endereço de e-mail MX Plan para uma conta de E-mail Pro ou Exchange.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) permite migrar as suas mensagens de um servidor de correio eletrónico para outro.<br>
> Se os seus e-mails estiverem apenas armazenados localmente (configuração em POP ou arquivamento local), pode efetuar um [exportação a partir do seu software de correio eletrónico](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), depois [importar o seu ficheiro PST através do OMM](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) ou [importar diretamente a partir do seu software de correio eletrónico](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Requisitos

- Dispor de um endereço de e-mail MX Plan (através da oferta MX Plan ou incluído numa oferta de [alojamento web OVHcloud](/links/web/hosting)).
- Dispor de um serviço [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) com pelo menos uma conta não configurada (que aparecerá na forma « @configureme.me ») ou [Zimbra](/links/web/zimbra).
- **Não ter configurado uma redirecionamento no endereço de e-mail MX Plan que pretende migrar**.
- Estar conectado ao seu [espaço cliente OVHcloud](/links/manager).

## Instruções

### Etapa 1: delimitar o seu projeto

As soluções E-mail Pro e Exchange dispõem de uma base comum de funcionalidades. No entanto, existem diferenças consoante os casos de utilização. Ao escolher um endereço Exchange, dispõe de todas as funções colaborativas, como a sincronização do calendário e dos contactos. A solução E-mail Pro, por sua vez, oferece algumas delas, mas estas estão limitadas a uma utilização apenas através de um webmail.

Antes de continuar, é importante saber para qual oferta pretende migrar os seus endereços de e-mail MX Plan. Para o ajudar nessa escolha, consulte a página das [soluções de e-mail profissionais da OVHcloud](/links/web/emails) que propõe um comparativo detalhado das ofertas. Pode acumular as soluções e, por isso, utilizar, para o mesmo nome de domínio, uma ou mais contas E-mail Pro e Exchange. Além disso, se tiver de migrar várias contas, aconselhamos a implementar um plano de migração.

### Etapa 2: encomendar as suas contas E-mail Pro ou Exchange

Esta etapa é facultativa se já dispuser de um serviço Exchange ou E-mail Pro para o qual está a realizar esta migração.

Caso contrário, faça login no seu [espaço cliente OVHcloud](/links/manager), em seguida encomende o serviço E-mail Pro ou Exchange da sua escolha. Siga as diferentes etapas, depois aguarde até à instalação do serviço. Um e-mail será enviado assim que esta terminar.

> [!primary]
>
> Após a encomenda da conta, deixe-a, em primeiro lugar, na forma « @configureme.me ». De fato, será renomeada durante a migração.
>

### Etapa 3: realizar a migração

Antes de iniciar a sua migração, terá de identificar a versão do MX Plan da qual está a migrar.

> [!primary]
>
> A tecnologia de e-mail da sua oferta MX Plan pode variar consoante a data de ativação da sua oferta ou se uma migração ocorreu recentemente. Esta tecnologia distingue-se, nomeadamente, pela interface do seu webmail. Para a identificar a partir do seu espaço cliente, siga estes passos :
>
> 1. Faça login no seu [espaço cliente OVHcloud](/links/manager).
> 1. Dirija-se à secção `Web Cloud`{.action}.
> 1. Clique em `MX Plan`{.action}.
> 1. Selecione o domínio em questão.
> 1. O separador `Informações Gerais`{.action} está selecionado por defeito.
> 1. Registe a tecnologia utilizada sob a menção **Webmail** no quadro `Subscrição`.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Migração manual de uma oferta MX Plan para Exchange, E-mail Pro ou Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> Esta secção aplica-se a todos os serviços MX Plan que utilizam a tecnologia webmail Rouncube, Zimbra ou OWA.
>
> No entanto, se pretender migrar um serviço MX Plan que utiliza o webmail Roundcube para uma plataforma Email Pro ou Exchange OVHcloud, siga a secção « [Migração automática de uma oferta MX Plan Roundcube para Exchange ou Email Pro](#roundcube-mxplan) » deste guia.

> [!warning]
>
> Se acabou de encomendar a sua nova oferta de e-mail, adicione primeiro o nome de domínio à sua plataforma de e-mail, antes de iniciar a sua migração. <br> - *Por exemplo, para migrar a conta « myemail@mydomain.ovh », tem de adicionar o nome de domínio « mydomain.ovh » à sua plataforma.*
>
> Selecione o separador `Domínios associados`{.action} ou `Domínio`{.action} na sua plataforma, em seguida clique em `Adicionar um domínio`{.action}. Uma vez o nome de domínio adicionado, certifique-se de que a menção `OK` ou `Ativo`{.action} está bem presente na coluna `Estado`.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Para mais detalhes sobre a adição de um nome de domínio, siga [o guia E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [o guia Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) ou [o guia Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

A migração do seu MX Plan será feita em 3 grandes etapas, **Renomear**, **Criar** e **Migrar**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Renomeie** a conta MX Plan a migrar com um nome provisório (exemplo: para migrar a conta MX plan *john.smith@mydomain.ovh*, renomeie-a para *john.smith01@mydomain.ovh*).

No separador `Contas de e-mail`{.action} da sua plataforma MX Plan, clique no botão `...`{.action} depois em `Modificar`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> A modificação da conta não é imediata, aguarde até ao fim da operação antes de passar para a etapa seguinte.

2\. **Crie** o seu endereço de e-mail na nova conta da sua plataforma E-mail Pro ou Exchange (tomando o exemplo anterior, vai criar *john.smith@mydomain.ovh* na sua nova plataforma).

No separador `Contas de e-mail`{.action} da sua plataforma E-mail Pro ou Exchange, clique no botão `...`{.action} depois em `Modificar`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migre** a conta MX Plan para a conta da sua nova plataforma com a ajuda do nosso [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Para mais informações sobre o OMM, consulte o nosso guia [Migrar contas de e-mail via OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

O prazo de migração depende da quantidade de conteúdo a migrar para a sua nova conta. Pode variar de alguns minutos a várias horas.

Verifique, após a migração, que encontra os seus elementos ao ligar-se ao webmail no endereço [Webmail](/links/web/email)

Pode conservar ou eliminar a conta de origem com o nome provisório após esta migração.

Se pretender eliminá-la, dirija-se ao separador `Contas de e-mail`{.action} do seu MX Plan, clique no botão `...`{.action} depois em `Reiniciar esta conta`{.action}.

#### 3.2 Migração automática de uma oferta MX Plan Roundcube para Exchange ou Email Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> Esta secção aplica-se apenas aos serviços MX Plan que utilizam a tecnologia webmail Rouncube.

> [!primary]
>
> A sua conta OVHcloud deve ser previamente contacto administrador **e** contacto técnico do serviço MX plan a migrar, **assim como** do serviço E-mail Pro ou Exchange para o qual está a migrar.
>
> Para mais informações sobre as alterações de contactos, consulte o nosso guia para [gerir os contactos dos seus serviços](/pages/account_and_service_management/account_information/managing_contacts).
>

A migração pode ser realizada a partir de duas interfaces :<br>

- **a do assistente de configuração Hosted Exchange**, apenas se acabou de encomendar um serviço Hosted Exchange e ainda não configurou nada sobre este último ;
- **a do MX Plan**, assim que tiver à disposição um serviço E-mail Pro ou Exchange (já configurado ou não) e um endereço MX Plan que pretende migrar.

> Como recordação, antes de iniciar a migração, certifique-se de que nenhuma **redirecionação** ou nenhum **resposta automática** está configurado no seu MX Plan.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Uma vez que esteja pronto, continue a ler esta documentação consoante a interface selecionada. Lembramos que o prazo de migração depende da quantidade de conteúdo a migrar para a sua nova conta. Pode variar de alguns minutos a várias horas.

> [!warning]
>
> Uma vez a migração confirmada, não poderá aceder ao seu antigo endereço de e-mail MX Plan nem cancelar o processo de migração. Aconselhamos vivamente de realizar esta operação a uma hora adequada.
>
> Mesmo se não puder aceder ao seu endereço de e-mail atual, as mensagens já recebidas assim como as recebidas não serão perdidas. Todas estarão imediatamente acessíveis a partir da sua nova conta.
>

##### **Migração a partir do assistente de configuração Exchange**

Para aceder a ele, selecione no [espaço cliente OVHcloud](/links/manager) o serviço em questão. O assistente deverá aparecer para o ajudar a configurar o seu novo serviço Exchange. Durante este processo, poderá selecionar as contas de e-mail MX Plan a migrar.

Se o assistente de configuração não aparecer, as informações gerais do serviço Exchange aparecerão no seu lugar. Neste caso, terá de realizar a migração das suas contas através da interface MX Plan.

##### **Migração a partir da interface MX Plan**

Para realizar a migração a partir desta interface, dirija-se à secção `E-mails`{.action} do seu espaço cliente OVHcloud. Escolha, em seguida, o serviço com o nome de domínio das suas contas de e-mail. Clique no logótipo em forma de engrenagem na linha da conta de e-mail em questão (também chamada de conta fonte) e depois em `Migrar a conta`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

Na janela que aparece, selecione o serviço de destino (aquele para o qual pretende migrar o endereço) e clique em `Seguinte`{.action}. Se este tiver pelo menos uma conta « livre » (ou seja, ainda não configurada), a migração será feita para uma destas contas. Nesse caso, tome conhecimento das informações que aparecem, valide-as, depois clique em `Seguinte`{.action} para continuar a operação.

Se não tiver nenhuma conta « livre », um botão `Comprar contas`{.action} aparecerá. Siga as etapas, depois aguarde o tempo necessário para que as contas sejam instaladas para realizar novamente a operação.

Confirme, por fim, a palavra-passe do endereço de e-mail fonte (aquele que pretende migrar), depois clique em `Migrar`{.action}. Esta operação deverá ser repetida tantas vezes quanto necessário para a migração de outras contas.

![exchange](images/account_migration_steps.png){.thumbnail}

### Etapa 4 : verificar ou modificar a configuração do seu domínio

Nesta etapa, os seus endereços de e-mail devem já estar migrados e funcionais. Por segurança, convidamo-lo a assegurar-se de que a configuração do seu domínio está correta consultando o seu espaço cliente.

Para isso, selecione o serviço E-mail Pro, Exchange ou Zimbra em questão, depois dirija-se ao separador `Domínios associados`{.action} ou `Domínio`{.action} na sua plataforma. Verifique a rubrica ou a coluna `Diagnóstico`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Se acabou de realizar a migração ou de modificar um registo DNS do seu domínio, pode ser que o ecrã no [espaço cliente OVHcloud](/links/manager) necessite de algumas horas para se atualizar.
>

Para modificar a configuração, clique no botão vermelho e realize a operação solicitada. Esta última necessita de um tempo de propagação de 4 a 24 horas no máximo para ser plenamente efetiva.

### Etapa 5 : utilizar os seus endereços de e-mail migrados

Basta-lhe apenas utilizar os seus endereços de e-mail migrados. Para isso, a OVHcloud coloca à disposição uma aplicação online (_web app_) acessível no endereço [Webmail](/links/web/email). Deverá introduzir os identificadores relativos ao seu endereço de e-mail.

Se configurou um dos contas migrados num cliente de correio (como o Outlook), deverá reconfigurá-lo novamente. As informações de ligação ao servidor OVHcloud mudaram após a migração. Para o ajudar nas suas operações, consulte a nossa documentação a partir das secções dos guias dedicadas a [E-mail Pro](/products/web-cloud-email-collaborative-solutions-email-pro) e [Hosted Exchange](/products/web-cloud-email-collaborative-solutions-mx-plan). Se não conseguir reconfigurar a conta imediatamente, o acesso através da aplicação online permanece possível.

### Organização do conteúdo dos seus endereços de e-mail após uma migração <a name="content-after-migration"></a>

Quando se ligar pela primeira vez ao seu novo endereço de e-mail, o conteúdo migrado pode estar parcialmente oculto. Para mostrar todos os elementos, a partir do webmail, clique na seta ao lado da `Caixa de entrada` para revelar os subdiretórios. O conteúdo migrado do seu antigo endereço de e-mail deverá aparecer.

![exchange](images/owa_migrate_content.png){.thumbnail}

Os diretórios por defeito, como « itens enviados » ou « lixeira » aparecem em inglês (« Sent items » e « Trash »), à exceção dos diretórios que criou.

Após uma migração, não hesite em explorar todos os diretórios e subdiretórios da sua conta para verificar que todos os elementos estão presentes.

### Migração Manual

Também pode migrar manualmente os seus endereços de e-mail para a sua nova oferta de e-mail OVHcloud utilizando apenas o seu software de correio. Baseie-se no nosso guia [Migrar manualmente o seu endereço de e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). Recomendamos, no entanto, que utilize este método apenas quando os métodos principais não forem possíveis.

## Quer saber mais?

[Gestão dos contactos dos seus serviços](/pages/account_and_service_management/account_information/managing_contacts).

[Primeiros passos com a oferta E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Primeiros passos com a oferta Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Primeiros passos com a oferta Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Fale com a nossa [comunidade de utilizadores](/links/community).