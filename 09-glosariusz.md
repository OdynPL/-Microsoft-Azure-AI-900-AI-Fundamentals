# Glosariusz AI-900

![Glosariusz](assets/glosariusz.svg)


[⟵ Poprzedni: Szybka ściąga i pułapki](08-last-minute-cram.md)


# 9. **Glosariusz pojęć AI-900**

- **AI (Artificial Intelligence)** – sztuczna inteligencja, systemy naśladujące ludzkie zdolności poznawcze
- **ML (Machine Learning)** – uczenie maszynowe, algorytmy uczące się na podstawie danych
- **Deep Learning** – głębokie sieci neuronowe, zaawansowana forma ML
- **Transformer** – nowoczesna architektura modeli AI (np. GPT, BERT)
- **Computer Vision** – analiza i interpretacja obrazów/wideo przez AI
- **NLP (Natural Language Processing)** – przetwarzanie i analiza języka naturalnego (tekst, mowa)
- **OCR (Optical Character Recognition)** – rozpoznawanie tekstu na obrazach, digitalizacja dokumentów
- **Sentiment Analysis** – analiza emocji w tekście (np. pozytywna/negatywna recenzja)
- **Entity Recognition** – rozpoznawanie nazw własnych w tekście (np. osób, miejsc)
- **Generative AI** – generatywna AI, modele tworzące nowe treści (tekst, obrazy, kod)
- **Responsible AI** – etyczne, bezpieczne i przejrzyste wdrażanie AI
- **Bias** – tendencyjność modelu wynikająca z danych lub procesu uczenia
- **Explainability** – możliwość wyjaśnienia, jak model podejmuje decyzje
- **Fairness** – sprawiedliwość, równe traktowanie wszystkich grup użytkowników
- **Compliance** – zgodność z regulacjami prawnymi (np. RODO)
- **Overfitting** – przeuczenie modelu, zbyt dobre dopasowanie do danych treningowych
- **Underfitting** – niedouczenie modelu, zbyt proste wzorce
- **Accuracy** – dokładność, odsetek poprawnych przewidywań
- **Precision** – precyzja, odsetek trafień wśród przewidzianych pozytywnych
- **Recall** – czułość, odsetek wykrytych pozytywnych
- **F1-score** – średnia harmoniczna precision i recall
- **Confusion Matrix** – macierz pomyłek, tabela poprawnych i błędnych klasyfikacji
- **Model Registry** – repozytorium do przechowywania i wersjonowania modeli ML
- **Endpoint** – punkt dostępu do wdrożonego modelu przez API
- **Data labeling** – etykietowanie danych do uczenia modeli
- **Feature Engineering** – przygotowanie i wybór cech do modelu ML
- **Pipeline ML** – sekwencja kroków przetwarzania danych i trenowania modelu
- **Azure AI Vision** – usługa do analizy obrazów/wideo na Azure (klasyfikacja, detekcja, OCR)
- **Azure AI Face** – usługa do rozpoznawania i analizy twarzy na Azure
- **Azure AI Language** – usługa do analizy tekstu, NLP na Azure
- **Azure AI Speech** – rozpoznawanie i synteza mowy na Azure
- **Azure OpenAI** – dostęp do modeli generatywnych (GPT, DALL-E) na Azure
- **Azure AI Foundry** – katalog, zarządzanie i wdrażanie modeli AI na Azure
- **Azure Machine Learning** – platforma do trenowania, wdrażania i monitorowania modeli ML
- **RAG (Retrieval Augmented Generation)** – technika łącząca LLM z zewnętrznymi źródłami wiedzy; redukuje halucynacje
- **Grounding (zakotwiczenie)** – powiązanie odpowiedzi modelu z konkretnymi, zweryfikowanymi danymi
- **System Message** – instrukcja inicjalizująca sesję modelu; definiuje rolę i ograniczenia
- **Token** – podstawowa jednostka tekstu dla LLM (~¾ słowa); cena API rozliczana za tokeny
- **Temperature** – parametr losowości odpowiedzi: 0=deterministyczny, 1+=kreatywny
- **Context Window** – maksymalna liczba tokenów przetwarzana jednorazowo przez model
- **Fine-tuning** – dodatkowe trenowanie pre-trenowanego modelu na własnych danych
- **Content Filters** – mechanizmy blokujące szkodliwe treści w Azure OpenAI
- **Prompt Injection** – atak na model AI przez wstrzyknięcie złośliwych instrukcji w danych wejściowych
- **CLU (Conversational Language Understanding)** – następca LUIS; rozumienie intencji i encji w chatbotach
- **Question Answering** – usługa tworzenia baz Q&A z dokumentów i FAQ (Azure AI Language)
- **PII (Personally Identifiable Information)** – dane osobowe; Azure AI Language wykrywa i maskuje je automatycznie
- **Summarization** – automatyczne streszczanie tekstu lub rozmowy (Azure AI Language)
- **Language Detection** – automatyczne wykrywanie języka tekstu
- **Custom Vision** – trenowanie własnych modeli klasyfikacji/detekcji obrazów bez kodu
- **Azure AI Document Intelligence** – ekstrakcja danych z formularzy, faktur, dokumentów (dawniej Form Recognizer)
- **Spatial Analysis** – śledzenie ruchu i zliczanie osób w wideo w czasie rzeczywistym
- **Face Liveness Detection** – wykrywanie żywej osoby (ochrona przed atakami zdjęciowymi)
- **Limited Access Policy** – niektóre funkcje AI (np. identyfikacja twarzy) wymagają formalnej zgody Microsoft
- **Azure AI Content Safety** – usługa filtrowania szkodliwych treści: mowy nienawiści, przemocy, treści seksualnych
- **MLOps** – praktyki DevOps stosowane do modeli ML: CI/CD, wersjonowanie, monitoring
- **Drift (dryfowanie danych)** – zmiana rozkładu danych wejściowych w czasie, pogarszająca jakość modelu
- **Custom Speech** – dostosowanie modelu rozpoznawania mowy do własnego słownictwa/akcentu
- **Custom Voice** – tworzenie spersonalizowanego, syntetycznego głosu
- **Prompt Flow** – narzędzie w Azure AI Foundry do orkiestracji pipeline’ów AI i RAG
- **AI Hub / AI Project** – środowisko pracy zespołowej w Azure AI Foundry
- **Responsible AI Dashboard** – panel w Azure ML do analizy fairness, explainability, error analysis
- **SHAP / LIME** – techniki wyjaśniania decyzji modeli ML (explainability)
- **Copilot Studio** – platforma no-code do budowy chatbotów i agentów AI (dawniej Power Virtual Agents)
- **AI Builder** – narzędzia AI w Power Platform dla użytkowników biznesowych
- **Batch Transcription** – masowa, asynchroniczna transkrypcja nagrań audio (Azure AI Speech)
- **Confusion Matrix** – tabela TP/FP/TN/FN do oceny jakości klasyfikatora
- **ROC / AUC** – krzywa ROC i pole pod krzywą – ocena skuteczności klasyfikatora binarnego
- **MSE (Mean Square Error)** – średnia kwadratów błędów – metryka oceny modeli regresyjnych
- **Data Augmentation** – sztyczne zwiększanie zbioru danych przez modyfikacje (obrót zdjęć, synonimy tekstu)
- **Transfer Learning** – wykorzystanie wytrenowanego modelu do nowego, pokrewnego zadania
