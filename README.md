# AI-900: Azure AI Fundamentals – Notatki i materiały do nauki

## Spis treści


1. [Wprowadzenie i profil egzaminu](01-wprowadzenie.md)
2. [Podstawy AI i rodzaje zadań](02-ai-workloads.md)
3. [Podstawy uczenia maszynowego](03-machine-learning.md)
4. [Computer Vision na Azure](04-computer-vision.md)
5. [Natural Language Processing (NLP)](05-nlp.md)
6. [Generatywna AI na Azure](06-generative-ai.md)
7. [Responsible AI – zasady i etyka](07-responsible-ai.md)
8. [Szybka ściąga i pułapki egzaminacyjne](08-last-minute-cram.md)
9. [Glosariusz pojęć](09-glosariusz.md)
10. [No-code i low-code ML](10-no-code-ml.md)
11. [Azure AI Vision](11-azure-ai-vision.md)
12. [Azure AI Face](12-azure-ai-face.md)
13. [Azure AI Language](13-azure-ai-language.md)
14. [Azure AI Speech](14-azure-ai-speech.md)
15. [Azure OpenAI](15-azure-openai.md)
16. [Azure AI Foundry](16-azure-ai-foundry.md)
17. [Azure Machine Learning](17-azure-machine-learning.md)

---

## Jak korzystać z tych notatek?
- Każdy plik odpowiada jednemu z głównych obszarów egzaminu AI-900.
- Materiały są zwięzłe, praktyczne, z przykładami i porównaniami usług Azure.
- Na końcu znajdziesz ściągę, glosariusz i checklistę powtórkową.

---

## Zakres egzaminu (skills measured)
- Opis zadań AI i rozpoznawanie typów workloadów (Computer Vision, NLP, Generative AI, Anomaly Detection, Recommendations)
- Podstawy ML: typy uczenia (supervised, unsupervised, reinforcement), metryki, overfitting, pipeline, AutoML, Designer
- Computer Vision: klasyfikacja, detekcja obiektów, segmentacja, OCR, Face, Custom Vision, Document Intelligence, Spatial Analysis
- NLP: sentyment, NER, PII, CLU, Question Answering, Speech-to-Text, Text-to-Speech, Custom Speech/Voice, tłumaczenia
- Generatywna AI: LLM, GPT, DALL-E, RAG, Grounding, System Message, Temperature, Tokens, Content Filters, Fine-tuning, Prompt Flow
- Responsible AI: Fairness, Reliability, Privacy, Inclusiveness, Transparency, Accountability, Content Safety, Explainability, Compliance

---


## Inspiracja
Materiały przygotowane w stylu notatek AZ-900, z naciskiem na praktyczne różnice, szybkie powtórki i pułapki egzaminacyjne.

---

## 9. Glosariusz pojęć AI-900

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

---

## 10. No-code i low-code Machine Learning na Azure

### Czym jest no-code/low-code ML?
- **No-code ML** to podejście, w którym budowanie, trenowanie i wdrażanie modeli uczenia maszynowego odbywa się bez pisania kodu programistycznego. Użytkownik korzysta z graficznego interfejsu (GUI), przeciąga i upuszcza komponenty (drag & drop), konfiguruje parametry i uruchamia procesy ML wizualnie.
- **Low-code ML** pozwala na minimalne użycie kodu, głównie do zaawansowanych konfiguracji lub automatyzacji.

### Zalety no-code/low-code ML
- Dostępność dla osób nietechnicznych i biznesowych
- Szybkie prototypowanie i testowanie pomysłów
- Automatyzacja powtarzalnych zadań ML
- Łatwe wdrażanie modeli do produkcji

### Ograniczenia
- Mniejsza elastyczność niż w pełnym kodowaniu
- Ograniczony dostęp do zaawansowanych opcji i niestandardowych algorytmów
- Często ograniczone możliwości debugowania

### Przykład: Azure Machine Learning Designer
- **Azure ML Designer** to narzędzie typu drag & drop dostępne w Azure Machine Learning.
- Pozwala budować pipeline'y ML, trenować modele, oceniać wyniki i wdrażać modele jako endpointy bez pisania kodu.
- Użytkownik wybiera gotowe moduły (np. wczytaj dane, podziel dane, wybierz algorytm, ocen model), łączy je graficznie i uruchamia eksperyment.

### Przykład: Automated ML (AutoML)
- **Automated ML** w Azure pozwala automatycznie wybrać najlepszy algorytm i parametry dla danego zadania ML.
- Użytkownik wskazuje dane, cel (np. klasyfikacja, regresja), a resztą zajmuje się platforma.
- Wynikowy model można wdrożyć jednym kliknięciem.

### Typowe zastosowania na egzaminie AI-900
- Klasyfikacja obrazów i tekstu bez kodowania
- Predykcja wartości liczbowych (regresja) na podstawie danych tabelarycznych
- Automatyczna analiza sentymentu
- Szybkie prototypowanie rozwiązań AI w biznesie

### Usługi Azure wspierające no-code/low-code ML
- **Azure Machine Learning Designer** – graficzne budowanie pipeline'ów ML
- **Automated ML** – automatyczne trenowanie modeli
- **Power Platform AI Builder** – narzędzia AI dla użytkowników biznesowych (np. predykcja, analiza tekstu, rozpoznawanie obrazów)
