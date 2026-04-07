# Azure AI Speech

## Przegląd usług Azure AI

![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure AI Speech to usługa umożliwiająca rozpoznawanie mowy, syntezę mowy, tłumaczenie mowy oraz analizę dźwięku. Pozwala na zamianę mowy na tekst (Speech-to-Text), tekstu na mowę (Text-to-Speech), tłumaczenie rozmów w czasie rzeczywistym oraz rozpoznawanie mówców. Usługa dostępna jest przez API, SDK oraz narzędzia w portalu Azure.

## Kluczowe funkcje
- **Rozpoznawanie mowy (Speech-to-Text)** – zamiana wypowiedzi na tekst w wielu językach.
- **Synteza mowy (Text-to-Speech)** – generowanie naturalnie brzmiącej mowy z tekstu.
- **Tłumaczenie mowy** – automatyczne tłumaczenie wypowiedzi na inne języki w czasie rzeczywistym.
- **Rozpoznawanie mówców** – identyfikacja i weryfikacja tożsamości na podstawie głosu.
- **Analiza dźwięku** – wykrywanie emocji, tła, jakości nagrania.

## Przykłady użycia (Use Cases)
- Automatyczna transkrypcja spotkań, wykładów, podcastów.
- Tworzenie asystentów głosowych i chatbotów obsługujących mowę.
- Tłumaczenie rozmów międzynarodowych w czasie rzeczywistym.
- Weryfikacja tożsamości klientów przez telefon (biometria głosowa).
- Ułatwienia dostępu dla osób z niepełnosprawnościami (np. czytanie tekstu na głos).

## Przykład implementacji (Python, REST API)
```csharp
// Przykład użycia Azure AI Speech (Speech-to-Text) w C#
using System;
using System.IO;
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        var endpoint = "https://<your-region>.stt.speech.microsoft.com/speech/recognition/conversation/cognitiveservices/v1";
        var subscriptionKey = "<your-key>";
        var audioFilePath = "audio.wav";

        using var client = new HttpClient();
        client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", subscriptionKey);
        client.DefaultRequestHeaders.Add("Content-Type", "audio/wav");

        var audioData = await File.ReadAllBytesAsync(audioFilePath);
        using var content = new ByteArrayContent(audioData);
        content.Headers.ContentType = new System.Net.Http.Headers.MediaTypeHeaderValue("audio/wav");

        var response = await client.PostAsync(endpoint, content);
        var result = await response.Content.ReadAsStringAsync();
        Console.WriteLine(result);
    }
}
```

## Ważne informacje
- Obsługa wielu języków i akcentów, w tym polskiego.
- Możliwość trenowania własnych modeli rozpoznawania mowy.
- Integracja z innymi usługami Azure (np. Bot Service, Power Automate).
- Wysoka dokładność i niskie opóźnienia.
- Rozliczanie za czas przetwarzania lub liczbę żądań.

---
[⟵ Powrót do spisu treści](README.md)
