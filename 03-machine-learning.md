[⟵ Poprzedni: Podstawy AI i rodzaje zadań](02-ai-workloads.md) | [Następny: Computer Vision ⟶](04-computer-vision.md)

# 3. **Podstawy uczenia maszynowego (ML)**

## Czym jest **ML**?
- **Uczenie maszynowe (Machine Learning, ML)** to dziedzina AI, w której algorytmy uczą się na podstawie danych, aby przewidywać lub klasyfikować nowe przypadki bez jawnego programowania reguł.
- Przykłady zastosowań ML:
	- **Klasyfikacja**: wykrywanie spamu, rozpoznawanie obrazów
	- **Regresja**: prognozowanie cen, przewidywanie popytu
	- **Klasteryzacja**: segmentacja klientów, grupowanie dokumentów

## Typy uczenia
- **Supervised Learning (uczenie nadzorowane)** – model uczy się na danych z etykietami (np. zdjęcia podpisane jako „kot” lub „pies”). Przykład: klasyfikacja maili jako spam/nie-spam.

![Supervised Learning](assets/supervised-learning.svg)

- **Unsupervised Learning (uczenie nienadzorowane)** – model sam szuka wzorców w nieoznaczonych danych (np. segmentacja klientów, klasteryzacja dokumentów).

![Unsupervised Learning](assets/unsupervised-learning.svg)

- **Reinforcement Learning (uczenie ze wzmocnieniem)** – model uczy się przez nagrody i kary, np. grając w gry komputerowe lub sterując robotem.

![Reinforcement Learning](assets/reinforcement-learning.svg)

## Sieci neuronowe (Neural Networks)
- **Sieć neuronowa** to model obliczeniowy inspirowany budową ludzkiego mózgu – składa się z warstw połączonych **neuronów** (węzłów), które przetwarzają dane wejściowe i uczą się rozpoznawać wzorce.
- Każdy neuron otrzymuje dane, mnoży je przez **wagi (weights)**, sumuje i przepuszcza przez **funkcję aktywacji** – wynik przekazuje dalej.
- Struktura sieci neuronowej:
	- **Warstwa wejściowa (Input Layer)** – przyjmuje dane (np. piksele obrazu, cechy liczbowe)
	- **Warstwy ukryte (Hidden Layers)** – przetwarzają dane, uczą się wzorców i zależności
	- **Warstwa wyjściowa (Output Layer)** – zwraca wynik (np. klasę, wartość liczbową)
- **Trening** sieci polega na podawaniu danych, porównywaniu wyników z oczekiwanymi i korygowaniu wag metodą **propagacji wstecznej (backpropagation)**.
- Im więcej warstw ukrytych, tym sieć potrafi uczyć się bardziej złożonych zależności – stąd termin **Deep Learning**.

![Sieć neuronowa – warstwy i połączenia](assets/neural-network.svg)

## Deep Learning
- **Deep Learning** – uczenie maszynowe z wykorzystaniem wielowarstwowych sieci neuronowych, szczególnie skuteczne w analizie obrazów i języka.

![Deep Learning](assets/deep-learning.svg)

## Transformers
- **Transformers** – nowoczesna architektura sieci neuronowych oparta na mechanizmie **uwagi (attention)**, który pozwala modelowi skupiać się na najważniejszych fragmentach danych wejściowych. Wykorzystywana m.in. w modelach językowych (np. **GPT**, **BERT**).

![Transformers](assets/transformers.svg)

## Cechy (Features) i etykiety (Labels)
- **Cechy (Features)** – zmienne wejściowe, na podstawie których model uczy się przewidywać wynik. Każda cecha opisuje jedną właściwość rekordu (np. metraż, liczba pokoi, lokalizacja).
- **Etykieta (Label)** – zmienna docelowa, którą model ma przewidzieć (np. cena mieszkania, klasa spam/nie-spam). W uczeniu nadzorowanym etykieta jest znana w danych treningowych.
- Przykład:

	| Metraż (feature) | Pokoje (feature) | Piętro (feature) | Cena (label) |
	|---|---|---|---|
	| 52 m² | 2 | 3 | 420 000 zł |
	| 75 m² | 3 | 1 | 610 000 zł |

- W **uczeniu nienadzorowanym** nie ma etykiet – model sam szuka wzorców w danych.

## Podział danych: zbiór treningowy, walidacyjny i testowy
- Dane dzielimy na trzy rozłączne zbiory, aby rzetelnie ocenić jakość modelu:
	- **Zbiór treningowy (Training set)** ~70–80% – model uczy się na tych danych, dostraja wagi i parametry.
	- **Zbiór walidacyjny (Validation set)** ~10–15% – służy do oceny modelu **w trakcie treningu**: porównywania wariantów, tuningu hiperparametrów i wykrywania overfittingu.
	- **Zbiór testowy (Test set)** ~10–15% – używany **tylko raz** na końcu, aby uzyskać obiektywną ocenę końcową modelu na danych, których nigdy nie widział.
- **Dlaczego dzielimy?** – gdyby model był oceniany na tych samych danych, na których się uczył, wyniki byłyby zawyżone (overfitting). Podział gwarantuje, że mierzymy rzeczywistą zdolność generalizacji.
- **Cross-validation (walidacja krzyżowa)** – technika wielokrotnego podziału danych, w której każdy fragment jest raz zbiorem walidacyjnym – daje bardziej stabilną ocenę.

## Kluczowe zadania ML
- **Regresja (Regression)** – przewidywanie wartości liczbowych (np. prognoza cen mieszkań, przewidywanie temperatury).
- **Klasyfikacja (Classification)** – przypisywanie do kategorii (np. wykrywanie spamu, rozpoznawanie gatunków zwierząt na zdjęciach).
- **Klasteryzacja (Clustering)** – grupowanie podobnych danych (np. segmentacja klientów sklepu, grupowanie artykułów prasowych).

## Overfitting i underfitting
- **Overfitting (przeuczenie)** – model zbyt dobrze dopasowany do danych treningowych, słabo generalizuje do nowych danych. Przykład: model zapamiętuje dane zamiast uczyć się ogólnych wzorców.
- **Underfitting (niedouczenie)** – model zbyt prosty, nie uczy się zależności w danych, osiąga niską skuteczność zarówno na danych treningowych, jak i testowych.

## Data Imbalance – klasy niezbalansowane

![Data Imbalance](assets/data-imbalance.svg)

- **Problem**: Zbiór danych ma nierówno rozłożone klasy (np. 95% negatywnych przykładów, 5% pozytywnych). Model uczy się faworyzować większość i osiąga wysoką Accuracy, ale źle radzi sobie z mniejszością.
  - Przykład: detekcja oszustw (99.95% transakcji legalne, 0.05% oszustwa) – model, który zawsze mówi „legalne”, będzie miał 99.95% Accuracy, ale nie złapie żadnego oszustwa.
- **Rozwiązania**:
  - **Class Weighting** – wagi wysoksze dla mniejszościowej klasy w funkcji strat
  - **Oversampling** – replikowanie przykładów mniejszości (SMOTE – Synthetic Minority Over-Sampling Technique)
  - **Undersampling** – zmniejszenie większości klasy
  - **Stratified Split** – dzielenie danych na trening/walidację/test z zachowaniem proporcji klas
  - **Wybór metryki** – zamiast Accuracy użyć F1-score, Recall lub Precision w zależności od scenariusza
- **Azure**: AutoML w Azure ML automatycznie wykrywa imbalance i stosuje Class Weighting, a w Designerze można konfigurować oversampling.

## A/B Testing – porównywanie modeli w produkcji

![A/B Testing – Traffic Split](assets/ab-testing.svg)

- **Co to jest**: Strategie wdrażania nowego modelu obok starego, gdzie część użytkowników otrzymuje stary model (A), część nowy (B). Porównuje się metryki biznesowe (CTR, konwersje, zadowolenie użytkownika).
- **Kroki**:
  1. Wytrenuj nowy model, oceń go na zbiorze testowym.
  2. Wdróż jako **Azure ML Managed Online Endpoint** z małym podziałem ruchu (np. 10%).
  3. Monitoruj metryki dla obu wersji (np. real-time latency, error rate, metryka biznesowa).
  4. Jeśli nowy model jest lepszy, stopniowo zwiększaj traffic (gradual rollout).
  5. Jeśli gorzej, wycofaj i powróć do starego modelu.
- **Typowe metryki**: CTR (click-through rate), conversion rate, user satisfaction, model latency, inference cost.
- **Azure**: Azure ML Endpoints obsługują traffic splitting i monitoring w real-time.

## Metryki oceny modeli

![Confusion Matrix – macierz pomyłek i metryki](assets/confusion-matrix.svg)

- **Accuracy (dokładność)** – odsetek poprawnych przewidywań. **Uwaga na egzaminie**: wysoka accuracy nie oznacza dobrego modelu przy niezbalansowanych danych!
- **Precision (precyzja)** – odsetek trafień wśród przewidzianych pozytywnych. Ważna gdy **fałszywy alarm jest kosztowny** (np. spam filter – nie chcesz usunąć ważnego maila).
- **Recall (czułość)** – odsetek wykrytych pozytywnych spośród wszystkich rzeczywistych. Ważna gdy **przeoczenie jest kosztowne** (np. wykrywanie raka – nie możesz przeoczyć chorego).
- **F1-score** – średnia harmoniczna precision i recall. Używaj gdy obie metryki są ważne.
- **Mean Square Error (MSE)** – średnia arytmetyczna kwadratów różnic między wartościami rzeczywistymi a przewidywanymi przez model. Im niższa wartość MSE, tym lepsze dopasowanie modelu regresyjnego.
- **Confusion Matrix (macierz pomyłek)** – tabela pokazująca liczbę poprawnych i błędnych klasyfikacji.
		- Przykład macierzy pomyłek:

	|                | Przewidziane: Pozytywne | Przewidziane: Negatywne |
	|----------------|------------------------|------------------------|
	| Rzeczywiste: Pozytywne | True Positive (TP)         | False Negative (FN)         |
	| Rzeczywiste: Negatywne | False Positive (FP)        | True Negative (TN)          |

	- **True Positive (TP)** – przypadki poprawnie zaklasyfikowane jako pozytywne
	- **False Positive (FP)** – przypadki błędnie zaklasyfikowane jako pozytywne (fałszywy alarm)
	- **True Negative (TN)** – przypadki poprawnie zaklasyfikowane jako negatywne
	- **False Negative (FN)** – przypadki błędnie zaklasyfikowane jako negatywne (przeoczenie)
- **ROC Curve, AUC** – krzywa ROC i pole pod krzywą, metryki oceny skuteczności klasyfikatorów. **AUC = 1.0** to idealny model, **AUC = 0.5** to losowy (bezwartościowy). Im wyższe AUC, tym lepiej model odróżnia klasy.

## Proces ML

![Proces ML – 8 kroków](assets/ml-process.svg)

1. **Zbieranie danych** – pozyskiwanie i przygotowanie danych do analizy.
2. **Podział danych** – na zbiory: treningowy, walidacyjny, testowy.
3. **Feature engineering** – wybór i przetwarzanie cech (features).
4. **Trening modelu** – uczenie modelu na danych treningowych.
5. **Walidacja** – ocena modelu na zbiorze walidacyjnym, tuning parametrów.
6. **Testowanie** – sprawdzenie skuteczności na nowych danych (zbiór testowy).
7. **Deployment** – wdrożenie modelu do produkcji (np. jako API).
8. **Monitorowanie** – śledzenie działania modelu i jego skuteczności w czasie.

**Dodatkowe pojęcia i praktyki:**
- **Drift** – zmiana rozkładu danych w czasie, która może pogorszyć skuteczność modelu
- **Data Imbalance** – nierównomierny rozkład klas w zbiorze danych
- **Transfer Learning** – wykorzystanie modelu wytrenowanego na innym zadaniu
- **Data Augmentation** – sztuczne zwiększanie liczby przykładów przez modyfikacje danych
- **Retraining** – ponowne trenowanie modelu na nowych danych
- **Monitoring** – śledzenie skuteczności i sprawiedliwości modeli po wdrożeniu
- **Interpretability** – możliwość zrozumienia, jak model podejmuje decyzje
- **Compliance** – zgodność z regulacjami prawnymi (np. RODO)
- **Fairness** – sprawiedliwość, równe traktowanie grup
- **Explainability** – wyjaśnialność decyzji modelu
- **Pipeline** – sekwencja kroków przetwarzania danych i trenowania modelu
- **Endpoint** – punkt dostępu do modelu przez API


## Cykl życia ML
![Cykl życia ML](assets/ml-lifecycle.svg)

## Usługi **Azure ML**
- **Azure Machine Learning** – platforma do trenowania, wdrażania i zarządzania modelami ML w chmurze Azure. Umożliwia:
	- Tworzenie eksperymentów ML (notebooki, pipeline’y)
	- Automatyzację procesu ML (AutoML)
	- Zarządzanie danymi i zasobami obliczeniowymi (Data/Compute)
	- Rejestrację i wersjonowanie modeli (**Model Registry**)
	- Wdrażanie modeli jako **endpointy** (API)
	- Monitorowanie i audyt modeli
- **Automated ML (AutoML)** – automatyczne trenowanie i wybór najlepszego modelu na podstawie danych:
	1. **Wskazujesz dane** – przesyłasz zbiór danych (CSV, Azure Blob, SQL)
	2. **Wybierasz typ zadania** – klasyfikacja, regresja lub prognozowanie szeregów czasowych
	3. **Wybierasz kolumnę docelową** (target column) – co model ma przewidywać
	4. **AutoML automatycznie**:
		- Testuje wiele algorytmów (np. LogisticRegression, XGBoost, LightGBM, RandomForest)
		- Przeprowadza **feature engineering** (normalizacja, kodowanie, imputacja braków)
		- Stosuje **cross-validation** (walidację krzyżową) do oceny modeli
		- Optymalizuje hiperparametry każdego algorytmu
	5. **Ranking modeli** – AutoML porównuje wyniki według wybranej metryki (Accuracy, AUC, RMSE itp.) i wskazuje **najlepszy model**
	6. **Wdrożenie** – najlepszy model można jednym kliknięciem wdrożyć jako **REST API endpoint**
- **Data/Compute** – zarządzanie danymi i mocą obliczeniową w chmurze.
- **Model Registry** – repozytorium do przechowywania i wersjonowania **własnych** wytrenowanych modeli ML (każdy model ma wersję, metadane, metryki)
- **Model Catalog (Azure AI Foundry)** – katalog gotowych, **pre-built** modeli do użycia od razu lub fine-tuningu:
	- **Modele OpenAI**: GPT-4, GPT-4o, GPT-4o-mini, GPT-3.5-Turbo, DALL-E 3, Whisper, text-embedding-ada-002
	- **Modele Meta**: Llama 3, Llama 2
	- **Modele Mistral**: Mistral Large, Mistral Small
	- **Modele Microsoft**: Phi-3, Phi-2 (małe, wydajne modele językowe)
	- **Modele Hugging Face**: tysiące modeli open-source (NLP – Natural Language Processing, Vision, Audio)
	- **Modele Cohere**: Command, Embed (generowanie, embeddingi)

[⟵ Poprzedni: Podstawy AI i rodzaje zadań](02-ai-workloads.md) | [Następny: Computer Vision ⟶](04-computer-vision.md)
