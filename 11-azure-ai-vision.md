# Azure AI Vision


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure AI Vision to kompleksowa usługa chmurowa umożliwiająca analizę obrazów i wideo. Pozwala na automatyczne rozpoznawanie obiektów, klasyfikację scen, wykrywanie tekstu (OCR), analizę twarzy oraz ekstrakcję metadanych z materiałów wizualnych. Usługa jest dostępna przez REST API, SDK oraz gotowe narzędzia w portalu Azure.

## Kluczowe funkcje
- **Klasyfikacja obrazów** – rozpoznawanie, co znajduje się na zdjęciu (np. pies, samochód, produkt).
- **Detekcja obiektów** – lokalizowanie i oznaczanie obiektów na obrazie (np. wykrycie kilku osób na zdjęciu).
- **OCR (Optical Character Recognition)** – rozpoznawanie tekstu na obrazach, skanach dokumentów, tablicach rejestracyjnych.
- **Analiza twarzy** – wykrywanie twarzy, określanie wieku, płci, emocji, identyfikacja osób (w połączeniu z Azure AI Face).
- **Analiza sceny** – opisanie sceny, generowanie tagów i opisów.
- **Ekstrakcja metadanych** – np. dominujące kolory, format obrazu, rozdzielczość.

## Przykłady użycia (Use Cases)
- Automatyczna kategoryzacja zdjęć w aplikacjach e-commerce.
- Weryfikacja dokumentów tożsamości (OCR + analiza twarzy).
- Wykrywanie niepożądanych treści na platformach społecznościowych.
- Digitalizacja archiwów papierowych (OCR).
- Systemy bezpieczeństwa: wykrywanie osób, pojazdów, tablic rejestracyjnych.
- Analiza ruchu w sklepach (liczenie osób, heatmapy).

## Przykład implementacji (Python, REST API)
```csharp
// Przykład użycia Azure AI Vision w C#
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

class Program
{
	static async Task Main()
	{
		var endpoint = "https://<your-region>.api.cognitive.microsoft.com/vision/v3.2/analyze";
		var subscriptionKey = "<your-key>";
		var imageUrl = "https://example.com/image.jpg";

		using var client = new HttpClient();
		client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", subscriptionKey);

		var requestParameters = "visualFeatures=Categories,Description,Objects,Tags";
		var uri = endpoint + "?" + requestParameters;
		var content = new StringContent($"{{\"url\":\"{imageUrl}\"}}", Encoding.UTF8, "application/json");

		var response = await client.PostAsync(uri, content);
		var result = await response.Content.ReadAsStringAsync();
		Console.WriteLine(result);
	}
}
```

## Ważne informacje
- Usługa obsługuje wiele języków i formatów obrazów.
- Możliwość trenowania własnych modeli (Custom Vision).
- Integracja z innymi usługami Azure (np. Logic Apps, Power Automate).
- Wysoka skalowalność i dostępność w regionach Azure.
- Rozliczanie za liczbę żądań lub czas przetwarzania.

---
[⟵ Powrót do spisu treści](README.md)
