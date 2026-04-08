[⟵ Poprzedni: Natural Language Processing](05-nlp.md) | [Następny: Responsible AI ⟶](07-responsible-ai.md)

# 6. **Generatywna AI (Generative AI)** na **Azure**

## Czym jest **generatywna AI**?
- **Generatywna AI (Generative AI)** to dziedzina sztucznej inteligencji, która koncentruje się na tworzeniu nowych treści przez modele AI. Modele te potrafią generować tekst, obrazy, kod, muzykę, a nawet wideo na podstawie dostarczonych poleceń (promptów) lub danych wejściowych. Generatywna AI znajduje zastosowanie w automatyzacji, kreatywnych projektach, wsparciu programistów i wielu innych obszarach.

## Typowe zadania

![Generative AI - przepływ](assets/generative-ai.svg)

- **Generowanie tekstu (Text Generation)** – tworzenie podsumowań, odpowiedzi w chatbotach, generowanie artykułów, e-maili, opisów produktów.
- **Tworzenie obrazów, kodu, muzyki (Image, Code, Music Generation)** – generowanie grafik na podstawie opisu, automatyczne pisanie kodu, komponowanie muzyki.
- **Wyszukiwanie semantyczne (Semantic Search)** – inteligentne wyszukiwanie informacji na podstawie znaczenia, a nie tylko słów kluczowych.
- **Podsumowywanie dokumentów** – automatyczne streszczanie długich tekstów.
- **Tłumaczenia maszynowe** – generowanie tłumaczeń na podstawie kontekstu.

## Cechy modeli generatywnych
- **Modele bazowe (Foundation Models)** – duże modele pre-trenowane na ogromnych zbiorach danych, które można dostosować do wielu zadań (GPT-4, Llama, Phi). Nazywane też **LLM (Large Language Models)** w przypadku modeli językowych.
- **Parametry modelu** – wagi wewnątrz sieci neuronowej (np. GPT-4 ma setki miliardów parametrów). Większa liczba parametrów = większa zdolność do rozumienia złożonych wzorców, ale też większy koszt i wolniejsze działanie.
- **Token** – podstawowa jednostka tekstu przetwarzana przez model (ok. ¾ słowa po angielsku). Rozliczanie za tokeny (input + output).
- **Context Window (okno kontekstowe)** – maksymalna liczba tokenów, które model przetwarza jednorazowo (pytanie + historia + odpowiedź). Przekroczenie limitu = utrata wcześniejszego kontekstu.
- **Temperature** – parametr losowości: `0` = deterministyczny (fakty, kod); `1+` = kreatywny, zróżnicowany.
- **Top-p (nucleus sampling)** – alternatywna kontrola losowości, ogranicza zbiór branych pod uwagę tokenów do najbardziej prawdopodobnych.
- **Embeddings** – reprezentacja tekstu/obrazów w postaci wektorów liczbowych, wykorzystywana do wyszukiwania semantycznego i porównywania treści.
- **Fine-tuning** – dodatkowe trenowanie modelu bazowego na własnych danych, by dostosować go do konkretnego zadania lub branży.

## Popularne modele
- **GPT-4 / GPT-4o (OpenAI)** – generowanie tekstu, chatboty, podsumowania, analiza obrazów (multimodal).
- **DALL-E** – generowanie obrazów na podstawie opisu tekstowego.
- **Stable Diffusion** – generowanie obrazów, grafiki artystycznej.
- **Llama (Meta)** – open-source LLM do generowania tekstu.
- **Phi (Microsoft)** – małe, wydajne modele językowe (SLM – Small Language Models).
- **Whisper (OpenAI)** – rozpoznawanie mowy i transkrypcja.

## Prompt engineering – zaawansowane techniki

![Prompt Engineering – techniki](assets/prompt-engineering.svg)

- **Prompt engineering** – sztuka tworzenia skutecznych poleceń (promptów) dla modeli generatywnych, aby uzyskać pożądane wyniki. Odpowiednio sformułowany prompt pozwala uzyskać bardziej precyzyjne, kreatywne lub zgodne z oczekiwaniami odpowiedzi. Przykład: "Napisz podsumowanie tego artykułu w 3 zdaniach".
- **Zero-shot learning** – model radzi sobie z zadaniem bez żadnych przykładów. Pytanie: "Przetłumacz na angielski: Cześć" – model wie, co to tłumaczenie, bez pokazania przykładu.
- **Few-shot learning** – model uczy się na 1–5 przykładach w promptie. Przykład:
  ```
  Klasyfikuj sentyment: Pozytywny/Negatywny
  "Ten produkt jest świetny!" → Pozytywny
  "Zła jakość, rozczarowanie." → Negatywny
  "Niespecjalnie się podoba" → ?
  ```
- **Chain-of-Thought (CoT)** – model prosi się o wypisanie kroków rozumowania zamiast od razu odpowiedzi. Prompt: "Pomyśl krok po kroku: Jaka jest cena X produktów po zniżce 20%?" – model pokazuje obliczenia, a odpowiedź jest dokładniejsza.
- **System Message** – instrukcja na początku sesji definiująca rolę (np. "Jesteś ekspertem w finansach"), tone, ograniczenia. Zwiększa spójność odpowiedzi.

## Multimodal Models – tekst + obrazy
- **Multimodal models** – modele AI, które rozumieją zarówno tekst, jak i obrazy, i potrafią je łączyć. Przykład: GPT-4V, GPT-4o.
- **Typowe scenariusze**:
  - Opis obrazu: "Co widzisz na zdjęciu?" – model generuje opis językiem naturalnym.
  - Analiza tekstu na obrazach: "Przeczytaj tekst z tego zdjęcia faktury" – model ekstrahuje dane.
  - Odpowiedź na pytania o obrazy: "Ile osób jest na tym zdjęciu?" – model analizuje zawartość wizualną.
  - Generowanie obrazów z tekstu: DALL-E (tekst → obraz).
- **Azure**: GPT-4o w Azure OpenAI obsługuje vision (obrazy), DALL-E 3 do generowania.

## RAG (Retrieval Augmented Generation) – praktyczne aspekty
- **Problem bez RAG**: Model generuje odpowiedź na podstawie danych treningowych (np. do 2023). Halucynuje, jeśli pyta się o bieżące dane firmy.
- **RAG solution**: Przed wysłaniem pytania do modelu, system wyszukuje w **Azure AI Search** (wektorowa baza danych) dokumenty/FAQ odpowiadające pytaniu. Model otrzymuje:
  ```
  System: Odpowiadaj na pytania na podstawie poniższych dokumentów.
  Dokumenty: [wynik wyszukiwania z Azure AI Search]
  User: Ile kosztuje produkt X?
  ```
- **Implementacja na Azure**:
  1. Wgraj dokumenty firmowe do Azure Blob Storage.
  2. Zindeksuj je w **Azure AI Search** (baza wektorowa) z embeddings.
  3. Użytkownik pyta → Azure AI Search wyszukuje dokumenty → Azure OpenAI generuje odpowiedź na bazie dokumentów.
- **Korzyści**: Aktualne dane (FAQ zmienia się codziennie), wiarygodne źródła, mniejsze halucynacje.

## Ograniczenia generatywnej AI
- **Halucynacje (Hallucinations)** – model może generować nieprawdziwe lub zmyślone informacje. **Na egzaminie**: to najczęściej pytany problem GenAI. Rozwiązanie: RAG + grounding.
- **Bias** – tendencyjność wyników, model może powielać uprzedzenia obecne w danych treningowych.
- **Ograniczona kontrola** – trudność w uzyskaniu bardzo precyzyjnych lub zgodnych z oczekiwaniami wyników.
- **Brak świadomości** – model nie rozumie świata, tylko przewiduje kolejne słowa/elementy na podstawie danych.
- **Prompt Injection** – atak polegający na przemyceniu złośliwych instrukcji w danych wejściowych, by zmanipulować zachowanie modelu.

## Kluczowe pojęcia – egzamin AI-900

![RAG – Retrieval Augmented Generation](assets/rag.svg)

- **RAG (Retrieval Augmented Generation)** – technika łącząca model LLM z zewnętrznymi źródłami wiedzy (bazy danych, dokumenty, wyszukiwarki). Model pobiera aktualny kontekst i na jego podstawie generuje odpowiedź. Redukuje halucynacje i pozwala odpowiadać na pytania o aktualne dane.
- **Grounding (zakotwiczenie)** – powiązanie odpowiedzi modelu z konkretnymi, zweryfikowanymi danymi lub dokumentami. Zwiększa dokładność i wiarygodność wyników.
- **System Message (komunikat systemowy)** – instrukcja przekazywana modelowi na początku sesji, definiująca jego rolę, ton i ograniczenia (np. „Jesteś pomocnym asystentem obsługi klienta firmy X. Nie omawiasz tematów niezwiązanych z produktem").
- **Roles w API (role)** – wiadomości w API mają trzy typy: **system** (instrukcja), **user** (pytanie użytkownika), **assistant** (poprzednia odpowiedź modelu). Pozwala to budować wieloturowe rozmowy.
- **Content Filters (filtry treści)** – mechanizmy Azure OpenAI automatycznie blokujące lub flagujące treści szkodliwe: mowę nienawiści, przemoc, treści seksualne, autodestrukcyjne. Konfigurowane na poziomie deployment.
- **Responsible AI w generatywnej AI** – stosowanie content filters, grounding, monitorowanie, transparentność źródeł, ochrona prywatności i danych użytkowników.

## Usługi **Azure**
- **Azure OpenAI** – dostęp do zaawansowanych modeli generatywnych (GPT-4, GPT-3.5, DALL-E, embeddings) przez API. Wymaga akceptacji przez Microsoft. Obsługuje chat completions, image generation, embeddings, RAG.
- **Azure AI Foundry** – katalog modeli AI (w tym open source: Llama, Mistral, Phi), Prompt Flow do budowy pipeline'ów AI, zarządzanie modelami i wdrożeniami.
- **Azure Machine Learning** – możliwość fine-tuningu i wdrażania własnych modeli generatywnych.
- **Azure AI Content Safety** – filtrowanie i moderowanie treści generowanych przez AI: mowa nienawiści, przemoc, treści seksualne, samookaleczenie. Konfigurowalne poziomy czułości.

## Vector Search & Embeddings – zaawansowana wyszukiwarka dla RAG

![Vector Search & Hybrid Search](assets/vector-search.svg)

- **Embeddings** – reprezentacja tekstu/obrazu w postaci wektora numerycznego (~1500 wymiarów dla tekstu). Wektory oddają semantyczne znaczenie — podobne treści mają zbliżone embeddingi.
- **Similarity Search** – zamiast słów kluczowych, pytanie zostaje zamienione w embedding, a wyszukiwarka zwraca dokumenty o najbardziej podobnych embeddings'ach.
- **Hybrid Search** – kombinacja vector search (semantyka) + keyword search (dokładne słowa):
  - Vector search: "pies" i "canine" mogą mieć podobne embeddings
  - Keyword search: tylko dokumenty z dokładnym słowem "pies"
  - Hybrid: połączenie obu, lepsze wyniki niż każde osobno
- **Multimodal Embeddings** – jedno embedding dla tekstu + obrazu, można szukać "psa" w obrazach i tekstach razem
- **Azure AI Search** – wektorowa baza danych do RAG:
  1. Dokumenty firmowe → chunking → embedding (za pomocą Azure OpenAI) → indeks w Azure AI Search
  2. Pytanie użytkownika → embedding → vector query do Azure AI Search
  3. Top-K dokumentów zwracane do modelu → model na bazie dokumentów generuje odpowiedź
- **Praktyka**: Azure AI Search obsługuje:
  - Integrated vectorization (automatyczne embeddings)
  - Filtered vector search (metadata filtering na dokumenty)
  - Hybrid queries (vector + keyword razem)
  - Vector store dla long-term memory agentów

## Przykłady zastosowań
- **Automatyzacja obsługi klienta** – chatboty, automatyczne odpowiedzi na e-maile
- **Tworzenie treści marketingowych** – generowanie opisów produktów, postów na media społecznościowe
- **Wsparcie programistów (AI pair programming)** – podpowiedzi kodu, generowanie fragmentów kodu
- **Tworzenie grafik i ilustracji** – generowanie obrazów na podstawie opisu
- **Podsumowywanie dokumentów** – automatyczne streszczanie raportów, artykułów
- **Tłumaczenia maszynowe** – szybkie tłumaczenie tekstów na różne języki

[⟵ Poprzedni: Natural Language Processing](05-nlp.md) | [Następny: Responsible AI ⟶](07-responsible-ai.md)
