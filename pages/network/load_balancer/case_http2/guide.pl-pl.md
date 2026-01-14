---
title: Konfiguracja HTTP/2 w usłudze Load Balancer
excerpt: Wybierz i skonfiguruj interfejsy użytkownika usługi OVHcloud Load Balancer do użytku z protokołem HTTP/2.
updated: 2026-01-14
---

> [!primary]
> **Uwaga dotycząca natywnego wsparcia dla HTTP/2**
>
> Od czerwca 2025 r. frontony HTTP i TLS wykorzystywane przez usługi OVHcloud Load Balancer natywnie obsługują protokół HTTP/2.
>
> Jednak niniejszy przewodnik nadal jest stosowalny dla frontonów TCP, które mogą być przydatne w aplikacjach o wysokiej wydajności i niskim opóźnieniu.
>
> Aby włączyć HTTP/2 na istniejących frontonach HTTP i TLS, należy wykonać następujące żądanie odświeżania za pomocą API, gdzie **{serviceName}** jest wewnętrzną nazwą Twojego Load Balancer.
>

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>

## Wprowadzenie

Ten przewodnik ma dwa główne cele:

- Pomoże Ci zrozumieć różnice między frontonami TCP, HTTP i TLS na OVHcloud Load Balancer, umożliwiając Ci określenie, czy fronton TCP jest najlepszym wyborem dla Twoich konkretnych wymagań aplikacji, szczególnie w przypadku ruchu HTTP/2.
- Jeśli fronton TCP wydaje się pożądany, dostarczy krok po kroku instrukcji, jak go skonfigurować, aby skutecznie rozdzielał ruch HTTP/2 między Twoje serwery backend.

## Wymagania początkowe

Będziesz potrzebował:

- Usługi [OVHcloud Load Balancer](/links/network/load-balancer);
- Frontonu TCP na swoim Load Balancerze;
- Klaster backendowy TCP z przynajmniej jednym serwerem dodanym do niego;
- Serwery backendowe skonfigurowane do obsługi i odpowiadania HTTP/2;
- Dostępu do [OVHcloud API](/links/api).

## W praktyce

### Dlaczego używać HTTP/2?

HTTP/2 przynosi wiele korzyści, które poprawiają wydajność i efektywność Twoich aplikacji:

- *Szybsze czasy ładowania* dzięki multiplexingowi, który pozwala wysyłać wiele żądań równolegle na tej samej połączeniu.
- *Zmniejszone opóźnienie* ograniczając wymianę danych między klientem a serwerem.
- *Optymalizacja wydajności sieci* dzięki kompresji nagłówków.

### Różnice między HTTP/2 a frontonami TCP

Fronton TCP działa na warstwie 4 (warstwa transportowa) modelu OSI. Gdy skonfigurujesz fronton TCP, load balancer nawiązuje połączenie TCP między klientem a serwerem backendowym. Oznacza to, że load balancer nie analizuje ani nie rozumie danych HTTP/2 w strumieniu TCP. W konsekwencji, frontony TCP oferują wysoką wydajność ze względu na minimalne potrzeby przetwarzania.

Jednak ponieważ nie rozumie protokołu aplikacji, nie może wykonywać zaawansowanych optymalizacji specyficznych dla HTTP, takich jak routing oparty na treści lub manipulowanie nagłówkami HTTP.

Frontony HTTP i TLS, z kolei, działają na warstwie 7 (warstwa aplikacji). Gdy klient łączy się z frontonem kompatybilnym z HTTP/2, load balancer całkowicie dekoduje ramki HTTP/2 przed nawiązaniem połączenia z serwerem backendowym.

Poprzez zrozumienie protokołu aplikacji, fronton kompatybilny z HTTP/2 może oferować wiele zaawansowanych funkcji. W tym zakresie znajdują się m.in. zakończenie SSL/TLS (przenoszenie szyfrowania/odszyfrowania z serwerów backendowych), routing oparty na treści (np. kierowanie żądań do różnych pul backendowych na podstawie ścieżki URL lub nagłówków), modyfikacja żądań/odpowiedzi oraz multiplexing HTTP/2.

**Powinieneś używać frontonu TCP, gdy:**

- Musisz rozdzielać obciążenie innych usług niebędących HTTP (np. bazy danych, niestandardowe aplikacje TCP, SSH);
- Wymagasz maksymalnej wydajności i minimalnego opóźnienia;
- Twoje serwery backendowe już obsługują zakończenie SSL/TLS;
- Nie potrzebujesz zaawansowanych funkcji specyficznych dla HTTP, takich jak routing oparty na treści, manipulowanie nagłówkami HTTP lub optymalizacje na poziomie protokołu HTTP/2.

**Powinieneś używać frontonu kompatybilnego z HTTP/2, gdy:**

- Głównie rozdzielasz obciążenie ruchu sieciowego (HTTP/HTTPS);
- Chcesz skorzystać z korzyści wydajności HTTP/2 między klientem a load balancerem;
- Musisz przenieść zakończenie SSL/TLS z Twoich serwerów backendowych;
- Wymagasz zaawansowanego logiki routingu opartej na nagłówkach HTTP, adresach URL lub innych atrybutach warstwy aplikacji;
- Chcesz zoptymalizować doświadczenie klienta, korzystając z funkcji HTTP/2.

*Jeśli zdecydujesz się użyć frontonu TCP, przejdź do kolejnych kroków tego przewodnika, aby skonfigurować go do użycia z HTTP/2*.

### Skonfiguruj interfejs TCP do użycia z HTTP/2

> [!warning]
>
> Ważna jest kolejność tworzenia elementów: najpierw muszą zostać utworzone trasy, aby potem można było do nich przypisać reguły.
> 

#### Dodawanie trasy

Dodaj trasę do Twojej usługi.

##### Za pomocą API OVHcloud

> [!faq]
>
> Metoda API:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> `<identyfikator Load Balancera>`
>> >
>> > **action**
>> >
>> >> **type**
>> >> >
>> >> > `"farm"`
>> >>
>> >> **target**
>> >> >
>> >> > `<ID farmy TCP zarządzającej HTTP/2>`
>> >
>> > **frontendId**
>> >
>> >> `<ID front-endu TCP 443>`
>

#### Dodawanie reguły

Dodaj regułę do trasy.

##### Za pomocą API OVHcloud

> [!faq]
>
> Metoda API:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/tcp/route/{routeId}/rule
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> `<identyfikator Load Balancera>`
>> >
>> > **routeId**
>> >
>> >> `<ID trasy utworzonej powyżej>`
>> >
>> > **field**
>> >
>> >> `"protocol"`
>> >
>> > **match**
>> >
>> >> `"is"`
>> >
>> > **pattern**
>> >
>> >> `"http/2.0"`
>

#### Wdrażanie modyfikacji

Modyfikacje wprowadzone w Load Balancerze muszą zostać *wyraźnie zatwierdzone* w każdej ze stref skonfigurowanych dla Twojej usługi. Dopiero po zatwierdzeniu staną się widoczne dla Twoich użytkowników. Dzięki temu możesz przeprowadzić wszystkie zmiany konfiguracji za jednym razem.

W przypadku kilku stref, musisz zastosować tę samą konfigurację dla każdej z nich.

##### Za pomocą API OVHcloud

Odświeżanie strefy:

> [!faq]
>
> Metoda API:
>
>> > [!api]
>> >
>> > @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
>> >
>>
>
> Ustawienia:
>
>> > **serviceName** *
>> >
>> >> `<identyfikator Load Balancera>`
>> >
>> > **zone**
>> >
>> >> `<strefa do konfiguracji >`
>

#### Weryfikacja

Po zakończeniu wszystkich powyższych etapów usługa równoważenia obciążenia serwerów wykorzystujących HTTP/2 jest aktywna. Możesz wówczas zatwierdzić stan usługi. W tym celu wyślij zapytanie do Load Balancera, a następnie sprawdź wersję w otrzymanej odpowiedzi: 

```bash
curl -I --http2 https://www.ovh.com/
HTTP/2 200
```

## Sprawdź również

Dołącz do [grona naszych użytkowników](/links/community).