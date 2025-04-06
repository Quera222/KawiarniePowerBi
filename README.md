# KawiarniePowerBi
# 📊 Power BI – Projekt z wyzwania 5-dniowego

Ten projekt został stworzony w ramach 5-dniowego wyzwania Power BI, którego celem było przejście przez cały proces budowy raportu – od przygotowania danych, przez modelowanie, aż po końcową wizualizację. 

Dane źródłowe pochodziły z plików Excel oraz folderów zawierających informacje o produktach, sprzedaży i sklepach. Projekt został wykonany krok po kroku, zgodnie z dobrymi praktykami BI.

## 🛠️ Technologie i narzędzia

- **Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- **Excel (źródła danych)**
- **ChatGPT** – jako wsparcie w analizie, optymalizacji i tworzeniu formuł

## 📌 Zakres projektu

- Import i transformacja danych z różnych źródeł (Excel, foldery)
- Czyszczenie danych i standaryzacja formatów
- Budowa modelu danych i tworzenie relacji między tabelami
- Stworzenie własnej tabeli kalendarza przy użyciu DAX
- Tworzenie miar analitycznych (sprzedaż, zysk, mediana, procent całkowitej sprzedaży itp.)
- Grupowanie i segmentacja danych (np. segmentacja miast)
- Projektowanie przejrzystych wizualizacji (karty, tabele, fragmentatory)
- Budowa dynamicznego i czytelnego raportu końcowego

## 🎯 Cel projektu

Projekt miał charakter edukacyjny i praktyczny – służył do nauki i utrwalenia umiejętności pracy z Power BI w realistycznym scenariuszu biznesowym. Efektem końcowym jest interaktywny raport wspierający analizę sprzedaży, kosztów i rentowności.

## 📁 Zawartość repozytorium

- Plik `.pbix` z gotowym raportem
- Dane źródłowe (produkty, sprzedaż, sklepy)
- Ten plik `README.md`

## 📊 Kod – Tabela kalendarza (DAX)

```DAX
Kalendarz = 
ADDCOLUMNS (
    CALENDAR( 
        DATE( YEAR( MIN( Sprzedaz[Data zamówienia] ) ), 1, 1 ),
        DATE( YEAR( MAX( Sprzedaz[Data zamówienia] ) ), 12, 31)
    ),
    "Dzień", DAY ( [Date] ),
    "Nr. dnia tygodnia", WEEKDAY ( [Date], 2 ),
    "Dzień tygodnia", FORMAT ( [Date], "DDDD" ),
    "Nr. tygodnia", WEEKNUM ( [Date], 2 ),
    "Nr. miesiąca", MONTH ( [Date] ),
    "Miesiąc", FORMAT ( [Date], "MMMM" ),
    "Kwartał", FORMAT ( [Date], "\Qq" ),
    "Rok", YEAR ( [Date] ) 
)
