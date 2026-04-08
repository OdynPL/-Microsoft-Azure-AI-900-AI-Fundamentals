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

### **Podstawy AI i Machine Learning**

| **Pojęcie** | **Opis** |
|---|---|
| **AI (Artificial Intelligence)** | Sztuczna inteligencja, systemy naśladujące ludzkie zdolności poznawcze |
| **Narrow AI (Weak AI)** | Wąska AI, systemy zaprojektowane do jednego, konkretnego zadania (np. klasyfikacja obrazów, chatbot) |
| **Strong AI (AGI)** | Silna AI, hipotetyczna sztuczna inteligencja o ogólnych zdolnościach poznawczych porównywalnych do człowieka |
| **ML (Machine Learning)** | Uczenie maszynowe, algorytmy uczące się na podstawie danych |
| **Deep Learning** | Głębokie sieci neuronowe |
| **Neural Network (sieć neuronowa)** | Model ML inspirowany mózgiem, złożony z warstw neuronów przetwarzających dane |
| **Supervised Learning** | Uczenie nadzorowane (dane z etykietami) |
| **Unsupervised Learning** | Uczenie nienadzorowane (grupowanie bez etykiet) |
| **Reinforcement Learning** | Uczenie ze wzmocnieniem (nagrody i kary) |
| **Weights (wagi)** | Parametry modelu neuronowego aktualizowane podczas treningu; definiują siłę połączeń między neuronami |
| **Activation Function** | Funkcja aktywacji w neuronach (ReLU, Sigmoid, Tanh) wprowadzająca nieliniowość do modelu |
| **Parameters (parametry modelu)** | Całkowita liczba wag i bias'ów w modelu (np. GPT-4 ma setki miliardów parametrów) |

### **Architektura Transformer i modele językowe**

| **Pojęcie** | **Opis** |
|---|---|
| **Transformer** | Nowoczesna architektura sieci neuronowej (podstawa GPT, BERT); korzysta z mechanizmu self-attention |
| **Self-Attention** | Mechanizm pozwalający modelowi oceniać ważność każdego tokenu w kontekście pozostałych |
| **Positional Encoding** | Kodowanie pozycji tokenu w sekwencji; pozwala Transformerowi rozumieć kolejność słów |
| **Encoder / Decoder** | Komponenty Transformer: encoder przetwarza wejście (np. BERT), decoder generuje wyjście (np. GPT) |
| **LLM (Large Language Model)** | Duży model językowy (np. GPT-4) trenowany na ogromnych zbiorach tekstu |
| **Foundation Model** | Duży, wstępnie wytrenowany model AI, który można adaptować do wielu zadań (np. GPT, BERT, DALL-E) |
| **SLM (Small Language Model)** | Mały model językowy (np. Microsoft Phi-3) – mniej parametrów, szybszy, tańszy, idealny do urządzeń edge |
| **Multi-Head Attention** | Wiele równoległych mechanizmów attention w Transformer; każdy uczy się innych zależności między tokenami |
| **RNN / LSTM** | Recurrent Neural Networks / Long Short-Term Memory – starsze architektury sekwencyjne, poprzedniki Transformera |
| **BERT** | Bidirectional Encoder Representations from Transformers – model encoder do analizy tekstu (NER, sentyment, Q&A) |
| **GPT** | Generative Pre-trained Transformer – model decoder do generowania tekstu (chatboty, treści, kod) |

### **Zadania ML i typy problemów**

| **Pojęcie** | **Opis** |
|---|---|
| **Regresja (Regression)** | Przewidywanie wartości liczbowych |
| **Rodzaje regresji** | 1. **Linear Regression** – prosta liniowa <br> 2. **Multiple Linear Regression** – wiele cech <br> 3. **Polynomial Regression** – krzywa <br> 4. **Decision Tree / Random Forest Regression** – drzewa decyzyjne <br> 5. **Neural Network Regression** – sieci neuronowe <br> Metryki: R², MAE, RMSE |
| **Klasyfikacja (Classification)** | Przypisywanie do kategorii |
| **Klasteryzacja (Clustering)** | Grupowanie podobnych danych (uczenie nienadzorowane) |
| **Anomaly Detection** | Wykrywanie obserwacji odbiegających od normy (np. oszustwa, defekty, awarie) |
| **Recommendation Systems** | Systemy rekomendacji przewidujące preferencje użytkownika (Collaborative Filtering, Content-Based, Hybrid) |
| **Collaborative Filtering** | Rekomendacje bazujące na podobieństwie użytkowników: „użytkownicy podobni do ciebie polubili…" |
| **Content-Based Filtering** | Rekomendacje porównujące cechy produktów: „produkty podobne do tych, które lubisz" |
| **Time Series Forecasting** | Prognozowanie wartości w czasie (sprzedaż, temperatura); obsługiwane przez AutoML |
| **One-class SVM** | Algorytm anomaly detection: uczy się granic normalnych danych, identyfikuje obserwacje poza nimi |
| **Isolation Forest** | Algorytm anomaly detection oparty na losowych podziałach; anomalie łatwiejsze do izolacji |

### **Dane, cechy i trening modelu**

| **Pojęcie** | **Opis** |
|---|---|
| **Feature (cecha)** | Pojedyncza właściwość lub atrybut wykorzystywany przez model ML do nauki (np. wiek, płeć, liczba transakcji) |
| **Label (etykieta)** | Prawidłowa odpowiedź przypisana do przykładu w uczeniu nadzorowanym (np. spam/nie-spam) |
| **Feature Engineering** | Przygotowanie i wybór cech |
| **Data Labeling** | Etykietowanie danych |
| **Training Set** | Zbiór danych do trenowania modelu (~70–80% danych) |
| **Validation Set** | Zbiór do oceny modelu podczas treningu i doboru hiperparametrów (~10–15%) |
| **Test Set** | Zbiór do końcowej, niezależnej oceny modelu (~10–15%) |
| **Data Imbalance** | Nierównomierny rozkład klas w zbiorze danych (np. 95% klasy A, 5% klasy B) |
| **Class Weighting** | Przypisanie wyższych wag mniejszościowej klasie, by model lepiej ją rozpoznawał |
| **SMOTE** | Synthetic Minority Over-Sampling Technique – syntetyczne generowanie przykładów klasy mniejszościowej |
| **Stratified Split** | Podział danych z zachowaniem proporcji klas w każdym zbiorze |
| **Data Augmentation** | Sztuczne zwiększanie liczby przykładów przez modyfikacje danych (np. obrót obrazu, synonimy) |
| **Normalization** | Skalowanie wartości cech do wspólnego zakresu (np. 0–1); ważne dla algorytmów opartych na odległościach |
| **One-hot Encoding** | Zamiana kategorii na wektory binarne (np. kolor: czerwony → [1,0,0], zielony → [0,1,0]) |

### **Proces trenowania i optymalizacja**

| **Pojęcie** | **Opis** |
|---|---|
| **Inference (wnioskowanie)** | Użycie wytrenowanego modelu do generowania predykcji na nowych danych |
| **Hyperparameter (hiperparametr)** | Parametr ustawiany przed treningiem (np. learning rate, liczba epok), w odróżnieniu od wag uczonych automatycznie |
| **Epoch (epoka)** | Jedno pełne przejście przez cały zbiór treningowy podczas trenowania modelu |
| **Loss Function (funkcja straty)** | Miara błędu modelu; cel treningu to jej minimalizacja |
| **Gradient Descent** | Algorytm optymalizacji minimalizujący funkcję straty poprzez iteracyjne dopasowywanie wag |
| **Backpropagation** | Mechanizm propagacji błędu wstecz w sieci neuronowej, do obliczania gradientów i aktualizacji wag |
| **Regularization** | Techniki zapobiegające overfittingowi (np. L1, L2, Dropout) |
| **Overfitting / Underfitting** | Przeuczenie (zbyt dobre dopasowanie do treningu) / niedouczenie (zbyt proste wzorce) |
| **Transfer Learning** | Wykorzystanie modelu wytrenowanego na jednym zadaniu do przyspieszenia nauki na innym |
| **Cross-Validation (K-fold)** | Wielokrotny podział danych na k zbiorów; każdy pełni rolę testu raz – bardziej stabilna ocena modelu |
| **Inference Pipeline** | Pipeline wnioskowania utworzony z training pipeline; wymagany przed wdrożeniem modelu do produkcji |
| **Pipeline ML** | Sekwencja kroków przetwarzania danych i trenowania modelu |

### **Metryki oceny modeli**

| **Pojęcie** | **Opis** |
|---|---|
| **True Positive (TP)** | Przypadek poprawnie zaklasyfikowany jako pozytywny |
| **False Positive (FP)** | Przypadek błędnie zaklasyfikowany jako pozytywny (fałszywy alarm) |
| **True Negative (TN)** | Przypadek poprawnie zaklasyfikowany jako negatywny |
| **False Negative (FN)** | Przypadek błędnie zaklasyfikowany jako negatywny (przeoczenie) |
| **Accuracy** | Dokładność – odsetek poprawnych przewidywań |
| **Precision** | Precyzja – odsetek trafień wśród przewidzianych pozytywnych |
| **Recall** | Czułość – odsetek wykrytych pozytywnych |
| **F1-score** | Średnia harmoniczna Precision i Recall |
| **Confusion Matrix** | Macierz pomyłek – tabela TP/FP/TN/FN |
| **ROC Curve, AUC** | Krzywa ROC i pole pod krzywą – ocena klasyfikatora binarnego |
| **MSE (Mean Square Error)** | Średnia kwadratów różnic między wartościami rzeczywistymi a przewidywanymi |
| **R² (R-Squared)** | Współczynnik determinacji; metryka regresji od 0 do 1 (1.0 = model idealny) |
| **MAE (Mean Absolute Error)** | Średnia wartość bezwzględna błędów predykcji |
| **RMSE (Root Mean Square Error)** | Pierwiastek z MSE; metryka w tych samych jednostkach co zmienna docelowa |

### **Computer Vision**

| **Pojęcie** | **Opis** |
|---|---|
| **Computer Vision** | Analiza i interpretacja obrazów/wideo |
| **Image Classification** | Klasyfikacja obrazów – co jest na obrazie |
| **Object Detection** | Detekcja obiektów – klasa + prawdopodobieństwo + bounding box |
| **Bounding Box** | Prostokąt otaczający wykryty obiekt na obrazie (x, y, szerokość, wysokość) |
| **OCR (Optical Character Recognition)** | Rozpoznawanie tekstu na obrazach |
| **Semantic Segmentation** | Klasyfikacja każdego piksela obrazu do kategorii (np. droga, budynek, niebo) |
| **Face Recognition** | Rozpoznawanie twarzy |
| **Face Liveness Detection** | Wykrywanie żywej osoby (ochrona przed atakami zdjęciowymi / deepfake) – Limited Access |
| **PersonGroup** | Grupa osób w Face API z wieloma zdjęciami; wymagana do Face Identification |
| **Limited Access Policy** | Niektóre funkcje AI (identyfikacja twarzy) wymagają formalnej zgody Microsoft |
| **Read API** | API Azure Vision do odczytu tekstu z dużych, wielostronicowych PDF (vs OCR API dla prostych obrazów) |
| **Spatial Analysis** | Śledzenie ruchu osób, liczenie w strefach, mierzenie dystansów w wideo real-time – Azure Vision |

### **NLP (Natural Language Processing)**

| **Pojęcie** | **Opis** |
|---|---|
| **NLP** | Przetwarzanie języka naturalnego |
| **Tokenizacja (Tokenization)** | Dzielenie tekstu na słowa/elementy |
| **Lematyzacja (Lemmatization)** | Sprowadzanie słów do formy podstawowej |
| **Stemming** | Obcinanie końcówek słów do rdzenia; normalizacja tekstu przed analizą częstości |
| **Embeddingi (Embeddings)** | Reprezentacja tekstu w postaci wektorów liczbowych |
| **Entity Recognition (NER)** | Rozpoznawanie encji nazwanych (osoby, miejsca, organizacje, daty) |
| **Entity Linking** | Identyfikacja encji + powiązanie z bazą wiedzy (np. Wikipedia); różni się od NER linkami |
| **PII Detection** | Automatyczne wykrywanie i maskowanie danych osobowych (PESEL, email, nr karty) |
| **Sentiment Analysis** | Analiza sentymentu (pozytywny, negatywny, neutralny, mieszany) |
| **Key Phrase Extraction** | Wyodrębnianie najważniejszych fraz i słów kluczowych z tekstu |
| **Summarization** | Automatyczne streszczanie długich dokumentów lub transkrypcji rozmów |
| **Language Detection** | Automatyczne rozpoznawanie języka tekstu |
| **Intent Recognition** | Rozpoznawanie intencji użytkownika (np. w chatbocie) |
| **CLU** | Conversational Language Understanding – następca LUIS; rozpoznawanie intencji i encji |
| **Question Answering** | Usługa tworzenia baz wiedzy Q&A z dokumentów, FAQ i stron internetowych |
| **Speech Recognition** | Rozpoznawanie mowy (Speech-to-Text) |
| **Speech Synthesis** | Synteza mowy z tekstu (Text-to-Speech) |
| **Speech Translation** | Tłumaczenie mowy w czasie rzeczywistym: speech-to-text + translation + text-to-speech |
| **Speaker Recognition** | Identyfikacja/weryfikacja osoby na podstawie głosu (kto mówi, nie co mówi) |
| **Custom Speech** | Dostosowanie modelu STT do własnego słownictwa, akcentu lub domeny (np. medyczna) |
| **Custom Voice** | Tworzenie spersonalizowanego, syntetycznego głosu TTS |
| **Custom Translator** | Dostosowanie modelu tłumaczenia do specjalistycznego słownictwa (prawo, medycyna) |
| **Transliteration** | Zmiana alfabetu bez tłumaczenia (np. arabski → łaciński); Azure Translator, ~20 języków |
| **Batch Transcription** | Masowa, asynchroniczna transkrypcja dużych zbiorów nagrań audio – Azure Speech |

### **Generatywna AI**

| **Pojęcie** | **Opis** |
|---|---|
| **Generative AI** | Generatywna AI – tworzenie nowych treści: tekst, obrazy, kod, muzyka |
| **Multimodal Models** | Modele przetwarzające jednocześnie tekst, obraz i audio (np. GPT-4o) |
| **Prompt** | Polecenie lub zapytanie przekazywane do modelu generatywnego |
| **Token** | Najmniejsza jednostka tekstu przetwarzana przez model językowy (~¾ słowa) |
| **Prompt Engineering** | Tworzenie skutecznych poleceń dla modeli generatywnych |
| **Zero-shot learning** | Model radzi sobie z zadaniem, którego nie widział podczas treningu |
| **Few-shot learning** | Model uczy się na bardzo małej liczbie przykładów (1–5 w promptie) |
| **Chain-of-Thought** | Technika zachęcająca model do wypisania kroków rozumowania (poprawia dokładność) |
| **System Message** | Instrukcja na początku sesji definiująca rolę, ton i ograniczenia modelu |
| **Temperature** | Parametr losowości: 0 = deterministyczny, 1+ = kreatywny |
| **Top-p (Nucleus Sampling)** | Alternatywny parametr kontrolujący różnorodność odpowiedzi |
| **Context Window** | Maksymalna liczba tokenów przetwarzana jednorazowo przez model (np. 128k dla GPT-4o) |
| **Fine-tuning** | Dodatkowe trenowanie pre-trenowanego modelu na własnych danych |
| **RAG** | Retrieval Augmented Generation – łączy LLM z zewnętrznymi źródłami wiedzy; redukuje halucynacje |
| **Grounding (zakotwiczenie)** | Powiązanie odpowiedzi modelu z konkretnymi, zweryfikowanymi dokumentami |
| **Hallucinations** | Generowanie nieprawdziwych informacji przez model |
| **Content Filters** | Mechanizmy Azure OpenAI blokujące szkodliwe treści (przemoc, mowa nienawiści) |
| **Prompt Injection** | Atak polegający na wstrzyknięciu złośliwych instrukcji w danych wejściowych |
| **XPIA** | Cross-Prompt Injection Attacks – atak przez wstrzyknięcie instrukcji w jedno ze źródeł RAG agenta |
| **Hybrid Search** | Kombinacja vector search (semantyka) + keyword search (dokładne słowa) – lepsze wyniki niż każde osobno |
| **Vector Store** | Baza danych przechowująca embeddingi; Azure AI Search pełni rolę vector store dla RAG |
| **Chunking** | Dzielenie dużych dokumentów na mniejsze fragmenty przed osadzeniem w embeddings; kluczowe dla RAG |
| **Integrated Vectorization** | Automatyczne konwertowanie dokumentów na embeddingi w Azure AI Search |

### **Responsible AI i etyka**

| **Pojęcie** | **Opis** |
|---|---|
| **Responsible AI** | Etyczne i bezpieczne wdrażanie AI |
| **Fairness** | Sprawiedliwość, równe traktowanie grup |
| **Bias** | Tendencyjność modelu wynikająca z danych |
| **Explainability** | Wyjaśnialność decyzji modelu |
| **Interpretability** | Możliwość zrozumienia, jak model podejmuje decyzje |
| **Compliance** | Zgodność z regulacjami (np. RODO/GDPR) |
| **Data Privacy** | Ochrona prywatności i bezpieczeństwa danych |
| **SHAP** | SHapley Additive exPlanations – technika pokazująca wpływ każdej cechy na predykcję modelu |
| **LIME** | Local Interpretable Model-agnostic Explanations – lokalne wyjaśnienia decyzji modelu |
| **Feature Importance** | Ranking cech wg wpływu na wynik modelu; obliczany przez SHAP/LIME |
| **Fairlearn** | Open-source narzędzie do pomiaru i poprawy sprawiedliwości modeli; w Azure ML RAI Dashboard |
| **Error Analysis** | Analiza błędów modelu pogrupowana wg cech/podgrup; diagnoza biasu – Azure ML RAI Dashboard |
| **Causal Analysis** | Analiza przyczynowości: „czy zmiana X powoduje zmianę Y?" (nie tylko korelacja) |
| **Counterfactual** | Kontrfaktyczne przykłady: „jak zmieniłby się wynik, gdyby…" – wyjaśnienie alternatywnych scenariuszy |

### **Cykl życia modelu i MLOps**

| **Pojęcie** | **Opis** |
|---|---|
| **Model Deployment** | Wdrożenie modelu do środowiska produkcyjnego |
| **Model Registry** | Repozytorium modeli z wersjonowaniem, metadanymi i metrykami |
| **Endpoint** | Punkt dostępu do wdrożonego modelu przez REST API (Online = real-time, Batch = wsadowy) |
| **Monitoring** | Śledzenie skuteczności i działania modelu po wdrożeniu |
| **Drift** | Zmiana rozkładu danych wejściowych/wyjściowych w czasie, pogarszająca skuteczność modelu |
| **Data Drift** | Zmiana rozkładu danych wejściowych w produkcji – najpowszechniejszy typ driftu na egzaminie |
| **Model Drift** | Pogorszenie metryki predykcyjnej (accuracy, precision) na nowych danych |
| **Prediction Drift** | Nagła zmiana przewidywań modelu bez zmian w danych wejściowych |
| **Retraining** | Ponowne trenowanie modelu na nowych danych |
| **Traffic Split (A/B Test)** | Podział ruchu użytkowników między model A i B; stopniowy rollout (10% → 50% → 100%) |
| **MLOps** | Praktyki DevOps dla modeli ML: CI/CD, wersjonowanie, monitoring, automatyczny retraining |
| **Audit Trail** | Pełna historia: kto trenował model, kiedy, z jakimi danymi, jakie wyniki – compliance |

### **Narzędzia i usługi Azure**

| **Pojęcie** | **Opis** |
|---|---|
| **Azure AI Services** | Rodzina gotowych usług AI na platformie Azure (Vision, Language, Speech, Face i inne) |
| **AutoML (Automated ML)** | Automatyczny dobór algorytmu i hiperparametrów (klasyfikacja, regresja, time series; NIE clustering) |
| **Designer** | Graficzny interfejs drag & drop w Azure ML do budowy pipeline'ów ML bez kodu |
| **Azure AI Translator** | Osobna usługa do tłumaczeń maszynowych tekstu (100+ języków) |
| **Azure AI Document Intelligence** | Ekstrakcja danych z formularzy, faktur, dokumentów (dawniej Form Recognizer) |
| **Azure AI Content Safety** | Filtrowanie szkodliwych treści: mowy nienawiści, przemocy, treści seksualnych |
| **Azure AI Search** | Wektorowa baza danych i platforma wyszukiwania (indexer, index, skillset); kluczowa dla RAG |
| **Custom Vision** | Trenowanie własnych modeli klasyfikacji/detekcji obrazów bez kodu |
| **Azure Bot Service** | Usługa do budowy chatbotów; jeden bot obsługuje wiele kanałów (Web Chat, Teams, Facebook) |
| **Copilot Studio** | Platforma no-code do budowy chatbotów i agentów AI (dawniej Power Virtual Agents) |
| **AI Builder** | Narzędzia AI w Power Platform dla użytkowników biznesowych |
| **Knowledge Mining** | Wydobywanie wiedzy z niestrukturyzowanych danych za pomocą AI (OCR, NLP, wzbogacanie) |
| **Vector Search** | Wyszukiwanie na bazie podobieństwa embeddingów (semantyczne, nie słowa kluczowe) |
| **AI Agents** | Aplikacje AI z LLM, instrukcjami i narzędziami, działające autonomicznie (3 typy: Prompt, Workflow, Hosted) |
| **RBAC** | Role-Based Access Control – kontrola dostępu do zasobów Azure (właściciel, współpracownik, czytelnik) |
| **Data Assets** | Zarządzanie danymi w Azure ML: rejestracja, wersjonowanie i udostępnianie zbiorów danych zespołom |
| **Compute Cluster** | Skalowalne klastry obliczeniowe w Azure ML do trenowania modeli |
| **Feature Store** | Centralne repozytorium cech ML do ponownego wykorzystania między projektami |
| **Prompt Flow** | Narzędzie w Azure AI Foundry do orkiestracji pipeline'ów AI, RAG i wielostopniowych aplikacji |
| **Model Catalog** | Centralna baza modeli w Foundry: GPT, Phi, Llama, Mistral – przeglądanie, ewaluacja, wdrażanie |

### **Moduły Azure ML Designer (egzamin!)**

| **Pojęcie** | **Opis** |
|---|---|
| **Split Data** | Dzieli dane na zbiory treningowe i testowe; wymagany przed Score/Evaluate |
| **Normalize Data** | Skaluje kolumny numeryczne do wspólnego zakresu (Min-Max, Z-score) |
| **Clean Missing Data** | Obsługa brakujących wartości (usunięcie wierszy, średnia, mediana) |
| **Select Columns in Dataset** | Wybór konkretnych kolumn z zestawu danych do dalszego przetwarzania |
| **Train Model** | Trenowanie modelu na danych treningowych (logistic regression, decision tree itp.) |
| **Train Clustering Model** | Trenowanie modelu klasteryzacji (K-Means); oddzielny od Train Model |
| **Score Model** | Predykcja modelu na danych testowych; zwraca przewidywania |
| **Evaluate Model** | Ocena modelu (Confusion Matrix, metryki); zasilany wyjściem Score Model |
| **Assign Data to Clusters** | Przypisanie nowych danych do klastrów K-Means; do inferencing klasteryzacji (NIE Score Model!) |

### **Komponenty Azure AI Search**

| **Pojęcie** | **Opis** |
|---|---|
| **Indexer** | Eksportuje dokumenty źródłowe do JSON i wstawia je do indeksu wyszukiwania |
| **Index** | Struktura przechowująca wyszukiwalne dane; zawiera pola z atrybutami (searchable, filterable) |
| **Skillset** | Opcjonalny pipeline AI enrichment: OCR, NER, key phrase extraction, language detection |
| **Knowledge Store** | Miejsce w Azure Storage do przechowywania wzbogaconych wyników AI (tabele, blob) |

### **Agenci AI – szczegóły**

| **Pojęcie** | **Opis** |
|---|---|
| **Prompt Agents** | Typ agenta: bez kodu, instrukcje + tools – szybkie prototypowanie w portalu Foundry |
| **Workflow Agents** | Typ agenta: orkiestracja w YAML; wielokrokowe procesy, decyzje logiczne |
| **Hosted Agents** | Typ agenta: kod-based (Agent Framework, LangGraph); pełna kontrola nad logiką |
| **Agent Tools** | Narzędzia agentów: web search, file search, memory, code interpreter, custom API |
| **MCP (Model Context Protocol)** | Standard integracji narzędzi z agentami – unified interface dla tool discovery i execution |
| **Agent Lifecycle** | Create → Test → Trace → Evaluate → Publish → Monitor |
| **Foundry IQ** | Knowledge base dla agentów; integracja z Azure AI Search (vector store) |
| **Guardrails** | Mechanizmy bezpieczeństwa agentów: content filters, prompt injection defense, output validation |

### **Metryki ewaluacji GenAI i agentów**

| **Pojęcie** | **Opis** |
|---|---|
| **Coherence** | Czy odpowiedź jest spójna i logiczna |
| **Fluency** | Czy odpowiedź brzmi naturalnie i poprawnie językowo |
| **Relevance** | Czy odpowiedź odnosi się do pytania |
| **Groundedness** | Czy odpowiedź jest oparta na dostarczonych źródłach/dokumentach (nie zmyślona) |

## Zakres egzaminu
- Podstawy **AI** i **ML**
- **Computer Vision**
- **Natural Language Processing (NLP)**
- **Generatywna AI**
- **Responsible AI**

---


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)
