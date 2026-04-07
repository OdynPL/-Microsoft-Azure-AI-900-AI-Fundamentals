# Azure Machine Learning


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure Machine Learning (Azure ML) to kompleksowa platforma do budowy, trenowania, wdrażania i zarządzania modelami uczenia maszynowego w chmurze. Umożliwia zarówno pracę no-code/low-code (Designer, AutoML), jak i zaawansowane projekty kodowane w Pythonie. Wspiera cały cykl życia ML, automatyzację, MLOps i integrację z innymi usługami Azure.

## Kluczowe funkcje
- **Projektowanie pipeline'ów ML** – graficzny interfejs (Designer) do budowy procesów ML bez kodowania.
- **Automated ML (AutoML)** – automatyczne dobieranie algorytmów i parametrów.
- **Trenowanie modeli** – obsługa popularnych frameworków (scikit-learn, PyTorch, TensorFlow).
- **Wdrażanie modeli** – publikacja jako endpointy REST API.
- **Monitorowanie i rejestracja modeli** – śledzenie wersji, metryk, wydajności.
- **Zarządzanie danymi** – rejestracja, wersjonowanie i przetwarzanie zbiorów danych.
- **MLOps** – automatyzacja wdrożeń, integracja z CI/CD, kontrola dostępu.

## Przykłady użycia (Use Cases)
- Budowa modeli predykcyjnych dla finansów, sprzedaży, produkcji.
- Automatyzacja analizy danych i raportowania.
- Szybkie prototypowanie rozwiązań AI przez osoby nietechniczne (Designer).
- Wdrażanie modeli do aplikacji biznesowych i API.
- Monitorowanie jakości i wydajności modeli w produkcji.

## Przykład implementacji (Python, SDK)
```csharp
// Przykład użycia Azure Machine Learning SDK w C#
using Azure.AI.MachineLearning;
using Azure.AI.MachineLearning.Models;
using Azure.Identity;

var credential = new DefaultAzureCredential();
var mlClient = new MachineLearningClient(
	new Uri("https://<your-workspace-name>.<region>.ml.azure.com"),
	credential);

// Załaduj dane, zdefiniuj eksperyment, wytrenuj model
// ...

// Publikacja modelu jako endpoint
var endpoint = new OnlineEndpoint(
	name: "my-endpoint",
	description: "Endpoint dla modelu AI"
);
mlClient.OnlineEndpoints.CreateOrUpdate(endpoint);
```

## Ważne informacje
- Obsługa pracy zespołowej i zarządzania uprawnieniami.
- Integracja z GitHub, Azure DevOps, Power BI.
- Wsparcie dla MLOps, automatyzacji i monitorowania.
- Możliwość pracy w trybie no-code, low-code i full-code.
- Rozliczanie za wykorzystane zasoby obliczeniowe i przechowywanie danych.

---
[⟵ Powrót do spisu treści](README.md)
