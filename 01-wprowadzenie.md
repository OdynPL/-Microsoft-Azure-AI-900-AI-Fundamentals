[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)


# 1. Wprowadzenie i profil egzaminu AI-900


**Azure AI Fundamentals (AI-900)** to certyfikat potwierdzający znajomość podstawowych pojęć **AI**, **ML** oraz usług **AI** na platformie **Azure**.

## Usługi Azure AI – przegląd

Platforma **Microsoft Azure** oferuje szeroki zestaw gotowych usług AI, które pozwalają szybko wdrażać rozwiązania sztucznej inteligencji bez konieczności budowania modeli od zera:

| **Usługa** | **Opis** |
|---|---|
| **Azure AI Vision** | Analiza obrazów i wideo, klasyfikacja, detekcja obiektów, OCR, rozpoznawanie twarzy |
| | ![Architektura Azure AI Vision](assets/arch-ai-vision.svg) |
| | **Komunikacja:** REST API, Python/C#/.NET SDK, Azure Portal <br><br> **Limity:** 20 TPS (transakcji/s) w warstwie Free, 10 TPS w S1 per region <br><br> **Koszty:** Free (20 wywołań/min), S1 od ~$1/1000 transakcji |
| **Azure AI Face** | Rozpoznawanie i analiza twarzy (np. identyfikacja, weryfikacja, emocje) |
| | ![Architektura Azure AI Face](assets/arch-ai-face.svg) |
| | **Komunikacja:** REST API, Python/C#/.NET SDK <br><br> **Limity:** 10 TPS (Free), PersonGroup do 10 000 osób (Large do 1M); identyfikacja wymaga **Limited Access** (wniosek do Microsoft) <br><br> **Koszty:** Free (30 000/mies.), S1 od ~$1/1000 transakcji |
| **Azure AI Language** | Przetwarzanie języka naturalnego: analiza tekstu, ekstrakcja kluczowych fraz, NER, sentyment, CLU, Question Answering |
| | ![Architektura Azure AI Language](assets/arch-ai-language.svg) |
| | **Komunikacja:** REST API, Python/C#/.NET SDK, Language Studio (portal no-code) <br><br> **Limity:** 5 000 znaków/dokument (sentyment, NER), 1 000 rekordów/żądanie batch <br><br> **Koszty:** Free (5 000 transakcji/mies.), S od ~$1–$2/1000 rekordów tekstowych |
| **Azure AI Speech** | Rozpoznawanie i synteza mowy, zamiana tekstu na mowę i odwrotnie, Speaker Recognition |
| | ![Architektura Azure AI Speech](assets/arch-ai-speech.svg) |
| | **Komunikacja:** REST API, Speech SDK (real-time streaming), Speech Studio (portal) <br><br> **Limity:** 20 współbieżnych żądań (STT), 200 żądań/min (TTS); audio do 60s (real-time), pliki do 2h (batch) <br><br> **Koszty:** Free (5h STT, 0.5M znaków TTS/mies.), S0 od ~$1/godz. STT, ~$16/1M znaków TTS |
| **Azure AI Translator** | Tłumaczenia maszynowe tekstu (100+ języków), transliteracja, Custom Translator |
| | ![Architektura Azure AI Translator](assets/arch-ai-translator.svg) |
| | **Komunikacja:** REST API, Python/C# SDK <br><br> **Limity:** 50 000 znaków/żądanie, 2M znaków/godz. (Free) <br><br> **Koszty:** Free (2M znaków/mies.), S1 od ~$10/1M znaków |
| **Azure OpenAI** | Dostęp do zaawansowanych modeli generatywnych (GPT, DALL-E, Whisper) do generowania tekstu, obrazów, kodu |
| | ![Architektura Azure OpenAI](assets/arch-azure-openai.svg) |
| | **Komunikacja:** REST API, Python/C#/JS SDK, Azure OpenAI Studio, Playground <br><br> **Limity:** TPM (Tokens Per Minute) i RPM (Requests Per Minute) per model/deployment per region; wymaga zatwierdzenia dostępu <br><br> **Koszty:** per token (input/output oddzielnie), np. GPT-4o ~$2.50/1M input, ~$10/1M output; DALL-E per obraz |
| **Azure AI Foundry** | Katalog modeli AI, zarządzanie i wdrażanie modeli, Prompt Flow, integracja z innymi usługami |
| | ![Architektura Azure AI Foundry](assets/arch-ai-foundry.svg) |
| | **Komunikacja:** Azure Portal (Foundry Portal), REST API, CLI, SDK <br><br> **Limity:** zależne od wdrożonego modelu i typu compute <br><br> **Koszty:** opłata za zużyty compute (VM), storage i wdrożone modele (Serverless API = per token, Managed Compute = per godz.) |
| **Azure Machine Learning** | Platforma do trenowania, wdrażania i zarządzania modelami ML, AutoML, Designer, rejestr modeli, endpointy |
| | ![Architektura Azure Machine Learning](assets/arch-azure-ml.svg) |
| | **Komunikacja:** Azure ML Studio (portal), Python SDK (v2), CLI (v2), REST API, Designer (drag & drop) <br><br> **Limity:** zależne od compute quota per region per subscription; AutoML max 1000 iteracji <br><br> **Koszty:** opłata za compute (Compute Instance, Cluster, Managed Endpoint), storage; sam workspace jest darmowy |
| **Azure AI Document Intelligence** | Ekstrakcja danych z formularzy, faktur, dokumentów (dawniej Form Recognizer) |
| | ![Architektura Azure AI Document Intelligence](assets/arch-ai-doc-intelligence.svg) |
| | **Komunikacja:** REST API, Python/C#/.NET SDK, Document Intelligence Studio (portal) <br><br> **Limity:** 15 stron/żądanie (Free), 2000 stron/żądanie (S0); pliki do 500 MB <br><br> **Koszty:** Free (500 stron/mies.), S0 od ~$1.50/1000 stron (prebuilt), ~$50/1000 stron (custom) |
| **Azure AI Search** | Wyszukiwanie wektorowe + AI enrichment (indexer, index, skillset); kluczowa dla RAG |
| | ![Architektura Azure AI Search](assets/arch-ai-search.svg) |
| | **Komunikacja:** REST API, Python/C#/.NET SDK, Azure Portal <br><br> **Limity:** Free (50 MB storage, 3 indeksy), Basic (2 GB, 15 indeksów); ilość partycji i replik zależy od tier <br><br> **Koszty:** Free tier, Basic od ~$75/mies., Standard od ~$250/mies.; AI enrichment dodatkowo per skillset |
| **Azure AI Content Safety** | Filtrowanie szkodliwych treści: mowa nienawiści, przemoc, treści seksualne, self-harm |
| | ![Architektura Azure AI Content Safety](assets/arch-ai-content-safety.svg) |
| | **Komunikacja:** REST API, Python/C# SDK; wbudowane w Azure OpenAI jako Content Filters <br><br> **Limity:** 1000 znaków/żądanie (tekst), 4 MB (obraz); 10 TPS (Free) <br><br> **Koszty:** Free (5 000 transakcji/mies.), S1 od ~$1/1000 transakcji |
| **Azure AI Custom Vision** | Trenowanie własnych modeli klasyfikacji/detekcji obrazów bez kodu |
| | ![Architektura Azure AI Custom Vision](assets/arch-ai-custom-vision.svg) |
| | **Komunikacja:** REST API, Python/C# SDK, Custom Vision Portal (no-code) <br><br> **Limity:** 2 projekty (Free), 100 projektów (S0); 5 000 obrazów/projekt (Free), 100 000 (S0) <br><br> **Koszty:** Free (2 projekty, 10 000 predykcji/mies.), S0 od ~$2/1000 predykcji, ~$10/godz. treningu |
| **Azure Bot Service** | Budowa chatbotów wielokanałowych (Web Chat, Teams, Facebook, Slack) |
| | ![Architektura Azure Bot Service](assets/arch-bot-service.svg) |
| | **Komunikacja:** Bot Framework SDK (C#, JS, Python), REST API, Azure Portal, Composer <br><br> **Limity:** wiele kanałów jednocześnie; limity związane z podłączonymi usługami AI <br><br> **Koszty:** kanał Web Chat/Direct Line – darmowy (Standard); Premium kanały płatne per wiadomość |
| **Copilot Studio** | Platforma no-code do budowy chatbotów i agentów AI (dawniej Power Virtual Agents) |
| | ![Architektura Copilot Studio](assets/arch-copilot-studio.svg) |
| | **Komunikacja:** portal Copilot Studio (no-code), Power Platform, Teams; integracja z Azure OpenAI i AI Services <br><br> **Limity:** zależne od licencji Power Platform; limity sesji/mies. <br><br> **Koszty:** licencja per tenant (~$200/mies.) lub per sesja; wliczone w licencje Microsoft 365 (ograniczone) |
| **Azure AI Immersive Reader** | Pomoc w czytaniu dla osób z dysleksją; tłumaczenie, czytanie na głos, wyróżnianie słów |
| | ![Architektura Azure AI Immersive Reader](assets/arch-immersive-reader.svg) |
| | **Komunikacja:** JavaScript SDK, REST API; osadzany w aplikacjach webowych <br><br> **Limity:** działa w przeglądarce (client-side rendering); wymaga Azure AD token <br><br> **Koszty:** Free (3M znaków/mies.), S0 od ~$1/1M znaków |
| **Azure AI Video Indexer** | Analiza wideo i audio: transkrypcja, OCR, rozpoznawanie twarzy, wykrywanie scen, ekstrakcja tematów i etykiet |
| | ![Architektura Azure AI Video Indexer](assets/arch-video-indexer.svg) |
| | **Komunikacja:** REST API, portal Video Indexer (vi.microsoft.com); upload pliku lub URL <br><br> **Limity:** Free: 10 h indeksowania/mies., 40 min na plik; Paid: zależne od planu <br><br> **Koszty:** Free (10h/mies.), Standard od ~$0.035/min (wideo), $0.012/min (audio) |
| **Azure AI Health Insights** | Analiza danych klinicznych: Clinical Matching, Trial Matcher, Radiology Insights; zgodność HIPAA |
| | ![Architektura Azure AI Health Insights](assets/arch-health-insights.svg) |
| | **Komunikacja:** REST API; dane wejściowe w formacie FHIR lub tekst kliniczny <br><br> **Limity:** preview/ograniczona dostępność regionalna; wymaga zatwierdzenia dostępu <br><br> **Koszty:** preview — pricing TBD; część funkcji w ramach Health Bot Service |

### Wycofane usługi (retired – mogą pojawić się jako dystraktory na egzaminie)

| **Usługa** | **Status** |
|---|---|
| **LUIS** | Wycofany → zastąpiony przez **CLU** (Conversational Language Understanding) w AI Language |
| **QnA Maker** | Wycofany → zastąpiony przez **Custom Question Answering** w AI Language |
| **Azure AI Personalizer** | Wycofany (wrzesień 2023) |
| **Azure AI Metrics Advisor** | Wycofany → funkcjonalność przeniesiona do Azure Monitor |
| **Azure AI Anomaly Detector** | Wycofany jako osobna usługa (2023) |

Każda z tych usług posiada gotowe API, które można łatwo zintegrować z aplikacjami biznesowymi, stronami internetowymi czy chatbotami.

## Inne ważne pojęcia: Data Mining, Knowledge Mining i pokrewne

W kontekście AI, ML i rozwiązań chmurowych warto znać także następujące pojęcia i technologie:

| **Pojęcie** | **Opis** |
|---|---|
| **Data Mining** | Proces odkrywania wzorców, zależności i wiedzy w dużych zbiorach danych przy użyciu metod statystycznych, ML i baz danych. W Azure najczęściej realizowany przez Azure Machine Learning, Synapse Analytics lub Spark. |
| | ![Architektura Data Mining](assets/arch-data-mining.svg) |
| **Knowledge Mining** | Łączenie wyszukiwania, AI i ekstrakcji wiedzy z nieustrukturyzowanych danych (np. dokumentów, plików, e-maili). W Azure realizowane głównie przez Azure AI Search (dawniej Cognitive Search) z enrichment pipeline. |
| | ![Architektura Knowledge Mining](assets/arch-knowledge-mining.svg) |
| **Text Mining** | Wydobywanie informacji, wzorców i relacji z tekstów (np. analiza sentymentu, ekstrakcja kluczowych fraz, NER). W Azure: AI Language, Cognitive Search, Synapse. |
| | ![Architektura Text Mining](assets/arch-text-mining.svg) |
| **Web Mining** | Automatyczna analiza i ekstrakcja wiedzy z zasobów internetowych (strony WWW, social media, logi). |
| **Process Mining** | Analiza logów procesów biznesowych w celu odkrycia rzeczywistych przepływów pracy i optymalizacji procesów. |
| | ![Architektura Process Mining](assets/arch-process-mining.svg) |
| **Pattern Mining** | Wyszukiwanie powtarzających się wzorców w danych (np. sekwencje, asocjacje, reguły). |
| **Predictive Analytics** | Wykorzystanie danych historycznych i modeli ML do przewidywania przyszłych zdarzeń lub trendów. |
| **Descriptive Analytics** | Analiza danych w celu opisania i zrozumienia przeszłych zdarzeń (raportowanie, dashboardy). |
| **Prescriptive Analytics** | Analiza danych i rekomendacje działań optymalizujących decyzje biznesowe. |
| **Big Data Analytics** | Przetwarzanie i analiza bardzo dużych, zróżnicowanych zbiorów danych (np. Hadoop, Spark, Synapse Analytics). |
| **Business Intelligence (BI)** | Zestaw narzędzi i procesów do analizy danych biznesowych, raportowania i wspierania decyzji (np. Power BI, Synapse). |
| **Data Science** | Dziedzina łącząca statystykę, ML, programowanie i wiedzę domenową do analizy i interpretacji danych. |
| **Feature Engineering** | Proces tworzenia, selekcji i przetwarzania cech (features) wykorzystywanych w modelach ML. |
| **Data Engineering** | Budowa i utrzymanie infrastruktury do gromadzenia, przetwarzania i udostępniania danych (np. ETL, Data Lake, Data Warehouse). |

Znajomość tych pojęć pomaga lepiej zrozumieć ekosystem rozwiązań AI/ML oraz rolę poszczególnych usług Azure w praktycznych scenariuszach.

## NIST AI Risk Management Framework (AI RMF)

1. **Identyfikacja potencjalnych szkód (Identifying potential harms)** – rozpoznanie możliwych zagrożeń i ryzyk
2. **Pomiar szkód (Measuring harms)** – ocena, czy i w jakim stopniu ryzyka występują
3. **Łagodzenie ryzyk (Mitigating risks)** – wdrożenie działań ograniczających ryzyka
4. **Planowanie wdrożenia (Planning for deployment)** – przygotowanie odpowiednich procedur i kontroli przed udostępnieniem rozwiązania

Proces ten skupia się na zrozumieniu i minimalizowaniu ryzyk przed wdrożeniem AI. Pozostałe działania (np. operacje, bezpieczeństwo, rozwój modeli ML) są ważne, ale nie stanowią sedna Responsible AI.
## Azure AI Services - co warto wiedzieć

**Azure AI Services** (historycznie: Cognitive Services) to rodzina gotowych modeli AI udostępnianych jako usługi chmurowe przez REST API i SDK. Z perspektywy egzaminu AI-900 najważniejsze jest rozumienie, kiedy wybrać gotową usługę AI Services, a kiedy budować model samodzielnie w Azure Machine Learning.

### Jak to działa w praktyce

| **Krok** | **Opis** |
|---|---|
| **1. Tworzenie zasobu** | Tworzysz zasób w Azure (portal / CLI / Bicep / Terraform) |
| **2. Autoryzacja** | Otrzymujesz **endpoint** i sposób autoryzacji (klucz API lub Entra ID) |
| **3. Wysyłanie danych** | Aplikacja wysyła dane do endpointu (tekst, obraz, audio, prompt) |
| **4. Wynik inferencji** | Usługa zwraca wynik (np. sentyment, transkrypcja, tagi obrazu, odpowiedź modelu) |

### Confidence Score (wynik pewności)

Większość usług Azure AI Services zwraca w odpowiedzi API **confidence score** – wartość liczbową od **0.0 do 1.0** (czyli 0–100%) określającą, jak pewny jest model swojej predykcji.

| **Aspekt** | **Opis** |
|---|---|
| **Czym jest** | Prawdopodobieństwo poprawności wyniku zwróconego przez model AI; im bliżej 1.0, tym większa pewność modelu |
| **Zakres** | Od 0.0 (brak pewności) do 1.0 (pełna pewność); może być wyrażony jako ułamek (0.95) lub procent (95%) |
| **Threshold (próg)** | Aplikacja powinna definiować **próg minimalny** (np. 0.7) – wyniki poniżej progu są odrzucane lub oznaczane do ręcznej weryfikacji |
| **Nie jest prawdopodobieństwem w sensie statystycznym** | Confidence score to wewnętrzna ocena modelu, nie gwarancja poprawności; wynik 0.9 nie oznacza 90% szans na poprawność w sensie częstościowym |
| **Gdzie występuje** | Praktycznie w każdej usłudze Azure AI Services |

**Przykłady w usługach Azure AI:**

| **Usługa** | **Co zwraca confidence score** |
|---|---|
| **Azure AI Vision** | Tagi obrazu, podpisy (caption), detekcja obiektów – każdy wynik z osobnym score |
| **Azure AI Face** | Weryfikacja twarzy (czy to ta sama osoba), identyfikacja (kto to jest), atrybuty twarzy |
| **Azure AI Language** | Sentiment analysis (score per kategoria: positive/negative/neutral), NER, PII detection, language detection, CLU (intent + entities) |
| **Azure AI Speech** | Pronunciation assessment (accuracy score), rozpoznawanie mówcy (speaker recognition) |
| **Custom Vision** | Klasyfikacja i detekcja obiektów – każda predykcja z confidence score |
| **Azure AI Document Intelligence** | Rozpoznane pola formularzy i dokumentów – każde pole z confidence score |
| **Azure AI Content Safety** | Severity score (0–6) dla kategorii: hate, violence, sexual, self-harm |

**Przykład odpowiedzi API (JSON):**

```json
{
  "documents": [
    {
      "sentiment": "positive",
      "confidenceScores": {
        "positive": 0.98,
        "neutral": 0.01,
        "negative": 0.01
      }
    }
  ]
}
```

> **Egzamin:** Pytania o confidence score pojawiają się w kontekście interpretacji wyników API. Zapamiętaj: (1) zawsze sprawdzaj confidence score przed podjęciem decyzji, (2) ustal threshold odpowiedni dla scenariusza biznesowego (np. medycyna wymaga wyższego progu niż tagowanie zdjęć), (3) niski confidence score = model nie jest pewny → potrzebna weryfikacja człowieka (human-in-the-loop).

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
| **Transparency Notes** | Microsoft publikuje Transparency Notes dla każdej usługi AI – dokument opisujący możliwości, ograniczenia i wytyczne odpowiedzialnego użycia; egzamin pyta o to w kontekście RAI |
| **AI Services Containers** | Niektóre usługi (Vision, Language, Speech) można uruchamiać jako kontenery Docker on-premises/edge – offline, niska latencja, data sovereignty; container pobiera model z Azure, wymaga billing endpoint |

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
| **AI (Artificial Intelligence)** | Systemy naśladujące ludzkie myślenie i działanie. |
| **Narrow AI (Weak AI)** | AI do jednego zadania, np. rozpoznawania obrazów lub chatbotów. |
| **Strong AI (AGI)** | AI o ogólnych zdolnościach poznawczych jak człowiek (hipotetyczna). |
| **ML (Machine Learning)** | Algorytmy uczące się na podstawie danych do przewidywania lub klasyfikacji. |
| **Deep Learning** | ML z wielowarstwowymi sieciami neuronowymi, automatycznie uczące się cech z dużych danych. |
| **Neural Network (sieć neuronowa)** | Model z warstw neuronów przetwarzających dane, inspirowany mózgiem. |
| | 1. **CNN (Convolutional Neural Network)** – analiza obrazów, rozpoznawanie wzorów wizualnych |
| | ![CNN](assets/nn-cnn.svg) |
| **Kernel (filtr)** | Mała macierz przesuwana po obrazie w CNN, wyłapująca wzorce (np. krawędzie). |
| | 2. **RNN (Recurrent Neural Network)** – dane sekwencyjne, tekst, szeregi czasowe |
| | ![RNN](assets/nn-rnn.svg) |
| | 3. **LSTM (Long Short-Term Memory)** – ulepszona RNN, lepsza pamięć długoterminowa |
| | ![LSTM](assets/nn-lstm.svg) |
| | 4. **GAN (Generative Adversarial Network)** – generator + dyskryminator; tworzenie obrazów, deepfake |
| | ![GAN](assets/nn-gan.svg) |
| | 5. **Autoencoder** – kompresja i rekonstrukcja danych; anomaly detection, denoising |
| | ![Autoencoder](assets/nn-autoencoder.svg) |
| | 6. **Transformer** – mechanizm attention; podstawa GPT, BERT (najważniejsza na egzaminie) |
| | ![Transformer](assets/nn-transformer.svg) |
| **Supervised Learning** | Uczenie nadzorowane (dane z etykietami) | |
| | | 1. <b>Linear Regression</b> (regresja liniowa – przewidywanie wartości liczbowych)<br>2. <b>Logistic Regression</b> (regresja logistyczna – klasyfikacja binarna)<br>3. <b>Decision Trees</b> (drzewa decyzyjne – klasyfikacja/regresja, interpretowalność)<br>4. <b>SVM</b> (maszyny wektorów nośnych – klasyfikacja liniowa/nieliniowa)<br>5. <b>k-NN</b> (k-najbliższych sąsiadów – klasyfikacja na podstawie podobieństwa)<br>6. <b>Random Forest</b> (las losowy – wiele drzew, większa dokładność)<br>7. <b>Neural Networks</b> (sieci neuronowe – złożone wzorce, deep learning) |
| **Unsupervised Learning** | Uczenie nienadzorowane (grupowanie bez etykiet) | |
| | | 1. <b>K-Means</b> (grupowanie na podstawie odległości)<br>2. <b>Hierarchical Clustering</b> (grupowanie hierarchiczne – drzewo klastrów)<br>3. <b>PCA</b> (analiza głównych składowych – redukcja wymiarów)<br>4. <b>t-SNE</b> (wizualizacja danych wielowymiarowych)<br>5. <b>DBSCAN</b> (gęstościowe grupowanie – wykrywanie anomalii)<br>6. <b>Autoencoders</b> (sieci do kompresji i rekonstrukcji danych) |
| **Reinforcement Learning** | Uczenie ze wzmocnieniem (nagrody i kary) | |
| | | 1. <b>Q-Learning</b> (uczenie przez nagrody – tablica wartości)<br>2. <b>SARSA</b> (uczenie przez nagrody – uwzględnia wybraną akcję)<br>3. <b>Deep Q-Networks</b> (Q-Learning z sieciami neuronowymi)<br>4. <b>Policy Gradients</b> (uczenie bezpośrednio strategii działania) |
| **Weights (wagi)** | Parametry modelu neuronowego aktualizowane podczas treningu; definiują siłę połączeń między neuronami |
| **Activation Function** | Funkcja aktywacji w neuronach wprowadzająca nieliniowość do modelu |
| | 1. **ReLU (Rectified Linear Unit)** – najczęstsza; f(x)=max(0,x); szybka, prosta |
| | ![ReLU](assets/af-relu.svg) |
| | 2. **Sigmoid** – wyjście 0–1; używana w klasyfikacji binarnej (warstwa wyjściowa) |
| | ![Sigmoid](assets/af-sigmoid.svg) |
| | 3. **Tanh** – wyjście -1 do 1; lepsza od Sigmoid w warstwach ukrytych |
| | ![Tanh](assets/af-tanh.svg) |
| | 4. **Softmax** – normalizuje wyjścia do prawdopodobieństw (suma=1); klasyfikacja wieloklasowa |
| | ![Softmax](assets/af-softmax.svg) |
| | 5. **Leaky ReLU** – wariant ReLU; przepuszcza małe wartości ujemne (zapobiega „martwym neuronom") |
| | ![Leaky ReLU](assets/af-leaky-relu.svg) |
| **Parameters (parametry modelu)** | Całkowita liczba wag i bias'ów w modelu (np. GPT-4 ma setki miliardów parametrów) |

### **Architektura Transformer i modele językowe**

| **Pojęcie** | **Opis** |
|---|---|
| **Transformer** | Architektura sieci neuronowej z mechanizmem self-attention, podstawa GPT/BERT. |
| **Self-Attention** | Mechanizm oceny ważności tokenów względem siebie w sekwencji. |
| **Positional Encoding** | Dodaje informację o kolejności tokenów w sekwencji do modelu. |
| **Encoder / Decoder** | Encoder przetwarza wejście, decoder generuje wyjście (np. BERT, GPT). |
| **LLM (Large Language Model)** | Duży model językowy trenowany na ogromnych zbiorach tekstu (np. GPT-4). |
| **Foundation Model** | Wstępnie wytrenowany model AI do wielu zadań (np. GPT, BERT, DALL-E). |
| **SLM (Small Language Model)** | Mały, szybki model językowy do edge i prostych zadań (np. Phi-3). |
| **Multi-Head Attention** | Równoległe mechanizmy attention uczące się różnych zależności. |
| **RNN / LSTM** | Starsze sieci sekwencyjne, poprzedzające Transformera. |
| **BERT** | Model encoder do analizy tekstu (NER, sentyment, Q&A). |
| **GPT** | Model decoder do generowania tekstu, kodu, rozmów (chatboty). |

### **Zadania ML i typy problemów**

| **Pojęcie** | **Opis** |
|---|---|
| **Regresja (Regression)** | Przewidywanie wartości liczbowych na podstawie danych wejściowych. |
| | 1. **Linear Regression** – prosta liniowa |
| | ![Linear Regression](assets/ml-linear-regression.svg) |
| | 2. **Multiple Linear Regression** – wiele cech |
| | ![Multiple Linear Regression](assets/ml-multiple-regression.svg) |
| | 3. **Polynomial Regression** – krzywa |
| | ![Polynomial Regression](assets/ml-polynomial-regression.svg) |
| | 4. **Decision Tree / Random Forest Regression** – drzewa decyzyjne |
| | ![Decision Tree / Random Forest Regression](assets/ml-tree-regression.svg) |
| | 5. **Neural Network Regression** – sieci neuronowe |
| | ![Neural Network Regression](assets/ml-nn-regression.svg) |
| **Klasyfikacja (Classification)** | Przypisywanie danych do określonych kategorii. |
| | 1. **Logistic Regression** – klasyfikacja binarna (tak/nie, spam/nie-spam) |
| | ![Logistic Regression](assets/ml-logistic-regression.svg) |
| | 2. **Decision Tree / Random Forest** – drzewa decyzyjne i lasy losowe |
| | ![Decision Tree / Random Forest](assets/ml-decision-tree.svg) |
| | 3. **Support Vector Machine (SVM)** – separacja klas hiperpłaszczyzną |
| | ![Support Vector Machine](assets/ml-svm.svg) |
| | 4. **K-Nearest Neighbors (KNN)** – klasyfikacja na podstawie najbliższych sąsiadów |
| | ![K-Nearest Neighbors](assets/ml-knn.svg) |
| | 5. **Neural Network Classification** – sieci neuronowe do złożonych wzorców |
| | ![Neural Network Classification](assets/ml-nn-classification.svg) |
| | 6. **Naive Bayes** – klasyfikator probabilistyczny (tekst, spam) |
| | ![Naive Bayes](assets/ml-naive-bayes.svg) |
| **Klasteryzacja (Clustering)** | Grupowanie podobnych danych bez etykiet (uczenie nienadzorowane). |
| **Silhouette Score** | Miara jakości klasteryzacji: ocenia, jak dobrze obiekty pasują do swojego klastra w porównaniu do innych klastrów (wartość od -1 do 1). |
| | 1. **K-Means** – podział na k klastrów wg średnich odległości (najczęstszy na egzaminie) |
| | ![K-Means](assets/ml-kmeans.svg) |
| | 2. **Hierarchical Clustering** – aglomeracyjne łączenie klastrów w drzewo (dendrogram) |
| | ![Hierarchical Clustering](assets/ml-hierarchical.svg) |
| | 3. **DBSCAN** – klasteryzacja gęstościowa; wykrywa klastry o dowolnym kształcie i szum |
| | ![DBSCAN](assets/ml-dbscan.svg) |
| | 4. **Mean Shift** – iteracyjnie przesuwa centroidy do obszarów najwyższej gęstości |
| | ![Mean Shift](assets/ml-mean-shift.svg) |
| | 5. **Gaussian Mixture Models (GMM)** – klastry jako rozkłady prawdopodobieństwa (miękkie przypisanie) |
| | ![Gaussian Mixture Models](assets/ml-gmm.svg) |
| **Anomaly Detection** | Wykrywanie nietypowych, odstających przypadków w danych. |
| | 1. **One-class SVM** – uczy się granic normalnych danych, identyfikuje obserwacje poza nimi |
| | ![One-class SVM](assets/ml-one-class-svm.svg) |
| | 2. **Isolation Forest** – losowe podziały; anomalie łatwiejsze do izolacji |
| | ![Isolation Forest](assets/ml-isolation-forest.svg) |
| | 3. **Autoencoder** – sieć neuronowa ucząca się rekonstrukcji; wysoki błąd = anomalia |
| | ![Autoencoder](assets/ml-autoencoder.svg) |
| | 4. **Statistical Methods (Z-score, IQR)** – progi statystyczne wykrywające outlierów |
| | ![Statistical Methods](assets/ml-statistical.svg) |
| | 5. **Azure Anomaly Detector** – gotowa usługa do wykrywania anomalii w szeregach czasowych |
| | ![Azure Anomaly Detector](assets/ml-azure-anomaly.svg) |
| **Recommendation Systems** | Systemy przewidujące, co użytkownik może polubić na podstawie danych lub podobieństw. |
| **Collaborative Filtering** | Rekomendacje bazujące na podobieństwie użytkowników: „użytkownicy podobni do ciebie polubili…" |
| **Content-Based Filtering** | Rekomendacje porównujące cechy produktów: „produkty podobne do tych, które lubisz" |
| **Time Series Forecasting** | Prognozowanie wartości w czasie (sprzedaż, temperatura); obsługiwane przez AutoML |
| **One-class SVM** | Algorytm anomaly detection: uczy się granic normalnych danych, identyfikuje obserwacje poza nimi |
| **Isolation Forest** | Algorytm anomaly detection oparty na losowych podziałach; anomalie łatwiejsze do izolacji |

### **Dane, cechy i trening modelu**

| **Pojęcie** | **Opis** |
|---|---|
| **Feature (cecha)** | Pojedyncza właściwość lub atrybut wykorzystywany przez model ML do nauki. |
| **Label (etykieta)** | Poprawna odpowiedź przypisana do przykładu w uczeniu nadzorowanym. |
| **Feature Engineering** | Przygotowanie i wybór cech |
| **Data Labeling** | Etykietowanie danych |
| **Data Grounding** | Powiązanie generowanych odpowiedzi AI z wiarygodnymi, aktualnymi danymi źródłowymi. |
| **Training Set** | Dane używane do nauki modelu (największa część zbioru). |
| **Validation Set** | Dane do oceny modelu podczas treningu i doboru parametrów. |
| **Test Set** | Dane do końcowej, niezależnej oceny skuteczności modelu. |
| **Data Imbalance** | Nierówny rozkład klas w danych, utrudniający naukę modelu. |
| **Class Weighting** | Przypisanie wyższych wag mniejszościowej klasie, by model lepiej ją rozpoznawał |
| **SMOTE** | Synthetic Minority Over-Sampling Technique – syntetyczne generowanie przykładów klasy mniejszościowej |
| **Stratified Split** | Podział danych z zachowaniem proporcji klas w każdym zbiorze |
| **Data Augmentation** | Sztuczne zwiększanie liczby przykładów przez modyfikacje danych |
| | 1. **Obraz: Flip / Rotation** – odbicie lustrzane, obrót |
| | ![Flip / Rotation](assets/aug-flip-rotation.svg) |
| | 2. **Obraz: Crop / Resize** – wycinanie fragmentów, zmiana rozmiaru |
| | ![Crop / Resize](assets/aug-crop-resize.svg) |
| | 3. **Obraz: Color Jitter** – losowe zmiany jasności, kontrastu, nasycenia |
| | ![Color Jitter](assets/aug-color-jitter.svg) |
| | 4. **Tekst: Synonym Replacement** – zamiana słów na synonimy |
| | ![Synonym Replacement](assets/aug-synonym.svg) |
| | 5. **Tekst: Back-Translation** – tłumaczenie na inny język i z powrotem |
| | ![Back-Translation](assets/aug-back-translation.svg) |
| **Normalization** | Skalowanie cech do wspólnego zakresu, by poprawić działanie modelu. |
| **One-hot Encoding** | Zamiana kategorii na wektory binarne do użycia w ML. |

### **Proces trenowania i optymalizacja**

| **Pojęcie** | **Opis** |
|---|---|
| **Inference (wnioskowanie)** | Generowanie przewidywań przez wytrenowany model na nowych danych. |
| **Hyperparameter (hiperparametr)** | Parametr ustalany przed treningiem, wpływający na naukę modelu. |
| **Epoch (epoka)** | Jedno pełne przejście przez dane treningowe podczas nauki modelu. |
| **Loss Function (funkcja straty)** | Miara błędu modelu, którą minimalizujemy podczas treningu. |
| | 1. **MSE (Mean Squared Error)** – regresja; średnia kwadratów błędów |
| | ![MSE](assets/loss-mse.svg) |
| | 2. **Cross-Entropy (Log Loss)** – klasyfikacja; mierzy różnicę między przewidywanym a rzeczywistym rozkładem |
| | ![Cross-Entropy](assets/loss-cross-entropy.svg) |
| | 3. **Binary Cross-Entropy** – klasyfikacja binarna (2 klasy) |
| | ![Binary Cross-Entropy](assets/loss-binary-ce.svg) |
| | 4. **Categorical Cross-Entropy** – klasyfikacja wieloklasowa |
| | ![Categorical Cross-Entropy](assets/loss-categorical-ce.svg) |
| | 5. **MAE (Mean Absolute Error)** – regresja; mniej wrażliwa na outliery niż MSE |
| | ![MAE](assets/loss-mae.svg) |
| **Gradient Descent** | Algorytm optymalizujący model przez stopniowe zmniejszanie błędu. |
| **Backpropagation** | Obliczanie i rozprzestrzenianie błędu w sieci neuronowej w celu aktualizacji wag. |
| **Regularization** | Techniki zapobiegające przeuczeniu modelu. |
| | 1. **L1 (Lasso)** – dodaje sumę wart. bezwzględnych wag do loss; zeruje nieistotne cechy (feature selection) |
| | ![L1 Lasso](assets/reg-l1-lasso.svg) |
| | 2. **L2 (Ridge)** – dodaje sumę kwadratów wag do loss; zmniejsza wagi, ale nie zeruje |
| | ![L2 Ridge](assets/reg-l2-ridge.svg) |
| | 3. **Elastic Net** – kombinacja L1 + L2 |
| | ![Elastic Net](assets/reg-elastic-net.svg) |
| | 4. **Dropout** – losowe wyłączanie neuronów podczas treningu; zapobiega współzależności |
| | ![Dropout](assets/reg-dropout.svg) |
| | 5. **Early Stopping** – zatrzymanie treningu, gdy metryka walidacyjna przestaje się poprawiać |
| | ![Early Stopping](assets/reg-early-stopping.svg) |
| **Overfitting (przeuczenie)** | Model działa świetnie na treningu, ale słabo na nowych danych. |
| **Underfitting (niedouczenie)** | Model zbyt prosty, nie uczy się wzorców z danych. |
| **Transfer Learning** | Wykorzystanie modelu wytrenowanego na innym zadaniu do przyspieszenia nauki. |
| **Cross-Validation (K-fold)** | Wielokrotny podział danych na k części dla stabilnej oceny modelu. |
| **Inference Pipeline** | Pipeline wnioskowania utworzony z training pipeline; wymagany przed wdrożeniem modelu do produkcji |
| **Pipeline ML** | Sekwencja kroków przetwarzania danych i trenowania modelu |

### **Metryki oceny modeli**

| **Pojęcie** | **Opis** |
|---|---|
| **True Positive (TP)** | Poprawnie wykryty przypadek pozytywny przez model. |
| **False Positive (FP)** | Przypadek błędnie oznaczony jako pozytywny (fałszywy alarm). |
| **True Negative (TN)** | Poprawnie wykryty przypadek negatywny przez model. |
| **False Negative (FN)** | Przypadek błędnie oznaczony jako negatywny (przeoczenie). |
| **Accuracy** | Odsetek poprawnych przewidywań modelu. |
| **Precision** | Odsetek trafień wśród przewidzianych pozytywnych przypadków. |
| **Recall** | Odsetek wykrytych przypadków pozytywnych. |
| **F1-score** | Średnia harmoniczna Precision i Recall. |
| **Confusion Matrix** | Tabela pokazująca liczbę TP, FP, TN, FN. |
| **ROC Curve, AUC** | Krzywa i pole pod nią oceniające skuteczność klasyfikatora binarnego. |
| **MSE (Mean Square Error)** | Średnia kwadratów różnic między wartościami rzeczywistymi a przewidywanymi. |
| **R² (R-Squared)** | Współczynnik pokazujący, jak dobrze model tłumaczy zmienność danych. |
| **MAE (Mean Absolute Error)** | Średnia wartość bezwzględna błędów predykcji modelu. |
| **RMSE (Root Mean Square Error)** | Pierwiastek z MSE, metryka w jednostkach zmiennej docelowej. |
| **Metryki wg typu zadania (egzamin!)** | **Classification:** Accuracy, Precision, Recall, F1, AUC, Confusion Matrix <br> **Regression:** MSE, MAE, RMSE, R² <br> **Clustering:** Silhouette Score, Average Distance to Cluster Center |

### **Computer Vision**

| **Pojęcie** | **Opis** |
|---|---|
| **Computer Vision** | Analiza i interpretacja obrazów oraz wideo przez AI. |
| **Image Classification** | Przypisywanie obrazów do kategorii na podstawie zawartości. |
| | 1. **Binary Classification** – dwie kategorie (np. kot/pies, zdrowy/chory) |
| | ![Binary Classification](assets/cv-binary-class.svg) |
| | 2. **Multi-class Classification** – wiele kategorii, jeden label na obraz (np. kot, pies, ptak) |
| | ![Multi-class Classification](assets/cv-multiclass.svg) |
| | 3. **Multi-label Classification** – wiele tagów na obraz (np. „plaża" + „zachód słońca" + „ludzie") |
| | ![Multi-label Classification](assets/cv-multilabel.svg) |
| **Object Detection** | Wykrywanie i lokalizacja obiektów na obrazie wraz z prawdopodobieństwem. |
| | ![Object Detection](assets/cv-object-detection.svg) |
| **Bounding Box** | Prostokąt wyznaczający położenie obiektu na obrazie. |
| **OCR (Optical Character Recognition)** | Automatyczne rozpoznawanie tekstu na obrazach. |
| | ![OCR](assets/cv-ocr.svg) |
| **Semantic Segmentation** | Przypisywanie każdemu pikselowi obrazu odpowiedniej kategorii. |
| | ![Semantic Segmentation](assets/cv-semantic-segmentation.svg) |
| **Instance Segmentation** | Segmentacja z rozróżnieniem poszczególnych obiektów na obrazie. |
| | ![Instance Segmentation](assets/cv-instance-segmentation.svg) |
| **Image Tagging / Captioning** | Automatyczne nadawanie tagów i opisów obrazom przez AI. |
| | ![Tagging / Captioning](assets/cv-tagging-captioning.svg) |
| **Dense Captions** | Wiele opisów dla różnych fragmentów obrazu. |
| **Smart Cropping** | Automatyczne kadrowanie obrazu z zachowaniem kluczowych elementów. |
| **Background Removal** | Usuwanie lub zamiana tła obrazu na przezroczyste. |
| **Depth Estimation** | Szacowanie głębokości sceny na podstawie obrazu 2D. |
| | ![Depth Estimation](assets/cv-depth-estimation.svg) |
| **Image Embeddings** | Wektorowa reprezentacja obrazu do wyszukiwania podobnych. |
| | ![Image Embeddings](assets/cv-image-embeddings.svg) |
| **Video Analysis** | Analiza wideo: śledzenie obiektów, detekcja scen, ekstrakcja metadanych. |
| | ![Video Analysis](assets/cv-video-analysis.svg) |
| **Face Recognition** | Automatyczne rozpoznawanie i analiza twarzy na obrazach. |
| | 1. **Face Detection** – wykrywanie twarzy na obrazie + atrybuty (wiek, okulary, emocje) |
| | ![Face Detection](assets/face-detection.svg) |
| | 2. **Face Verification** – porównanie 1:1 – „czy to ta sama osoba?" |
| | ![Face Verification](assets/face-verification.svg) |
| | 3. **Face Identification** – porównanie 1:N – „kto to jest?" (wymaga PersonGroup) |
| | ![Face Identification](assets/face-identification.svg) |
| | 4. **Face Grouping** – grupowanie podobnych twarzy ze zbioru zdjęć |
| | ![Face Grouping](assets/face-grouping.svg) |
| | 5. **Find Similar** – wyszukiwanie twarzy podobnych do podanej |
| | ![Find Similar](assets/face-find-similar.svg) |
| **Face Liveness Detection** | Wykrywanie żywej osoby (ochrona przed atakami zdjęciowymi / deepfake) – Limited Access |
| **PersonGroup** | Grupa osób w Face API z wieloma zdjęciami; wymagana do Face Identification |
| **Limited Access Policy** | Niektóre funkcje AI (identyfikacja twarzy) wymagają formalnej zgody Microsoft |
| **Read API** | API Azure Vision do odczytu tekstu z dużych, wielostronicowych PDF (vs OCR API dla prostych obrazów) |
| **Spatial Analysis** | Śledzenie ruchu osób, liczenie w strefach, mierzenie dystansów w wideo real-time – Azure Vision |
| | ![Spatial Analysis](assets/cv-spatial-analysis.svg) |

### **NLP (Natural Language Processing)**

| **Pojęcie** | **Opis** |
|---|---|
| **NLP** | Przetwarzanie i analiza języka naturalnego przez AI. |
| **Tokenizacja (Tokenization)** | Dzielenie tekstu na mniejsze elementy (tokeny). |
| **Token** | Token to mały kawałek tekstu: słowo, część słowa, znak lub znak interpunkcyjny. W nowoczesnych modelach (np. BERT, GPT) tokeny to często fragmenty słów. |
| **Lematyzacja (Lemmatization)** | Sprowadzanie słów do ich podstawowej formy. |
| **Stemming** | Obcinanie końcówek słów do rdzenia dla uproszczenia analizy. |
| **Embeddingi (Embeddings)** | Zamiana tekstu na wektory liczbowe do analizy przez modele. |
| | 1. **Word2Vec** – klasyczny; każde słowo = jeden wektor (nie rozróżnia kontekstu) |
| | ![Word2Vec](assets/emb-word2vec.svg) |
| | 2. **GloVe** – Global Vectors; wektory na bazie statystyk współwystępowania słów |
| | ![GloVe](assets/emb-glove.svg) |
| | 3. **BERT Embeddings** – kontekstowe; to samo słowo ma różny wektor zależnie od zdania |
| | ![BERT Embeddings](assets/emb-bert.svg) |
| | 4. **OpenAI text-embedding** – modele embeddingów Azure OpenAI (text-embedding-ada, text-embedding-3) do RAG i wyszukiwania semantycznego |
| | ![OpenAI text-embedding](assets/emb-openai.svg) |
| **Entity Recognition (NER)** | Automatyczne wykrywanie nazw własnych w tekście. |
| | 1. **Person** (imiona, nazwiska) <br> 2. **Location** (miasta, kraje, adresy) <br> 3. **Organization** (firmy, instytucje) <br> 4. **DateTime** (daty, godziny, okresy) <br> 5. **Quantity** (liczby, procenty, waluty) <br> 6. **Email** (adresy e-mail) <br> 7. **URL** (adresy internetowe) <br> 8. **IP Address** (adresy IP) <br> 9. **Phone Number** (numery telefonów) |
| **Entity Linking** | Łączenie wykrytych encji z bazą wiedzy (np. Wikipedia). |
| **PII Detection** | Automatyczne wykrywanie i maskowanie danych osobowych w tekście. |
| **Sentiment Analysis** | Określanie, czy tekst jest pozytywny, negatywny czy neutralny. |
| **Sentiment** | Ogólny wydźwięk emocjonalny tekstu, wypowiedzi lub opinii; może być pozytywny, negatywny lub neutralny. |
| **Key Phrase Extraction** | Automatyczne wyodrębnianie kluczowych fraz z tekstu. |
| **Summarization** | Automatyczne skracanie i streszczanie długich tekstów. |
| **Language Detection** | Automatyczne rozpoznawanie języka tekstu przez AI. |
| **Intent Recognition** | Rozpoznawanie celu lub zamiaru użytkownika w tekście. |
| **CLU** | Usługa rozpoznawania intencji i encji w rozmowach (następca LUIS). |
| **Utterance** | Wypowiedź użytkownika analizowana przez model NLP. |
| **Intent** | Zamiar użytkownika rozpoznany z wypowiedzi. |
| **Entity** | Wartość wyodrębniona z wypowiedzi użytkownika (np. miasto, data). |
| | Główne typy entity w NLP:<br>1. <b>Regular expression entity</b> – wykrywa dane o określonym wzorcu (np. numer lotu, e-mail, telefon)<br>2. <b>Machine learned entity</b> – wykrywa encje na podstawie wytrenowanego modelu ML<br>3. <b>Prebuilt entity</b> – gotowe typy, np. data, lokalizacja, waluta<br>4. <b>List entity</b> – rozpoznaje wartości z ustalonej listy (np. marki, produkty) |
| **Conversational AI Flow** | Przepływ: wypowiedź → intencja → encje → odpowiedź. |
| **Multi-turn Conversation** | Rozmowa, w której chatbot pamięta kontekst kilku wypowiedzi. |
| **Question Answering** | Usługa odpowiadania na pytania na podstawie bazy wiedzy. |
| **Active Learning (Q&A)** | System automatycznie sugeruje nowe pytania i odpowiedzi do bazy Q&A. |
| **Speech Recognition** | Automatyczne zamienianie mowy na tekst. |
| **Speech Synthesis** | Zamiana tekstu na mowę przez AI. |
| **SSML (Speech Synthesis Markup Language)** | Znaczniki XML do sterowania syntezą mowy (pauzy, głos, tempo). |
| **Speech Translation** | Tłumaczenie mowy na inny język w czasie rzeczywistym. |
| **Speaker Recognition** | Rozpoznawanie osoby na podstawie jej głosu. |
| **Custom Speech** | Dostosowanie rozpoznawania mowy do własnych potrzeb i słownictwa. |
| **Custom Voice** | Tworzenie własnego, syntetycznego głosu do TTS. |
| **Custom Neural Voice** | Bardzo realistyczny, spersonalizowany głos TTS (wymaga zgody Microsoft). |
| **Pronunciation Assessment** | Ocena poprawności wymowy użytkownika przez AI. |
| **Keyword Recognition** | Rozpoznawanie słów-kluczy na urządzeniu, np. „Hey Cortana”. |
| **Custom Translator** | Tłumaczenie tekstu z uwzględnieniem specjalistycznego słownictwa. |
| **Transliteration** | Zamiana alfabetu tekstu bez tłumaczenia (np. arabski → łaciński). |
| **Batch Transcription** | Masowa transkrypcja wielu plików audio na tekst. |

### **Generatywna AI**

| **Pojęcie** | **Opis** |
|---|---|
| **Generative AI** | AI generująca nowe treści (tekst, obrazy, kod) na podstawie promptów. |
| | ![Traditional AI vs Generative AI](assets/genai-vs-traditional.svg) |
| **Multimodal Models** | Modele obsługujące tekst, obraz i dźwięk jednocześnie. |
| **DALL-E** | Model AI generujący obrazy na podstawie opisu tekstowego. |
| **Whisper** | Model AI zamieniający mowę na tekst. |
| **Codex** | Model AI generujący kod z poleceń tekstowych. |
| **Prompt** | Polecenie lub zapytanie przekazywane do modelu AI. |
| | 1. <b>Instruction prompt</b> – polecenie, co model ma zrobić<br>2. <b>Input prompt</b> – tekst wejściowy do analizy lub generowania<br>3. <b>Few-shot prompt</b> – z przykładami poprawnych odpowiedzi<br>4. <b>Chain-of-thought prompt</b> – z prośbą o pokazanie rozumowania<br>5. <b>Negative prompting</b> – określenie, czego model NIE powinien generować<br>6. <b>System prompt</b> – ustawia styl, rolę lub ograniczenia modelu |
| **Token** | Najmniejsza jednostka tekstu przetwarzana przez model językowy. |
| **Prompt Engineering** | Sztuka tworzenia skutecznych poleceń dla modeli AI. |
| | 1. **Zero-shot** – bez przykładów; model radzi sobie sam |
| | ![Zero-shot](assets/pe-zero-shot.svg) |
| | 2. **One-shot** – jeden przykład w promptie |
| | ![One-shot](assets/pe-one-shot.svg) |
| | 3. **Few-shot** – kilka przykładów (1–5) w promptie |
| | ![Few-shot](assets/pe-few-shot.svg) |
| | 4. **Chain-of-Thought (CoT)** – krok po kroku; poprawia rozumowanie |
| | ![Chain-of-Thought](assets/pe-chain-of-thought.svg) |
| | 5. **System Message** – instrukcja definiująca rolę i ograniczenia modelu |
| | ![System Message](assets/pe-system-message.svg) |
| | 6. **Retrieval Augmented Generation (RAG)** – wzbogacenie promptu danymi z bazy wiedzy |
| | ![RAG](assets/pe-rag.svg) |
| **Zero-shot learning** | Model wykonuje zadanie, którego nie widział podczas treningu. |
| **Few-shot learning** | Model uczy się na kilku przykładach podanych w promptach. |
| **Chain-of-Thought** | Technika wymuszająca wypisanie kroków rozumowania przez model. |
| **System Message** | Instrukcja określająca rolę i ograniczenia modelu AI. |
| **Temperature** | Parametr określający losowość odpowiedzi modelu AI. |
| | Temperatura przyjmuje wartości od 0 (odpowiedzi deterministyczne) do 1 (większa losowość); typowe zakresy to 0–1, czasem do 2. |
| **Top-p (Nucleus Sampling)** | Parametr kontrolujący różnorodność odpowiedzi modelu. |
| **Context Window** | Maksymalna liczba tokenów, które model może przetworzyć naraz. |
| **Fine-tuning** | Dodatkowe trenowanie modelu na własnych danych. |
| **MaaS (Model as a Service)** | Udostępnianie modelu przez API bez zarządzania infrastrukturą. |
| | ![MaaS](assets/genai-maas.svg) |
| **Azure OpenAI Deployment Types** | 1. **Standard** – shared compute, TPM/RPM quota, najczęstszy <br> 2. **Provisioned (PTU)** – dedykowana przepustowość, stała opłata <br> 3. **Global** – routing między regionami, najlepsza dostępność |
| **Azure OpenAI Playground** | Portal do testowania i prototypowania modeli OpenAI na Azure. |
| **Azure OpenAI vs OpenAI (publiczny)** | Azure OpenAI: dane klientów nie są trenowane, compliance, content filters, wymaga zgody. |
| **Azure OpenAI Data Privacy** | Dane klientów nie są używane do trenowania modeli i nie opuszczają regionu Azure. |
| **Azure OpenAI Abuse Monitoring** | Wszystkie żądania są logowane i monitorowane pod kątem nadużyć. |
| **Model Versioning (Azure OpenAI)** | Modele mają wersje i daty wycofania, można je aktualizować ręcznie. |
| **RAG (Retrieval Augmented Generation)** | Technika łącząca LLM z zewnętrznymi danymi, by odpowiedzi były aktualne i oparte na źródłach. |
| | ![RAG Pipeline](assets/genai-rag-pipeline.svg) |
| **Grounding (zakotwiczenie)** | Powiązanie odpowiedzi modelu z konkretnymi, zweryfikowanymi źródłami. |
| **Hallucinations** | Model generuje nieprawdziwe informacje (halucynacje). |
| | ![Hallucinations](assets/genai-hallucinations.svg) |
| | 1. **Factual Hallucination** – fałszywe fakty, daty, nazwiska (np. „stolica Australii to Sydney") |
| | ![Factual Hallucination](assets/hal-factual.svg) |
| | 2. **Fabrication** – zmyślone źródła, cytaty, artykuły naukowe, URL-e (wyglądają wiarygodnie!) |
| | ![Fabrication](assets/hal-fabrication.svg) |
| | 3. **Instruction Hallucination** – model ignoruje System Message, format, język, ograniczenia |
| | ![Instruction Hallucination](assets/hal-instruction.svg) |
| | 4. **Context Hallucination** – odpowiedź sprzeczna z dostarczonym kontekstem (RAG/dokument) |
| | ![Context Hallucination](assets/hal-context.svg) |
| | 5. **Autocomplete Hallucination** – generuje token „bo statystycznie pasuje", nie sprawdza prawdziwości |
| | ![Autocomplete Hallucination](assets/hal-autocomplete.svg) |
| **Content Filters** | Mechanizmy blokujące szkodliwe treści w odpowiedziach AI. |
| | 1. **Hate (nienawiść)** – mowa nienawiści, dyskryminacja grup |
| | ![Hate](assets/cf-hate.svg) |
| | 2. **Violence (przemoc)** – treści promujące przemoc fizyczną |
| | ![Violence](assets/cf-violence.svg) |
| | 3. **Sexual (treści seksualne)** – treści dla dorosłych |
| | ![Sexual](assets/cf-sexual.svg) |
| | 4. **Self-harm (samookaleczenie)** – treści promujące samookaleczenie |
| | ![Self-harm](assets/cf-self-harm.svg) |
| | 5. **Jailbreak detection** – wykrywanie prób obejścia ograniczeń modelu |
| | ![Jailbreak](assets/cf-jailbreak.svg) |
| | Severity levels: Safe, Low, Medium, High |
| **Prompt Injection** | Atak polegający na wstrzyknięciu złośliwych instrukcji do promptu. |
| **XPIA** | Cross-Prompt Injection Attacks – atak przez wstrzyknięcie instrukcji w jedno ze źródeł RAG agenta |
| **Hybrid Search** | Połączenie wyszukiwania semantycznego i słów kluczowych dla lepszych wyników. |
| **Vector Store** | Baza danych przechowująca embeddingi do wyszukiwania semantycznego. |
| **Chunking** | Dzielenie dokumentów na mniejsze fragmenty do analizy przez AI. |
| **Integrated Vectorization** | Automatyczne zamienianie dokumentów na embeddingi w Azure AI Search. |

### **Modele w Azure OpenAI – tabela (egzamin!)**

| **Model** | **Typ** | **Zastosowanie** |
|---|---|---|
| **GPT-4o / GPT-4** | Text generation | Chat, generowanie tekstu, kod, rozumowanie, analiza obrazów (multimodal) |
| **GPT-3.5 Turbo** | Text generation | Szybszy i tańszy chat/tekst; mniej zaawansowany niż GPT-4 |
| **DALL-E 3** | Image generation | Generowanie obrazów z opisu tekstowego (text-to-image) |
| **Whisper** | Speech-to-text | Transkrypcja audio na tekst |
| **text-embedding-3-large** | Embeddings | Wektorowa reprezentacja tekstu do RAG i wyszukiwania semantycznego |
| **Phi-3 / Phi-4** | SLM (Small LM) | Mniejsze modele Microsoftu; tańsze, szybsze, dobre do edge i fine-tuningu |

### **Responsible AI i etyka**

| **Pojęcie** | **Opis** |
|---|---|
| **Responsible AI** | Etyczne i bezpieczne wdrażanie oraz używanie AI. |
| | 1. **Fairness** – sprawiedliwość, równe traktowanie <br> 2. **Reliability & Safety** – niezawodność i bezpieczeństwo <br> 3. **Privacy & Security** – ochrona danych <br> 4. **Inclusiveness** – dostępność dla wszystkich <br> 5. **Transparency** – przejrzystość działania <br> 6. **Accountability** – odpowiedzialność ludzi za systemy AI |
| **Responsible AI Process (Microsoft)** | Kluczowe etapy wdrażania Responsible AI w GenAI:<br>1. Identyfikacja potencjalnych szkód<br>2. Pomiar szkód<br>3. Łagodzenie ryzyk<br>4. Planowanie wdrożenia |
| | ![Responsible AI Process](assets/rai-process.svg) |
| **Fairness** | Sprawiedliwe i równe traktowanie wszystkich przez AI. |
| **Reliability & Safety** | Model działa poprawnie i nie powoduje szkód. |
| **Inclusiveness** | AI dostępne dla wszystkich, bez wykluczeń. |
| **Transparency** | Użytkownicy wiedzą, że korzystają z AI i jak działa model. |
| **Accountability** | Odpowiedzialność ludzi za decyzje i działanie AI. |
| **Bias** | Model faworyzuje pewne grupy przez dane lub algorytm. |
| **Explainability** | Możliwość wyjaśnienia, jak model podjął decyzję. |
| **Interpretability** | Możliwość zrozumienia działania modelu przez człowieka. |
| **Compliance** | Zgodność AI z przepisami i regulacjami. |
| **Data Privacy** | Ochrona prywatności i bezpieczeństwa danych użytkowników. |
| **SHAP** | Technika pokazująca wpływ cech na predykcję modelu. |
| **LIME** | Technika lokalnego wyjaśniania decyzji modelu. |
| **Feature Importance** | Ranking cech według ich wpływu na wynik modelu. |
| **Fairlearn** | Narzędzie do pomiaru i poprawy sprawiedliwości modeli AI. |
| **Error Analysis** | Analiza błędów modelu według cech i grup użytkowników. |
| **Causal Analysis** | Analiza, czy zmiana jednej cechy powoduje zmianę wyniku. |
| **Counterfactual** | Przykłady pokazujące, jak zmiana cechy wpływa na wynik modelu. |
| **Responsible AI Dashboard** | Panel w Azure ML do analizy sprawiedliwości, błędów i wyjaśnialności modeli. |
| **Human-in-the-Loop** | Człowiek podejmuje ostateczną decyzję, AI tylko wspiera. |
| **Responsible AI Impact Assessment** | Ocena ryzyk i wpływu AI przed wdrożeniem (wymóg Microsoft). |

### **Cykl życia modelu i MLOps**

| **Pojęcie** | **Opis** |
|---|---|
| **Model Deployment** | Wdrożenie modelu do produkcji, by mógł obsługiwać żądania. |
| | 1. **Managed Online Endpoint** – real-time REST API zarządzany przez Azure ML; auto-scaling, blue/green deployment <br> 2. **Kubernetes Online Endpoint** – wdrożenie na AKS (Azure Kubernetes Service); pełna kontrola nad infrastrukturą <br> 3. **Batch Endpoint** – przetwarzanie wsadowe dużych zbiorów; wyniki do storage <br> 4. **Serverless API (MaaS)** – modele z Model Catalog (Foundry) bez zarządzania compute; płatność per token <br> 5. **Container (Docker)** – eksport modelu do kontenera; deploy gdzie chcesz (edge, on-prem, inny cloud) |
| **Model Registry** | Repozytorium do przechowywania i wersjonowania modeli ML. |
| **Endpoint** | Adres API do komunikacji z wdrożonym modelem. |
| **Online Endpoint (Real-time)** | Punkt API do natychmiastowych predykcji modelu. |
| **Batch Endpoint** | Punkt API do przetwarzania dużych zbiorów danych wsadowo. |
| **Monitoring** | Śledzenie skuteczności i poprawności działania modelu po wdrożeniu. |
| **Drift** | Zmiana rozkładu danych lub wyników modelu w czasie. |
| **Data Drift** | Zmiana rozkładu danych wejściowych w produkcji. |
| **Model Drift** | Pogorszenie skuteczności modelu na nowych danych. |
| **Prediction Drift** | Nagła zmiana przewidywań modelu bez zmian w danych wejściowych. |
| **Retraining** | Ponowne trenowanie modelu na nowych danych, by poprawić skuteczność. |
| **Traffic Split (A/B Test)** | Podział ruchu między różne modele do testowania skuteczności. |
| **MLOps** | Praktyki DevOps dla ML: automatyzacja, wersjonowanie, monitoring modeli. |
| **Audit Trail** | Historia zmian i treningów modelu dla zgodności i audytu. |
| **Jobs w Azure ML** | 1. **Command Job** – uruchamianie skryptu trenującego <br> 2. **Pipeline Job** – wielokrokowy workflow <br> 3. **Sweep Job** – automatyczne przeszukiwanie hiperparametrów |

### **Narzędzia i usługi Azure**

![Jak znaleźć Azure AI Services](assets/azure-nav-ai-services.svg)

| **Pojęcie** | **Opis** |
|---|---|
| **Azure AI Services** | Gotowe usługi AI na platformie Azure (np. Vision, Language, Speech). |
| **AutoML (Automated ML)** | Automatyczny dobór algorytmu i parametrów dla ML. |
| **Designer** | Graficzny interfejs do budowy pipeline'ów ML bez kodu. |
| **Azure AI Translator** | Usługa do tłumaczeń maszynowych tekstu na wiele języków. |
| **Azure AI Document Intelligence** | Usługa do ekstrakcji danych z dokumentów i formularzy. |
| **Document Intelligence – Prebuilt Models** | Gotowe modele do ekstrakcji danych z różnych typów dokumentów. |
| **Prebuilt vs Custom Model** | Prebuilt: gotowy model, Custom: trenujesz na własnych danych. |
| **Custom Model Workflow (Doc Intelligence)** | Oznacz pola → trenuj model → testuj → wdrażaj do produkcji. |
| **Azure AI Content Safety** | Usługa do filtrowania szkodliwych treści (nienawiść, przemoc, seks). |
| **Azure AI Search** | Wektorowa baza danych i platforma wyszukiwania, kluczowa dla RAG. |
| **Custom Vision** | Usługa do trenowania własnych modeli klasyfikacji obrazów bez kodu. |
| **Azure Bot Service** | Usługa do budowy chatbotów obsługujących wiele kanałów. |
| **Copilot Studio** | Platforma no-code do budowy chatbotów i agentów AI. |
| **Bot Service vs Copilot Studio** | Bot Service: dla developerów, Copilot Studio: no-code dla biznesu. |
| **AI Builder** | Narzędzia AI w Power Platform dla użytkowników biznesowych. |
| **Knowledge Mining** | Wydobywanie wiedzy z niestrukturyzowanych danych przez AI. |
| **Knowledge Mining Pipeline** | Ingest (dane) → Enrich (AI) → Explore (wyszukiwanie/analiza). |
| **Vector Search** | Wyszukiwanie na podstawie podobieństwa embeddingów (semantycznie). |
| **AI Agents** | Autonomiczne aplikacje AI z LLM, instrukcjami i narzędziami. |
| | 1. **Prompt Agents** (bez kodu, tylko instrukcje i narzędzia) <br> 2. **Workflow Agents** (orkiestracja procesów, YAML) <br> 3. **Hosted Agents** (pełna kontrola, kod) <br> |
| **LLM (Large Language Model)** | Duży model językowy, np. GPT-4, trenowany na ogromnych zbiorach tekstu do generowania i rozumienia języka naturalnego. |
| **RBAC** | Kontrola dostępu do zasobów Azure na podstawie ról. |
| | 1. **AI Services User** (wywoływanie modeli) <br> 2. **AI Services Contributor** (wdrażanie modeli) <br> 3. **AI Services Owner** (pełna administracja AI) <br> 4. **Foundry Project Contributor/Reader** (projekty/agenci w Foundry) <br> 5. **Content Safety Administrator** (filtry treści GenAI) <br> |
| **Data Assets** | Rejestracja, wersjonowanie i udostępnianie danych w Azure ML. |
| **Compute Instance** | Maszyna wirtualna w Azure ML do eksperymentów i developmentu. |
| **Compute Cluster** | Skalowalne klastry obliczeniowe do trenowania modeli ML. |
| **Serverless Compute** | Obliczenia na żądanie bez tworzenia klastra w Azure ML. |
| **Datastores** | Połączenia do źródeł danych w Azure ML (Blob, SQL, Data Lake). |
| **Feature Store** | Repozytorium cech ML do ponownego wykorzystania w projektach. |
| **Prompt Flow** | Narzędzie do orkiestracji pipeline'ów AI i RAG w Foundry. |
| **Model Catalog** | Baza modeli AI w Foundry do przeglądania i wdrażania. |
| | 1. **Centralized AI models repository** (jedno miejsce na wszystkie modele AI; np. Foundry Model Catalog) <br> 2. **Pre-trained models** (gotowe, wytrenowane modele; np. GPT-4, CLIP, Whisper) <br> 3. **Third-party models** (modele partnerów i open source; np. Llama, Mistral, Falcon) <br> 4. **Custom models** (modele trenowane na własnych danych; np. fine-tuned GPT, własny model Vision) <br> |
| **Azure AI Video Indexer** | Usługa do analizy wideo: transkrypcja, OCR, rozpoznawanie twarzy. |
| **Microsoft Copilot** | Asystent AI w produktach Microsoft, bazujący na GPT. |
| **Regions & Availability** | Dostępność usług AI zależy od regionu Azure. |

### **Azure AI Foundry vs Azure Machine Learning Studio (egzamin!)**

| **Aspekt** | **Azure AI Foundry** | **Azure Machine Learning Studio** |
|---|---|---|
| **Główne zadanie** | Budowa aplikacji AI (GenAI, RAG, agenci) | Trenowanie i wdrażanie modeli ML |
| **Typowy użytkownik** | Developer AI, prompt engineer | Data scientist, ML engineer |
| **Modele** | Model Catalog (GPT, Phi, Llama) – gotowe | AutoML, Designer, własne skrypty – trenujesz sam |
| **Kluczowe narzędzia** | Prompt Flow, Playground, Model Catalog, Agents | AutoML, Designer, Jobs, Pipelines, Endpoints |
| **RAG / GenAI** | Natywne wsparcie (Prompt Flow + AI Search) | Możliwe, ale nie główny cel |
| **Kiedy wybrać** | Chcesz korzystać z gotowych modeli LLM/SLM | Chcesz trenować własne modele ML od zera |

### **Moduły Azure ML Designer (egzamin!)**

| **Pojęcie** | **Opis** |
|---|---|
| **Split Data** | Dzieli dane na zbiory treningowe i testowe. |
| **Normalize Data** | Skaluje dane numeryczne do wspólnego zakresu. |
| **Clean Missing Data** | Obsługa brakujących danych (usuwanie, uzupełnianie). |
| **Select Columns in Dataset** | Wybór kolumn do dalszego przetwarzania danych. |
| **Train Model** | Trenowanie modelu ML na danych treningowych. |
| **Train Clustering Model** | Trenowanie modelu klasteryzacji (np. K-Means). |
| **Score Model** | Generowanie przewidywań modelu na danych testowych. |
| **Evaluate Model** | Ocena skuteczności modelu na podstawie metryk. |
| **Assign Data to Clusters** | Przypisanie nowych danych do klastrów przez model klasteryzacji. |

### **Komponenty Azure AI Search**

| **Pojęcie** | **Opis** |
|---|---|
| **Indexer** | Przetwarza i ładuje dane do indeksu wyszukiwania. |
| **Index** | Struktura przechowująca dane do wyszukiwania. |
| **Skillset** | Zestaw AI do wzbogacania danych (OCR, NER, frazy, język). |
| **Knowledge Store** | Miejsce do przechowywania wzbogaconych wyników AI. |
| **Semantic Ranker** | AI poprawiający trafność wyników wyszukiwania przez rozumienie kontekstu. |

### **Agenci AI – szczegóły**

| **Pojęcie** | **Opis** |
|---|---|
| **Prompt Agents** | Agenci AI bez kodu, oparte na instrukcjach i narzędziach. |
| **Workflow Agents** | Agenci AI orkiestrujący procesy w YAML. |
| **Hosted Agents** | Agenci AI z pełną kontrolą logiki, oparci o kod. |
| **Agent Tools** | Narzędzia agentów: web/file search, memory, code interpreter, API. |
| **MCP (Model Context Protocol)** | Standard integracji narzędzi z agentami AI. |
| **Agent Lifecycle** | Cykl życia agenta: tworzenie, test, śledzenie, ocena, publikacja, monitoring. |
| **Foundry IQ** | Baza wiedzy dla agentów, zintegrowana z Azure AI Search. |
| **Guardrails (Foundry)** | Zestaw zabezpieczeń: filtry treści, ochrona przed prompt injection, walidacja outputu, grounding detection. |
| | 1. **Content Filters** – blokowanie szkodliwych treści (hate, violence, sexual, self-harm) na wejściu i wyjściu <br> 2. **Prompt Injection Defense** – wykrywanie prób manipulacji instrukcjami modelu (jailbreak, XPIA) <br> 3. **Output Validation** – weryfikacja formatu, długości i poprawności odpowiedzi przed zwróceniem <br> 4. **Grounding Detection** – sprawdzanie czy odpowiedź jest oparta na dostarczonych źródłach <br> 5. **PII Redaction** – automatyczne maskowanie danych osobowych w odpowiedziach <br> 6. **Rate Limiting** – ograniczanie liczby żądań (TPM/RPM) zapobiegające nadużyciom <br> 7. **Blocklists** – niestandardowe listy zabronionych słów/fraz definiowane przez organizację |

### **Metryki ewaluacji GenAI i agentów**

| **Pojęcie** | **Opis** |
|---|---|
| **Coherence** | Spójność i logiczność odpowiedzi AI. |
| **Fluency** | Naturalność i poprawność językowa odpowiedzi AI. |
| **Relevance** | Trafność odpowiedzi względem pytania. |
| **Groundedness** | Oparcie odpowiedzi AI na dostarczonych źródłach. |

---

# AI-901: Nowości i różnice względem AI-900

Od 30.06.2026 AI-900 zastępuje AI-901. Nowy egzamin kładzie nacisk na Foundry, agentów, orkiestrację, ewaluację GenAI i bezpieczeństwo promptów. Poniżej najważniejsze nowe pojęcia i zmiany (ultra-zwięzłe, jednozdaniowe definicje):

### **Nowe pojęcia i narzędzia AI-901**

| **Pojęcie** | **Opis** |
|---|---|
| **Microsoft Foundry** | Nowa platforma do budowy, wdrażania i zarządzania aplikacjami AI (GenAI, RAG, agenci). |
| **Prompt Flow** | Narzędzie do projektowania, testowania i orkiestracji pipeline'ów GenAI i agentów. |
| **Model Catalog (Foundry)** | Centralna baza gotowych modeli (GPT, Phi, Llama, Mistral) do wdrażania i testowania. |
| **Hosted Agents** | Agenci AI z własną logiką, wdrażani i zarządzani w Foundry. |
| **Foundry IQ** | Baza wiedzy dla agentów, integracja z Azure AI Search (vector store). |
| **Guardrails (Foundry)** | Zestaw zabezpieczeń: filtry treści, ochrona przed prompt injection, walidacja outputu, grounding detection. |
| **Prompt Injection Defense** | Mechanizmy wykrywające i blokujące próby manipulacji promptem (jailbreak, XPIA). |
| **Output Validation** | Automatyczna weryfikacja formatu, długości i poprawności odpowiedzi agenta. |
| **Grounding Detection** | Sprawdzanie, czy odpowiedź agenta jest oparta na dostarczonych źródłach. |
| **PII Redaction** | Automatyczne maskowanie danych osobowych w odpowiedziach agentów. |
| **Rate Limiting** | Ograniczanie liczby żądań do agentów (TPM/RPM) dla bezpieczeństwa. |
| **Blocklists** | Listy zabronionych słów/fraz definiowane przez organizację. |
| **PTU (Provisioned Throughput Unit)** | Dedykowana przepustowość dla wdrożeń modeli w Foundry, stała opłata. |
| **Global Deployment** | Wdrażanie modeli z automatycznym routingiem między regionami. |
| **Serverless API (Foundry)** | Udostępnianie modeli przez API bez zarządzania infrastrukturą, płatność per token. |
| **Ewaluacja agentów GenAI** | Ocena agentów na podstawie metryk: coherence, groundedness, relevance, fluency. |
| **XPIA (Cross-Prompt Injection Attacks)** | Ataki polegające na wstrzyknięciu instrukcji w jedno ze źródeł agenta (np. dokument RAG). |
| **Orkiestracja agentów** | Projektowanie złożonych przepływów decyzyjnych i integracji narzędzi w Foundry. |
| **Foundry vs ML Studio** | Foundry: GenAI, agenci, RAG, orkiestracja; ML Studio: trenowanie własnych modeli ML. |

### **Nowe metryki i ewaluacja GenAI (AI-901)**

| **Metryka** | **Opis** |
|---|---|
| **Coherence** | Spójność i logiczność odpowiedzi agenta. |
| **Fluency** | Naturalność i poprawność językowa odpowiedzi agenta. |
| **Relevance** | Trafność odpowiedzi względem pytania i kontekstu. |
| **Groundedness** | Oparcie odpowiedzi na dostarczonych źródłach (brak halucynacji). |

---


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

[Następny: Podstawy AI i rodzaje zadań ⟶](02-ai-workloads.md)
