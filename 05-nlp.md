[⟵ Poprzedni: Computer Vision](04-computer-vision.md) | [Następny: Generatywna AI ⟶](06-generative-ai.md)

# 5. **Natural Language Processing (NLP)**

## Czym jest **NLP**?
- **Natural Language Processing (NLP)** to dziedzina AI zajmująca się przetwarzaniem, analizą i rozumieniem języka naturalnego przez komputery. Obejmuje zarówno tekst pisany, jak i mowę. NLP pozwala maszynom rozumieć, generować, tłumaczyć i analizować język ludzki.

## Typowe zadania

![NLP - przepływ](assets/nlp.svg)

- **Ekstrakcja fraz kluczowych (Key Phrase Extraction)** – wyodrębnianie najważniejszych słów i zwrotów z tekstu.
- **Rozpoznawanie encji (Entity Recognition)** – identyfikacja nazw własnych, takich jak osoby, miejsca, organizacje.
- **Analiza sentymentu (Sentiment Analysis)** – określanie emocji w tekście (np. pozytywny/negatywny komentarz).
- **Modelowanie języka (Language Modeling)** – przewidywanie kolejnych słów w zdaniu, generowanie tekstu.
- **Rozpoznawanie i synteza mowy (Speech Recognition & Synthesis)** – zamiana mowy na tekst i odwrotnie.
- **Tłumaczenia (Translation)** – automatyczne tłumaczenie tekstu na inne języki.
- **Tokenizacja (Tokenization)** – dzielenie tekstu na słowa, zdania lub inne jednostki.
- **Lematyzacja (Lemmatization)** – sprowadzanie słów do formy podstawowej (np. „pies” zamiast „psa”, „psom”).
- **Embeddingi (Embeddings)** – zamiana tekstu na wektory liczbowe, które mogą być analizowane przez modele ML.
- **Rozpoznawanie intencji (Intent Recognition)** – określanie celu wypowiedzi użytkownika (np. pytanie o pogodę, zamówienie pizzy).

## Usługi **Azure**

- **Azure AI Language** – kompleksowa usługa do analizy i rozumienia tekstu. Umożliwia:
	- **Analizę sentymentu (Sentiment Analysis)** – określanie nastroju: pozytywny, negatywny, neutralny, mieszany
	- **Ekstrakcję fraz kluczowych (Key Phrase Extraction)**
	- **Rozpoznawanie encji (Named Entity Recognition, NER)** – osoby, miejsca, organizacje, daty, kwoty
	- **Wykrywanie PII (Personally Identifiable Information)** – automatyczne wykrywanie i maskowanie danych osobowych (numery PESEL, adresy, numery kart)
	- **Klasyfikację tekstu** – przypisywanie dokumentów do kategorii
	- **Podsumowywanie (Summarization)** – automatyczne streszczanie dokumentów i rozmow
	- **Wykrywanie języka (Language Detection)** – automatyczne rozpoznawanie języka tekstu
	- **Tłumaczenia maszynowe**
	- **Wyszukiwanie semantyczne (Semantic Search)** – wyszukiwanie oparte na znaczeniu, nie słowach kluczowych

- **Conversational Language Understanding (CLU)** – następca LUIS. Służy do rozumienia języka naturalnego w chatbotach:

![CLU – Conversational Language Understanding](assets/clu.svg)

  - **Intent Recognition** – rozpoznawanie zamiaru użytkownika (np. „zamów pizza”, „sprawdź pogodę”)
  - **Entity Extraction** – wyodrębnianie encji z wypowiedzi (np. rodzaj pizzy, miasto)
  - Integracja z Azure Bot Service / Copilot Studio

- **Question Answering** – budowanie baz wiedzy Q&A:
	- Tworzenie pary pytanie-odpowiedź z dokumentów, FAQ, URL
	- Odpowiedzi na pytania w języku naturalnym
	- Integracja z chatbotami i asystentami

![Azure AI Language](assets/azure-ai-language.svg)

- **Azure AI Speech** – usługa do rozpoznawania i syntezy mowy. Pozwala na:
	- **Speech-to-Text** – zamiana mowy na tekst w wielu językach i akcentach
	- **Text-to-Speech** – synteza naturalnie brzmiącej mowy z tekstu
	- **Speaker Recognition** – identyfikacja i weryfikacja tożsamości na podstawie głosu
	- **Speech Translation** – tłumaczenie mowy w czasie rzeczywistym
	- **Custom Speech** – dostosowanie modelu rozpoznawania mowy do własnego słownictwa, akcentu lub stylu
	- **Custom Voice** – tworzenie własnego, spersonalizowanego głosu syntetycznego
	- **Batch Transcription** – masowa transkrypcja dużych ilości nagrań audio

![Azure AI Speech](assets/azure-ai-speech.svg)

## Przykłady zastosowań
- **Chatboty** – automatyzacja obsługi klienta, odpowiadanie na pytania użytkowników
- **Analiza opinii klientów** – monitorowanie nastrojów w recenzjach i mediach społecznościowych
- **Automatyczne tłumaczenia** – szybkie tłumaczenie dokumentów i komunikacji
- **Wyszukiwanie semantyczne (Semantic Search)** – inteligentne wyszukiwanie informacji w dużych zbiorach tekstu
- **Asystenci głosowi** – sterowanie urządzeniami za pomocą mowy
- **Transkrypcje spotkań** – automatyczne zapisywanie rozmów i spotkań

[⟵ Poprzedni: Computer Vision](04-computer-vision.md) | [Następny: Generatywna AI ⟶](06-generative-ai.md)
