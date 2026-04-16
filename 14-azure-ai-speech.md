[⟵ Poprzedni: Azure AI Language](13-azure-ai-language.md) | [Następny: Azure OpenAI ⟶](15-azure-openai.md)

# Azure AI Speech

![Azure AI Speech](assets/azure-ai-speech-service.svg)

## Opis usługi
Azure AI Speech to usługa umożliwiająca rozpoznawanie mowy, syntezę mowy, tłumaczenie mowy oraz analizę dźwięku. Pozwala na zamianę mowy na tekst (Speech-to-Text), tekstu na mowę (Text-to-Speech), tłumaczenie rozmów w czasie rzeczywistym oraz rozpoznawanie mówców. Usługa dostępna jest przez API, SDK oraz narzędzia w portalu Azure.

## Kluczowe funkcje
- **Rozpoznawanie mowy (Speech-to-Text)** – zamiana wypowiedzi na tekst w ponad 100 językach i wielu akcentach.
- **Synteza mowy (Text-to-Speech)** – generowanie naturalnie brzmiącej mowy z tekstu, w tym z wyrażeniem emocji.
- **Tłumaczenie mowy (Speech Translation)** – automatyczne tłumaczenie mowy na inne języki w czasie rzeczywistym.
- **Rozpoznawanie mówców (Speaker Recognition)** – identyfikacja i weryfikacja tożsamości na podstawie głosu.
- **Custom Speech** – dostosowanie modelu rozpoznawania mowy do własnego słownictwa, akcentu lub specjalistycznej terminologii (np. medycznej, prawniczej).
- **Custom Voice** – tworzenie własnego, spersonalizowanego głosu syntetycznego dla asystentów i chatbotów.
- **Batch Transcription** – masowa transkrypcja dużych zbiorów nagrań audio (asynchronicznie, bez limitu długości).
- **Pronunciation Assessment** – ocena poprawności wymowy (przyda się w aplikacjach edukacyjnych).
- **Analiza dźwięku** – wykrywanie emocji, tła, jakości nagrania.

## Przykłady użycia (Use Cases)
- Automatyczna transkrypcja spotkań, wykładów, podcastów.
- Tworzenie asystentów głosowych i chatbotów obsługujących mowę.
- Tłumaczenie rozmów międzynarodowych w czasie rzeczywistym.
- Weryfikacja tożsamości klientów przez telefon (biometria głosowa).
- Ułatwienia dostępu dla osób z niepełnosprawnościami (np. czytanie tekstu na głos).

## Przykład implementacji (C#)
```csharp
// Azure AI Speech – Speech-to-Text (SDK: Microsoft.CognitiveServices.Speech)
using Microsoft.CognitiveServices.Speech;
using Microsoft.CognitiveServices.Speech.Audio;

var speechKey = Environment.GetEnvironmentVariable("AZURE_AI_SPEECH_KEY")!;
var speechRegion = Environment.GetEnvironmentVariable("AZURE_AI_SPEECH_REGION")!;

var speechConfig = SpeechConfig.FromSubscription(speechKey, speechRegion);
speechConfig.SpeechRecognitionLanguage = "pl-PL";

// Z pliku audio
using var audioConfig = AudioConfig.FromWavFileInput("audio.wav");
using var recognizer = new SpeechRecognizer(speechConfig, audioConfig);

var result = await recognizer.RecognizeOnceAsync();

switch (result.Reason)
{
    case ResultReason.RecognizedSpeech:
        Console.WriteLine($"Rozpoznano: {result.Text}");
        break;
    case ResultReason.NoMatch:
        Console.WriteLine("Nie rozpoznano mowy.");
        break;
    case ResultReason.Canceled:
        var cancellation = CancellationDetails.FromResult(result);
        Console.WriteLine($"Anulowano: {cancellation.Reason} – {cancellation.ErrorDetails}");
        break;
}
```

## Ważne informacje
- Obsługa wielu języków i akcentów, w tym polskiego.
- **Universal Language Model** używany przez API Speech-to-Text jest zoptymalizowany pod kątem scenariuszy konwersacyjnych i dyktowania. Scenariusze akustyczne, językowe i wymowy wymagają stworzenia własnego modelu.
- Możliwość trenowania własnych modeli rozpoznawania mowy.
- Integracja z innymi usługami Azure (np. Bot Service, Power Automate).
- Wysoka dokładność i niskie opóźnienia.
- Rozliczanie za czas przetwarzania lub liczbę żądań.

---
[⟵ Poprzedni: Azure AI Language](13-azure-ai-language.md) | [Następny: Azure OpenAI ⟶](15-azure-openai.md)
