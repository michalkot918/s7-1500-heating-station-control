# Symulacja i sterowanie ciepłownią

>  **Status projektu: w trakcie realizacji**
>
> Projekt jest rozwijany i będzie aktualizowany wraz z postępem prac. Panel HMI został wykonany, natomiast projekt pozostaje symulacją programową — nie jest uruchomiony na fizycznym sterowniku PLC.

## Opis projektu

Projekt przedstawia model systemu sterowania ciepłownią, opracowywany w środowisku **Siemens TIA Portal**. Obejmuje logikę sterowania procesem, symulację działania instalacji oraz panel operatorski HMI umożliwiający obserwację stanu systemu i zmianę wybranych parametrów pracy.

System odwzorowuje podstawowe elementy sieci grzewczej, w tym pompy, zawory i czujniki, a także proces regulacji temperatury i ciśnienia. Program uwzględnia stany pracy urządzenia, komendy uruchamiania i zatrzymywania oraz współpracę poszczególnych bloków sterujących.

Celem projektu jest praktyczne wykorzystanie zagadnień z zakresu automatyki przemysłowej, programowania sterowników PLC, regulacji procesów oraz projektowania interfejsów operatorskich.

## Główne funkcjonalności

### Sterowanie procesem
- Logika stanów pracy ciepłowni.
- Obsługa komend uruchomienia i zatrzymania pracy.
- Sterowanie elementami instalacji, w tym pompą i zaworami.
- Wybór pomiędzy sterowaniem automatycznym a innym dostępnym trybem obsługi elementów.

### Regulacja parametrów
- Regulacja temperatury z wykorzystaniem zaworu i regulatora procesu.
- Regulacja ciśnienia z wykorzystaniem pompy i regulatora procesu.
- Konfiguracja wartości zadanych temperatury i ciśnienia.

### Symulacja instalacji
- Programowe odwzorowanie zmian temperatury i ciśnienia.
- Symulacja wpływu ogrzewania i odbioru ciepła na parametry procesu.
- Modelowanie odbioru ciepła przez cztery bloki odbiorcze.
- Symulacja działania wybranych elementów instalacji bez konieczności korzystania z fizycznego sterownika PLC.

### Panel operatorski HMI
W projekcie wykonano panel HMI umożliwiający wizualizację i obsługę symulowanego systemu. Interfejs obejmuje:

- Graficzne odwzorowanie sieci grzewczej.
- Sterowanie elementami instalacji, w tym pompami i zaworami.
- Możliwość włączania i wyłączania sterowania automatycznego.
- Podgląd aktualnego stanu maszyny.
- Ustawianie wartości zadanych temperatury i ciśnienia.

Panel HMI stanowi interfejs pomiędzy operatorem a symulowanym procesem, ułatwiając obserwację jego działania i zmianę parametrów pracy.

## Struktura programu

Program został podzielony na bloki odpowiadające za poszczególne elementy systemu.

| Blok | Przeznaczenie |
|---|---|
| `OB1` – Main | Wywołanie głównej logiki ciepłowni |
| `OB30` – 100 ms | Cykliczne wywołanie bloków regulacji i symulacji |
| `FC4` – `cieplownia` | Główna logika sterowania i koordynacja komponentów |
| `FC7` – `cieplownia_operacja` | Obsługa komend start/stop i wartości zadanych |
| `FB2` – `CE_PID` | Obsługa regulatorów temperatury i ciśnienia opartych na bloku `CONT_C` |
| `FB3` – `CE_symulacja` | Model zmian temperatury i ciśnienia |
| `FC5` – `cieplownia_warstwa_IO` | Wydzielony blok obsługi warstwy wejść/wyjść |
| `FC6` – `cieplownia_bledy` | Blok przeznaczony do obsługi błędów |

W przedstawionej konfiguracji regulatorów wykorzystano człony proporcjonalny i całkujący (PI). Człon różniczkujący jest wyłączony.

## Technologie i narzędzia

- Siemens TIA Portal
- Programowanie sterowników PLC
- LAD (Ladder Diagram)
- Bloki funkcyjne i funkcje PLC
- Regulacja procesów z wykorzystaniem `CONT_C`
- Projektowanie panelu operatorskiego HMI
- Symulacja procesu technologicznego

## Status projektu i dalszy rozwój

Projekt jest w trakcie realizacji i będzie sukcesywnie aktualizowany.

Aktualny zakres obejmuje logikę sterowania ciepłownią, symulację parametrów procesu, bloki regulacji oraz wykonany panel HMI. Kolejne etapy prac będą skupiać się na dalszym rozwijaniu, testowaniu i weryfikacji działania poszczególnych elementów systemu oraz uzupełnianiu dokumentacji.

Projekt ma charakter symulacyjny. Nie zakłada obecnie uruchomienia na fizycznym sterowniku PLC, a jego rozwój koncentruje się na programowym modelu procesu i współpracy logiki sterowania z interfejsem HMI.

## Dokumentacja i materiały

W repozytorium będą sukcesywnie udostępniane materiały związane z projektem, w tym kod programu, dokumentacja bloków oraz zrzuty ekranu prezentujące panel operatorski i działanie symulacji.

