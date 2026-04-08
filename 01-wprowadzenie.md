[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)


# 1. Wprowadzenie i profil egzaminu AI-900


**Azure AI Fundamentals (AI-900)** to certyfikat potwierdzający znajomość podstawowych pojęć **AI**, **ML** oraz usług **AI** na platformie **Azure**.

## Usługi Azure AI – przegląd

Platforma **Microsoft Azure** oferuje szeroki zestaw gotowych usług AI, które pozwalają szybko wdrażać rozwiązania sztucznej inteligencji bez konieczności budowania modeli od zera:

- **Azure AI Vision** – analiza obrazów i wideo, klasyfikacja, detekcja obiektów, OCR, rozpoznawanie twarzy.
- **Azure AI Face** – rozpoznawanie i analiza twarzy (np. identyfikacja, emocje).
- **Azure AI Language** – przetwarzanie języka naturalnego: analiza tekstu, ekstrakcja kluczowych fraz, rozpoznawanie encji, analiza sentymentu, tłumaczenia.
- **Azure AI Speech** – rozpoznawanie i synteza mowy, zamiana tekstu na mowę i odwrotnie.
- **Azure OpenAI** – dostęp do zaawansowanych modeli generatywnych (np. GPT, DALL-E) do generowania tekstu, obrazów, kodu.
- **Azure AI Foundry** – katalog modeli AI, zarządzanie i wdrażanie modeli, integracja z innymi usługami.
- **Azure Machine Learning** – platforma do trenowania, wdrażania i zarządzania własnymi modelami ML, automatyzacja procesów ML (AutoML), rejestr modeli, endpointy.

Każda z tych usług posiada gotowe API, które można łatwo zintegrować z aplikacjami biznesowymi, stronami internetowymi czy chatbotami. Usługi te są szeroko wykorzystywane w zadaniach takich jak: rozpoznawanie obrazów, analiza tekstu, automatyzacja obsługi klienta, generowanie treści, digitalizacja dokumentów czy monitorowanie bezpieczeństwa.

## Azure AI Services - co warto wiedzieć

**Azure AI Services** (historycznie: Cognitive Services) to rodzina gotowych modeli AI udostępnianych jako usługi chmurowe przez REST API i SDK. Z perspektywy egzaminu AI-900 najważniejsze jest rozumienie, kiedy wybrać gotową usługę AI Services, a kiedy budować model samodzielnie w Azure Machine Learning.

### Jak to działa w praktyce
- Tworzysz zasób w Azure (portal/CLI/Bicep/Terraform).
- Otrzymujesz **endpoint** i sposób autoryzacji (klucz API lub Entra ID).
- Aplikacja wysyła dane do endpointu (tekst, obraz, audio, prompt).
- Usługa zwraca wynik inferencji (np. sentyment, transkrypcja, tagi obrazu, odpowiedź modelu).

### Typy zasobów
- **Single-service resource** - zasób dla jednej usługi (np. sam Language lub sam Speech).
- **Multi-service resource** - jeden wspólny zasób dla wielu usług AI Services.
- **Azure OpenAI resource** - osobny typ zasobu dla modeli OpenAI wdrażanych na Azure.

### Kiedy Azure AI Services, a kiedy Azure Machine Learning?
- **Azure AI Services**: gdy chcesz szybko wdrożyć gotowe AI bez trenowania modelu od zera.
- **Azure Machine Learning**: gdy potrzebujesz pełnej kontroli nad danymi, treningiem, eksperymentami i MLOps (Machine Learning Operations).

### Bezpieczeństwo i zgodność
- Uwierzytelnianie: klucze API lub Microsoft Entra ID (rekomendowane w środowisku produkcyjnym).
- Kontrola dostępu: RBAC, Managed Identity, Private Endpoints, VNet.
- Ochrona danych i zgodność: wsparcie dla standardów korporacyjnych i regulacji (np. RODO/GDPR).
- Dla GenAI: filtry treści, logowanie, monitorowanie i praktyki Responsible AI.

### Koszty i skalowanie
- Rozliczanie przeważnie za liczbę żądań, tokeny, sekundy audio lub strony dokumentów.
- Różne warstwy cenowe (tiers), limity i throughput zależne od usługi i regionu.
- Skalowanie odbywa się po stronie platformy - aplikacja korzysta z gotowego endpointu.

### Typowe scenariusze biznesowe
- **Contact center**: Speech-to-Text + Sentiment + podsumowanie rozmów.
- **Digitalizacja dokumentów**: OCR + Document Intelligence + walidacja danych.
- **Moderacja treści**: Vision/Language + Azure AI Content Safety.
- **Asystent firmowy**: Azure OpenAI + RAG (np. Azure AI Search) + polityki Responsible AI.

## Najważniejsze pojęcia AI na egzaminie

- **AI (Artificial Intelligence)** – sztuczna inteligencja, systemy naśladujące ludzkie zdolności poznawcze
- **Narrow AI (Weak AI)** – wąska AI, systemy zaprojektowane do jednego, konkretnego zadania (np. klasyfikacja obrazów, chatbot)
- **Strong AI (AGI)** – silna AI, hipotetyczna sztuczna inteligencja o ogólnych zdolnościach poznawczych porównywalnych do człowieka
- **ML (Machine Learning)** – uczenie maszynowe, algorytmy uczące się na podstawie danych
- **Deep Learning** – głębokie sieci neuronowe
- **Supervised Learning** – uczenie nadzorowane (dane z etykietami)
- **Unsupervised Learning** – uczenie nienadzorowane (grupowanie bez etykiet)
- **Reinforcement Learning** – uczenie ze wzmocnieniem (nagrody i kary)
- **Feature Engineering** – przygotowanie i wybór cech
- **Data Labeling** – etykietowanie danych
- **Regresja (Regression)** – przewidywanie wartości liczbowych
- **Klasyfikacja (Classification)** – przypisywanie do kategorii
- **Klasteryzacja (Clustering)** – grupowanie podobnych danych
- **Feature (cecha)** – pojedyncza właściwość lub atrybut wykorzystywany przez model ML do nauki (np. wiek, płeć, liczba transakcji)
- **Label (etykieta)** – prawidłowa odpowiedź przypisana do przykładu w uczeniu nadzorowanym (np. kategoria: spam/nie-spam)
- **True Positive (TP)** – przypadek poprawnie zaklasyfikowany jako pozytywny
- **False Positive (FP)** – przypadek błędnie zaklasyfikowany jako pozytywny (fałszywy alarm)
- **True Negative (TN)** – przypadek poprawnie zaklasyfikowany jako negatywny
- **False Negative (FN)** – przypadek błędnie zaklasyfikowany jako negatywny (przeoczenie)
- **Mean Square Error (MSE)** – średnia arytmetyczna kwadratów różnic między wartościami rzeczywistymi a przewidywanymi przez model
- **Prompt** – polecenie lub zapytanie przekazywane do modelu generatywnego
- **Token** – najmniejsza jednostka tekstu przetwarzana przez model językowy (np. słowo, znak)
- **Drift** – zmiana rozkładu danych wejściowych lub wyjściowych w czasie, która może pogorszyć skuteczność modelu
- **Data Imbalance** – nierównomierny rozkład klas w zbiorze danych (np. 95% klasy A, 5% klasy B)
- **Transfer Learning** – wykorzystanie modelu wytrenowanego na jednym zadaniu do przyspieszenia nauki na innym, pokrewnym zadaniu
- **Zero-shot learning** – model radzi sobie z zadaniem, którego nie widział podczas treningu
- **Few-shot learning** – model uczy się na bardzo małej liczbie przykładów
- **Data Augmentation** – sztuczne zwiększanie liczby przykładów przez modyfikacje danych (np. obrót obrazu, synonimy w tekście)
- **Model Deployment** – wdrożenie modelu do środowiska produkcyjnego
- **Monitoring** – śledzenie skuteczności i działania modelu po wdrożeniu
- **Retraining** – ponowne trenowanie modelu na nowych danych
- **Data Privacy** – ochrona prywatności i bezpieczeństwa danych
- **Interpretability** – możliwość zrozumienia, jak model podejmuje decyzje
- **Pipeline ML** – sekwencja kroków przetwarzania danych i trenowania modelu
- **Overfitting/Underfitting** – przeuczenie/niedouczenie modelu
- **Accuracy, Precision, Recall, F1-score** – metryki oceny modeli
- **Confusion Matrix** – macierz pomyłek
- **ROC Curve, AUC** – krzywa ROC, pole pod krzywą
- **Computer Vision** – analiza i interpretacja obrazów/wideo
- **OCR (Optical Character Recognition)** – rozpoznawanie tekstu na obrazach
- **Image Classification** – klasyfikacja obrazów
- **Object Detection** – detekcja obiektów
- **Face Recognition** – rozpoznawanie twarzy
- **NLP (Natural Language Processing)** – przetwarzanie języka naturalnego
- **Tokenizacja (Tokenization)** – dzielenie tekstu na słowa/elementy
- **Lematyzacja (Lemmatization)** – sprowadzanie słów do formy podstawowej
- **Embeddingi (Embeddings)** – reprezentacja tekstu w postaci wektorów
- **Entity Recognition** – rozpoznawanie encji
- **Sentiment Analysis** – analiza sentymentu
- **Intent Recognition** – rozpoznawanie intencji
- **Speech Recognition** – rozpoznawanie mowy
- **Generative AI** – generatywna AI (tworzenie nowych treści)
- **Prompt Engineering** – tworzenie skutecznych poleceń dla modeli generatywnych
- **Hallucinations** – generowanie nieprawdziwych informacji przez model
- **Responsible AI** – etyczne i bezpieczne wdrażanie AI
- **Bias** – tendencyjność modelu wynikająca z danych
- **Explainability** – wyjaśnialność decyzji modelu
- **Fairness** – sprawiedliwość, równe traktowanie grup
- **Compliance** – zgodność z regulacjami
- **Model Registry** – repozytorium modeli
- **Endpoint** – punkt dostępu do modelu przez API
- **Azure AI Services** – gotowe usługi AI na platformie Azure

## Zakres egzaminu
- Podstawy **AI** i **ML**
- **Computer Vision**
- **Natural Language Processing (NLP)**
- **Generatywna AI**
- **Responsible AI**

---


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)
