[⟵ Poprzedni: Azure AI Face](12-azure-ai-face.md) | [Następny: Azure AI Speech ⟶](14-azure-ai-speech.md)

# Azure AI Language


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure AI Language to zaawansowana usługa do przetwarzania i analizy języka naturalnego (NLP). Pozwala na analizę tekstu, ekstrakcję kluczowych fraz, rozpoznawanie encji, analizę sentymentu, tłumaczenia oraz budowanie własnych modeli językowych. Usługa dostępna jest przez API, SDK oraz narzędzia w portalu Azure.

## Kluczowe funkcje
- **Analiza sentymentu (Sentiment Analysis)** – określanie emocji w tekście: pozytywne, negatywne, neutralne, mieszane.
- **Ekstrakcja kluczowych fraz (Key Phrase Extraction)** – wyodrębnianie najważniejszych słów i zwrotów z tekstu.
- **Rozpoznawanie encji (Named Entity Recognition, NER)** – identyfikacja nazw własnych: osoby, miejsca, organizacje, daty, kwoty, numery.
- **Wykrywanie PII (Personally Identifiable Information)** – automatyczne wykrywanie i maskowanie danych osobowych (np. PESEL, numery kart, adresy e-mail).
- **Podsumowywanie (Summarization)** – automatyczne streszczanie długich dokumentów, artykułów lub transkrypcji rozmów.
- **Tłumaczenia maszynowe** – automatyczne tłumaczenie tekstu na ponad 100 języków.
- **Kategoryzacja dokumentów (Text Classification)** – przypisywanie tekstów do określonych kategorii, w tym trenowanie własnych klasyfikatorów.
- **Detekcja języka (Language Detection)** – automatyczne rozpoznawanie języka tekstu spośród ponad 120 języków.
- **Conversational Language Understanding (CLU)** – następca LUIS. Budowanie modeli rozumienia języka naturalnego dla chatbotów:
	- Rozpoznawanie intencji (Intent Recognition)
	- Wyodrębnianie encji z wypowiedzi (Entity Extraction)
	- Obsługa wielu języków jednocześnie
- **Question Answering** – tworzenie baz wiedzy Q&A z dokumentów, FAQ i adresów URL:
	- Pytania i odpowiedzi w języku naturalnym
	- Obsługa stron otwartych (chitchat), rankowanie odpowiedzi
	- Integracja z Azure Bot Service i Copilot Studio
- **Custom NER (Named Entity Recognition)** – trenowanie własnego rozpoznawania encji specyficznych dla branży (np. kody produktów, terminy medyczne).
- **Custom Text Classification** – klasyfikacja tekstu na ręcznie zdefiniowane kategorie.

## Przykłady użycia (Use Cases)
- Analiza opinii klientów w mediach społecznościowych.
- Automatyczne tłumaczenie treści na stronach internetowych.
- Wyszukiwanie informacji w dużych zbiorach dokumentów.
- Automatyczne tagowanie i kategoryzacja wiadomości e-mail.
- Weryfikacja tożsamości na podstawie analizy tekstu (np. chatboty).

## Przykład implementacji (C#)
```csharp
// Przykład użycia Azure AI Language (Sentiment Analysis) w C#
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

class Program
{
	static async Task Main()
	{
		var endpoint = "https://<your-region>.api.cognitive.microsoft.com/text/analytics/v3.2/sentiment";
		var subscriptionKey = "<your-key>";

		using var client = new HttpClient();
		client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", subscriptionKey);

		var json = "{\"documents\":[{\"id\":\"1\",\"language\":\"pl\",\"text\":\"To jest świetny produkt!\"}]}";
		var content = new StringContent(json, Encoding.UTF8, "application/json");

		var response = await client.PostAsync(endpoint, content);
		var result = await response.Content.ReadAsStringAsync();
		Console.WriteLine(result);
	}
}
```

## Ważne informacje
- Obsługa wielu języków, w tym polskiego.
- Możliwość trenowania własnych modeli (Custom Text Classification, Custom NER).
- Integracja z innymi usługami Azure (np. Power Automate, Logic Apps).
- Wysoka skalowalność i bezpieczeństwo danych.
- Rozliczanie za liczbę żądań lub ilość przetworzonych znaków.

---
[⟵ Poprzedni: Azure AI Face](12-azure-ai-face.md) | [Następny: Azure AI Speech ⟶](14-azure-ai-speech.md)
