# Azure OpenAI


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure OpenAI to usługa umożliwiająca dostęp do zaawansowanych modeli generatywnych, takich jak GPT (Generative Pre-trained Transformer), DALL-E (generowanie obrazów), Codex (generowanie kodu) oraz innych dużych modeli językowych. Usługa pozwala na integrację generatywnej AI z aplikacjami biznesowymi, automatyzację procesów, analizę tekstu, generowanie treści i wiele więcej.

## Kluczowe funkcje
- **Generowanie tekstu** – tworzenie podsumowań, odpowiedzi, artykułów, e-maili, kodu programistycznego.
- **Generowanie obrazów** – tworzenie grafik na podstawie opisu tekstowego (DALL-E).
- **Przetwarzanie języka naturalnego** – analiza, klasyfikacja, ekstrakcja informacji z tekstu.
- **Tworzenie chatbotów** – budowa zaawansowanych asystentów konwersacyjnych.
- **Automatyzacja procesów** – generowanie dokumentów, automatyczne odpowiedzi, wsparcie obsługi klienta.

## Przykłady użycia (Use Cases)
- Automatyczne generowanie treści marketingowych i raportów.
- Tworzenie chatbotów i asystentów AI dla stron internetowych i aplikacji.
- Generowanie kodu na podstawie opisu (np. SQL, Python).
- Tworzenie obrazów do prezentacji, reklam, mediów społecznościowych.
- Wsparcie analizy dokumentów i ekstrakcji danych.

## Przykład implementacji (Python, REST API)
```csharp
// Przykład użycia Azure OpenAI (Chat Completion) w C#
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        var endpoint = "https://<your-resource-name>.openai.azure.com/openai/deployments/gpt-35-turbo/chat/completions?api-version=2023-05-15";
        var apiKey = "<your-key>";

        using var client = new HttpClient();
        client.DefaultRequestHeaders.Add("api-key", apiKey);

        var json = "{\"messages\":[{\"role\":\"user\",\"content\":\"Wygeneruj podsumowanie tego tekstu...\"}]}";
        var content = new StringContent(json, Encoding.UTF8, "application/json");

        var response = await client.PostAsync(endpoint, content);
        var result = await response.Content.ReadAsStringAsync();
        Console.WriteLine(result);
    }
}
```

## Ważne informacje
- Wymaga utworzenia zasobu Azure OpenAI i uzyskania dostępu (może wymagać akceptacji przez Microsoft).
- Obsługa modeli GPT-3.5, GPT-4, DALL-E, Codex i innych.
- Możliwość dostosowania modeli (fine-tuning) do własnych potrzeb.
- Integracja z innymi usługami Azure (np. Logic Apps, Power Automate).
- Rozliczanie za liczbę tokenów (słów) lub żądań.
- Wysokie wymagania dotyczące bezpieczeństwa i zgodności z regulacjami.

---
[⟵ Powrót do spisu treści](README.md)
