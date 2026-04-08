[⟵ Poprzedni: Azure AI Vision](11-azure-ai-vision.md) | [Następny: Azure AI Language ⟶](13-azure-ai-language.md)

# Azure AI Face

![Azure AI Face](assets/azure-ai-face.svg)

## Opis usługi
Azure AI Face to specjalistyczna usługa do wykrywania, analizy i rozpoznawania twarzy na obrazach i wideo. Umożliwia identyfikację osób, analizę emocji, określanie wieku, płci oraz porównywanie twarzy. Usługa jest szeroko wykorzystywana w systemach bezpieczeństwa, kontroli dostępu i personalizacji usług.

## Kluczowe funkcje
- **Wykrywanie twarzy** – lokalizowanie twarzy na zdjęciach i wideo.
- **Analiza cech twarzy** – określanie wieku, płci, emocji, zarostu, okularów, pozycji głowy.
- **Rozpoznawanie tożsamości** – identyfikacja osób na podstawie bazy referencyjnej (Face Identification).
- **Porównywanie twarzy** – sprawdzanie, czy dwie twarze należą do tej samej osoby (Face Verification).
- **Grupowanie twarzy** – automatyczne grupowanie podobnych twarzy.
- **Face Liveness Detection** – wykrywanie, czy przed kamerą jest żywa osoba (ochrona przed atakami ze zdjęciem/wideo – anti-spoofing).

## Przykłady użycia (Use Cases)
- Systemy kontroli dostępu (biometryczne wejście do budynków).
- Personalizacja reklam i usług na podstawie analizy demograficznej.
- Weryfikacja tożsamości w aplikacjach bankowych i rządowych.
- Analiza emocji klientów w sklepach lub podczas obsługi klienta.
- Automatyczne tagowanie zdjęć w galeriach i mediach społecznościowych.

## Przykład implementacji (C#)
```csharp
// Azure AI Face – Face Detection (SDK: Azure.AI.Vision.Face)
using Azure;
using Azure.AI.Vision.Face;

var endpoint = new Uri("https://<your-resource>.cognitiveservices.azure.com/");
var credential = new AzureKeyCredential(Environment.GetEnvironmentVariable("AZURE_AI_FACE_KEY")!);

var client = new FaceClient(endpoint, credential);

var result = await client.DetectAsync(
    new Uri("https://example.com/photo.jpg"),
    FaceDetectionModel.Detection03,
    FaceRecognitionModel.Recognition04,
    returnFaceId: true,
    returnFaceAttributes: new[]
    {
        FaceAttributeType.HeadPose,
        FaceAttributeType.Glasses,
        FaceAttributeType.QualityForRecognition
        // UWAGA: age, gender, emotion – usunięte przez Microsoft (Responsible AI)
    });

foreach (var face in result.Value)
{
    Console.WriteLine($"Face ID: {face.FaceId}");
    Console.WriteLine($"Glasses: {face.FaceAttributes.Glasses}");
    Console.WriteLine($"Quality: {face.FaceAttributes.QualityForRecognition}");
}
```

## Ważne informacje
- Wysoka dokładność wykrywania i rozpoznawania twarzy.
- Obsługa zdjęć, wideo oraz strumieni na żywo.
- Możliwość tworzenia własnych baz referencyjnych osób (PersonGroup, LargePersonGroup).
- Zgodność z przepisami o ochronie danych osobowych (RODO/GDPR).
- **Ograniczony dostęp (Limited Access Policy)** – funkcje identyfikacji twarzy i weryfikacji tożsamości są dostępne tylko po formalnej akceptacji przez Microsoft. Wymagane uzasadnienie biznesowe.
- **Face Liveness Detection** – wykrywa próby wyłudzenia dostępu za pomocą zdjęć lub nagrań wideo (ochrona przed atakami typu „presentation attack”).
- **Responsible AI** – Microsoft ograniczył dostęp do niektórych funkcji (np. rozpoznawanie emocji jako wnioskowanie o stanie psychicznym), by zapobiec nadużyciom i dyskryminacji.
- Zakaz użycia do masowej, nieautoryzowanej inwigilacji osób publicznych.

---
[⟵ Poprzedni: Azure AI Vision](11-azure-ai-vision.md) | [Następny: Azure AI Language ⟶](13-azure-ai-language.md)
