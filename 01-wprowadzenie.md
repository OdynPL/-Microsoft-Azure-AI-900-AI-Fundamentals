[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)


# 1. Wprowadzenie i profil egzaminu AI-900


**Azure AI Fundamentals (AI-900)** to certyfikat potwierdzający znajomość podstawowych pojęć **AI**, **ML** oraz usług **AI** na platformie **Azure**.

## Usługi Azure AI – przegląd

Platforma **Microsoft Azure** oferuje szeroki zestaw gotowych usług AI, które pozwalają szybko wdrażać rozwiązania sztucznej inteligencji bez konieczności budowania modeli od zera:

| **Usługa** | **Opis** |
|---|---|
| **Azure AI Vision** | Analiza obrazów i wideo, klasyfikacja, detekcja obiektów, OCR, rozpoznawanie twarzy |
| | ![Architektura Azure AI Vision](assets/arch-ai-vision.svg) |
| | Komunikacja: REST API, Python/C#/.NET SDK, Azure Portal <br> Limity: 20 TPS (transakcji/s) w warstwie Free, 10 TPS w S1 per region <br> Koszty: Free (20 wywołań/min), S1 od ~$1/1000 transakcji |
| **Azure AI Face** | Rozpoznawanie i analiza twarzy (np. identyfikacja, weryfikacja, emocje) |
| | ![Architektura Azure AI Face](assets/arch-ai-face.svg) |
| | Komunikacja: REST API, Python/C#/.NET SDK <br> Limity: 10 TPS (Free), PersonGroup do 10 000 osób (Large do 1M); identyfikacja wymaga **Limited Access** (wniosek do Microsoft) <br> Koszty: Free (30 000/mies.), S1 od ~$1/1000 transakcji |
| **Azure AI Language** | Przetwarzanie języka naturalnego: analiza tekstu, ekstrakcja kluczowych fraz, NER, sentyment, CLU, Question Answering |
| | ![Architektura Azure AI Language](assets/arch-ai-language.svg) |
| | Komunikacja: REST API, Python/C#/.NET SDK, Language Studio (portal no-code) <br> Limity: 5 000 znaków/dokument (sentyment, NER), 1 000 rekordów/żądanie batch <br> Koszty: Free (5 000 transakcji/mies.), S od ~$1–$2/1000 rekordów tekstowych |
| **Azure AI Speech** | Rozpoznawanie i synteza mowy, zamiana tekstu na mowę i odwrotnie, Speaker Recognition |
| | ![Architektura Azure AI Speech](assets/arch-ai-speech.svg) |
| | Komunikacja: REST API, Speech SDK (real-time streaming), Speech Studio (portal) <br> Limity: 20 współbieżnych żądań (STT), 200 żądań/min (TTS); audio do 60s (real-time), pliki do 2h (batch) <br> Koszty: Free (5h STT, 0.5M znaków TTS/mies.), S0 od ~$1/godz. STT, ~$16/1M znaków TTS |
| **Azure AI Translator** | Tłumaczenia maszynowe tekstu (100+ języków), transliteracja, Custom Translator |
| | ![Architektura Azure AI Translator](assets/arch-ai-translator.svg) |
| | Komunikacja: REST API, Python/C# SDK <br> Limity: 50 000 znaków/żądanie, 2M znaków/godz. (Free) <br> Koszty: Free (2M znaków/mies.), S1 od ~$10/1M znaków |
| **Azure OpenAI** | Dostęp do zaawansowanych modeli generatywnych (GPT, DALL-E, Whisper) do generowania tekstu, obrazów, kodu |
| | ![Architektura Azure OpenAI](assets/arch-azure-openai.svg) |
| | Komunikacja: REST API, Python/C#/JS SDK, Azure OpenAI Studio, Playground <br> Limity: TPM (Tokens Per Minute) i RPM (Requests Per Minute) per model/deployment per region; wymaga zatwierdzenia dostępu <br> Koszty: per token (input/output oddzielnie), np. GPT-4o ~$2.50/1M input, ~$10/1M output; DALL-E per obraz |
| **Azure AI Foundry** | Katalog modeli AI, zarządzanie i wdrażanie modeli, Prompt Flow, integracja z innymi usługami |
| | ![Architektura Azure AI Foundry](assets/arch-ai-foundry.svg) |
| | Komunikacja: Azure Portal (Foundry Portal), REST API, CLI, SDK <br> Limity: zależne od wdrożonego modelu i typu compute <br> Koszty: opłata za zużyty compute (VM), storage i wdrożone modele (Serverless API = per token, Managed Compute = per godz.) |
| **Azure Machine Learning** | Platforma do trenowania, wdrażania i zarządzania modelami ML, AutoML, Designer, rejestr modeli, endpointy |
| | ![Architektura Azure Machine Learning](assets/arch-azure-ml.svg) |
| | Komunikacja: Azure ML Studio (portal), Python SDK (v2), CLI (v2), REST API, Designer (drag & drop) <br> Limity: zależne od compute quota per region per subscription; AutoML max 1000 iteracji <br> Koszty: opłata za compute (Compute Instance, Cluster, Managed Endpoint), storage; sam workspace jest darmowy |
| **Azure AI Document Intelligence** | Ekstrakcja danych z formularzy, faktur, dokumentów (dawniej Form Recognizer) |
| | ![Architektura Azure AI Document Intelligence](assets/arch-ai-doc-intelligence.svg) |
| | Komunikacja: REST API, Python/C#/.NET SDK, Document Intelligence Studio (portal) <br> Limity: 15 stron/żądanie (Free), 2000 stron/żądanie (S0); pliki do 500 MB <br> Koszty: Free (500 stron/mies.), S0 od ~$1.50/1000 stron (prebuilt), ~$50/1000 stron (custom) |
| **Azure AI Search** | Wyszukiwanie wektorowe + AI enrichment (indexer, index, skillset); kluczowa dla RAG |
| | ![Architektura Azure AI Search](assets/arch-ai-search.svg) |
| | Komunikacja: REST API, Python/C#/.NET SDK, Azure Portal <br> Limity: Free (50 MB storage, 3 indeksy), Basic (2 GB, 15 indeksów); ilość partycji i replik zależy od tier <br> Koszty: Free tier, Basic od ~$75/mies., Standard od ~$250/mies.; AI enrichment dodatkowo per skillset |
| **Azure AI Content Safety** | Filtrowanie szkodliwych treści: mowa nienawiści, przemoc, treści seksualne, self-harm |
| | ![Architektura Azure AI Content Safety](assets/arch-ai-content-safety.svg) |
| | Komunikacja: REST API, Python/C# SDK; wbudowane w Azure OpenAI jako Content Filters <br> Limity: 1000 znaków/żądanie (tekst), 4 MB (obraz); 10 TPS (Free) <br> Koszty: Free (5 000 transakcji/mies.), S1 od ~$1/1000 transakcji |
| **Azure AI Custom Vision** | Trenowanie własnych modeli klasyfikacji/detekcji obrazów bez kodu |
| | ![Architektura Azure AI Custom Vision](assets/arch-ai-custom-vision.svg) |
| | Komunikacja: REST API, Python/C# SDK, Custom Vision Portal (no-code) <br> Limity: 2 projekty (Free), 100 projektów (S0); 5 000 obrazów/projekt (Free), 100 000 (S0) <br> Koszty: Free (2 projekty, 10 000 predykcji/mies.), S0 od ~$2/1000 predykcji, ~$10/godz. treningu |
| **Azure Bot Service** | Budowa chatbotów wielokanałowych (Web Chat, Teams, Facebook, Slack) |
| | ![Architektura Azure Bot Service](assets/arch-bot-service.svg) |
| | Komunikacja: Bot Framework SDK (C#, JS, Python), REST API, Azure Portal, Composer <br> Limity: wiele kanałów jednocześnie; limity związane z podłączonymi usługami AI <br> Koszty: kanał Web Chat/Direct Line – darmowy (Standard); Premium kanały płatne per wiadomość |
| **Copilot Studio** | Platforma no-code do budowy chatbotów i agentów AI (dawniej Power Virtual Agents) |
| | ![Architektura Copilot Studio](assets/arch-copilot-studio.svg) |
| | Komunikacja: portal Copilot Studio (no-code), Power Platform, Teams; integracja z Azure OpenAI i AI Services <br> Limity: zależne od licencji Power Platform; limity sesji/mies. <br> Koszty: licencja per tenant (~$200/mies.) lub per sesja; wliczone w licencje Microsoft 365 (ograniczone) |
| **Azure AI Immersive Reader** | Pomoc w czytaniu dla osób z dysleksją; tłumaczenie, czytanie na głos, wyróżnianie słów |
| | ![Architektura Azure AI Immersive Reader](assets/arch-immersive-reader.svg) |
| | Komunikacja: JavaScript SDK, REST API; osadzany w aplikacjach webowych <br> Limity: działa w przeglądarce (client-side rendering); wymaga Azure AD token <br> Koszty: Free (3M znaków/mies.), S0 od ~$1/1M znaków |

### Wycofane usługi (retired – mogą pojawić się jako dystraktory na egzaminie)

| **Usługa** | **Status** |
|---|---|
| **LUIS** | Wycofany → zastąpiony przez **CLU** (Conversational Language Understanding) w AI Language |
| **QnA Maker** | Wycofany → zastąpiony przez **Custom Question Answering** w AI Language |
| **Azure AI Personalizer** | Wycofany (wrzesień 2023) |
| **Azure AI Metrics Advisor** | Wycofany → funkcjonalność przeniesiona do Azure Monitor |
| **Azure AI Anomaly Detector** | Wycofany jako osobna usługa (2023) |

Każda z tych usług posiada gotowe API, które można łatwo zintegrować z aplikacjami biznesowymi, stronami internetowymi czy chatbotami.

## Azure AI Services - co warto wiedzieć

**Azure AI Services** (historycznie: Cognitive Services) to rodzina gotowych modeli AI udostępnianych jako usługi chmurowe przez REST API i SDK. Z perspektywy egzaminu AI-900 najważniejsze jest rozumienie, kiedy wybrać gotową usługę AI Services, a kiedy budować model samodzielnie w Azure Machine Learning.

### Jak to działa w praktyce

| **Krok** | **Opis** |
|---|---|
| **1. Tworzenie zasobu** | Tworzysz zasób w Azure (portal / CLI / Bicep / Terraform) |
| **2. Autoryzacja** | Otrzymujesz **endpoint** i sposób autoryzacji (klucz API lub Entra ID) |
| **3. Wysyłanie danych** | Aplikacja wysyła dane do endpointu (tekst, obraz, audio, prompt) |
| **4. Wynik inferencji** | Usługa zwraca wynik (np. sentyment, transkrypcja, tagi obrazu, odpowiedź modelu) |

### Typy zasobów

| **Typ zasobu** | **Opis** |
|---|---|
| **Single-service resource** | Zasób dla jednej usługi (np. sam Language lub sam Speech) |
| **Multi-service resource** | Jeden wspólny zasób dla wielu usług AI Services |
| **Azure OpenAI resource** | Osobny typ zasobu dla modeli OpenAI wdrażanych na Azure |

### Kiedy Azure AI Services, a kiedy Azure Machine Learning?

| **Opcja** | **Kiedy wybrać** |
|---|---|
| **Azure AI Services** | Gdy chcesz szybko wdrożyć gotowe AI bez trenowania modelu od zera |
| **Azure Machine Learning** | Gdy potrzebujesz pełnej kontroli nad danymi, treningiem, eksperymentami i MLOps |

### Bezpieczeństwo i zgodność

| **Obszar** | **Opis** |
|---|---|
| **Uwierzytelnianie** | Klucze API lub Microsoft Entra ID (rekomendowane w środowisku produkcyjnym) |
| **Kontrola dostępu** | RBAC, Managed Identity, Private Endpoints, VNet |
| **Ochrona danych** | Wsparcie dla standardów korporacyjnych i regulacji (np. RODO/GDPR) |
| **GenAI** | Filtry treści, logowanie, monitorowanie i praktyki Responsible AI |

### Koszty i skalowanie

| **Aspekt** | **Opis** |
|---|---|
| **Rozliczanie** | Przeważnie za liczbę żądań, tokeny, sekundy audio lub strony dokumentów |
| **Warstwy cenowe** | Różne tiers, limity i throughput zależne od usługi i regionu |
| **Skalowanie** | Po stronie platformy – aplikacja korzysta z gotowego endpointu |

### Typowe scenariusze biznesowe

| **Scenariusz** | **Usługi** |
|---|---|
| **Contact center** | Speech-to-Text + Sentiment + podsumowanie rozmów |
| **Digitalizacja dokumentów** | OCR + Document Intelligence + walidacja danych |
| **Moderacja treści** | Vision/Language + Azure AI Content Safety |
| **Asystent firmowy** | Azure OpenAI + RAG (np. Azure AI Search) + polityki Responsible AI |

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
| | 1. **CNN (Convolutional Neural Network)** – analiza obrazów, rozpoznawanie wzorów wizualnych <br> 2. **RNN (Recurrent Neural Network)** – dane sekwencyjne, tekst, szeregi czasowe <br> 3. **LSTM (Long Short-Term Memory)** – ulepszona RNN, lepsza pamięć długoterminowa <br> 4. **GAN (Generative Adversarial Network)** – generator + dyskryminator; tworzenie obrazów, deepfake <br> 5. **Autoencoder** – kompresja i rekonstrukcja danych; anomaly detection, denoising <br> 6. **Transformer** – mechanizm attention; podstawa GPT, BERT (najważniejsza na egzaminie) |
| **Supervised Learning** | Uczenie nadzorowane (dane z etykietami) |
| **Unsupervised Learning** | Uczenie nienadzorowane (grupowanie bez etykiet) |
| **Reinforcement Learning** | Uczenie ze wzmocnieniem (nagrody i kary) |
| **Weights (wagi)** | Parametry modelu neuronowego aktualizowane podczas treningu; definiują siłę połączeń między neuronami |
| **Activation Function** | Funkcja aktywacji w neuronach wprowadzająca nieliniowość do modelu |
| | 1. **ReLU (Rectified Linear Unit)** – najczęstsza; f(x)=max(0,x); szybka, prosta <br> 2. **Sigmoid** – wyjście 0–1; używana w klasyfikacji binarnej (warstwa wyjściowa) <br> 3. **Tanh** – wyjście -1 do 1; lepsza od Sigmoid w warstwach ukrytych <br> 4. **Softmax** – normalizuje wyjścia do prawdopodobieństw (suma=1); klasyfikacja wieloklasowa <br> 5. **Leaky ReLU** – wariant ReLU; przepuszcza małe wartości ujemne (zapobiega „martwym neuronom”) |
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
| | 1. **Linear Regression** – prosta liniowa <br> 2. **Multiple Linear Regression** – wiele cech <br> 3. **Polynomial Regression** – krzywa <br> 4. **Decision Tree / Random Forest Regression** – drzewa decyzyjne <br> 5. **Neural Network Regression** – sieci neuronowe |
| **Klasyfikacja (Classification)** | Przypisywanie do kategorii |
| | 1. **Logistic Regression** – klasyfikacja binarna (tak/nie, spam/nie-spam) <br> 2. **Decision Tree / Random Forest** – drzewa decyzyjne i lasy losowe <br> 3. **Support Vector Machine (SVM)** – separacja klas hiperpłaszczyzną <br> 4. **K-Nearest Neighbors (KNN)** – klasyfikacja na podstawie najbliższych sąsiadów <br> 5. **Neural Network Classification** – sieci neuronowe do złożonych wzorców <br> 6. **Naive Bayes** – klasyfikator probabilistyczny (tekst, spam) |
| **Klasteryzacja (Clustering)** | Grupowanie podobnych danych (uczenie nienadzorowane) |
| | 1. **K-Means** – podział na k klastrów wg średnich odległości (najczęstszy na egzaminie) <br> 2. **Hierarchical Clustering** – aglomeracyjne łączenie klastrów w drzewo (dendrogram) <br> 3. **DBSCAN** – klasteryzacja gęstościowa; wykrywa klastry o dowolnym kształcie i szum <br> 4. **Mean Shift** – iteracyjnie przesuwa centroidy do obszarów najwyższej gęstości <br> 5. **Gaussian Mixture Models (GMM)** – klastry jako rozkłady prawdopodobieństwa (miękkie przypisanie) |
| **Anomaly Detection** | Wykrywanie obserwacji odbiegających od normy (np. oszustwa, defekty, awarie) |
| | 1. **One-class SVM** – uczy się granic normalnych danych, identyfikuje obserwacje poza nimi <br> 2. **Isolation Forest** – losowe podziały; anomalie łatwiejsze do izolacji <br> 3. **Autoencoder** – sieć neuronowa ucząca się rekonstrukcji; wysoki błąd = anomalia <br> 4. **Statistical Methods (Z-score, IQR)** – progi statystyczne wykrywające outlierów <br> 5. **Azure Anomaly Detector** – gotowa usługa do wykrywania anomalii w szeregach czasowych |
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
| **Data Augmentation** | Sztuczne zwiększanie liczby przykładów przez modyfikacje danych |
| | 1. **Obraz: Flip / Rotation** – odbicie lustrzane, obrót <br> 2. **Obraz: Crop / Resize** – wycinanie fragmentów, zmiana rozmiaru <br> 3. **Obraz: Color Jitter** – losowe zmiany jasności, kontrastu, nasycenia <br> 4. **Tekst: Synonym Replacement** – zamiana słów na synonimy <br> 5. **Tekst: Back-Translation** – tłumaczenie na inny język i z powrotem |
| **Normalization** | Skalowanie wartości cech do wspólnego zakresu (np. 0–1); ważne dla algorytmów opartych na odległościach |
| **One-hot Encoding** | Zamiana kategorii na wektory binarne (np. kolor: czerwony → [1,0,0], zielony → [0,1,0]) |

### **Proces trenowania i optymalizacja**

| **Pojęcie** | **Opis** |
|---|---|
| **Inference (wnioskowanie)** | Użycie wytrenowanego modelu do generowania predykcji na nowych danych |
| **Hyperparameter (hiperparametr)** | Parametr ustawiany przed treningiem (np. learning rate, liczba epok), w odróżnieniu od wag uczonych automatycznie |
| **Epoch (epoka)** | Jedno pełne przejście przez cały zbiór treningowy podczas trenowania modelu |
| **Loss Function (funkcja straty)** | Miara błędu modelu; cel treningu to jej minimalizacja |
| | 1. **MSE (Mean Squared Error)** – regresja; średnia kwadratów błędów <br> 2. **Cross-Entropy (Log Loss)** – klasyfikacja; mierzy różnicę między przewidywanym a rzeczywistym rozkładem <br> 3. **Binary Cross-Entropy** – klasyfikacja binarna (2 klasy) <br> 4. **Categorical Cross-Entropy** – klasyfikacja wieloklasowa <br> 5. **MAE (Mean Absolute Error)** – regresja; mniej wrażliwa na outliery niż MSE |
| **Gradient Descent** | Algorytm optymalizacji minimalizujący funkcję straty poprzez iteracyjne dopasowywanie wag |
| **Backpropagation** | Mechanizm propagacji błędu wstecz w sieci neuronowej, do obliczania gradientów i aktualizacji wag |
| **Regularization** | Techniki zapobiegające overfittingowi |
| | 1. **L1 (Lasso)** – dodaje sumę wart. bezwzględnych wag do loss; zeruje nieistotne cechy (feature selection) <br> 2. **L2 (Ridge)** – dodaje sumę kwadratów wag do loss; zmniejsza wagi, ale nie zeruje <br> 3. **Elastic Net** – kombinacja L1 + L2 <br> 4. **Dropout** – losowe wyłączanie neuronów podczas treningu; zapobiega współzależności <br> 5. **Early Stopping** – zatrzymanie treningu, gdy metryka walidacyjna przestaje się poprawiać |
| **Overfitting (przeuczenie)** | Model zbyt dobrze dopasowany do danych treningowych; świetne wyniki na treningu, słabe na nowych danych |
| **Underfitting (niedouczenie)** | Model zbyt prosty, nie wychwytuje wzorców; słabe wyniki zarówno na treningu, jak i na nowych danych |
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
| | 1. **Binary Classification** – dwie kategorie (np. kot/pies, zdrowy/chory) <br> 2. **Multi-class Classification** – wiele kategorii, jeden label na obraz (np. kot, pies, ptak) <br> 3. **Multi-label Classification** – wiele tagów na obraz (np. „plaża” + „zachód słońca” + „ludzie”) |
| **Object Detection** | Detekcja obiektów – klasa + prawdopodobieństwo + bounding box |
| **Bounding Box** | Prostokąt otaczający wykryty obiekt na obrazie (x, y, szerokość, wysokość) |
| **OCR (Optical Character Recognition)** | Rozpoznawanie tekstu na obrazach |
| **Semantic Segmentation** | Klasyfikacja każdego piksela obrazu do kategorii (np. droga, budynek, niebo) |
| **Face Recognition** | Rozpoznawanie twarzy |
| | 1. **Face Detection** – wykrywanie twarzy na obrazie + atrybuty (wiek, okulary, emocje) <br> 2. **Face Verification** – porównanie 1:1 – „czy to ta sama osoba?” <br> 3. **Face Identification** – porównanie 1:N – „kto to jest?” (wymaga PersonGroup) <br> 4. **Face Grouping** – grupowanie podobnych twarzy ze zbioru zdjęć <br> 5. **Find Similar** – wyszukiwanie twarzy podobnych do podanej |
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
| | 1. **Word2Vec** – klasyczny; każde słowo = jeden wektor (nie rozróżnia kontekstu) <br> 2. **GloVe** – Global Vectors; wektory na bazie statystyk współwystępowania słów <br> 3. **BERT Embeddings** – kontekstowe; to samo słowo ma różny wektor zależnie od zdania <br> 4. **OpenAI text-embedding** – modele embeddingów Azure OpenAI (text-embedding-ada, text-embedding-3) do RAG i wyszukiwania semantycznego |
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
| | 1. **Zero-shot** – bez przykładów; model radzi sobie sam <br> 2. **One-shot** – jeden przykład w promptie <br> 3. **Few-shot** – kilka przykładów (1–5) w promptie <br> 4. **Chain-of-Thought (CoT)** – krok po kroku; poprawia rozumowanie <br> 5. **System Message** – instrukcja definiująca rolę i ograniczenia modelu <br> 6. **Retrieval Augmented Generation (RAG)** – wzbogacenie promptu danymi z bazy wiedzy |
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
| **Content Filters** | Mechanizmy Azure OpenAI blokujące szkodliwe treści |
| | 1. **Hate (nienawiść)** – mowa nienawiści, dyskryminacja grup <br> 2. **Violence (przemoc)** – treści promujące przemoc fizyczną <br> 3. **Sexual (treści seksualne)** – treści dla dorosłych <br> 4. **Self-harm (samookaleczenie)** – treści promujące samookaleczenie <br> 5. **Jailbreak detection** – wykrywanie prób obejścia ograniczeń modelu <br> Severity levels: Safe, Low, Medium, High |
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

| **Domena** | **Udział w egzaminie** |
|---|---|
| **Podstawy AI i ML (AI Workloads)** | 15–20% |
| **Machine Learning na Azure** | 15-20% |
| **Computer Vision** | 15–20% |
| **Natural Language Processing (NLP)** | 15–20% |
| **Generatywna AI** | 20–25% |

---


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)
