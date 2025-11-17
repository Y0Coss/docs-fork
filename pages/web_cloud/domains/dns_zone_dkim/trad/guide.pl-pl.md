60 - Zamówienie jednej z poniższych ofert e-mail:
    - MX Plan OVHcloud (dostępny poprzez [ofertę Web Cloud](/links/web/hosting)), [darmowe 100M hostingowanie](/links/web/domains-free-hosting) lub osobno zamówiony MX Plan.
    - [Exchange](/links/web/emails-hosted-exchange) lub [Private Exchange](/links/web/emails-hosted-exchange).
    - [E-mail Pro](/links/web/email-pro).
    - [Zimbra](/links/web/zimbra).
    - Oferta e-mail spoza OVHcloud z DKIM.

85 - [Automatyczna konfiguracja DKIM dla oferty e-mail OVHcloud](#auto-dkim)
- [Konfiguracja DKIM przez API dla oferty e-mail OVHcloud](#internal-dkim)
    - [API - Pełna konfiguracja DKIM](#firststep)
        - [Dla MX Plan i Zimbra](#confemail)
        - [Dla Exchange](#confex)
        - [Dla E-mail Pro](#confemp)
    - [API - Różne stany DKIM](#dkim-status)
    - [API - Włączanie lub zmiana selektora DKIM](#enable-switch)
    - [API - Wyłączanie i usuwanie DKIM](#disable-delete)

106 Aby dobrze zrozumieć, dlaczego DKIM pozwala na zabezpieczenie Twoich wiadomości e-mail, należy zrozumieć, jak działa. DKIM korzysta z „**skrótu**” i „**szyfrowania asymetrycznego**”, aby stworzyć bezpieczną sygnaturę. **Platforma e-mail** i **strefa DNS** Twojej domeny pomogą przekazać informacje DKIM odbiorcom.

108 /// details | Hashowanie <a name="hash"></a>

118 ///

120 /// details | Szyfrowanie asymetryczne <a name="encrypt"></a>

136 ///

138 /// details | Jak skrót i szyfrowanie asymetryczne są wykorzystywane w DKIM ? <a name="encrypt-and-hash"></a>

144 ///

146 /// details | Dlaczego trzeba skonfigurować serwery DNS ? <a name="dns-and-dkim"></a>

150 ///

152 /// details | Co to jest selektor DKIM ? <a name="selector"></a>

165 ///

167 /// details | Przykład wysłania wiadomości e-mail za pomocą DKIM <a name="example"></a>

177 ///

179 ### Automatyczna konfiguracja DKIM dla oferty e-mail OVHcloud <a name="auto-dkim"></a>

Automatyczna konfiguracja DKIM jest dostępna dla wszystkich naszych ofert e-mail:

- MX Plan wchodzący w skład [hostingu Web Cloud](/links/web/hosting), [darmowego 100M hostingu](/links/web/domains-free-hosting) lub zamówiony osobno.
- [Exchange](/links/web/emails).
- [E-mail Pro](/links/web/email-pro).
- [Zimbra](/links/web/zimbra).

Podczas konfiguracji swojej domeny na rozwiązaniu e-mail OVHcloud, automatyczna konfiguracja DKIM jest proponowana i realizowana domyślnie, jeśli nie zostanie ona wyłączona.

Jeśli DKIM nie został włączony podczas dodawania domeny do Twojej platformy e-mail, należy uruchomić proces konfiguracji automatycznej za pomocą panelu klienta.

Kliknij na zakładkę poniżej odpowiadającą Twojej ofercie.

> [!tabs]
> **MX Plan**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. Kliknij `MX Plan`{.action}.
>> 1. Wybierz odpowiedni domenę.
>> 1. Na koniec przejdź do zakładki `Informacje ogólne`{.action}.
>>
>> W ramce **Informacje ogólne**, możesz zauważyć, że guzik `DKIM` jest czerwony pod opisem **Diagnostyka**.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Aby włączyć DKIM, wystarczy kliknąć guzik `DKIM` czerwony, a następnie kliknąć `Zatwierdź`{.action} z pojawiającej się okienka aktywacji.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> W przypadku, gdy Twoja domena nie jest zarządzana w tym samym panelu klienta OVHcloud, co Twoja platforma e-mail, lub jest zarejestrowana poza OVHcloud, otrzymasz poniższe okno:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/emails/general-information/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
>> W tym oknie zostaniesz poproszony o wprowadzenie dwóch wartości CNAME w strefie DNS Twojej domeny, co pozwoli powiązać tę domenę z selektorami DKIM Twojej usługi e-mail. Należy wprowadzić te wartości i upewnić się, że zostały rozpropagowane, zanim klikniesz `Włącz`{.action}.
>>
> **Exchange**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. W sekcji `MICROSOFT`, kliknij `Exchange`{.action}.
>> 1. Wybierz odpowiednią platformę.
>> 1. Na koniec przejdź do zakładki `Powiązane domeny`{.action}.
>>
>> Po prawej stronie od nazwy domeny możesz zauważyć, że guzik `DKIM` jest czerwony.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Aby włączyć DKIM, wystarczy kliknąć guzik `DKIM` czerwony, a następnie kliknąć `Zatwierdź`{.action} z pojawiającej się okienka aktywacji.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. Kliknij `Email Pro`{.action}.
>> 1. Wybierz odpowiednią platformę.
>> 1. Na koniec przejdź do zakładki `Powiązane domeny`{.action}.
>>
>> Po prawej stronie od nazwy domeny możesz zauważyć, że guzik `DKIM` jest czerwony.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto01.png){.thumbnail .w-400 .h-600}
>>
>> Aby włączyć DKIM, wystarczy kliknąć guzik `DKIM` czerwony, a następnie kliknąć `Zatwierdź`{.action} z pojawiającej się okienka aktywacji.
>> 
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}
>>
> **Zimbra**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. Kliknij `Zimbra Mail`{.action}.
>> 1. Na koniec przejdź do zakładki `Domena`{.action}.
>> 1. Po prawej stronie od domeny kliknij `⁝`{.action}, a następnie `Diagnostyka`{.action}.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/access.png){.thumbnail .w-400 .h-600}
>>
>> Po prawej stronie od opisu `DKIM` na odpowiedniej zakładce powinieneś zauważyć ostrzeżenie wskazujące, że DKIM jest niepoprawny. Kliknij zakładkę `DKIM`{.action}, aby uzyskać dostęp do statusu konfiguracji DKIM. Aby poprawić błąd, musisz dodać lub zmodyfikować dwie wpisy DNS typu CNAME w strefie DNS Twojej domeny, zgodnie z informacjami widocznymi z tej zakładki.
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/zimbra/domain/diagnostics/dkim-cname-conf.png){.thumbnail .w-400 .h-600}
>>
>> > [!primary]
>> > **Szybki sposób na utworzenie wpisu CNAME**
>> >
>> > Z [panelu klienta OVHcloud](/links/manager), w którym znajduje się Twoja domena e-mail, w sekcji `Web Cloud`{.action}, kliknij `Domeny`{.action} w lewej kolumnie i wybierz odpowiednią domenę.<br>
>> > Wybierz zakładkę `Strefa DNS`{.action}, a następnie kliknij `Dodaj wpis`{.action} w oknie, które się pojawi. Wybierz `CNAME`, a następnie uzupełnij zgodnie z wartościami, które zanotowałeś.

Aby włączyć DKIM, wystarczy kliknąć guzik `DKIM` czerwony, a następnie kliknąć `Zatwierdź`{.action} z pojawiającej się okienka aktywacji.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto02.png){.thumbnail .w-400 .h-600}

Automatyczna aktywacja DKIM trwa od 30 minut do maksymalnie 24 godzin. Aby sprawdzić, czy Twój DKIM działa poprawnie, wróć do sekcji zarządzania domeną, jak w powyższych zakładkach, i sprawdź, czy guzik `DKIM` jest zielony, lub, w przypadku oferty Zimbra, czy zakładka `DKIM` nie zawiera już ikony ostrzeżenia.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-auto03.png){.thumbnail .w-400 .h-600}

Po upływie 24 godzin, jeśli Twój guzik `DKIM` jest czerwony, skorzystaj z sekcji [„Dlaczego DKIM nie działa i pojawia się w kolorze czerwonym w panelu klienta ?”](#reddkim) tego przewodnika.

### Konfiguracja DKIM przez API dla e-maila OVHcloud <a name="internal-dkim"></a>

Dla platformy Exchange lub E-mail Pro, musisz najpierw pobrać odniesienie do swojej platformy, aby skonfigurować DKIM.

Kliknij na zakładkę poniżej odpowiadającą Twojej ofercie.

> [!tabs]
> **Exchange**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. W sekcji `MICROSOFT`, kliknij `Exchange`{.action}.
>> 1. Wybierz odpowiednią platformę.
>>
>> Domyślnie nazwa Twojej platformy odpowiada jej odniesieniu lub będzie widoczna pod nazwą, którą jej nadałeś (patrz poniższy obraz).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/general-information/dns-dkim-platform-exchange.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. Kliknij `Email Pro`{.action}.
>> 1. Wybierz odpowiednią platformę.
>>
>> Domyślnie nazwa Twojej platformy odpowiada jej odniesieniu lub będzie widoczna pod nazwą, którą jej nadałeś (patrz poniższy obraz).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/email-pro/general-information/dns-dkim-platform-emailpro.png){.thumbnail .w-400 .h-600}

Upewnij się również, że nazwa domeny, którą chcesz używać do swoich wiadomości e-mail, jest aktywna w sekcji `Powiązane domeny`{.action}.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dns-dkim-domain.png){.thumbnail .w-400 .h-600}

#### API - Pełna konfiguracja DKIM <a name="firststep"></a>

Aby skonfigurować DKIM, przejdź na [stronę API OVHcloud](/links/console) i zaloguj się:

1. Kliknij `Authentication`{.action} w lewym górnym rogu.
1. Kliknij następnie `Login with OVHcloud SSO`{.action}.
1. Wprowadź swoje dane logowania OVHcloud.
1. Kliknij przycisk `Authorize`{.action}, aby zezwolić na wywołania API z tej strony.

> [!primary]
>
> Skorzystaj z naszego przewodnika „[Pierwsze kroki z API OVHcloud](/pages/manage_and_operate/api/first-steps)”, jeśli nigdy wcześniej nie korzystałeś z API.

Przejdź do sekcji `/email/domain/` (oferty MX Plan i Zimbra), `/email/exchange` (oferta Exchange) lub `/email/pro` (oferta E-mail Pro) API i wpisz „dkim” w polu `Filter`, aby wyświetlić tylko funkcje API związane z DKIM.

Kliknij zakładkę odpowiadającą Twojej ofercie:

> [!tabs]
> **MX Plan i Zimbra**
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

##### **Dla MX Plan i Zimbra** <a name="confemail"></a>

Wykonaj **5 kroków**, klikając kolejno na poniższe 5 zakładek:

> [!tabs]
> **1. Włączanie DKIM dla swojego domeny**
>> Aby włączyć DKIM dla swojego domeny, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : wpisz nazwę domeny przypisaną do swojego konta E-mail, na którym chcesz włączyć DKIM.
>>
>> Kliknij `EXECUTE`{.action}, aby rozpocząć włączanie.<br>
>>
>> *Przykładowy wynik:*
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
>> Powinieneś otrzymać wynik podobny do powyższego przykładu z wzmianką `"status": "todo"`, która oznacza, że DKIM zostanie zainstalowany.
>>
> **2. Sprawdzenie statusu operacji DKIM**
>> Po uruchomieniu procesu włączania DKIM, sprawdź status instalacji, aby upewnić się, że instalacja się zakończyła lub aby pobrać rekordy DNS, jeśli Twoja strefa DNS jest zarządzana poza Twoim panelem klienta OVHcloud.<br>
>>.
>> <br>
>> Aby to zrobić, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : wpisz nazwę domeny przypisaną do swojego konta E-mail.<br>
>> <br>
>> Kliknij `EXECUTE`{.action}, aby wyświetlić wynik.<br>
>>
>> *Przykładowy wynik :*
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
>> W powyższym przykładzie ostatnia linia statusu `"status": "modifying"` oznacza, że konfiguracja jest w toku. Poczekaj około **10 minut** i ponownie uruchom wywołanie API.
>>
>> - jeśli wartość to `"status": "enabled"`, Twoja konfiguracja jest zakończona i działa.
>> - jeśli wartość to `"status": "disabled"`, Twoja konfiguracja musi zostać ukończona ręcznie, przejdź do następnego kroku.
>>
> **3. Pobranie rekordu DNS**
>> Musisz ręcznie skonfigurować strefę DNS swojej domeny **w następujących przypadkach** :
>>
>> - Twoje konto E-mail jest powiązane z domeną zarządzaną w innym koncie klienta OVHcloud;
>> - Twoje konto E-mail jest powiązane z domeną zarządzaną w innym rejestrze.
>>
>> Aby skonfigurować swoją strefę DNS, musisz pobrać wartości rekordu DNS **dla obu selektorów**. Aby to zrobić, użyj wyniku wywołania API z poprzedniego kroku :
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>> >
>>
>> - `domain` : wpisz nazwę domeny przypisaną do swojego konta E-mail.
>>
>> Kliknij `EXECUTE`{.action}, aby wyświetlić wynik.
>>
>> *Przykładowy wynik :*
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
>> Wartości `"status": "toSet"` i `"status": "disabled"` oznaczają, że rekordy CNAME należy skonfigurować. Pobierz obie wartości `cname` do pliku tekstowego i przejdź do następnego kroku.
>>
> **4. Konfiguracja rekordu DNS**
>> Z [panelu klienta OVHcloud](/links/manager), w którym znajduje się Twoja domena e-mail, w zakładce `Web Cloud`{.action}, kliknij `Noms de domaine`{.action} w lewej kolumnie i wybierz odpowiednią domenę.<br>
>> Przejdź do zakładki `Zone DNS`{.action}, a następnie kliknij `Ajouter une entrée`{.action} w oknie, które się otworzy. Wybierz `CNAME`, a następnie uzupełnij dane zgodnie z wartościami, które zanotowałeś.
>>
>> Jeśli rozłożymy wartości z przykładu w kroku "**3. Pobranie rekordu DNS**" :
>>
>> - `ovhmo3456789-selector1._domainkey.mydomain.ovh` odpowiada poddomenie rekordu CNAME. Zostawiamy tylko `ovhmo3456789-selector1._domainkey`, ponieważ `.mydomain.ovh` jest już wstępnie wypełnione. <br>
>> - `ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net."` odpowiada celowi rekordu. Trzeba zachować kropkę na końcu, aby zakończyć wartość.<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api022.png){.thumbnail .w-400 .h-600}
>>
>> Po wpisaniu wartości kliknij `Suivant`{.action}, a następnie `Valider`{.action}.
>>
>> > [!primary]
>> >
>> > **Powtórz tę operację dla drugiego selektora.**
>>
>> Jeśli konfigurujesz swoją strefę DNS w interfejsie zewnętrznym poza OVHcloud, Twój rekord CNAME powinien mieć następującą postać :
>>
>> ```console
>> ovhmo3456789-selector1._domainkey IN CNAME ovhmo3456789-selector1._domainkey.123403.aj.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Pamiętaj, że zmiana w strefie DNS może wymagać czasu propagacji. Jest on zazwyczaj krótki, ale może sięgać nawet 24 godzin.
>>
> **5. Włączenie DKIM**
>>
>> Po propagacji Twojej konfiguracji DNS, użyj ponownie poniższego wywołania API, aby włączyć DKIM:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/enable
>>
>> - `domain` : wpisz nazwę domeny przypisaną do swojego konta E-mail, na którym chcesz włączyć DKIM.
>>
>> Kliknij `EXECUTE`{.action}, aby rozpocząć włączanie.<br>
>>
>> *Przykładowy wynik :*
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
>> - Jeśli zauważysz wartości `"status": "set"` dla obu selektorów, oznacza to, że są one poprawnie skonfigurowane.
>> - Jeśli zauważysz wartości `"status": "toSet"` dla obu selektorów, oznacza to, że Twoje zmiany DNS nie są widoczne. Wróć do kroku „**4. Konfiguracja rekordu DNS**”.
>> - Jeśli zauważysz wartości `"status": "toFix"` dla obu selektorów, oznacza to, że rekordy CNAME zostały wykryte w strefie DNS Twojej domeny, ale wartości są niepoprawne. Wróć do kroku „**4. Konfiguracja rekordu DNS**”.
>>
>> > [!success]
>> >
>> > Teraz wykonałeś wszystkie operacje potrzebne do włączenia DKIM. Aby upewnić się, że jest on aktywny, sprawdź jego status, wracając do kroku „**2. Sprawdzenie statusu operacji DKIM**”, aby upewnić się, że wartość `status:` jest ustawiona na `enabled`. Jeśli tak, to Twój DKIM jest teraz aktywny.
>>

##### **Dla Exchange** <a name="confex"></a>

Wykonaj poniższe **5 kroków**, klikając każdy z zakładek.

> [!tabs]
> **1. Lista selektorów**
>> Przed utworzeniem jednego z selektorów dla swojego domeny, musisz uzyskać nazwę, która jest automatycznie przypisana przez platformę Exchange.<br>
>> <br>
>> Aby to zrobić, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkimSelector
>> >
>> <br>
>>
>> - `domainName` : wprowadź nazwę domeny przypisanej do Twojej platformy Exchange, na której chcesz włączyć DKIM. <br>
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”. <br>
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”. <br>
>>
>> *Przykładowy wynik :*
>>
>> ```console
>> "ovhex123456-selector1"
>> "ovhex123456-selector2"
>> ```
>>
> **2. Utwórz selektor**
>> Teraz utworzysz selektor, wygenerujesz parę kluczy i zarejestrujesz rekord DNS dla swojej domeny.<br>
>> <br>
>> Aby to zrobić, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisanej do Twojej platformy Exchange, na której chcesz włączyć DKIM.
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `"selectorName"` : w zakładce **EXAMPLE** sekcji **REQUEST BODY**, wprowadź nazwę selektora, którą zanotowałeś w poprzednim kroku (np. „ovhex123456-selector1”).
>>
>> *Przykładowe dane wejściowe :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhex123456-selector1"
>> }
>> ```
>>
>> Kliknij `EXECUTE`{.action}, aby rozpocząć tworzenie selektora.<br>
>>
>> > [!primary]
>> >
>> > Zalecamy wykonanie tej operacji dwukrotnie dla każdego z wcześniej wymienionych selektorów. Drugi selektor pozwoli Ci zmienić parę kluczy, gdy to będzie konieczne. Zalecamy, abyś zapoznał się z naszym przypadkiem użycia [„Jak zmienić parę kluczy DKIM”](#2selectors), gdy zechcesz przełączyć się na drugi selektor.
>> <br>
>>
>> *Przykładowy wynik :*
>>
>> ```console
>> status: "todo",
>> function: "addExchangeDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Pobierz rekord DNS**
>> Musisz ręcznie skonfigurować strefę DNS swojej domeny **w poniższych przypadkach** :
>>
>> - Twoja platforma Exchange jest powiązana z domeną, która jest zarządzana w innym koncie klienta OVHcloud ;<br>
>> - Twoja platforma Exchange jest powiązana z domeną, która jest zarządzana w innym rejestrze ;<br>
>>
>> Aby skonfigurować swoją strefę DNS, musisz pobrać wartości rekordu DNS **dla każdego selektora, jeśli utworzyłeś dwa**. Aby to zrobić, użyj poniższego wywołania API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisanej do Twojej platformy Exchange, na której chcesz skonfigurować DKIM.
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `selectorName` : wprowadź nazwę selektora, którą utworzyłeś w poprzednim kroku.
>>
>> *Przykładowy wynik :*
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
>> Pobierz wartości `customerRecord` i `targetRecord` do pliku tekstowego. Przejdź do następnego kroku.
>>
>> > [!primary]
>> >
>> > Możliwe, że `status:` będzie w stanie `todo`, to nie wpływa na konfigurację Twojej strefy DNS.
>>
> **4. Skonfiguruj rekord DNS**
>> Z [panelu klienta OVHcloud](/links/manager), w którym znajduje się Twoja domena, przejdź do zakładki `Web Cloud`{.action}, kliknij `Noms de domaine`{.action} w lewej kolumnie i wybierz odpowiednią domenę.<br>
>> Przejdź do zakładki `Zone DNS`{.action}, a następnie kliknij `Ajouter une entrée`{.action} w oknie, które się otworzy. Wybierz `CNAME`, a następnie uzupełnij dane zgodnie z wartościami, które zanotowałeś.<br>
>>
>> Jeśli weźmiemy wartości z przykładu w kroku "**3. Pobierz rekord DNS**":
>>
>> - `customerRecord: "ovhex123456-selector1._domainkey.mydomain.ovh"` odpowiada poddomenie rekordu CNAME. Pozostawiamy tylko `ovhex123456-selector1._domainkey`, ponieważ `.mydomain.ovh` jest już wstępnie wypełnione. <br>
>> - `targetRecord: "ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` odpowiada docelowi rekordu. Dodaj kropkę na końcu, aby zakończyć wartość. Otrzymujemy `ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Po wprowadzeniu wartości kliknij `Suivant`{.action}, a następnie `Valider`{.action}.<br>
>>
>> **Powtórz tę operację dla drugiego selektora, jeśli go utworzyłeś.**<br>
>>
>> Jeśli konfigurujesz swoją strefę DNS w interfejsie zewnętrznym poza OVHcloud, Twój rekord CNAME powinien mieć następującą postać :
>>
>> ```console
>> ovhex123456-selector1._domainkey IN CNAME ovhex123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Pamiętaj, że zmiana w strefie DNS może być poddana opóźnieniu propagacji. Jest to zazwyczaj krótkie, ale może trwać nawet do 24 godzin.
>>
> **5. Włączanie DKIM**
>> > [!warning]
>> >
>> > W sekcji „[API - Różne stany DKIM](#dkim-status)” tego przewodnika upewnij się, że wartość `status:` jest `ready`, zanim włączysz DKIM.
>>
>> Aby włączyć DKIM, użyj poniższego wywołania API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/enable
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisanej do Twojej platformy Exchange, na której chcesz włączyć DKIM.
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange, która ma postać „hosted-zz111111-1” lub „private-zz111111-1”.
>> - `selectorName` : wprowadź nazwę selektora, którą utworzyłeś.
>>
>> *Przykładowy wynik :*
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
>> > Teraz wykonano wszystkie operacje potrzebne do włączenia DKIM. Aby upewnić się, że jest on aktywny, sprawdź sekcję „[API - Różne stany DKIM](#dkim-status)” tego przewodnika, aby upewnić się, że wartość `status:` jest `inProduction`. Jeśli tak, to Twój DKIM jest teraz aktywny.<br><br> **Jeśli utworzyłeś dwa selektory**, drugi selektor powinien mieć `status: "ready"`.
>>

##### **Dla E-mail Pro** <a name="confemp"></a>

Wykonaj poniższe **5 kroków**, klikając w każdy z zakładek.

> [!tabs]
> **1. Lista selektorów**
>> Przed utworzeniem jednego z selektorów dla swojego nazwy domeny, musisz odzyskać nazwę, która jest automatycznie przypisana przez platformę E-mail Pro.<br>
>> <br>
>> Aby to zrobić, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim
>> <br>
>>
>> - `service` : wpisz nazwę swojej platformy E-mail Pro w formie "emailpro-zz111111-1". <br>
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy E-mail Pro, na której chcesz włączyć DKIM. <br>
>>
>> *Przykład wyniku :*
>>
>> ```console
>> "ovhemp123456-selector1"
>> "ovhemp123456-selector2"
>> ```
>>
> **2. Utwórz selektor**
>> Teraz utworzysz selektor, wygenerujesz parę kluczy i wpis DNS powiązany z nazwą domeny.<br>
>>
>> > [!primary]
>> >
>> > Zalecamy wykonanie tej operacji dwukrotnie dla każdego z wcześniej wymienionych selektorów. Drugi selektor pozwoli Ci zmienić parę kluczy, gdy to będzie konieczne. Zachęcamy do zapoznania się z naszym przypadkiem użycia [„Jak zmienić parę kluczy DKIM”](#2selectors).
>> <br>
>> Aby to zrobić, użyj poniższego wywołania API:<br>
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim
>> >
>>
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy E-mail Pro, na której chcesz włączyć DKIM.
>> - `service` : wpisz nazwę swojej platformy E-mail Pro w formie "emailpro-zz111111-1". <br>
>> - `"selectorName"` : W zakładce **EXAMPLE** sekcji **REQUEST BODY**, wpisz nazwę selektora, którą zanotowałeś w poprzednim kroku. (przykład: "ovhemp123456-selector1").
>>
>> *Przykład wpisu :*
>>
>> ```console
>> {
>>    "autoEnableDKIM": false,
>>    "configureDkim": false,
>>    "selectorName": "ovhemp123456-selector1"
>> }
>> ```
>>
>> Kliknij `EXECUTE`{.action}, aby rozpocząć tworzenie selektora.<br>
>>
>> > [!primary]
>> >
>> > Zalecamy wykonanie tej operacji dwukrotnie dla każdego z wcześniej wymienionych selektorów. Drugi selektor pozwoli Ci zmienić parę kluczy, gdy to będzie konieczne. Zachęcamy do zapoznania się z naszym przypadkiem użycia [„Jak zmienić parę kluczy DKIM”](#2selectors), gdy chcesz przełączyć się na drugi selektor.
>>
>> *Przykład wyniku :*
>>
>> ```console
>> status: "todo",
>> function: "addDomainDKIM",
>> id : 107924143,
>> "finishDate": null,
>> "todoDate": "2023-05-05T11:32:07+02:00"
>> ```
>>
> **3. Pobierz wpis DNS**
>> Musisz ręcznie skonfigurować strefę DNS swojej nazwy domeny **w następujących przypadkach** :
>>
>> - Twoja platforma E-mail Pro jest powiązana z nazwą domeny zarządzaną w innym koncie klienta OVHcloud ;<br>
>> - Twoja platforma E-mail Pro jest powiązana z nazwą domeny zarządzaną w innym rejestrze ;<br>
>>
>> Aby skonfigurować swoją strefę DNS, musisz pobrać wartości wpisu DNS **dla każdego selektora, jeśli stworzyłeś dwa**. Aby to zrobić, użyj poniższego wywołania API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : wpisz nazwę swojej platformy E-mail Pro w formie "emailpro-zz111111-1".
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy E-mail Pro, na której chcesz skonfigurować DKIM.
>> - `selectorName` : wpisz nazwę selektora, którą stworzyłeś w poprzednim kroku.
>>
>> *Przykład wyniku :*
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
>> Pobierz wartości `customerRecord` i `targetRecord` do pliku tekstowego. Przejdź do następnego kroku.
>>
>> > [!primary]
>> >
>> > Możliwe, że `status:` będzie w stanie `todo`, to nie wpływa na konfigurację Twojej strefy DNS.
>>
> **4. Skonfiguruj wpis DNS**
>> Z [panelu klienta OVHcloud](/links/manager), w którym znajduje się nazwa domeny Twojej platformy E-mail Pro, kliknij `Web Cloud`{.action} w górnym pasku, a następnie kliknij `Noms de domaine`{.action} w lewej kolumnie i wybierz odpowiednią nazwę domeny.<br>
>> Przejdź do zakładki `Zone DNS`{.action}, a następnie kliknij `Ajouter une entrée`{.action} w oknie, które się otworzy. Wybierz `CNAME`, a następnie uzupełnij dane zgodnie z wartościami, które zanotowałeś.<br>
>>
>> Jeśli weźmiemy wartości z przykładu w kroku "**3. Pobierz wpis DNS**":
>>
>> - `customerRecord: "ovhemp123456-selector1._domainkey.mydomain.ovh"` odpowiada poddomenie wpisu CNAME. Pozostawiamy tylko `ovhemp123456-selector1._domainkey`, ponieważ `.mydomain.ovh` jest już wypełnione. <br>
>> - `targetRecord: "ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net"` odpowiada celowi wpisu. Dodaj kropkę na końcu, aby zakończyć wartość. Otrzymujemy `ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.`<br>
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-api02.png){.thumbnail .w-400 .h-600} <br>
>> 
>> Po wpisaniu wartości kliknij `Suivant`{.action}, a następnie `Valider`{.action}.<br>
>>
>> **Wykonaj tę operację ponownie dla drugiego selektora, jeśli go stworzyłeś.**<br>
>>
>> Jeśli konfigurujesz swoją strefę DNS w zewnętrznym interfejsie poza OVHcloud, wpis CNAME powinien mieć poniższą formę :
>>
>> ```console
>> ovhemp123456-selector1._domainkey IN CNAME ovhemp123456-selector1._domainkey.1500.ab.dkim.mail.ovh.net.
>> ```
>>
>> > [!warning]
>> >
>> > Pamiętaj, że zmiana w strefie DNS może wymagać czasu propagacji. Jest to zazwyczaj krótki czas, ale może wynosić nawet 24 godziny.
>>
> **5. Włączanie DKIM**
>> > [!warning]
>> >
>> > W sekcji „[API - Różne stany DKIM](#dkim-status)” tego przewodnika upewnij się, że wartość `status:` jest ustawiona na `ready`, zanim włączysz DKIM.
>>
>> Aby włączyć DKIM, użyj poniższego wywołania API :
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : wpisz nazwę swojej platformy E-mail Pro w formie "emailpro-zz111111-1".
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy E-mail Pro, na której chcesz włączyć DKIM.
>> - `selectorName` : wpisz nazwę selektora, którą stworzyłeś.
>>
>> *Przykład wyniku :*
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
>> > Wykonałeś teraz wszystkie czynności potrzebne do włączenia DKIM. Aby upewnić się, że jest on aktywny, sprawdź sekcję „[API - Różne stany DKIM](#dkim-status)”, aby upewnić się, że wartość `status:` jest ustawiona na `inProduction`. Jeśli tak, to DKIM jest teraz aktywny.<br><br> **Jeśli stworzyłeś dwa selektory**, drugi selektor powinien być w stanie `status: "ready"`.
>>

#### API - Różne stany DKIM <a name="dkim-status"></a>

Wybierz ofertę e-mail w odpowiednich zakładkach poniżej :

> [!tabs]
> **MX Plan i Zimbra**
>> W trakcie operacji na DKIM Twojej platformy e-mail, użyj poniższego wywołania API, aby sprawdzić aktualny stan DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ GET /email/domain/{domain}/dkim
>>
>> - `domain` : wpisz nazwę domeny przypisaną do Twojej usługi e-mail, na której DKIM powinien być obecny.
>>
>> Sprawdź następnie ogólną wartość `status:` w wyniku :
>>
>> - `disabled` : DKIM jest wyłączony, nie został jeszcze skonfigurowany lub został wyłączony przez API. <br>
>> - `modifying` : konfiguracja DKIM jest w toku, należy poczekać na zakończenie procesu.<br>
>> - `toConfigure` : konfiguracja DKIM oczekuje na parametry DNS nazwy domeny. Musisz ręcznie wprowadzić wpisy DNS w strefie nazwy domeny. W tym celu skorzystaj z [kroku 4 „Pełna konfiguracja DKIM” dla MX Plan i Zimbra](#confemail).<br>
>> - `enabled` : DKIM jest skonfigurowany i działa.<br>
>> - `error` : Proces instalacji napotkał błąd. Zachęcamy do otwarcia [biletu do wsparcia](https://help.ovhcloud.com/csm?id=csm_get_help), określając nazwę domeny.<br>
>>
>> Na poziomie selektorów masz również trzy możliwe stany:
>>
>> - `set` : selektor jest poprawnie skonfigurowany i aktywny.
>> - `toSet` : selektor nie został skonfigurowany w strefie DNS nazwy domeny. W tym celu skorzystaj z [kroku 4 „Pełna konfiguracja DKIM” dla MX Plan i Zimbra](#confemail).
>> - `toFix` : selektor został poprawnie skonfigurowany w strefie DNS nazwy domeny, ale wartości są nieprawidłowe. W tym celu skorzystaj z [kroku 4 „Pełna konfiguracja DKIM” dla MX Plan i Zimbra](#confemail).
>>
> **Exchange**
>> W trakcie operacji na DKIM Twojej platformy Exchange, użyj poniższego wywołania API, aby sprawdzić aktualny stan DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange GET /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy Exchange, na której DKIM powinien być obecny. <br>
>> - `exchangeService` : wpisz nazwę swojej platformy Exchange w formie "hosted-zz111111-1" lub "private-zz111111-1". <br>
>> - `organizationName` : wpisz nazwę swojej platformy Exchange w formie "hosted-zz111111-1" lub "private-zz111111-1". <br>
>> - `selectorName` : wpisz nazwę selektora, którą stworzyłeś. <br>
>>
>> Sprawdź następnie wartość `status:` w wyniku :
>>
>> - `todo` : zadanie zostało zainicjowane, będzie się wykonywać. <br>
>> - `WaitingRecord` : wpisy DNS oczekują na konfigurację lub są w trakcie weryfikacji w strefie DNS nazwy domeny. Wykonywana jest regularna automatyczna weryfikacja, czy wpis DNS istnieje i jest poprawnie wprowadzony.
>> - `ready` : wpisy DNS są obecne w strefie. DKIM może teraz zostać włączony. <br>
>> - `inProduction` : DKIM jest poprawnie skonfigurowany i włączony, działa więc w pełni. <br>
>> - `disabling` : DKIM jest w trakcie wyłączania. <br>
>> - `deleting` : DKIM jest w trakcie usuwania. <br>
>>
>> Jeśli napotkasz poniższy błąd podczas wywołania API, oznacza to, że selektor nie istnieje lub został usunięty. Musisz go stworzyć.
>>
>> ```console
>> Not Found (404)
>> { "message": "The requested object (selectorName = ovhemp123456-selector1) does not exist" }
>> ```
>>
> **E-mail Pro**
>> W trakcie operacji na DKIM Twojej platformy E-mail Pro, użyj poniższego wywołania API, aby sprawdzić aktualny stan DKIM.
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro GET /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `service` : wpisz nazwę swojej platformy E-mail Pro w formie "emailpro-zz111111-1". <br>
>> - `domainName` : wpisz nazwę domeny przypisaną do Twojej platformy E-mail Pro, na której DKIM powinien być obecny. <br>
>> - `selectorName` : wpisz nazwę selektora, którą stworzyłeś. <br>
>>
>> Sprawdź następnie wartość `status:` w wyniku :
>>
>> - `todo` : zadanie zostało zainicjowane, będzie się wykonywać. <br>
>> - `WaitingRecord` : wpisy DNS oczekują na konfigurację lub są w trakcie weryfikacji w strefie DNS nazwy domeny. Wykonywana jest regularna automatycz

> [!primary]
>
> W przypadku rotacji selektora DKIM możesz bezpośrednio aktywować drugi selektor, który utworzyłeś, aby przełączyć się na niego, jednocześnie zachowując pierwszy selektor, który pozostanie aktywny przez czas, w którym wszystkie wiadomości e-mail wysłane za pomocą niego zostaną prawidłowo przeanalizowane przez odbiorcę.

#### API - Wyłączenie i usunięcie DKIM <a name="enable-switch"></a>

> [!warning]
>
> **Dla ofert Exchange i E-mail Pro** <br>
>
> Selektor DKIM musi mieć status `inProduction` lub `ready`, zanim będzie można go wyłączyć.

Wybierz ofertę e-mail spośród poniższych kart:

> [!tabs]
> **MX Plan i Zimbra**
>> Jeśli chcesz wyłączyć DKIM bez usuwania selektorów i ich par kluczy, użyj poniższego wywołania API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/domain/ PUT /email/domain/{domain}/dkim/disable
>> <br>
>>
>> - `domain` : wprowadź nazwę domeny przypisaną do Twojej usługi E-mail, na której DKIM powinien być obecny. <br>
>>
>> *Przykład wyniku:*
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
>> Jeśli chcesz wyłączyć DKIM bez usuwania selektora i jego pary kluczy, użyj poniższego wywołania API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange POST /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisaną do Twojej platformy Exchange. <br>
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange w formacie « hosted-zz111111-1 » lub « private-zz111111-1 ». <br>
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange w formacie « hosted-zz111111-1 » lub « private-zz111111-1 ». <br>
>> - `selectorName` : wprowadź nazwę selektora, który chcesz wyłączyć. <br>
>>
>> Jeśli chcesz usunąć selektor DKIM i jego parę kluczy, użyj poniższego wywołania API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/exchange DELETE /email/exchange/{organizationName}/service/{exchangeService}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisaną do Twojej platformy Exchange. <br>
>> - `exchangeService` : wprowadź nazwę swojej platformy Exchange w formacie « hosted-zz111111-1 » lub « private-zz111111-1 ». <br>
>> - `organizationName` : wprowadź nazwę swojej platformy Exchange w formacie « hosted-zz111111-1 » lub « private-zz111111-1 ». <br>
>> - `selectorName` : wprowadź nazwę selektora, który chcesz usunąć. <br>
>>
> **E-mail Pro**
>> Jeśli chcesz wyłączyć DKIM bez usuwania selektora i jego pary kluczy, użyj poniższego wywołania API:
>> 
>> > [!api]
>> >
>> > @api {v1} /email/pro POST /email/pro/{service}/domain/{domainName}/dkim/{selectorName}/disable
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisaną do Twojej platformy E-mail Pro. <br>
>> - `selectorName` : wprowadź nazwę selektora, który chcesz wyłączyć. <br>
>> - `service` : wprowadź nazwę swojej platformy E-mail Pro w formacie « emailpro-zz111111-1 ». <br>
>>
>> Jeśli chcesz usunąć selektor DKIM i jego parę kluczy, użyj poniższego wywołania API:
>>
>> > [!api]
>> >
>> > @api {v1} /email/pro DELETE /email/pro/{service}/domain/{domainName}/dkim/{selectorName}
>> >
>>
>> - `domainName` : wprowadź nazwę domeny przypisaną do Twojej platformy E-mail Pro. <br>
>> - `selectorName` : wprowadź nazwę selektora, który chcesz usunąć. <br>
>> - `service` : wprowadź nazwę swojej platformy E-mail Pro w formacie « emailpro-zz111111-1 ». <br>
>>

### Konfiguracja DKIM dla oferty e-mail spoza Twojego konta OVHcloud <a name="external-dkim"></a>

Jeśli chcesz skonfigurować swoją strefę DNS, aby dodać wpis DKIM dla swojej oferty, wykonaj poniższe instrukcje.

Z [panelu klienta OVHcloud](/links/manager) kliknij kartę `Web Cloud`{.action}, a następnie `Domeny`{.action} w lewej kolumnie i wybierz odpowiednią nazwę domeny.

Kliknij kartę `Strefa DNS`{.action}, a następnie `Dodaj wpis`{.action}. Istnieją 3 sposoby dodania wpisu, aby skonfigurować DKIM w Twojej strefie DNS:

- [wpis DKIM](#dkim-record) : konfiguracja umożliwiająca wyświetlenie wszystkich parametrów wpisu DKIM.
- [wpis TXT](#txt-record) : wpis do użycia, gdy wszystkie parametry DKIM zostały Ci dostarczone.
- [wpis CNAME](#cname-record) : wpis używany dla oferty e-mail OVHcloud lub serwera e-mail Microsoft.

#### Wpis DKIM <a name="dkim-record"></a>

Ten wpis nosi nazwę DKIM na interfejsie, ale w rzeczywistości jest to wpis TXT. Wpis DKIM ma na celu ułatwić odczyt różnych elementów konfiguracji DKIM, prezentując je w formie niezależnych pól.

![email](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dns-dkim-add.png){.thumbnail .w-400 .h-600}

- **Poddomena** : wprowadź nazwę selektora DKIM i dodaj `._domainkey` jako sufiks, nazwa domeny zostanie automatycznie dodana na końcu.

*przykład:*

```console
  selector-name._domainkey.mydomain.ovh.
```

- **Wersja (v=)** : służy do wskazania wersji DKIM. Zaleca się jej użycie, a jej wartość domyślna to `DKIM1`.<br>
Jeśli jest określona, ten tag musi być umieszczony na początku wpisu i musi mieć wartość "DKIM1" (bez cudzysłowów). Wpisy rozpoczynające się od tagu "v=" z inną wartością powinny być zignorowane.

- **Granularność (g=)** : umożliwia określenie części « local-part » adresu e-mail, czyli części przed « @ ».<br>
Umożliwia określenie adresów e-mail, które są uprawnione do podpisywania wiadomości e-mail za pomocą klucza DKIM selektora.<br>
Domyślna wartość "g=" to "\*", co oznacza, że wszystkie adresy e-mail są uprawnione do użycia klucza podpisującego DKIM.<br>
Podając konkretną wartość dla "g=", można ograniczyć użycie klucza do określonej części adresu e-mail lub do określonego zakresu adresów e-mail za pomocą symboli ogólnozastępczych (np. "\*-group").

- **Algorytm (hash) (h=)** : umożliwia określenie algorytmów hashowania używanych do podpisywania nagłówków e-mail. Ten tag umożliwia określenie listy algorytmów hashowania, które będą używane do wygenerowania podpisu DKIM dla konkretnej wiadomości.

- **Typ klucza (k=)** : określa algorytm podpisu używany do podpisywania wiadomości e-mail wychodzących. Pozwala odbiorcom zrozumieć, jak wiadomość została podpisana i jaką metodę wykorzystano do weryfikacji jej autentyczności.<br>
Możliwe wartości dla tagu "k=" obejmują "rsa" dla algorytmu podpisu RSA i "ed25519" dla algorytmu podpisu Ed25519. Wybór algorytmu zależy od polityki bezpieczeństwa nadawcy i od obsługi przez odbiorcę.

- **Notatki (n=)** : służą do wstawiania notatek ważnych dla administratorów zarządzających systemem kluczy DKIM.<br>
Te notatki mogą być przydatne z punktu widzenia dokumentacji lub pomóc administratorom zrozumieć lub zarządzać działaniem DKIM. Notatki zawarte w n= nie są interpretowane przez programy i nie wpływają na działanie DKIM.

- **Klucz publiczny (base64) (p=)** : służy do wprowadzania danych klucza publicznego DKIM, które są zakodowane w formacie base64.<br>
Ten tag jest wymagany w podpisie DKIM i umożliwia odbiorcom odzyskanie klucza publicznego koniecznego do weryfikacji autentyczności podpisanej wiadomości.

- **Wycofaj klucz publiczny** : jeśli klucz publiczny DKIM został wycofany (np. w przypadku naruszenia prywatnego klucza), należy użyć pustej wartości dla tagu "p=", wskazując, że ten klucz publiczny nie jest już ważny. Odbiorcy powinni zwrócić błąd dla każdej podpisy DKIM odnoszącej się do wycofanego klucza.

- **Typ usługi (s=)**: Tag "s=" (Typ usługi) jest opcjonalny i nie jest domyślnie obecny. Pozwala określić, do jakich usług dotyczy ten wpis DKIM.<br>
Typy usług są definiowane przy użyciu listy słów kluczowych oddzielonych dwukropkiem ":".<br>
Odbiorca powinien zignorować ten wpis, jeśli odpowiedni typ usługi nie jest wymieniony.<br>
Tag "s=" ma na celu ograniczenie użycia kluczy do innych celów, w przypadku, gdy użycie DKIM będzie określone dla innych usług w przyszłości.<br>
Obecnie zdefiniowane typy usług to "\*" (wszystkie typy usług), "email" (e-mail).

- **Tryb testowy (t=y)** : umożliwia właścicielom domeny przetestowanie wdrożenia DKIM bez ryzyka, że wiadomości zostaną odrzucone lub oznaczone jako SPAM, jeśli weryfikacja podpisu DKIM zakończy się niepowodzeniem.<br>
Gdy używany jest flaga "t=y", odbiorca nie powinien inaczej traktować wiadomości podpisanych w trybie testowym ani wiadomości niepodpisanych. Jednak odbiorca może śledzić wynik trybu testowego, aby pomóc nadawcom.

- **Poddomeny (t=s)** : umożliwia ograniczenie użycia podpisu DKIM do samej nazwy domeny (np. @mydomain.ovh) lub dozwolenie wysyłania z nazwy domeny i jej poddomen (np. @mydomain.ovh, @test.mydomain.ovh, @other.mydomain.ovh, itp.).

#### Wpis TXT <a name="txt-record"></a>

Jest to rodzaj wpisu natywnego używanego do konfiguracji DKIM w strefie DNS Twojej nazwy domeny. Wymaga on dobrej znajomości jego składni, aby go uzupełnić.

Tego rodzaju konfiguracja DKIM jest zalecana, gdy dane do wpisania zostały Ci dostarczone przez dostawcę usługi e-mail.

Aby dobrze zrozumieć skład wpisu DKIM, zapoznaj się z poprzednią częścią tego przewodnika o tytule « [Wpis DKIM](#dkim-record) ».

**Przykład wpisu DKIM**

- poddomena :

```console
selector-name._domainkey.mydomain.ovh.
```

- cel :

```console
v=DKIM1;t=s;p= MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA77VDAIfyhjtoF0DIE5V7 rev1EKk4L0nxdBpD5O/jPrM4KP0kukeuB6IMpVplkkq52MSDeRcjoO50h0DmwZOr RUkyGjQwOnAh0VhY3fqkuwBYftEX7vWo8C2E1ylzimABkwPpSL62jZ1DheoXcil9 1M35wWBKtlYdXVedKjCQKOEnwTo+0hdNe38rU9NMgq6nbTIMjDntvxoVI+yF3kcx q/VpAY8BIYbcAXkVFvUyfUBABnnKpf0SfblsfcLW0Koy/FRxPDFOvnjNxXeOxMFR UI6K6PaW2WvtbJG2v+gHLY5M4tB0+/FNJU9emZfkPOk3DmRhZ8ENi7+oZa2ivUDj OQIDAQAB
```

#### Wpis CNAME <a name="cname-record"></a>

Wpis CNAME to alias. Oznacza to, że wartość celu wskazuje na adres URL, który samodzielnie dostarczy wpis DKIM serwerowi, który zapyta o wpis CNAME. Taki typ wpisu CNAME do konfiguracji DKIM jest powszechny w przypadku użycia serwera e-mail Microsoft.

Jest to dokładnie typ wpisu używany do włączenia DKIM na nazwie domeny zadeklarowanej dla oferty Exchange OVHcloud. Ten proces umożliwia Twojemu dostawcy rozwiązania e-mail zarządzanie dla Ciebie bezpieczeństwem i aktualizacją DKIM.

### Testowanie DKIM <a name="test-dkim"></a>

Zalecamy wysłanie wiadomości e-mail z konta na Twojej platformie Exchange do adresu e-mail, który sprawdza podpis DKIM podczas odbioru.

Oto, co możesz znaleźć w nagłówku otrzymanej wiadomości:

<pre class="bgwhite"><code>ARC-Authentication-Results: i=1; mx.example.com;
       dkim=pass header.i=@mydomain.ovh header.s=ovhex123456-selector1 header.b=KUdGjiMs;
       spf=pass (example.com: domain of test-dkim@mydomain.ovh designates 54.36.141.6 as permitted sender) smtp.mailfrom=test-dkim@mydomain.ovh
Return-Path: &lt;test-dkim@mydomain.ovh&gt;
</code></pre>

Aby pobrać nagłówek wiadomości e-mail, zapoznaj się z naszym przewodnikiem « [Pobranie nagłówka wiadomości e-mail](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/diagnostic_headers) ».

### Przypadki użycia <a name="usecases"></a>

#### Jak i dlaczego zmienić parę kluczy DKIM na mojej ofercie ? <a name="2selectors"></a>

> [!warning]
>
> Ta kwestia dotyczy wyłącznie ofert Exchange i E-mail Pro.

Gdy aktywujesz DK

Zauważasz, że Twoje e-maile nie są podpisywane DKIM, mimo że DKIM jest włączony lub skonfigurowany. W pierwszym kroku zaloguj się do swojego panelu klienta, aby sprawdzić stan DKIM.

Kliknij odpowiedni pasek zakładek poniżej, aby sprawdzić stan DKIM na Twojej platformie e-mail.

> [!tabs]
> **Exchange**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. W sekcji `MICROSOFT`, kliknij `Exchange`{.action}.
>> 1. Wybierz odpowiednią platformę.
>>
>> W sekcji `Domainy skojarzone`{.action}, sprawdź kolor ikony `DKIM` po prawej stronie nazwy domeny (patrz poniższy obraz).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>
> **E-mail Pro**
>>
>> 1. Zaloguj się do swojego [panelu klienta OVHcloud](/links/manager).
>> 1. Przejdź do sekcji `Web Cloud`{.action}.
>> 1. Kliknij `E-mail Pro`{.action}.
>> 1. Wybierz odpowiednią platformę.
>> 1. Na koniec przejdź do zakładki `Domainy skojarzone`{.action}.
>>
>> W sekcji `Domainy skojarzone`{.action}, sprawdź kolor ikony `DKIM` po prawej stronie nazwy domeny (patrz poniższy obraz).
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/red-dkim.png){.thumbnail .w-400 .h-600}
>>

Poniżej przedstawiamy 4 stany, które powodują czerwoną ikonę DKIM w Twoim panelu klienta. Kliknij zakładkę odpowiadającą Twojemu kodowi błędu:

> [!tabs]
> **501**
>>
>> " **Tylko jeden selektor DKIM został zainicjalizowany** "<br><br>
>> W Twojej konfiguracji istnieje tylko jeden selektor DKIM. Aby umożliwić przełączenie na nowy klucz, gdy to konieczne, należy skonfigurować oba selektory oferowane przez usługę.<br><br>
>> Aby poprawić ten błąd:
>>
>> - Sprawdź stan selektorów DKIM, aby zidentyfikować ten, który należy skonfigurować. W tym celu skorzystaj z sekcji „[API - Różne stany DKIM](#dkim-status)” tego przewodnika.
>> - Po zidentyfikowaniu selektora do skonfigurowania, wykonaj kroki z sekcji „[API - Pełna konfiguracja DKIM](#firststep)”, zgodnie z Twoją ofertą (Exchange lub E-mail Pro), stosując je wyłącznie do odpowiedniego selektora.
>> Poczekaj maksymalnie 24 godziny po skonfigurowaniu selektora.
>>
> **502**
>>
>> " **Wystąpił błąd podczas konfiguracji DKIM** "<br><br>
>> Wystąpił błąd podczas konfiguracji DKIM. Jeśli po 24 godzinach konfiguracja nadal znajduje się w tym stanie, prosimy o otwarcie [biletu do wsparcia](https://help.ovhcloud.com/csm?id=csm_get_help).
>>
> **503**
>>
>> " **Zapis CNAME jest niepoprawny** "<br><br>
>> Wartość zapisu CNAME wymaganego do konfiguracji DKIM nie została poprawnie wprowadzona. Musisz poprawnie skonfigurować strefę DNS dla przypisanego domeny.
>> Aby skonfigurować swoją strefę DNS, pobierz wartości zapisu CNAME, który się wyświetla:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Weźmy przykład z powyższego zrzutu ekranu, gdzie domena to „ **mydomain.ovh** ”, a wymagane jest skonfigurowanie selektora „ **2** ”. W tym przypadku należy dodać zapis CNAME o wartości poddomeny `ovhex1234567-selector2.domainkey.mydomain.ovh` i jako cel `ovhex1234567-selector2.domainkey.7890.dkim.mail.ovh.net`.<br><br>
>> Po skonfigurowaniu strefy DNS, poczekaj na propagację DNS (maksymalnie 24 godziny)
>>
> **504**
>>
>> " **Brakuje zapisu CNAME** "<br><br>
>> Wartość zapisu CNAME wymaganego do konfiguracji DKIM jest brakująca. Musisz skonfigurować strefę DNS dla przypisanego domeny.
>> Aby skonfigurować swoją strefę DNS, pobierz wartości zapisu CNAME, który się wyświetla:
>>
>> ![email](/pages/assets/screens/control_panel/product-selection/web-cloud/microsoft/exchange/associated-domains/dkim-503.png){.thumbnail .w-400 .h-600}
>>
>> Weźmy przykład z powyższego zrzutu ekranu, gdzie domena to „ **mydomain.ovh** ”, a wymagane jest skonfigurowanie selektora „ **2** ”. W tym przypadku należy dodać zapis CNAME o wartości poddomeny `ovhex1234567-selector2.domainkey.mydomain.ovh` i jako cel `ovhex1234567-selector2.domainkey.890123.dkim.mail.ovh.net`.<br><br>
>> Po skonfigurowaniu strefy DNS, poczekaj na propagację DNS (maksymalnie 24 godziny)
>>

#### Jak zrozumieć stan DKIM, który nie działa, korzystając z interfejsu API OVHcloud? <a name="api-error"></a>

Jeśli korzystasz z API OVHcloud do konfiguracji DKIM i ten nie działa, skorzystaj z sekcji „[API - Różne stany DKIM](#dkim-status)” tego przewodnika, aby zidentyfikować stan Twoich selektorów.

Poniżej znajdziesz stany, które mogą blokować działanie DKIM oraz odpowiednie rozwiązania dla każdej sytuacji.

> [!tabs]
> **Exchange i E-mail Pro**
>> - `WaitingRecord` : Zapisy DNS są w trakcie konfiguracji lub weryfikacji w strefie DNS domeny. Wykonuje się regularne automatyczne sprawdzenia, czy zapis DNS istnieje i jest poprawnie wprowadzony. Zgodnie z Twoją ofertą, wykonaj **krok 5** w sekcji „[API - Pełna konfiguracja DKIM](#firststep)”, aby poprawnie skonfigurować strefę DNS dla odpowiedniej domeny.
>> - `ready` : Zapisy DNS są obecne w strefie. DKIM może zostać teraz włączony. Wystarczy włączyć selektor, korzystając z sekcji „[API - Włączanie lub zmiana selektora DKIM](#enable-switch)”.
>> - `deleting` : DKIM jest w trakcie usuwania. Po usunięciu należy wykonać sekcję „[API - Pełna konfiguracja DKIM](#firststep)”.
>> - `disabling` : DKIM jest w trakcie wyłączania. Po tej operacji, możesz włączyć selektor, korzystając z sekcji „[API - Włączanie lub zmiana selektora DKIM](#enable-switch)”.
>> - `todo` : Zadanie zostało zainicjalizowane, ale nie zostało uruchomione. Jeśli po 24 godzinach Twój selektor nadal znajduje się w tym stanie, prosimy o otwarcie [biletu do wsparcia](https://help.ovhcloud.com/csm?id=csm_get_help), podając numer odpowiedniego selektora.
> **MX Plan i Zimbra**
>> - `disabled` : DKIM jest wyłączony, nie został jeszcze skonfigurowany lub został wyłączony przez API. <br>
>> - `modifying` : Konfiguracja DKIM jest w trakcie, należy poczekać na zakończenie procesu.<br>
>> - `toConfigure` : Konfiguracja DKIM oczekuje na parametry DNS domeny. Musisz ręcznie wprowadzić zapisy DNS w strefie domeny. W tym celu skorzystaj z kroku „[Pełna konfiguracja DKIM](#confemail)” tego przewodnika. <br>
>> - `error` : W trakcie instalacji wystąpił błąd. Prosimy o otwarcie [biletu do wsparcia](https://help.ovhcloud.com/csm?id=csm_get_help), podając nazwę odpowiedniej domeny.
>>
>> W zakresie selektorów masz również dwa stany związane z błędem:
>>
>> - `toSet` : Selektor nie został skonfigurowany w strefie DNS domeny. Skorzystaj z [kroku 4 „Pełna konfiguracja DKIM” dla MX Plan i Zimbra](#confemail).
>> - `toFix` : Selektor został poprawnie skonfigurowany w strefie DNS domeny, ale wartości są niepoprawne. Skorzystaj z [kroku 4 „Pełna konfiguracja DKIM” dla MX Plan i Zimbra](#confemail).

## Sprawdź również
Dołącz do [grona naszych użytkowników](/links/community).

W przypadku wdrożenia dynamicznego zapisu DNS (DynHost), użycie wildcard (znak `*`) w polu `poddomena`{.action} formularza zapisu DNS nie jest dostępne.