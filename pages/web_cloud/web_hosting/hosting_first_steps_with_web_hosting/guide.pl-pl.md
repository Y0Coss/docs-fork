---
title: "Jak rozpocząć korzystanie z hostingu WWW"
excerpt: "Dowiedz się, jak zamieścić w Internecie nową stronę WWW za pomocą opcji"Moduły za 1 kliknięciem", jak utworzyć nowy spersonalizowany adres e-mail z nazwą domeny, a wszystko to za pomocą naszego rozwiązania hostingowego"
updated: 2025-04-02
---

<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>

## Wprowadzenie

Chcesz stworzyć stronę WWW dla swojej firmy lub własny blog? A może wdrożyć sklep internetowy, aby sprzedawać swoje produkty online? Niniejszy przewodnik Pierwsze kroki z hostingiem WWW OVHcloud wyjaśni kluczowe etapy jego konfiguracji, w tym tworzenie profesjonalnych kont e-mail związanych z Twoją domeną. Umożliwi on łatwą i szybką publikację Twojego projektu, aby skutecznie komunikować się z odbiorcami.

**Dowiedz się, jak szybko i łatwo umieścić nową stronę WWW w Internecie za pomocą naszego rozwiązania "Moduł za 1 kliknięciem". Z tego przewodnika dowiesz się, jak utworzyć nowy spersonalizowany adres e-mail z nazwą Twojej domeny.**

> [!primary]
>
> Jeśli chcesz przenieść istniejącą stronę WWW do innego dostawcy hostingu, zapoznaj się bezpośrednio z naszym przewodnikiem: [Przeniesienie strony WWW i powiązanych z nią usług do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh).

## Wymagania

- Posiadanie hostingu [OVHcloud](/links/web/hosting) z co najmniej jedną dostępną bazą danych.
- Otrzymanie wiadomości e-mail z potwierdzeniem, że Twój hosting został zainstalowany.
- Posiadanie domeny [domena](/links/web/domains) oraz powiązanej strefy DNS w OVHcloud.
- Wszystkie wyżej wymienione usługi muszą być dostępne z poziomu jednego konta OVHcloud.
- Dostęp do [panelu klienta OVHcloud](/links/manager), sekcja `Web Cloud`{.action}.

## W praktyce

### 1 - Przypisz domenę do hostingu <a name="part-1"></a>

> [!success]
>
> Jeśli zamówiłeś domenę i hosting w ramach jednego zamówienia, te dwie usługi są już powiązane. Przejdź bezpośrednio do [Część 2](#część-2) tego przewodnika.

1. Kliknij menu `Hosting`{.action}, następnie wybierz odpowiedni hosting.
2. Wybierz zakładkę `MultiSite`{.action} po wybraniu odpowiedniego hostingu.
3. Na stronie, która się wyświetli kliknij przycisk `Operacje`{.action} znajdujący się nad tabelą zawierającą nazwy domen już zadeklarowanych na hostingu. Następnie kliknij `Dodaj domenę lub subdomenę`{.action}.
4. W oknie, które się otworzy, zaznacz i uzupełnij wymagane elementy aż do ich zatwierdzenia.

/// details | Kliknij tutaj, aby uzyskać więcej informacji.

Zapoznaj się ze szczegółowymi przewodnikami:

- [Instalacja kilku stron WWW na jednym hostingu](/pages/web_cloud/web_hosting/multisites_configure_multisite).
- [Hosting WWW - Zmiana nazwy domeny powiązanej z hostingiem](/pages/web_cloud/web_hosting/multisites_modify_domain).

///

### 2 - Zainstaluj "Moduły CMS" dla Twojej strony WWW <a name="part-2"></a>

Dzięki opcji "Moduły CMS", na hostingach OVHcloud można zainstalować za darmo systemy CMS WordPress, Joomla!, PrestaShop i Drupal.

1. Kliknij menu `Hosting`{.action}, następnie wybierz odpowiedni hosting.
2. Wybierz zakładkę `Moduły CMS`{.action} po wybraniu odpowiedniego hostingu WWW.
3. Na stronie, która się wyświetli kliknij przycisk `Dodaj moduł CMS`{.action}.
4. W wyświetlonym oknie wybierz CMS, który chcesz zainstalować. Następnie wybierz domenę, na której ma zostać zainstalowany moduł, wybierając nazwę domeny **bez** "www" przed (przykład: `domain.tld`, a nie `www.domain.tld`), po czym kliknij bezpośrednio na `Instaluj`{.action}.

/// details | Kliknij tutaj, aby uzyskać więcej informacji.

Zapoznaj się ze szczegółowymi przewodnikami:

- [Instalacja strony WWW za pomocą 'modułu za 1 kliknięciem' (CMS)](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
- [Jak zarządzać modułem za 1 kliknięciem?](/pages/web_cloud/web_hosting/cms_manage_1_click_module).

///

### 3 - Aktywacja adresów e-mail zawartych w hostingu <a name="part-3"></a>

> [!success]
>
> Jeśli zamówiłeś domenę i hosting w ramach jednego zamówienia, adresy e-mail zawarte w hostingu są już powiązane z Twoją domeną. Przejdź bezpośrednio do [Część 4](#część-4) tego przewodnika.

1. Kliknij menu `Hosting`{.action}, następnie wybierz odpowiedni hosting.
2. Na stronie, która się wyświetli i w ramce **Konfiguracja** kliknij przycisk `...`{.action} znajdujący się po prawej stronie wzmianki `Adresy e-mail`{.action}, a następnie `Włącz mój pakiet e-mail`{.action}. Na stronie, która się otworzy, wybierz odpowiednią nazwę domeny w sekcji `(1)`, następnie kontynuuj, aż do aktywacji kont e-mail.

/// details | Kliknij tutaj, aby uzyskać więcej informacji.

Zapoznaj się ze szczegółowym przewodnikiem "[Hosting WWW - Włącz konta e-mail zawarte w ofercie](/pages/web_cloud/web_hosting/activate-email-hosting)".

///

### 4 - Tworzenie spersonalizowanego adresu e-mail z nazwą domeny <a name="part-4"></a>

1. Kliknij menu `E-maile`{.action} (lub `MX Plan`{.action}, jeśli korzystasz z nowej wersji Panelu klienta OVHcloud), następnie wybierz odpowiednią nazwę domeny.
2. Na stronie, która się wyświetli kliknij zakładkę `E-maile`{.action}.
3. Na nowej stronie, która się wyświetli, kliknij przycisk `Stwórz adres e-mail`{.action}.
4. W oknie, które się otworzy, uzupełnij wymagane elementy aż do zatwierdzenia.

Powtórz tę operację dla każdego konta e-mail, które chcesz założyć (z ograniczeniem Twojej oferty hostingowej).

/// details | Kliknij tutaj, aby uzyskać więcej informacji.

Zapoznaj się ze szczegółowym przewodnikiem "[Tworzenie konta e-mail](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_creation)".

///

### 5 - Dodatkowe opcje dostępne z Twoim hostingiem <a name="part-5"></a>

Instalacja modułu za pomocą 1 kliknięcia nie ogranicza się do Twojego hostingu. Możesz hostować strony internetowe stworzone przez Ciebie lub przez programistę WWW (blog, CMS, sklep internetowy, etc.). Jeśli chcesz dowiedzieć się więcej o możliwościach Twojego hostingu, zapoznaj się z naszym przewodnikiem "[Jak stworzyć stronę WWW - 5 etapów realizacji projektu](/pages/web_cloud/web_hosting/website-project)".

## Sprawdź również

Poniżej znajdziesz kilka linków do przewodników dotyczących głównych opcji dostępnych w ramach naszych ofert hostingu:

- [Hosting WWW - Zarządzanie certyfikatem SSL](/pages/web_cloud/web_hosting/ssl_on_webhosting).
- [Przewodnik dotyczący usługi CDN na hostingu www](/pages/web_cloud/web_hosting/cdn_how_to_use_cdn).
- [Hosting WWW - Środowisko, wersja PHP, .ovhconfig](/pages/web_cloud/web_hosting/configure_your_web_hosting).
- [Hosting WWW - sprawdzanie statystyk i logów strony www](/pages/web_cloud/web_hosting/logs_and_statistics).
- [Monitoring i zarządzanie automatycznymi wiadomościami e-mail na Twoim hostingu](/pages/web_cloud/web_hosting/mail_function_script_records).
- [Jak geolokalizować stronę WWW w danym kraju?](/pages/web_cloud/web_hosting/multisites_geolocation).
- [Aktywacja zapory systemowej](/pages/web_cloud/web_hosting/multisites_activating_application_firewall).
- [Konfiguracja i korzystanie z Git na hostingu OVHcloud](/pages/web_cloud/web_hosting/git_integration_webhosting).
- [Logowanie do przestrzeni dyskowej FTP hostingu](/pages/web_cloud/web_hosting/ftp_connection).
- [Tworzenie automatycznych zadań (CRON) na Twoim hostingu](/pages/web_cloud/web_hosting/cron_tasks).
 
W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).
 
Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).
 
Dołącz do [grona naszych użytkowników](/links/community).