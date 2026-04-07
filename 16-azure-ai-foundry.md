# Azure AI Foundry


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure AI Foundry to platforma do zarządzania, katalogowania i wdrażania modeli AI w środowisku Azure. Umożliwia organizacjom centralne przechowywanie modeli, zarządzanie ich wersjami, udostępnianie modeli zespołom oraz monitorowanie ich wykorzystania i wydajności. Foundry wspiera zarówno modele własne, jak i modele open source oraz komercyjne.

## Kluczowe funkcje
- **Katalogowanie modeli** – centralna baza modeli AI dostępnych w organizacji.
- **Wersjonowanie modeli** – śledzenie zmian i historii modeli.
- **Wdrażanie modeli** – szybkie publikowanie modeli jako endpointy API.
- **Zarządzanie dostępem** – kontrola, kto może korzystać z danego modelu.
- **Monitorowanie wydajności** – analiza wykorzystania, skuteczności i błędów modeli.
- **Integracja z Azure Machine Learning** – płynne wdrażanie i zarządzanie cyklem życia modeli.

## Przykłady użycia (Use Cases)
- Udostępnianie modeli AI zespołom deweloperskim i analitycznym.
- Zarządzanie cyklem życia modeli w dużych organizacjach.
- Monitorowanie skuteczności modeli wdrożonych w produkcji.
- Szybkie wdrażanie modeli open source do środowiska chmurowego.
- Zapewnienie zgodności i bezpieczeństwa modeli AI.

## Przykład implementacji (CLI, Azure ML)
```csharp
// Rejestracja modelu i publikacja endpointu w Azure ML za pomocą C#
using Azure.AI.MachineLearning;
using Azure.AI.MachineLearning.Models;
using Azure.Identity;

var credential = new DefaultAzureCredential();
var mlClient = new MachineLearningClient(
	new Uri("https://<your-workspace-name>.<region>.ml.azure.com"),
	credential);

// Rejestracja modelu
var model = new Model(
	name: "my-model",
	path: "./model.pkl"
);
mlClient.Models.CreateOrUpdate(model);

// Publikacja modelu jako endpoint
var endpoint = new OnlineEndpoint(
	name: "my-endpoint",
	description: "Endpoint dla modelu AI"
);
mlClient.OnlineEndpoints.CreateOrUpdate(endpoint);
```

## Ważne informacje
- Ułatwia zarządzanie dużą liczbą modeli w organizacji.
- Wspiera standardy MLOps i automatyzację wdrożeń.
- Integracja z narzędziami CI/CD i monitorowaniem.
- Zapewnia zgodność z regulacjami i bezpieczeństwo danych.
- Rozliczanie za wykorzystanie zasobów i liczbę endpointów.

---
[⟵ Powrót do spisu treści](README.md)
