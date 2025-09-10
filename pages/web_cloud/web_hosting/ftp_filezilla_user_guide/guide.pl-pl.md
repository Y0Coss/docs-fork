---
title: "Hosting WWW - Jak używać programu FileZilla"
excerpt: "Dowiedz się, jak zalogować się do przestrzeni dyskowej hostingu OVHcloud i zarządzać danymi w niej zawartymi za pomocą oprogramowania FileZilla"
updated: 2025-09-09
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

> [!primary]
> **Wyłączanie narzędzia FTP Explorer/Net2FTP**
>
> W przypadku hostingu WWW nie jest już możliwe zalogowanie się do przestrzeni FTP przy użyciu narzędzia online FTP Explorer/Net2FTP. Aby kontynuować łączenie się przez FTP z Twoim hostingiem, skorzystaj z oprogramowania [FileZilla](https://filezilla-project.org/download.php) lub [Cyberduck](https://cyberduck.io/).

## Wprowadzenie 

FileZilla to oprogramowanie dostępne bezpłatnie w wielu systemach operacyjnych (Windows, macOS, etc).
Umożliwia wgranie plików lub Twojej strony WWW do trybu online poprzez [zalogowanie się do przestrzeni dyskowej](/pages/web_cloud/web_hosting/ftp_connection) na Twoim hostingu.

**Dowiedz się, jak zalogować się do przestrzeni dyskowej hostingu OVHcloud i zarządzać danymi w niej zawartymi za pomocą oprogramowania FileZilla.**

## Wymagania początkowe

- Dostęp do [Panelu klienta OVHcloud](/links/manager).
- Posiadanie [hostingu WWW](/links/web/hosting).
- Instalacja programu FileZilla na Twoim komputerze Jest on dostępny bezpłatnie na stronie [filezilla-project.org](https://filezilla-project.org/download.php).

## Prezentacja interfejsu <a name="interface"></a>

/// details | Kliknij tutaj, aby wyświetlić zawartość tej sekcji.

![FileZilla-interface](/pages/assets/screens/other/web-tools/filezilla/main-interface.png){.thumbnail}

- W górnej **ramce** możesz szybko połączyć się z hostingiem podając nazwę **hosta**, nazwę **użytkownika**, **hasło** oraz numer **portu**.
- **strefa 1**: szczegółowe informacje na temat historii operacji, logowania do przestrzeni FTP, transferów plików, błędów itp. Więcej informacji znajdziesz w oficjalnej [dokumentacji Filezilla](https://filezilla-project.org/).
- **strefa 2**: drzewo katalogów/plików lokalnych na komputerze.
- **strefa 3**: drzewo zdalnych katalogów/plików po zalogowaniu się do hostingu.
- **strefa 4**: lista katalogów/plików w katalogu wybranym lokalnie na Twoim komputerze.
- **strefa 5**: lista zdalnych katalogów/plików w wybranym katalogu na Twoim hostingu.
- **strefa 6**: lista operacji transferu w trakcie, oczekujących lub z błędem między Twoim komputerem i hostingiem.

///

## W praktyce

### 1 - Pobieranie danych do logowania do przestrzeni dyskowej hostingu WWW <a name="part-1"></a>

Wykonaj następujące czynności:

1. Zaloguj się do [Panelu klienta OVHcloud](/links/manager) i przejdź do sekcji `Web Cloud`{.action}.
2. Kliknij menu `Hosting`{.action}, następnie wybierz odpowiedni hosting.
3. Na stronie, która się wyświetli kliknij zakładkę `FTP - SSH`{.action}.
4. Na nowej stronie wyświetlają się informacje dotyczące Twojej przestrzeni dyskowej. W mailu znajdziesz następujące elementy:
    - `Serwer FTP i SFTP` przedstawiony w następującej formie: `ftp.clusterXXX.hosting.ovh.net` (gdzie każda z 3 `X` odpowiada cyfrze między `0` i `9`).
    - Jeden z użytkowników w kolumnie `Login` tabeli na dole strony. Możesz również użyć `Login główny`, jeśli chcesz.
    - Numer `Port FTP` lub numer `Port SFTP` w zależności od protokołu połączenia, którego będziesz chciał użyć do zalogowania się do przestrzeni dyskowej.

> [!primary]
>
> Ze względów bezpieczeństwa hasło użytkownika nie pojawia się na stronie zakładki `FTP - SSH`{.action}. Jeśli nie pamiętasz hasła, zapoznaj się z [tym przewodnikiem](/pages/web_cloud/web_hosting/ftp_change_password), aby wprowadzić zmiany.

### Połączenie z Filezilla przez FTP

![hosting](/pages/assets/screens/other/web-tools/filezilla/quick-connect.png){.thumbnail}

W tabeli poniżej wpisz informacje korzystając z paska szybkiego połączenia:

|Dane do uzupełnienia|Szczegóły|
|---|---|
|Host| Adres serwera pozwalający na dostęp do przestrzeni dyskowej Twojego hostingu.<br><br> Dla hostingu współdzielonego zazwyczaj ma taką formę: `ftp.clusterXXX.hosting.ovh.net` (`XXX` to numer klastra, w którym znajduje się Twój hosting)|
|Użytkownik|Identyfikator pozwalający na dostęp do przestrzeni dyskowej Twojego hostingu.|
|Hasło|Hasło przypisane do użytkownika.|
|Port|Jest to zazwyczaj uzupełniane automatycznie przez oprogramowanie. W przeciwnym razie wprowadź:<br><br>- port "21" dla połączenia FTP;<br>- port "22" dla połączenia SFTP (w przypadku gdy połączenie jest włączone). Więcej informacji o SFTP znajdziesz w [sekcji poświęconej temu tutorialu](#sftp).|

Jeśli nie posiadasz wskazanych wyżej informacji, zaloguj się do [Panelu klienta OVHcloud](/links/manager) w sekcji `Web Cloud`{.action} i kliknij `Hosting`{.action}. Wybierz odpowiedni hosting i przejdź do zakładki `FTP - SSH`{.action}. Wyświetlą się wówczas informacje dotyczące Twojej przestrzeni dyskowej:

![hosting](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/tab-pro.png){.thumbnail}

> [!warning]
>
> Niektóre oferty OVHcloud nie używają portu 22 do połączenia przez SFTP i/lub SSH. Użyj więc portów, które wyświetlają się w Twoim [Panelu klienta OVHcloud](/links/manager).
>

Po poprawnym wpisaniu wszystkiego w ramce **1** poniższego obrazka kliknij `Szybkie`{.action} połączenie.

![hosting](/pages/assets/screens/other/web-tools/filezilla/quick-connect-successfull.png){.thumbnail}

Jeśli logowanie przebiegło pomyślnie, zostaniesz o tym poinformowany poprzez status w ramce **2**. Możesz wyświetlić katalogi, katalogi i pliki już zainstalowane na Twoim hostingu (patrz ramka **3**).

### Połączenie z Filezilla przez SFTP <a name="sftp"></a>

**SFTP** (**S**ecure **F**ile **T**ransfer **P**rotocol) to protokół podobny do protokołu **FTP**. Podobnie jak SSH, używa domyślnego portu 22 zamiast portu 21. Jeśli korzystasz z hostingu Cloud Web, powinieneś użyć portu, który wyświetla się w Twoim [Panelu klienta OVHcloud](/links/manager). Port 22 został dezaktywowany przez bezpieczeństwo poprzez SSH i SFTP dla hostingu Cloud Web.

> [!success]
>
> Usługa SFTP jest dostępna bezpłatnie dla wszystkich ofert hostingu OVHcloud (z wyjątkiem starych ofert 60free/demo1g).
> 

#### Sprawdź aktywację SFTP

Sprawdź najpierw, czy SFTP jest aktywny dla Twojego **Login FTP**.

Przejdź do [Panelu klienta OVHcloud](/links/manager), w sekcji `Web Cloud`{.action}, następnie kliknij `Hosting`{.action}. Wybierz odpowiedni hosting i przejdź do zakładki `FTP - SSH`{.action}.

Następnie sprawdź, czy **SFTP** jest aktywny w tabeli na dole strony.

![Aktywacja SFTP oferuje start](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/sftp-enabled-pro.png){.thumbnail}

Jeśli nie jest aktywny:

- Kliknij przycisk `...`{.action} po prawej stronie tabeli, a następnie `Edytuj`{.action}.

![Włączenie SFTP 1](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/edit-login.png){.thumbnail}

- W oknie, które się wyświetla sprawdź, czy aktywowana jest jedna z 2 poniższych opcji:
    - **FTP i SFTP**: aby włączyć tylko SFTP poza FTP.
    - **FTP, SFTP i SSH**: aby włączyć FTP, SFTP i SSH.

![Włączenie SFTP 2](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/modify-user-step-1-connexion-protocols.png){.thumbnail}

- Następnie kliknij `Dalej`{.action}, a następnie `Zatwierdź`{.action}

#### Uruchom połączenie SFTP

![hosting](/pages/assets/screens/other/web-tools/filezilla/quick-connect.png){.thumbnail}

W górnej części Filezilla i w celu nawiązania połączenia z zdalnym serwerem (hosting) wprowadź następujące elementy:

- Host: `ftp.clusterXXX.hosting.ovh.net` (pamiętaj, aby zastąpić `X` X klastrem hostingowym)
- Identyfikator: swój login FTP
- Hasło: hasło FTP przypisane do loginu
- Port: 22

Po kliknięciu przycisku Szybki `Logowanie`{.action} otworzy się okno dialogowe (patrz zdjęcie poniżej), w celu potwierdzenia logowania do hosta, do którego zamierzasz się zalogować. Po zalogowaniu się do hosta OVHcloud możesz zaznaczyć kratkę *Zawsze zaufaj temu hoście, dodaj ten klucz do pamięci cache*, aby w przyszłości program nie zapytany o to ponownie.

![hosting](/pages/assets/screens/other/web-tools/filezilla/unknown-host-key-message.png){.thumbnail}

#### Błędy połączenia

**Kliknij napotkany błąd, aby wyświetlić rozwiązanie.**

/// details | Authentication failed - Could not connect to server 

Wyświetlony poniżej komunikat wskazuje błąd w identyfikacji podczas logowania przez FTP lub SFTP do hostingu:

![hosting](/pages/assets/screens/other/web-tools/filezilla/authentification-failed-could-not-connect-server.png){.thumbnail}

Ten rodzaj wiadomości jest generowany przez błąd w momencie połączenia Login/Hasło.

Sprawdź dane dostępowe, aby upewnić się, że nie podano błędu. W razie potrzeby możesz [zmienić hasło dostępu FTP](/pages/web_cloud/web_hosting/ftp_change_password) bezpośrednio w panelu [Panel klienta OVHcloud](/links/manager).

///

/// details | Connection timed out after 20 seconds of inactivity - Could not connect to server

W poniższym przypadku błąd jest generowany przez nieprawidłową nazwę hosta:

![hosting](/pages/assets/screens/other/web-tools/filezilla/connection-timed-out-after-20s.png){.thumbnail}

Sprawdź nazwę hosta zadeklarowaną w Twoim [Panelu klienta OVHcloud](/links/manager).

///

### 3 - Transfer plików

Aby wykonać transfer plików przez (S)FTP, możesz je wybrać, a następnie przeciągnąć i upuścić katalogi/pliki z lewego okna *(komputer)* do prawego okna *(hosting)* (**strefy 4 i 5** opisane w sekcji niniejszego tutoriala dotyczącej [interfejsu](#interface) FileZilla).

Pamiętaj, aby wybrać docelowy katalog w prawym oknie.

Po przeprowadzeniu tej operacji Twoje pliki zostaną automatycznie uruchomione w kolejce, po czym zostaną złożone na serwerze.

![hosting](/pages/assets/screens/other/web-tools/filezilla/drag-drop-en.png){.thumbnail}

### 4 - Inne funkcje programu FileZilla

**Kliknij na nagłówki poniżej, aby wyświetlić ich zawartość.**

/// details | Widok kolejki

Dostępny jest widok kolejki (**strefa 6** opisana w sekcji niniejszego tutoriala [dotyczącej interfejsu](#interface) Filezilla).

W tej strefie znajdziesz:

- pliki oczekujące na złożenie na zdalnym serwerze jeszcze obecnym w kolejce;
- pliki, w przypadku których przeniesienie nie powiodło się;
- pliki, dla których operacja transferu została wykonana na zdalnym hostingu.

![hosting](/pages/assets/screens/other/web-tools/filezilla/waiting-list-view.png){.thumbnail}

///

/// details | Menu kontekstowe Serwer

Kliknij prawym przyciskiem myszy jeden z plików znajdujących się w **strefie 5** (opisanych w sekcji niniejszego tutoriala [dotyczącej interfejsu](#interface) FileZilla).

Pojawi się menu kontekstowe i masz do wyboru kilka opcji:

- Pobierz: Pobierz plik do otwartego lokalnego folderu.
- Dodaj pliki do kolejki: Dodaj plik do kolejki oczekujących, możesz na przykład odroczyć pobieranie danych.
- Wyświetl/Edytuj: Pozwala na bezpośrednie wyświetlanie lub edytowanie pliku znajdującego się na Twoim hostingu. Musisz mieć program, który potrafi odczytać plik zainstalowany na komputerze.
- Utwórz katalog: Umożliwia utworzenie nowego katalogu bezpośrednio na zdalnym hostingu.
- Aktualizacja: Aktualizuje wyświetlanie danych, aby poprawnie wyświetlać różne pliki.
- Usuń: Pozwala usunąć wybrany plik.
- Zmień nazwę: Pozwala zmienić nazwę wybranego pliku.
- Skopiuj adres (adresy) do schowka: Umożliwia automatyczne skopiowanie bezpośredniego linku do wybranego pliku. Przykład URL, który może zostać wygenerowany: `ftp://loginftp@ftp.clusterXXX.hosting.ovh.net/www/my_folder1/my_file.jpg`.
- Uprawnienia pliku: Daje możliwość zmiany uprawnień dla plików (Chmod).

![hosting](/pages/assets/screens/other/web-tools/filezilla/contextual-menu-server.png){.thumbnail}

///

/// details | Prawa dostępu (Chmod) do plików i folderów

Kliknij prawym przyciskiem myszy jeden z plików znajdujących się na serwerze, a następnie wybierz `Uprawnienia do pliku ...`{.action}.

Możesz zmienić uprawnienia dostępu (Chmod) do plików i katalogów znajdujących się na hostingu.

Na ogół łatwiej jest zarządzać uprawnieniami Chmod, używając wartości `XXX` (składającej się z 3 cyfr, od 0 do 7). Panel uprawnień może wówczas wahać się od `000` (bez uprawnień) do `777` (wszystkie prawa).

> [!alert]
>
> Uwaga, nie zaleca się umieszczania uprawnień Chmod 000 na folderach lub plikach. Nie będziesz już miał możliwości (przynajmniej w przypadku FTP) zarządzania tym elementem (w tym jako administrator FTP).
>
> To samo dotyczy praw Chmod 777, ponieważ w przeciwieństwie do Chmod 000, każdy może działać na folderze lub pliku, co powoduje istotną lukę w zabezpieczeniach dla hostowanych danych.
>

Pierwsza z trzech cyfr `XXX` definiujących chmod odpowiada prawom właściciela/administratora, druga - prawom grup (rzadko używane i zazwyczaj równe 0), a trzecia - użytkownikom strony WWW na hostingu.

Domyślnie zalecamy, aby nie przekraczać praw Chmod **705** do akt i praw Chmod **604** do plików.

Im wyższa liczba, tym większe uprawnienia.

![hosting](/pages/assets/screens/other/web-tools/filezilla/change-file-attributes.png){.thumbnail}

Wpisz uprawnienia, które chcesz przyznać, wartość Chmod zostanie automatycznie zaktualizowana.

Możesz zaznaczyć kratkę "Rekurencja w podfolderach".

W ten sposób prawa do akt sprawy oraz katalogi i pliki, które mogą być w nim przechowywane, ulegną zmianie.

///

/// details | Odblokowanie

> [!primary]
>
> Niezależnie od podjętych przez Ciebie działań, Twój hosting może zostać wyłączony po wykryciu przez nasze systemy bezpieczeństwa złośliwych lub nieautoryzowanych plików na Twoim hostingu.
>
> Następnie należy [zabezpieczyć Twoje rozwiązania](/pages/web_cloud/web_hosting/diagnostic_403_forbidden), usuwając luki bezpieczeństwa wskazane w powiadomieniu o blokadzie otrzymanym na e-mail.
>

Następnie kliknij `Serwer`{.action}, a następnie wybierz `Wpisz spersonalizowane`{.action} polecenie (ta opcja może się również nazywać `Wprowadź polecenie FTP`{.action}).

Wpisz następujące polecenie:

```bash
SITE CHMOD 705 /
```

> [!warning]
>
> To zamówienie nie działa w przypadku SFTP.
>

![hosting](/pages/assets/screens/other/web-tools/filezilla/site-chmod-705-command.png){.thumbnail}

Jeśli otrzymasz błąd `550 would not change perms on /. not such file or directory`, użyj następującego polecenia:

```bash
SITE CHMOD 705 .
```

> [!primary]
>
> Aby sprawdzić, czy ponowne otwarcie strony zostało wykonane, przetestuj ją w przeglądarce internetowej po kilku minutach.
>

> [!warning]
>
> Przetestuj wyświetlacz maksymalnie po 3 godzinach.<br>
> Nasze roboty spędzają co najmniej 3 godziny, aby sprawdzić zmiany stanu.<br>
> W zależności od tego, kiedy zostanie przeprowadzona powyższa operacja, przywrócenie prawidłowego wyświetlania Twojej strony będzie możliwe.<br>
> Jeśli upłynęło 3 godzin, Twoja strona WWW nie jest jeszcze dostępna w sieci, sprawdź, czy podane zamówienie zostało zrealizowane i czy operacja została ponownie uruchomiona.<br>
> Jeśli to nadal nie działa, skontaktuj się z pomocą techniczną.
> 

///

/// details | Transfer plików binarnych

W przypadku plików typu binarnego, takich jak pliki typu **CGI**, warto wybrać sposób, w jaki zostanie zrealizowany transfer.

Aby zmienić typ transferu, wybierz `Transfer`{.action} w menu głównym, a następnie `Typ transferu`{.action}.

![hosting](/pages/assets/screens/other/web-tools/filezilla/transfert-binary-files.png){.thumbnail}

///

/// details | Porównanie plików

![hosting](/pages/assets/screens/other/web-tools/filezilla/comparison-tool.png){.thumbnail}

Opcja porównywania plików wyświetla kolory w **strefach 4** i **5** (przedstawione w sekcji niniejszego tutoriala [w interfejsie](#interface) FileZilla). Ta opcja pozwala na podkreślenie różnic między plikami i folderami lokalnymi i na serwerze. 

Po kliknięciu prawym przyciskiem myszy na ikonę, możesz zmienić sposób porównania. Będziesz mógł włączyć lub wyłączyć opcję, ale również:

- porównanie rozmiaru plików;
- porównanie czasu;
- ukryć identyczne pliki.

**Znaczenie kolorów:**

- Żółty: Plik istnieje tylko z jednej strony.
- Zielony: Plik jest nowszy niż niekolorowy plik po drugiej stronie.
- Czerwony: Rozmiar plików jest inny.

///

## Sprawdź również <a name="go-further"></a>

Poniżej znajdziesz link do naszej dokumentacji, aby [usunąć powtarzające się błędy podczas korzystania z programu FTP](/pages/web_cloud/web_hosting/ftp_recurring_ftp_problems).

Zapoznaj się [z przewodnikami dotyczącymi hostingu współdzielonego](/products/web-cloud-hosting).

Zapoznaj się z oficjalną [stroną FileZilla](https://filezilla-project.org/).

Skontaktuj się z [partnerami OVHcloud](/links/partner), jeśli szukasz zaawansowanych rozwiązań (indeksowanie, rozwój, etc).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i korzystania z rozwiązań OVHcloud, sprawdź naszą [ofertę wsparcia](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).