---
title: "E-Mail Pro - Konfiguracja konta E-Mail Pro w nowej aplikacji Outlook na Windows"
excerpt: "Dowiedz się, jak skonfigurować swoją adres E-Mail Pro w nowej aplikacji Outlook na Windows."
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

## Wprowadzenie

Adresy e-mail w ramach oferty [E-Mail Pro](/links/web/email-pro) mogą być konfigurowane na kompatybilnym kliencie pocztowym. Umożliwia to wysyłanie i odbieranie wiadomości z wybranej aplikacji.

**Nowa aplikacja Outlook** zastępuje od dnia 1 stycznia 2025 roku aplikację **Poczta** w systemie Windows. Więcej informacji na ten temat można znaleźć na oficjalnej stronie Microsoft « [Outlook dla systemu Windows: przyszłość poczty, kalendarza i kontaktów w systemie Windows 11](https://support.microsoft.com/office/outlook-pour-windows-l-avenir-du-courrier-du-calendrier-et-des-personnes-sur-windows-11-715fc27c-e0f4-4652-9174-47faa751b199) ».

**Dowiedz się, jak skonfigurować swoją adresę E-Mail Pro w nowej aplikacji Outlook na Windows.**

## Wymagania początkowe

- Posiadanie adresu [E-Mail Pro](/links/web/email-pro).
- Posiadanie [nowej aplikacji Outlook](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) na system Windows.
- Posiadanie danych dostępowych do konfigurowanego adresu e-mail.

> [!warning]
>
> Ta dokumentacja dotyczy wyłącznie **nowej aplikacji Outlook** i nie obejmuje « [klasycznego Outlook](https://support.microsoft.com/office/installer-ou-r%C3%A9installer-outlook-classique-sur-un-pc-windows-5c94902b-31a5-4274-abb0-b07f4661edf5) », dostępnego w pakiecie Microsoft 365 lub wcześniej zainstalowanego na komputerze.

/// details | Informacje dotyczące zarządzania i konfiguracji usług OVHcloud

OVHcloud udostępnia usługi, za których konfigurację, zarządzanie i działanie jesteś odpowiedzialny. Należy do Ciebie zapewnić ich poprawne funkcjonowanie.

Zapewniamy tę dokumentację, aby ułatwić Ci wykonywanie typowych zadań. W przypadku problemów zalecam skontaktowanie się z [specjalistycznym partnerem](https://marketplace.ovhcloud.com/c/support-collaboration) lub producentem usługi. Nie będziemy mogli udzielić dalszej pomocy. Więcej informacji w sekcji « Sprawdź również » niniejszej dokumentacji.

///

## W praktyce

### Dodanie konta <a name="add-account"></a>

> [!warning]
>
> W naszym przykładzie używamy serwera: pro?.mail.ovh.net. Należy zastąpić znak «?» numerem serwera dla usługi E-Mail Pro.
> 
> Numer serwera można znaleźć w [Kundencenter OVHcloud](/links/manager), w sekcji `Web Cloud`{.action} a następnie `E-Mail Pro`{.action}. Nazwa serwera jest widoczna w sekcji **Połączenie** zakładki `Informacje Główne`{.action}.

> [!tabs]
> **Krok 1**
>> - Otwórz aplikację Outlook. W lewym menu kliknij przycisk `Dodaj konto`{.action}, aby rozpocząć konfigurację.
>>
>> ![outlook](images/configuration-newoutlook-windows-01.png){.thumbnail .w-400}
>>
> **Krok 2**
>> - Wprowadź swój adres e-mail, a następnie kliknij przycisk `Dalej`{.action}.
>> - Wprowadź swoje hasło i kliknij przycisk `Pokaż więcej`{.action}.
>>
>> ![outlook](images/configuration-newoutlook-windows-02.png){.thumbnail .w-400}
>>
> **Krok 3**
>> - Wprowadź następujące parametry:
>>    - **Serwer IMAP dla przychodzących wiadomości**: pro?.mail.ovh.net
>>    - **Port**: 993
>>    - **Typ bezpiecznego połączenia**: SSL/TLS
>>    - **Nazwa użytkownika SMTP**: adres e-mail, który dodajesz.
>>    - **Serwer SMTP dla wychodzących wiadomości**: pro?.mail.ovh.net
>>    - **Port**: 587
>>    - **Typ bezpiecznego połączenia**: STARTTLS
>>    - **Hasło**: nie wprowadzaj niczego, użyje się hasła wprowadzonego wcześniej.
>> - Kliknij przycisk `Dalej`{.action}, aby zakończyć konfigurację.
>>
>> ![outlook](images/configuration-newoutlook-windows-emp-03.png){.thumbnail .w-400}

### Użycie adresu e-mail <a name="use-account"></a>

Po skonfigurowaniu adresu e-mail możesz go już używać! Możesz teraz wysyłać i odbierać wiadomości.

OVHcloud oferuje również aplikację webową, która umożliwia dostęp do Twojego adresu e-mail przez przeglądarkę, dostępną pod adresem [Webmail](/links/web/email). Możesz się do niej zalogować, używając danych dostępowych do swojego adresu e-mail.

### Modyfikacja istniejących ustawień <a name="modify-settings"></a>

Aplikacja Outlook nie pozwala na modyfikację parametrów serwera dla konta e-mail.

Jeśli Twoje konto e-mail jest już skonfigurowane i chcesz je skonfigurować ponownie, musisz je najpierw usunąć, a następnie ponownie dodać:

- Kliknij ikonę ustawień « &#9965; » u dołu lewego menu.
- W sekcji « Twoje konta » kliknij przycisk `Zarządzaj`{.action} obok odpowiedniego adresu e-mail.

![outlook](images/configuration-newoutlook-windows-04.png){.thumbnail .w-400}

- Przewiń do dołu strony.
- Kliknij przycisk `Usuń`{.action}, aby rozpocząć proces usuwania.
- Zdecyduj, czy chcesz usunąć konto tylko z tego urządzenia, czy też z innych urządzeń korzystających z Outlook.

![outlook](images/configuration-newoutlook-windows-emp-05.png){.thumbnail .w-400}

> [!success]
>
> Po usunięciu konta e-mail postępuj zgodnie z instrukcjami w sekcji « [Dodanie konta](#add-account) » niniejszej dokumentacji.

### Ogólne ustawienia wysyłania i odbierania <a name="settings-account"></a>

#### Ustawienia IMAP i POP dla odbierania wiadomości <a name="imap-pop"></a>

Do odbierania e-maili zalecamy użycie **IMAP**. Możesz również wybrać **POP**.

Wybierz odpowiednią kartę w zależności od typu konfiguracji:

> [!tabs]
> **Konfiguracja IMAP**
>>
>> - **Nazwa użytkownika**: Wprowadź **pełny** adres e-mail.
>> - **Hasło**: Wprowadź hasło do adresu e-mail.
>> - **Serwer dla przychodzących wiadomości**: pro?.mail.ovh.net (zamień «?» na numer Twojego serwera).
>> - **Port**: 993.
>> - **Typ bezpiecznego połączenia**: SSL/TLS.
>>
> **Konfiguracja POP**
>>
>> - **Nazwa użytkownika**: Wprowadź **pełny** adres e-mail.
>> - **Hasło**: Wprowadź hasło do adresu e-mail.
>> - **Serwer dla przychodzących wiadomości**: pro?.mail.ovh.net (zamień «?» na numer Twojego serwera).
>> - **Port**: 995.
>> - **Typ bezpiecznego połączenia**: SSL/TLS.

#### Ustawienia SMTP dla wysyłania wiadomości <a name="smtp"></a>

Do wysyłania e-maili użyj następujących parametrów **SMTP**:

**Konfiguracja SMTP**

- **Nazwa użytkownika**: Wprowadź **pełny** adres e-mail.
- **Hasło**: Wprowadź hasło do adresu e-mail.
- **Serwer dla wychodzących wiadomości**: pro?.mail.ovh.net (zamień «?» na numer Twojego serwera).
- **Port**: 587.
- **Typ bezpiecznego połączenia**: STARTTLS.

## Sprawdź również <a name="go-further"></a>

> [!primary]
>
> Więcej informacji na temat konfiguracji adresu e-mail w nowej aplikacji Outlook na Windows można znaleźć w [centrum pomocy Microsoft](https://support.microsoft.com/office/start-using-new-outlook-for-windows-4395454d-cb2f-4c16-bb24-fa4bb36650ae).

[Podstawowe informacje o rozwiązaniu E-Mail Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)

W przypadku usług specjalistycznych (SEO, rozwój etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli potrzebujesz pomocy w zakresie konfiguracji i użytkowania swoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [społeczności użytkowników](/links/community).