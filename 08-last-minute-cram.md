# Szybka ściąga AI-900
![Last Minute Cram](assets/last-minute-cram.svg)

[⟵ Poprzedni: Responsible AI](07-responsible-ai.md) | [Następny: Glosariusz ⟶](09-glosariusz.md)

# 8. **Szybka ściąga i pułapki egzaminacyjne AI-900**

## Najważniejsze różnice i pułapki
- **Computer Vision** ≠ **NLP** ≠ **Generatywna AI** – rozpoznawaj typ workloadu po opisie zadania (np. "analiza obrazu" to Computer Vision, "analiza tekstu" to NLP).
- **OCR** = rozpoznawanie tekstu na obrazach, nie analiza sentymentu (OCR to Computer Vision, nie NLP).
- **Sentiment analysis** = **NLP**, nie **Computer Vision** (emocje w tekście, nie na obrazach).
- **GPT** = **generatywna AI**, nie klasyczne **ML** (GPT generuje tekst, nie klasyfikuje danych).
- **Responsible AI** = etyka, bezpieczeństwo, przejrzystość – zawsze wybieraj odpowiedzi promujące te wartości.
- **Klasyfikacja** to przypisywanie do kategorii, **regresja** to przewidywanie liczby.
- **Klasteryzacja** nie wymaga etykiet – to uczenie nienadzorowane.
- **Overfitting** – model działa świetnie na danych treningowych, słabo na nowych.
- **Precision** i **recall** – nie myl tych metryk!

## Szybkie porównania usług Azure AI
| Zadanie | Usługa **Azure** | Opis |
|---------|--------------|------|
| Klasyfikacja obrazów | **AI Vision / Custom Vision** | Rozpoznawanie, tagowanie, analiza obrazów; Custom Vision – własne modele |
| Detekcja twarzy | **AI Face** | Identyfikacja, analiza emocji, weryfikacja tożsamości |
| Analiza tekstu | **AI Language** | Sentyment, frazy kluczowe, NER, PII, podsumowanie |
| Rozpoznawanie intencji w chatbocie | **AI Language (CLU)** | Conversational Language Understanding – następca LUIS |
| Baza Q&A | **AI Language (Question Answering)** | Odpowiedzi na pytania z dokumentów i FAQ |
| Rozpoznawanie mowy | **AI Speech** | Zamiana mowy na tekst i odwrotnie |
| Synteza mowy | **AI Speech (TTS)** | Text-to-Speech, Custom Voice |
| Generowanie tekstu/kodu | **Azure OpenAI** | GPT-4, GPT-3.5 – tworzenie treści, kodu, podsumowań |
| Generowanie obrazów | **Azure OpenAI (DALL-E)** | Text-to-image |
| Ekstrakcja danych z dokumentów | **AI Document Intelligence** | Faktury, paragony, formularze, dowody tożsamości |
| Moderacja treści AI | **AI Content Safety** | Blokowanie szkodliwych treści, mowy nienawiści |
| Katalog modeli AI | **AI Foundry** | Zarządzanie i wdrażanie modeli, Prompt Flow |
| Trenowanie własnych modeli | **Azure Machine Learning** | AutoML, Designer, pipeline’y, MLOps |

## RAG vs Fine-tuning – kluczowa różnica
| Aspekt | **RAG** | **Fine-tuning** |
|--------|--------|----------------|
| Cel | Zasilanie modelu aktualną wiedzą z zewnętrznych źródeł | Dostosowanie zachowania i stylu modelu |
| Dane treningowe | Nie zmienia wag modelu | Zmienia wagi modelu |
| Koszt | Niższy (tylko zapytania) | Wyższy (trening) |
| Aktualizacja wiedzy | Łatwa (zmiana bazy) | Trudna (ponowny trening) |
| Zastosowanie | Aktualne dane firmowe, FAQ, dokumenty | Specyficzny styl, ton, terminologia |

## Strategie egzaminacyjne
- Czytaj uważnie scenariusz – kluczowe są słowa: „**klasyfikacja**”, „**generowanie**”, „**ekstrakcja**”, „**tłumaczenie**”, „**rozpoznawanie**”.
- Eliminuj odpowiedzi niepassujące do typu workloadu (np. nie wybieraj usługi tekstowej do zadania z obrazem).
- Zwracaj uwagę na metryki – jeśli pytanie dotyczy skuteczności modelu, sprawdź czy chodzi o accuracy, precision, recall czy F1-score.
- **Responsible AI** – zawsze wybieraj odpowiedzi promujące etykę, bezpieczeństwo, przejrzystość i zgodność z regulacjami.
- Jeśli nie znasz odpowiedzi, wybierz opcję najbliższą zasadom Responsible AI lub bezpieczeństwa danych.
- **RAG** – jeśli pytanie mówi o „zasilaniu modelu wiedzą z danych firmowych” lub „aktualne informacje” – to RAG, nie fine-tuning.
- **CLU** – jeśli pytanie dotyczy budowania chatbota rozumiejącego intencje użytkownika – to Azure AI Language / CLU (następca LUIS).
- **Document Intelligence** – jeśli pytanie dotyczy automatycznego odczytywania faktur/formularzy – to Azure AI Document Intelligence.
- **Custom Vision** – jeśli pytanie dotyczy trenowania modelu na własnych zdjęciach – to Custom Vision lub Azure ML.
- **Content Safety** – jeśli pytanie dotyczy blokowania szkodliwych treści w AI – to Azure AI Content Safety.
- **Limited Access** – identyfikacja twarzy i niektóre inne funkcje wymagają formalnej zgody Microsoft.

[⟵ Poprzedni: Responsible AI](07-responsible-ai.md) | [Następny: Glosariusz ⟶](09-glosariusz.md)
