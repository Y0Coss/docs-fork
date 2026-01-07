---
title: 'Migrowanie adresu e-mail MX Plan do konta E-mail Pro, Exchange lub Zimbra'
excerpt: 'Dowiedz się, jak przeprowadzić migrację adresu e-mail MX Plan do konta E-mail Pro, Exchange lub Zimbra'
updated: 2025-12-22
---

## Wprowadzenie

OVHcloud oferuje kilka rozwiązań e-mail: MX Plan (sprzedawany osobno lub zawarty w ofercie hostingu), E-mail Pro, Exchange i Zimbra. Każde z nich posiada własne funkcje i może być dostosowane do różnych zastosowań. Zmieniły się Twoje potrzeby? OVHcloud udostępnia narzędzie migracji umożliwiające przejście z jednego rozwiązania do drugiego.

**Dowiedz się, jak przeprowadzić migrację adresu e-mail MX Plan do konta E-mail Pro lub Exchange.**

<iframe class="video" width="560" height="315" src="https://www.youtube-nocookie.com/embed/0JLLoBBvsCc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> [!warning]
>
> [OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm) umożliwia migrację wiadomości z jednego serwera e-mail do drugiego.<br>
> Jeśli Twoje e-maile są zapisane lokalnie (konfiguracja POP lub archiwizacja lokalna), możesz wykonać [eksport z Twojego klienta poczty](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), a następnie [zaimportować plik PST przez OMM](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm#realiser-une-migration-par-fichier) lub [zaimportować bezpośrednio z Twojego klienta poczty](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration).

## Wymagania początkowe
- Posiadanie adresu e-mail MX Plan (za pośrednictwem oferty MX Plan lub zawartego w ofercie [hostingu OVHcloud](/links/web/hosting)).
- Posiadanie usługi [Exchange](/links/web/emails-hosted-exchange), [E-mail Pro](/links/web/email-pro) z co najmniej jednym niezakonfigurowanym kontem (które będzie miało postać „@configureme.me”) lub [Zimbra](/links/web/zimbra).
- **Nie skonfigurować przekierowania na adres e-mail MX Plan, który chcesz zmigrować**.
- Zalogowanie się do swojego [espace client OVHcloud](/links/manager).


## W praktyce

### Krok 1: zdefiniowanie projektu

Rozwiązania E-mail Pro i Exchange mają wspólną podstawę funkcjonalności. Niemniej istnieją różnice w zależności od przypadku użycia. Wybierając adres Exchange, masz dostęp do pełnej funkcjonalności współpracy, takiej jak synchronizacja kalendarza i kontaktów. Rozwiązanie E-mail Pro oferuje niektóre z tych funkcji, ale są one ograniczone do użycia wyłącznie przez webmail.

Przed kontynuowaniem ważne jest, aby wiedzieć, do której oferty chcesz przenieść swoje adresy e-mail MX Plan. Aby pomóc Ci w tym wyborze, zapoznaj się z [stroną z profesjonalnymi rozwiązaniami e-mail od OVHcloud](/links/web/emails), która zawiera szczegółowy porównanie ofert. Możesz łączyć rozwiązania i używać dla tego samego domeny jednego lub kilku kont E-mail Pro i Exchange. Ponadto, jeśli musisz przenieść wiele kont, zalecamy opracowanie planu migracji.

### Krok 2: zamówienie kont E-mail Pro lub Exchange

Ten krok jest opcjonalny, jeśli już masz usługę Exchange lub E-mail Pro, do której przeprowadzasz tę migrację.

W przeciwnym razie zaloguj się do [panelu klienta OVHcloud](/links/manager), a następnie zamów usługę E-mail Pro lub Exchange. Postępuj zgodnie z kolejnymi krokami, a następnie poczekaj na instalację usługi. Otrzymasz e-mail, gdy ta czynność zostanie zakończona.

> [!primary]
>
> Po złożeniu zamówienia pozostaw konto w formie „@configureme.me” na początku. Będzie ono zmienione w trakcie migracji.
>

### Krok 3: wykonanie migracji

Przed rozpoczęciem migracji musisz zidentyfikować wersję MX Plan, z której przenosisz dane.

> [!primary]
>
> Technologia e-maila oferty MX Plan może się różnić w zależności od daty aktywacji oferty lub jeśli niedawno miała miejsce migracja. Ta technologia różni się m.in. wyglądem interfejsu webmaila. Aby ją zidentyfikować w panelu klienta, wykonaj poniższe kroki:
>
> 1. Zaloguj się do [panelu klienta OVHcloud](/links/manager).
> 1. Przejdź do sekcji `Web Cloud`{.action}.
> 1. Kliknij `MX Plan`{.action}.
> 1. Wybierz odpowiedni domenę.
> 1. Zazwyczaj wybrany jest zakładka `Informacje ogólne`{.action}.
> 1. Zanotuj technologię używaną pod hasłem **Webmail** w sekcji `Subskrypcja`.
>
> ![MX plan](/pages/assets/schemas/emails/technology-email.png){.thumbnail .w-640}
>

#### 3.1 Ręczna migracja oferty MX Plan do Exchange, E-mail Pro lub Zimbra  <a name="all-mxplan"></a>

> [!warning]
>
> Ta sekcja dotyczy wszystkich usług MX Plan korzystających z technologii webmaila Rouncube, Zimbra lub OWA.
>
> Jednak jeśli chcesz przenieść usługę MX Plan korzystającą z webmaila Roundcube do platformy Email Pro lub Exchange OVHcloud, przejdź do sekcji « [Automatyczna migracja oferty MX Plan Roundcube do Exchange lub Email Pro](#roundcube-mxplan) » tego przewodnika.

> [!warning]
>
> Jeśli właśnie zamówiłeś nową ofertę e-mail, dodaj najpierw nazwę domeny do swojej platformy e-mail, zanim zaczniesz migrację. <br> - *Na przykład, aby przenieść konto „myemail@mydomain.ovh”, musisz dodać nazwę domeny „mydomain.ovh” do swojej platformy.*
>
> Wybierz kartę `Domaines associés`{.action} lub `Domaine`{.action} na swojej platformie, a następnie kliknij `Ajouter un domaine`{.action}. Po dodaniu nazwy domeny upewnij się, że w kolumnie `Statut` znajduje się oznaczenie `OK` lub `Actif`{.action}.
>
> ![exchange](images/account_migration_adddomain.png){.thumbnail}
>
> Aby uzyskać więcej informacji na temat dodawania nazwy domeny, zapoznaj się z [przewodnikiem E-mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config#etape-2-ajouter-votre-nom-de-domaine), [przewodnikiem Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_adding_domain) lub [przewodnikiem Zimbra](/pages/web_cloud/email_and_collaborative_solutions/zimbra/getting_started_zimbra).

Migracja Twojego MX Plan przebiegnie w trzech głównych etapach: **Zmiana nazwy**, **Tworzenie** i **Migracja**.

![exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Zmień nazwę** konta MX Plan, które chcesz przenieść, na tymczasową (np. dla konta MX Plan *john.smith@mydomain.ovh*, zmień nazwę na *john.smith01@mydomain.ovh*).

Na karcie `Comptes e-mail`{.action} swojej platformy MX Plan kliknij przycisk `...`{.action}, a następnie `Modifier`{.action}.

![exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> Zmiana konta nie jest natychmiastowa, poczekaj na zakończenie operacji przed przejściem do następnego kroku.

2\. **Utwórz** adres e-mail na nowym koncie na swojej platformie E-mail Pro lub Exchange (w powyższym przykładzie utworzysz *john.smith@mydomain.ovh* na nowej platformie).

Na karcie `Comptes e-mail`{.action} swojej platformy E-mail Pro lub Exchange kliknij przycisk `...`{.action}, a następnie `Modifier`{.action}.

![exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Przenieś** konto MX Plan do konta na nowej platformie za pomocą naszego narzędzia [OMM](/links/web/omm) (OVHcloud Mail Migrator).

Aby uzyskać więcej informacji na temat OMM, zapoznaj się z naszym przewodnikiem [Migracja kont e-mail przez OVHcloud Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm).

![exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

Czas migracji zależy od ilości treści do przeniesienia do nowego konta. Może on sięgać od kilku minut do kilku godzin.

Po migracji sprawdź, czy wszystkie elementy są dostępne, logując się do webmaila pod adresem [Webmail](/links/web/email)

Możesz zachować lub usunąć konto z tymczasową nazwą po tej migracji.

Jeśli chcesz je usunąć, przejdź do karty `Comptes e-mail`{.action} swojego MX Plan, kliknij przycisk `...`{.action}, a następnie `Réinitialiser ce compte`{.action}.

#### 3.2 Automatyczna migracja oferty MX Plan Roundcube do Exchange lub Email Pro <a name="roundcube-mxplan"></a>

> [!warning]
>
> Ta sekcja dotyczy wyłącznie usług MX Plan korzystających z technologii webmaila Rouncube.

> [!primary]
>
> Twoje konto OVHcloud musi być wcześniej administratorem kontaktowym **i** technicznym usługi MX Plan do migracji, **oraz** usługi E-mail Pro lub Exchange, do której przenosisz.
>
> Aby uzyskać więcej informacji na temat zmian kontaktów, zapoznaj się z naszym przewodnikiem [Zarządzanie kontaktami swoich usług](/pages/account_and_service_management/account_information/managing_contacts).
>

Migrację można przeprowadzić z dwóch interfejsów:<br>

- **asystenta konfiguracji Hosted Exchange**, tylko jeśli właśnie zamówiłeś usługę Hosted Exchange i jeszcze nic nie skonfigurowałeś na niej;
- **interfejsu MX Plan**, gdy masz już usługę E-mail Pro lub Exchange (skonfigurowaną lub nie) i chcesz przenieść adres MX Plan.

> Na przypomnienie, przed rozpoczęciem migracji upewnij się, że nie ustawiono żadnej **przekierowania** ani **odpowiednika** na Twoim MX Plan.
>
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Po przygotowaniu, kontynuuj odczyt tej dokumentacji zgodnie z wybranym interfejsem. Pamiętaj, że czas migracji zależy od ilości treści do przeniesienia do nowego konta. Może on sięgać od kilku minut do kilku godzin.

> [!warning]
>
> Po potwierdzeniu migracji nie będziesz już mógł uzyskać dostępu do starego adresu e-mail MX Plan ani anulować procesu migracji. Zalecamy wykonanie tej operacji w odpowiednim czasie.
>
> Nawet jeśli nie będziesz mógł uzyskać dostępu do swojego obecnego adresu e-mail, wiadomości już odebrane oraz nowe nie zostaną utracone. Wszystkie będą natychmiast dostępne z nowego konta.
>

##### **Migracja z asystenta konfiguracji Exchange**

Aby do niego dotrzeć, wybierz odpowiednią usługę w [panelu klienta OVHcloud](/links/manager). Asystent powinien się pojawić, aby pomóc Ci skonfigurować nową usługę Exchange. W trakcie tego procesu możesz wybrać konta e-mail MX Plan do migracji.

Jeśli asystent konfiguracji nie pojawi się, zamiast tego pojawią się ogólne informacje o usłudze Exchange. W takim przypadku musisz przeprowadzić migrację swoich kont za pomocą interfejsu MX Plan.

##### **Migracja z interfejsu MX Plan**

Aby przeprowadzić migrację z tego interfejsu, przejdź do sekcji `E-mails`{.action} w swoim panelu klienta OVHcloud. Wybierz usługę o nazwie domeny swoich adresów e-mail. Kliknij na logo w kształcie koła zębatego w wierszu konta e-mail (nazywanego również kontem źródłowym) i wybierz `Migrer le compte`{.action}.

![exchange](images/access_the_migration_tool.png){.thumbnail}

W oknie, które się otworzy, wybierz usługę docelową (tą, do której chcesz przenieść adres) i kliknij `Suivant`{.action}. Jeśli posiada ona co najmniej jedno „wolne” konto (czyli jeszcze nie skonfigurowane), migracja zostanie przeprowadzona do jednego z tych kont. Następnie zapoznaj się z wyświetlonymi informacjami, potwierdź je, a następnie kliknij `Suivant`{.action}, aby kontynuować.

Jeśli nie masz konta „wolnego”, pojawi się przycisk `Commander des comptes`{.action}. Postępuj zgodnie z krokami, a następnie poczekaj, aż konta zostaną zainstalowane, aby ponownie wykonać czynność.

Na koniec potwierdź hasło adresu e-mail źródłowego (który chcesz przenieść), a następnie kliknij `Migrer`{.action}. Tę czynność należy powtórzyć tyle razy, ile potrzeba do migracji innych kont.

![exchange](images/account_migration_steps.png){.thumbnail}


### Krok 4: sprawdzenie lub zmiana konfiguracji swojego domeny

W tym etapie Twoje adresy e-mail powinny być już przeniesione i działające. Dla bezpieczeństwa zachęcamy, aby upewnić się, że konfiguracja Twojego domeny jest poprawna, przeglądając swój panel klienta.

Aby to zrobić, wybierz usługę E-mail Pro, Exchange lub Zimbra, a następnie przejdź do zakładki `Domaines associés`{.action} lub `Domaine`{.action} na swojej platformie. Sprawdź sekcję lub kolumnę `Diagnostic`{.action}.

![exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

> [!primary]
>
> Jeśli dopiero co wykonano migrację lub zmodyfikowano rekord DNS swojego domeny, może być konieczne odczekanie kilku godzin, aby zmiany zostały odzwierciedlone w [panelu klienta OVHcloud](/links/manager).
>

Aby zmienić konfigurację, kliknij na czerwoną karczkę i wykonaj żądaną czynność. Ta czynność wymaga czasu propagacji wynoszącego maksymalnie 4 do 24 godzin, aby być w pełni skuteczną.

### Krok 5: korzystanie z przeniesionych adresów e-mail

Wszystko, co zostało Ci do zrobienia, to korzystanie z przeniesionych adresów e-mail. Aby to zrobić, OVHcloud udostępnia aplikację online (_web app_), dostępne pod adresem [Webmail](/links/web/email). Musisz tam wprowadzić dane logowania związane z Twoim adresem e-mail.

Jeśli skonfigurowałeś któryś z przeniesionych kont na kliencie poczty (np. Outlook), musisz go ponownie skonfigurować. Dane logowania do serwera OVHcloud zostały zmienione po migracji. Aby pomóc Ci w tych czynnościach, zapoznaj się z naszą dokumentacją w sekcjach przewodników poświęconych [E-mail Pro](/products/web-cloud-email-collaborative-solutions-email-pro) i [Hosted Exchange](/products/web-cloud-email-collaborative-solutions-mx-plan). Jeśli nie możesz natychmiast ponownie skonfigurować konta, dostęp przez aplikację online nadal jest możliwy.

### Organizacja zawartości adresów e-mail po migracji <a name="content-after-migration"></a>

Po pierwszym połączeniu się z nowym kontem e-mail, przeniesiona zawartość może być częściowo ukryta. Aby wyświetlić wszystkie elementy, z webmaila kliknij strzałkę obok `Skrytki odbiorczej`, aby odkryć podfoldery. Zawartość przeniesiona ze starego konta e-mail powinna się pojawić.

![exchange](images/owa_migrate_content.png){.thumbnail}

Domyślne foldery, takie jak „wysłane” lub „kosz” pojawiają się w języku angielskim („Sent items” i „Trash”), z wyjątkiem folderów, które utworzyłeś.

Po migracji nie zapomnij sprawdzić wszystkich folderów i podfolderów swojego konta, aby upewnić się, że wszystkie elementy są obecne.

### Ręczna migracja

Możesz również ręcznie przenieść swoje adresy e-mail do nowej oferty e-mail OVHcloud, korzystając wyłącznie z oprogramowania pocztowego. Skorzystaj z naszego przewodnika [Ręczna migracja adresu e-mail](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration). Zalecamy jednak użycie tej metody tylko wtedy, gdy główne metody nie są możliwe.

## Sprawdź również
[Zarządzanie kontaktami swoich usług](/pages/account_and_service_management/account_information/managing_contacts).

[Przewodniki E-mail Pro](/products/web-cloud-email-collaborative-solutions-email-pro).

[Przewodniki Exchange](/products/web-cloud-email-collaborative-solutions-microsoft-exchange).

Dołącz do [grona naszych użytkowników](/links/community).