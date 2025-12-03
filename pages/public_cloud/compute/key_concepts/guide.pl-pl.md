---
title: 'Public Cloud Instances - Podstawowe pojęcia'
excerpt: 'Dowiedz się podstaw Public Cloud Compute: jak działają instancje, dostępne rodziny i rozmiary, wdrożenia wielu stref dostępności, zarządzanie obrazami, bezpieczeństwo SSH, mechanizmy kopii zapasowych, sieci publiczne/prywatne i korzyści z planów oszczędnościowych.'
updated: 2025-12-03
---

## Wprowadzenie

Ten przewodnik ma na celu zapewnienie Ci jasnego zrozumienia podstawowych pojęć niezbędnych do tworzenia, konfigurowania i zarządzania pierwszymi instancjami OVHcloud Public Cloud Compute. Nauczysz się, jak działają instancje, jak wybrać odpowiedni typ instancji i jak kluczowe elementy, takie jak obrazy, strefy dostępności, sieci, bezpieczeństwo i kopie zapasowe, współdziałają w ekosystemie OVHcloud.

## Co to jest instancja (maszyna wirtualna)?

Instancja, czyli maszyna wirtualna (VM), to całkowicie izolowany serwer działający na udostępnionej infrastrukturze fizycznej OVHcloud. Działa jak tradycyjny serwer, ale oferuje elastyczność i skalowalność chmury. Wybierasz system operacyjny, definiujesz zasoby CPU, RAM i magazynu oraz wdrażasz swoje aplikacje, strony internetowe lub środowiska programistyczne.

Instancje Public Cloud Compute oferują:

- Tworzenie na żądanie i elastyczne rozmiary – skaluj zasoby w górę lub w dół zgodnie z potrzebami.
- Opłatę za rzeczywiste użycie – rozliczane godzinowo lub miesięcznie na podstawie rzeczywistego wykorzystania.
- Płynną integrację z usługami OVHcloud – w tym Object Storage, Sieć, Kopie zapasowe i wiele innych.

Instancje można zarządzać za pomocą Panelu klienta OVHcloud, interfejsu Horizon, punktów końcowych API lub za pomocą narzędzi automatyzacji i orchestracji, takich jak OVHcloud CLI i Terraform.

## Typy instancji

OVHcloud oferuje wiele rodziny instancji zaprojektowanych do spełniania różnych wymagań dotyczących obciążenia. Każda rodzina oferuje zakres rozmiarów (flavorów), aby dokładnie dopasować potrzeby zasobowe.

| Typy instancji | Opis | Typowe przypadki użycia |
| ---------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| General Purpose | Zrównoważone CPU i pamięć | Nadaje się do serwerów deweloperskich, aplikacji internetowych i ogólnych obciążeń biznesowych. Zapewnia zrównoważony stosunek CPU do RAM. |
| CPU Optimized | Wysoka wydajność procesora | Idealne dla aplikacji intensywnie obliczeniowych, zadań przetwarzania równoległego, potoków CI/CD lub mikroserwisów wymagających wysokiej częstotliwości CPU. |
| Memory Optimized | Duża pojemność pamięci | Zaprojektowane do analizy danych, dużych obciążeń danych i buforowania baz danych. Charakteryzuje się wysokim stosunkiem RAM do CPU i przyspieszonymi IOPS. Wirtualne rdzenie są taktowane z częstotliwością 2 GHz lub wyższą. |
| Storage Optimized | Wysoka wydajność IOPS | Wyposaży w magazyn NVMe do ultra szybkiego odczytu i zapisu danych, idealne do baz danych i dużych aplikacji danych. |
| GPU | Grafika z akceleracją sprzętową | Zapewnia wspaniałą wydajność przetwarzania równoległego, nawet do 1000 razy szybszą niż CPU dla niektórych obciążeń. Nadaje się do AI, uczenia głębokiego i renderowania 3D. |
| Discovery | Kosztowy, udostępnione zasoby | Instancje wstępne z udostępnionymi zasobami, oferujące stabilną wydajność po atrakcyjnej cenie. Idealne do środowisk testowych, szkoleń lub projektów dowodowych. |

Każda rodzina instancji zawiera wiele rozmiarów (flavorów), aby pomóc Ci dostosować instancję do konkretnych potrzeb zasobowych Twojej aplikacji.

## Lokalizacja i strefy dostępności

Instancje OVHcloud Compute są wdrażane w [wielu centrach danych na całym świecie](&#x2F;links&#x2F;infrareg), zapewniając wysoką dostępność i bliskość użytkowników. Przykłady regionów obejmują:

- GRA – Gravelines, Francja
- BHS – Beauharnois, Kanada
- DE – Frankfurt, Niemcy

**Typy stref dostępności:**

| Typy stref | Opis | Zalecane użycie |
| ------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| 1-AZ (Jedna strefa dostępności) | Instancje są wdrażane w jednej strefie. | Proste środowiska, rozwój, testowanie lub niekrytyczne obciążenia. |
| 3-AZ (Trzy strefy dostępności) | Instancje są rozproszone w trzech nadmiarowych strefach w tym samym regionie. | Obciążenia produkcyjne wymagające wysokiej dostępności i odporności na awarie. |
| Lokalne strefy | Lokalizacje krawędziowe bliżej użytkowników końcowych, aby zmniejszyć opóźnienia. | Aplikacje wrażliwe na opóźnienia, takie jak przetwarzanie danych w czasie rzeczywistym, gry, czy interaktywne usługi internetowe. |

&gt; [!primary]
&gt; 
&gt; **Najlepsza praktyka:** Dla krytycznych obciążeń preferuj [wdrożenie wielostrefowe](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_cross_functional&#x2F;3az_ref_architecture), aby zapewnić odporność usługi i ciągłość działania.
&gt;

## Dostępne obrazy systemowe

Podczas tworzenia instancji wybierasz obraz zawierający system operacyjny i opcjonalnie zainstalowane wcześniej aplikacje. OVHcloud oferuje różnorodne obrazy, aby spełnić różne potrzeby:

- **Dystrybucje Linux:** Ubuntu, Debian, CentOS, AlmaLinux, Rocky Linux i inne. Te obrazy są gotowe do użycia dla serwerów internetowych, środowisk deweloperskich i ogólnych obciążeń.
- **Windows Server:** Wersje z wbudowanymi licencjami, umożliwiające natychmiastowe wdrożenie aplikacji opartych na Microsoft i obciążeń przedsiębiorstwa.
- **Zaawansowane aplikacje:** Obrazy z zainstalowanym oprogramowaniem, takim jak cPanel, Plesk, Docker lub NVIDIA GPU Cloud (NGC). Ułatwiają one wdrożenie i przyspieszają czas trwania produkcji.
- **[Niestandardowe obrazy](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;upload_own_image):** Możesz zaimportować własne obrazy w formacie QCOW2 lub RAW, zapewniając pełną kontrolę nad swoim środowiskiem i umożliwiając migracje, standardowe szablony lub specjalistyczne konfiguracje.

**Cykl życia i wsparcie:** OVHcloud regularnie aktualizuje katalog obrazów. Zawsze sprawdzaj ogłoszenia dotyczące cyklu życia i końca wsparcia, aby upewnić się, że Twoje obrazy są bezpieczne i wspierane. Zobacz [tutaj](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;image-life-cycle).

## Klucze SSH

Klucze SSH zapewniają bezpieczny sposób dostępu do Twoich instancji bez użycia haseł. Składają się z dwóch elementów:

- **Klucz publiczny:** Zainstalowany na instancji, aby umożliwić dostęp.
- **Klucz prywatny:** Trzymany bezpiecznie na Twoim komputerze lokalnym i używany do uwierzytelnienia połączenia.

Uwierzytelnianie przez SSH zapewnia szyfrowany i niezawodny dostęp do Twoich serwerów.

Najlepsze praktyki:

- Nigdy nie udostępniaj swojego klucza prywatnego.
- Używaj unikalnego klucza dla każdego użytkownika.
- Zapisuj swoje klucze w bezpiecznym menedżerze lub skarbcu.

Aby uzyskać szczegółowe instrukcje dotyczące tworzenia i używania kluczy SSH, skorzystaj z [przewodnika OVHcloud dotyczącego SSH](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;creating-ssh-keys-pci).

## Kopia zapasowa

Kopie zapasowe chronią Twoje dane i konfiguracje przed przypadkową utratą lub błędami. OVHcloud oferuje kilka mechanizmów kopii zapasowych, aby zapewnić, że Twoje instancje i dane pozostają bezpieczne:

- **Typy kopii zapasowych:**
    - Ręczne kopie zapasowe: Wykonaj migawkę dysku w dowolnym momencie.
    - Automatyczne kopie zapasowe: Tworzone w regularnych odstępach czasu.
    - Tworzenie i przywracanie instancji: Wdróż nową instancję bezpośrednio z istniejącej kopii zapasowej.
- **Lokalizacje kopii zapasowych:**
    - Lokalna kopia zapasowa: Zapisywana w tym samym regionie co Twoja instancja.
    - Kopia zapasowa zdalna: Automatycznie tworzona kopię lokalną w wybranym przez Ciebie innym regionie.

&gt; [!primary]
&gt;
&gt; **Najlepsza praktyka:** Kopia zapasowa nie zastępuje [odporności architektonicznej](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_cross_functional&#x2F;3az_ref_architecture). Dla krytycznych środowisk połącz kopie zapasowe z replikacją wielostrefową, aby zapewnić maksymalną ochronę danych i dostępność usługi.
&gt;

## Sieci publiczne i prywatne

Instancje OVHcloud Compute mogą być podłączone do różnych typów sieci w zależności od potrzeb Twojej aplikacji.

| Typy sieci | Opis | Przypadki użycia |
| ------------------------| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Sieć publiczna | Instancje są podłączone do Internetu za pomocą publicznego adresu IP. | Gospodarowanie witrynami internetowymi, API lub zapewnianie zdalnego dostępu do Twoich serwerów. |
| Sieć prywatna (vRack) | Prywatna interkoneksja Twoich zasobów OVHcloud, izolowana od publicznego Internetu. | Łączenie baz danych, usług backendowych lub komunikacji wewnętrznego między instancjami. |

vRack umożliwia utworzenie bezpiecznej, izolowanej sieci, nawet w różnych regionach lub projektach.

**Przykład:** Umieść swoją bazę danych na prywatnej sieci, podczas gdy tylko serwer internetowy jest dostępny na sieci publicznej.

Aby uzyskać bardziej szczegółowe wskazówki dotyczące konfigurowania sieci Public Cloud, skorzystaj z oficjalnego [przewodnika OVHcloud dotyczącego sieci](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_network_services&#x2F;concepts-01-public-cloud-networking-concepts).

## Plany oszczędnościowe

Plan oszczędnościowy pozwala Ci obniżyć koszty Public Cloud Compute w zamian za zobowiązanie do spójnego użycia przez określony czas od 1 miesiąca do 3 lat.

**Kluczowe korzyści:**

- **Niższe koszty:** Więcej opłacalne niż rozliczanie na żądanie.
- **Automatyczne stosowanie:** Zniżki są automatycznie stosowane do wszystkich kompatybilnych instancji.
- **Elastyczne:** Możesz zmieniać typy lub rozmiary instancji, zachowując korzyści z planu.

**Idealne przypadki użycia:**

- Stabilne i przewidywalne obciążenia, takie jak aplikacje produkcyjne lub serwery biznesowe.
- Usługi z konsekwentnymi wymaganiami dotyczącymi zasobów, które korzystają z optymalizacji kosztów.

Plan oszczędnościowy pomaga Ci zoptymalizować budżet, jednocześnie zachowując wydajność i niezawodność Twojego środowiska chmurowego. Aby uzyskać więcej informacji, zapoznaj się z oficjalnym [przewodnikiem OVHcloud dotyczącym planów oszczędnościowych](&#x2F;pages&#x2F;public_cloud&#x2F;public_cloud_cross_functional&#x2F;savings_plans).

## Sprawdź również

Po zapoznaniu się z podstawowymi pojęciami Public Cloud Compute OVHcloud możesz zająć się bardziej zaawansowanymi operacjami i zadaniami zarządzania.

- [Jak utworzyć instancję Public Cloud i połączyć się z nią](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;public-cloud-first-steps)
- [Zarządzanie instancjami Public Cloud](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;first_steps_with_public_cloud_instance)
- [Uruchomienie instancji na wolumenie startowym](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;start_instance_on_attached_volume)
- [Zawieszenie lub wstrzymanie instancji](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;suspend_or_pause_an_instance)
- [Pierwsze kroki z wstępnie zainstalowanymi aplikacjami](&#x2F;pages&#x2F;public_cloud&#x2F;Compute&#x2F;apps_first_steps)
- [Dodawanie kredytu chmurowego](&#x2F;pages&#x2F;account_and_service_management&#x2F;managing_billing_payments_and_services&#x2F;add_cloud_credit_to_project)

Dołącz do [grona naszych użytkowników](&#x2F;links&#x2F;community).