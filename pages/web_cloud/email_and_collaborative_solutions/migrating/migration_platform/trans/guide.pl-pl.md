---
title: "Migrowanie adresów e-mail z jednej platformy e-mail OVHcloud do drugiej"
excerpt: "Dowiedz się, jak migrować adresy e-mail z jednej platformy Exchange lub E-mail Pro do innej platformy Exchange, E-mail Pro, MX Plan lub Zimbra"
updated: 2025-12-22
---

## Wprowadzenie

Chcesz przenieść swoje adresy e-mail z jednej platformy Exchange lub E-mail Pro do innej platformy Exchange, E-mail Pro lub MX Plan. W tym przewodniku znajdziesz dwuetapowy proces migracji:

1. **Skonfiguruj platformę docelową**.
2. **Przenieś konta e-mail** z obecnej platformy do nowej.

![email-migration](images/migration_platform01.gif){.thumbnail}

> [!primary]
>
> Aby przenieść rozwiązanie MX Plan do platformy Exchange lub E-mail Pro, zapraszamy do przeczytania naszego przewodnika [Migrowanie adresu e-mail MX Plan do konta E-mail Pro lub Exchange](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_control_panel).
>

**Dowiedz się, jak przenieść adresy e-mail z jednej platformy Exchange lub E-mail Pro do innej platformy Exchange lub E-mail Pro.**

## Wymagania początkowe

- Posiadaj platformę **źródłową** z skonfigurowanymi kontami [Exchange](/links/web/emails-hosted-exchange) lub [E-mail Pro](/links/web/email-pro) lub [Zimbra](/links/web/zimbra).
- Posiadaj platformę **docelową** z kontami [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) lub MX Plan (za pośrednictwem oferty MX Plan lub zawartą w ofercie [hostingu OVHcloud](/links/web/hosting)). Ta platforma musi mieć konta niezainstalowane lub dostępne, aby przyjąć adresy e-mail, które mają zostać przeniesione.
- Zaloguj się do swojego [konta OVHcloud](/links/manager).

## W praktyce

### Skonfiguruj platformę docelową

> [!warning]
>
> Przed rozpoczęciem migracji, jeśli właśnie zamówiłeś nową ofertę e-mail, najpierw dodaj nazwę domeny do swojej platformy e-mail. Jeśli migrujesz do platformy MX Plan, ponieważ nazwa domeny jest „stała”, możesz przejść bezpośrednio do [następnej etapu](#accountsmigration).
>
> Wybierz kartę `Domaines associés`{.action} lub `Domaine`{.action} na swojej platformie, a następnie kliknij `Ajouter un domaine`{.action}. Po dodaniu nazwy domeny upewnij się, że w kolumnie `Statut` widoczna jest marka `OK` lub `Actif`{.action}.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Aby uzyskać więcej informacji na temat dodawania nazwy domeny, zapoznaj się z [przewodnikiem E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [przewodnikiem Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) lub [przewodnikiem Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

### Migrowanie kont e-mail <a name="accountsmigration"></a>

Migracja kont e-mail składa się z trzech głównych etapów: **Zmiana nazwy** konta e-mail źródłowego, **utworzenie** nowego konta e-mail i **przeniesienie** z platformy źródłowej do nowej.

![email-migration](images/migration_platform03.gif){.thumbnail}

> [!warning]
>
> Przypadek specjalny:
>
> - Jeśli musisz przenieść **konto Exchange lub Zimbra PRO** do konta **E-mail Pro** lub **Zimbra STARTER**, musisz upewnić się, że Twoje konta e-mail nie przekraczają 10 Go (E-mail Pro) lub 15 Go (Zimbra STARTER). Funkcje współpracy, synchronizacja kalendarzy i kontaktów nie są dostępne w E-mail Pro ani Zimbra STARTER i nie mogą być przeniesione.
> - Jeśli musisz przenieść **konto Exchange, E-mail Pro lub Zimbra** do konta **MX Plan**, musisz upewnić się, że Twoje konto e-mail nie przekracza 5 Go. Funkcje współpracy, synchronizacja kalendarzy i kontaktów nie są dostępne w MX Plan i nie mogą być przeniesione.

#### Zmiana nazwy

Zmień nazwę konta e-mail, które chcesz przenieść, na tymczasową (np. do przeniesienia konta e-mail *john.smith@mydomain.ovh*, zmień jego nazwę na *john.smith01@mydomain.ovh*).

Na karcie `Comptes e-mail`{.action} swojej platformy e-mail kliknij przycisk `...`{.action}, a następnie `Modifier`{.action}.

![email-migration](images/migration_platform04.png){.thumbnail}

#### Utwórz

Utwórz adres e-mail na nowym koncie swojej platformy E-mail Pro, Exchange lub MX Plan (w powyższym przykładzie utworzysz więc *john.smith@mydomain.ovh* na nowej platformie).

Na karcie `Comptes e-mail`{.action} swojej platformy kliknij przycisk `...`{.action}, po prawej stronie konta e-mail docelowego, a następnie `Modifier`{.action}.

![email-migration](images/migration_platform05.png){.thumbnail}

#### Przenieś

> [!warning]
> 
> Tylko dane kont e-mail zostaną przeniesione (e-maile, kontakty, kalendarze, reguły skrzynki odbiorczej itp.). Funkcje związane z Twoją platformą muszą zostać ponownie utworzone na nowej platformie:
>
> - [Aliasy](/pages/web_cloud/email_and_collaborative_solutions/common_email_features/feature_redirections) 
> - [Delegacje uprawnień](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_delegation) 
> - [Grupy](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_groups)
> - Kontakty zewnętrzne
> - [Stopka](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/feature_footers)

Przenieś konto e-mail „źródłowe” do konta na nowej platformie za pomocą naszego narzędzia [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Aby uzyskać więcej informacji na temat OMM, zapoznaj się z naszym przewodnikiem [Migrowanie kont e-mail za pomocą OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![email-migration](images/migration_platform06.png){.thumbnail}

Czas migracji zależy od ilości danych do przeniesienia do nowego konta. Może on sięgać od kilku minut do kilku godzin.

Po migracji upewnij się, że wszystkie elementy są dostępne, logując się do webmaila pod adresem [Webmail](/links/web/email).

Po wykonaniu migracji możesz zachować lub usunąć konto źródłowe z tymczasową nazwą.

Jeśli chcesz je usunąć, przejdź do karty `Comptes e-mail`{.action} swojej platformy e-mail źródłowej, kliknij przycisk `...`{.action}, a następnie `Réinitialiser ce compte`{.action}.

### Sprawdź lub zmień konfigurację swojego domeny

W tym etapie Twoje adresy e-mail powinny być już przeniesione i działać. Dla bezpieczeństwa zalecamy, aby upewnić się, że konfiguracja Twojego domeny jest poprawna, sprawdzając to w Twoim panelu klienta.

Aby to zrobić, wybierz odpowiedni serwis E-mail Pro, Exchange lub Zimbra, a następnie przejdź do karty `Domaines associés`{.action} lub `Domaine`{.action} na swojej platformie. Sprawdź sekcję lub kolumnę `Diagnostic`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Jeśli dopiero co wykonałeś migrację lub zmodyfikowałeś rekord DNS swojego domeny, może zajść potrzeba kilku godzin, aby wyświetlenie w [panelu klienta OVHcloud](/links/manager) zostało zaktualizowane.
>

Aby zmienić konfigurację, kliknij czerwoną pastylkę i wykonaj żądaną operację. Ta operacja może wymagać czasu propagacji od 4 do 24 godzin, aby być w pełni skuteczną.

### Użyj swoich przeniesionych adresów e-mail

Pozostało Ci już tylko używać swoich przeniesionych adresów e-mail. Aby to zrobić, OVHcloud oferuje aplikację online (_web app_), dostępne pod adresem [Webmail](/links/web/email). Musisz tam wprowadzić dane uwierzytelniające dotyczące swojego adresu e-mail.

Jeśli skonfigurowałeś jedno z przeniesionych kont na kliencie poczty (np. Outlook, Thunderbird), musisz ponownie go skonfigurować. Dane połączenia z serwerem OVHcloud zostały zmienione po migracji.

> [!primary]
>
> Możesz również ręcznie przenieść adresy e-mail do OVHcloud, korzystając z naszego narzędzia [OVHcloud Mail Migrator (OMM)](/links/web/omm). Aby to zrobić, musisz mieć dostępne dane (użytkownik, hasło, serwery) dla poczty źródłowej i docelowej.
>

## Sprawdź również

[Zarządzanie kontaktami swoich usług](/pages/account_and_service_management/account_information/managing_contacts).

[Pierwsze kroki z ofertą E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config).

[Pierwsze kroki z ofertą Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted).

[Pierwsze kroki z ofertą Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra)

Dołącz do [grona naszych użytkowników](/links/community).