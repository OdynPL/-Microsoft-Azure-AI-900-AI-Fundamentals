# Azure AI Language


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure AI Language to zaawansowana usługa do przetwarzania i analizy języka naturalnego (NLP). Pozwala na analizę tekstu, ekstrakcję kluczowych fraz, rozpoznawanie encji, analizę sentymentu, tłumaczenia oraz budowanie własnych modeli językowych. Usługa dostępna jest przez API, SDK oraz narzędzia w portalu Azure.

## Kluczowe funkcje
- **Analiza sentymentu** – określanie emocji w tekście (pozytywne, negatywne, neutralne).
- **Ekstrakcja kluczowych fraz** – wyodrębnianie najważniejszych informacji z tekstu.
- **Rozpoznawanie encji** – identyfikacja nazw własnych (osoby, miejsca, organizacje).
- **Tłumaczenia maszynowe** – automatyczne tłumaczenie tekstu na wiele języków.
- **Kategoryzacja dokumentów** – przypisywanie tekstów do określonych kategorii.
- **Detekcja języka** – rozpoznawanie, w jakim języku napisany jest tekst.
- **Tworzenie własnych modeli** – trenowanie modeli do specyficznych zadań (np. klasyfikacja, ekstrakcja encji).

## Przykłady użycia (Use Cases)
- Analiza opinii klientów w mediach społecznościowych.
- Automatyczne tłumaczenie treści na stronach internetowych.
- Wyszukiwanie informacji w dużych zbiorach dokumentów.
- Automatyczne tagowanie i kategoryzacja wiadomości e-mail.
- Weryfikacja tożsamości na podstawie analizy tekstu (np. chatboty).

## Przykład implementacji (Python, REST API)
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
[⟵ Powrót do spisu treści](README.md)
