---
title: "Zimbra Pro - Skonfigurowanie konta e-mail za pomocą ActiveSync w klasycznym Outlooku dla Windows"
excerpt: "Dowiedz się, jak skonfigurować adres e-mail Zimbra Pro w Outlooku dla Windows za pomocą protokołu ActiveSync"
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

## Wprowadzenie

Konta Zimbra Pro mogą być skonfigurowane w systemie Windows przy użyciu protokołu ActiveSync, co umożliwia jednoczesne skonfigurowanie wszystkich funkcji kollaboracyjnych adresu e-mail. Aplikacja Outlook dla Windows umożliwia korzystanie z konta e-mail Zimbra Pro za pomocą protokołu ActiveSync.

**Dowiedz się, jak skonfigurować adres e-mail Zimbra Pro w Outlooku dla Windows za pomocą protokołu ActiveSync.**

## Wymagania początkowe

- Posiadanie adresu e-mail [Zimbra Pro](/links/web/emails-zimbra).
- Posiadanie aplikacji [klasycznego Outlooka](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) na Windowsie.
- Posiadanie danych logowania do adresu e-mail, który chcesz skonfigurować.

/// details | Informacje dotyczące zarządzania i konfiguracji usług OVHcloud

OVHcloud oferuje usługi, których konfiguracja, zarządzanie i odpowiedzialność należy do Ciebie. Musisz więc zadbać o ich prawidłowe działanie.

Dostarczamy ten przewodnik, aby pomóc Ci w wykonywaniu codziennych zadań. Jednak zalecamy, aby w przypadku trudności skonsultować się z [specjalistycznym partnerem](/links/transversal/marketplace-support-collaboration) i/lub skontaktować się z wydawcą usługi. Nie będziemy bowiem mogli Ci pomóc. Więcej informacji znajdziesz w sekcji „[Sprawdź również](go-further)”.

///

## W praktyce

> [!warning]
>
> Przed rozpoczęciem konfiguracji warto zauważyć, że aplikacja Outlook dostarczana bezpłatnie z Windows 11 jest niekompatybilna z protokołem ActiveSync, niezbędnym do skonfigurowania konta Zimbra Pro. Musisz użyć wersji **klasycznego Outlooka**, aby skorzystać z obsługi protokołu ActiveSync.
>
> Aby zainstalować klasyczny Outlook na swoim komputerze z Windows, pobierz go ze strony Microsofta „[Zainstaluj lub ponownie zainstaluj klasyczny Outlook na komputerze z Windows](https://support.microsoft.com/fr-fr/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5)”, a następnie zainstaluj.
>
> Po zakończeniu instalacji, aby odróżnić obie wersje, gdy są zainstalowane, wpisz „Outlook” w pasku wyszukiwania Windows. Możesz wtedy zauważyć różnicę, jak poniżej.
>
> ![outlook Windows](images/outlook-windows-identify01.png){.thumbnail .h-500}

### Dodanie konta <a name="add-account"></a>

Aby dodać konto Zimbra Pro w klasycznym Outlooku, wykonaj poniższe kroki, klikając kolejno na odpowiednie karty:

> [!tabs]
> **Krok 1**
>>
>> 1. Przejdź do **panelu konfiguracji** systemu Windows.
>> 2. Kliknij `Konta użytkowników`{.action}.
>> 3. Kliknij `Poczta`{.action}.
>> 4. Kliknij `Konta poczty...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step01.png){.thumbnail .h-500}
>>
> **Krok 2**
>>
>> - W oknie **Ustawienia konta**, w zakładce `Poczta`, kliknij `Nowe...`{.action}.
>>
>> ![outlook Windows](images/outlook-windows-add-step02.png){.thumbnail .h-500}
>>
> **Krok 3**
>>
>> - W oknie **Dodaj konto**, wybierz `Ręczna konfiguracja lub dodatkowe typy serwerów`{.action}.
>> - Kliknij `Dalej`{.action}, aby kontynuować.
>>
>> ![outlook Windows](images/outlook-windows-add-step03.png){.thumbnail .h-500}
>>
> **Krok 4**
>>
>> - Wybierz `Exchange ActiveSync`{.action}.
>> - Kliknij `Dalej`{.action}, aby kontynuować.
>>
>> ![outlook Windows](images/outlook-windows-add-step04.png){.thumbnail .h-500}
>>
> **Krok 5**
>>
>> Wprowadź dane logowania do swojego konta:
>>
>> - **Twoje imię**: Ustaw nazwę wyświetlaną.
>> - **Adres e-mail**: Wprowadź pełny adres e-mail.
>> - **Serwer poczty**: Wprowadź „zimbra1.mail.ovh.net”.
>> - **Nazwa użytkownika**: Wprowadź pełny adres e-mail.
>> - **Hasło**: Wprowadź hasło przypisane do adresu e-mail.
>>
>> Kliknij `Dalej`{.action}, aby zakończyć dodawanie konta.
>>
>> ![outlook Windows](images/outlook-windows-add-step05.png){.thumbnail .h-500}
>>
> **Krok 6**
>>
>> Twój adres e-mail jest teraz skonfigurowany w Outlooku. Aby uzyskać pełną synchronizację funkcji konta Zimbra Pro, **pobierz i zainstaluj** moduł „[Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/)”.
>> 
>> ![outlook Windows](images/outlook-windows-add-step06.png){.thumbnail .h-500}
>>
> **Krok 7**
>>
>> Po zainstalowaniu modułu „[Zimbra Connector for Outlook](https://www.zimbra.com/product/addons/zimbra-connector-for-outlook-download/)”, uruchom klasyczny Outlook.
>> Po raz pierwszy, pojawi się okno konfiguracji **Zimbra Server configuration Settings**. Uzupełnij poniższe dane:
>>
>> - **Nazwa serwera**: Wprowadź „zimbra1.mail.ovh.net”.
>> - **Adres e-mail**: Wprowadź pełny adres e-mail.
>> - **Hasło**: Wprowadź hasło przypisane do adresu e-mail.
>>
>> Nie ma potrzeby zmieniania innych ustawień. Kliknij `Zastosuj`{.action}, aby potwierdzić ustawienia i upewnić się, że są poprawne. Na końcu kliknij `OK`{.action}, aby uzyskać dostęp do Outlooka i rozpocząć korzystanie z adresu e-mail.
>>
>> ![outlook Windows](images/outlook-windows-add-step-07.png){.thumbnail .h-500}

> [!warning]
>
> Jeśli po wykonaniu powyższych kroków konfiguracji napotkasz problemy z wysyłaniem lub odbieraniem wiadomości, zapoznaj się z sekcją „[Zmiana istniejących ustawień](#modify-settings)”.

### Użycie adresu e-mail

Po skonfigurowaniu adresu e-mail możesz zacząć go używać! Możesz teraz wysyłać i odbierać wiadomości, a także zarządzać swoimi kalendarzami i zadaniami.

OVHcloud oferuje również aplikację internetową umożliwiającą dostęp do adresu e-mail za pomocą przeglądarki internetowej. Możesz się zalogować do [webmaila OVHcloud](/links/web/email) przy użyciu danych logowania do adresu e-mail. W przypadku pytań dotyczących jego użycia, zapoznaj się z naszym przewodnikiem „[Użycie webmaila Zimbra](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_zimbra)”.

### Jak zmienić istniejące ustawienia ? <a name="modify-settings"></a>

Aby zmienić ustawienia już skonfigurowanego konta e-mail, wykonaj poniższe instrukcje:

1. Przejdź do **panelu konfiguracji** systemu Windows.
1. Kliknij `Konta użytkowników`{.action}.
1. Kliknij `Poczta`{.action}.
1. Kliknij `Konta poczty...`{.action}.
1. Wybierz odpowiednie konto e-mail z listy i kliknij `Zmień...`{.action}.

![outlook ios](images/outlook-windows-modify-01.png){.thumbnail .h-500}

Znajdziesz ustawienia w **kroku 7** rozdziału „[Dodanie konta](#add-account)”.

### Jak usunąć konto e-mail ? <a name="delete-account"></a>

Aby usunąć swoje konto e-mail, wykonaj poniższe instrukcje:

1. Przejdź do **panelu konfiguracji** systemu Windows.
1. Kliknij `Konta użytkowników`{.action}.
1. Kliknij `Poczta`{.action}.
1. Kliknij `Konta poczty...`{.action}.
1. Wybierz odpowiednie konto e-mail z listy i kliknij `Usuń`{.action}.

![outlook ios](images/outlook-windows-delete-01.png){.thumbnail .h-500}

> [!warning]
>
> Aby móc usunąć konto e-mail, nie może ono być kontem e-mail domyślnym.

## Sprawdź również <a name="go-further"></a>

> [!primary]
>
> Aby uzyskać więcej informacji na temat konfiguracji adresu e-mail w aplikacji Outlook na Windows, zapoznaj się z [centrum pomocy Microsoft](https://support.microsoft.com/fr-fr/office/ajouter-un-compte-de-messagerie-%C3%A0-outlook-pour-windows-6e27792a-9267-4aa4-8bb6-c84ef146101b?ocmsassetID=HA102823161&CorrelationId=778d1d8d-9ac2-449b-9624-1268559fa794).

W przypadku usług specjalistycznych (SEO, rozwój, itp.), skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz skorzystać z pomocy w użyciu i konfiguracji swoich rozwiązań OVHcloud, zapoznaj się z naszymi różnymi [ofertami wsparcia](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).