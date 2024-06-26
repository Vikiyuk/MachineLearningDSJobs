
# MachineLearningDSJobs

## Jaki problem będzie rozwiązywany z użyciem uczenia maszynowego?
Projekt ma na celu rozwiązanie problemu prognozowania wynagrodzeń w dziedzinie Data Science oraz analizę wpływu czynników związanych z doświadczeniem zawodowym, typem zatrudnienia i stopniem pracy zdalnej na wysokość wynagrodzenia. Dodatkowo analizowany będzie wpływ tych czynników na koeficjent pracy zdalnej.

## Na podstawie jakich danych historycznych?
Dane używane do analizy pochodzą z Kaggle.com ([Data Science Job Salaries](https://www.kaggle.com/datasets/ruchi798/data-science-job-salaries)). Poniżej znajduje się struktura danych:
- `work_year`: Rok, w którym wypłacono wynagrodzenie.
- `experience_level`: Poziom doświadczenia w pracy w danym roku, z kategorią:
  - `EN`: Poziom początkujący / Junior
  - `MI`: Poziom średni / Pośredni
  - `SE`: Poziom starszy / Ekspert
  - `EX`: Poziom wykonawczy / Dyrektor
- `employment_type`: Typ zatrudnienia dla danej roli, z kategoriami:
  - `PT`: Praca w niepełnym wymiarze godzin
  - `FT`: Praca w pełnym wymiarze godzin
  - `CT`: Praca na umowę
  - `FL`: Praca na zlecenie
- `job_title`: Stanowisko pracy w danym roku.
- `salary`: Całkowita kwota brutto wypłaconego wynagrodzenia.
- `salary_currency`: Waluta, w której wypłacono wynagrodzenie, w formie kodu waluty ISO 4217.
- `salary_in_usd`: Kwota wynagrodzenia przeliczona na USD, obliczona na podstawie kursu wymiany walut podzielonego przez średni kurs USD dla danego roku.
- `employee_residence`: Główny kraj zamieszkania pracownika w danym roku, w formie kodu kraju ISO 3166.
- `remote_ratio`: Ogólny odsetek pracy wykonywanej zdalnie, z możliwymi wartościami:
  - `0`: Brak pracy zdalnej (mniej niż 20%)
  - `50`: Częściowo zdalna
  - `100`: W pełni zdalna (powyżej 80%)
- `company_location`: Kraj głównego biura pracodawcy lub oddziału kontraktowego, w formie kodu kraju ISO 3166.
- `company_size`: Średnia liczba osób pracujących dla firmy w danym roku, z kategoriami:
  - `S`: mniej niż 50 pracowników (mała firma)
  - `M`: od 50 do 250 pracowników (średnia firma)
  - `L`: więcej niż 250 pracowników (duża firma)

## Typ modelu

Ponieważ mamy dane oznaczone labelami, zastosujemy uczenie nadzorowane. W związku z złożonością problemu oraz potencjalną potrzebą uwzględnienia nieliniowych zależności, wybór algorytmu jest istotny. Dwa główne kandydatury to:

1. **Las Losowy (Random Forest Regressor):** Jest to optymalny wybór ze względu na możliwość radzenia sobie zarówno z cechami numerycznymi, jak i kategorycznymi. Ten algorytm jest odporny na nadmierne dopasowanie i potrafi efektywnie uchwycić złożone interakcje między cechami. Ponadto, często osiąga dobre wyniki bez potrzeby intensywnej optymalizacji hiperparametrów.

2. **Gradient Boosting Regressor:** Ten algorytm potrafi efektywnie modelować złożone zależności między cechami a zmienną docelową, co jest istotne w przypadku prognozowania wynagrodzeń na podstawie różnorodnych czynników zawodowych. Ponadto, dzięki sekwencyjnemu budowaniu drzew decyzyjnych, algorytm ten może dopasowywać się do błędów poprzednich modeli, co może przyczynić się do poprawy jakości prognoz.
