[⟵ Poprzedni: Azure AI Foundry](16-azure-ai-foundry.md)

# Azure Machine Learning


![Przegląd usług Azure AI](assets/azure-ai-overview.svg)

## Opis usługi
Azure Machine Learning (Azure ML) to kompleksowa platforma do budowy, trenowania, wdrażania i zarządzania modelami uczenia maszynowego w chmurze. Umożliwia zarówno pracę no-code/low-code (Designer, AutoML), jak i zaawansowane projekty kodowane w Pythonie. Wspiera cały cykl życia ML, automatyzację, MLOps i integrację z innymi usługami Azure.

## Kluczowe funkcje
- **Projektowanie pipeline'ów ML (Designer)** – graficzny interfejs drag & drop do budowy procesów ML bez kodowania.
- **Automated ML (AutoML)** – automatyczne dobieranie algorytmów i hiperparametrów. Obsługuje klasyfikację, regresję, klasteryzację, szeregi czasowe, Computer Vision i NLP.
- **Trenowanie modeli** – obsługa frameworków: scikit-learn, PyTorch, TensorFlow, XGBoost.
- **Wdrażanie modeli** – publikacja jako REST endpointy: **Managed Online Endpoint** (real-time), **Batch Endpoint** (wsadowe).
- **Monitorowanie i rejestracja modeli (Model Registry)** – wersjonowanie, śledzenie metryk, audyt.
- **Zarządzanie danymi (Data Assets)** – rejestracja, wersjonowanie i przetwarzanie zbiorów danych.
- **Compute clusters i compute instances** – klastry do trenowania (skalowalne) i instancje do dewelopmentu/notebooków.
- **Data Labeling** – narzędzie do etykietowania danych (obrazy, tekst) z opcją asysty ML.
- **MLOps** – automatyzacja wdrożeń ML: integracja z GitHub, Azure DevOps, CI/CD dla modeli ML.
- **Responsible AI Dashboard** – kompleksowy panel do analizy modeli pod kątem:
	- **Fairness** (wykrywanie dyskryminacji między grupami)
	- **Error Analysis** (analiza błędów modelu)
	- **Explainability** (SHAP, LIME – wyjaśnienie decyzji modelu)
	- **Data Explorer** (eksploracja danych wejściowych)
	- **Causal Analysis** (przyczynowość i kontrfaktualne przykłady)
- **Feature Store** – centralne repozytorium cech ML do ponownego wykorzystania między projektami.
- **Environments** – zarządzanie środowiskami Python (kontenery Docker) do reprodukowalnego trenowania.

## Przykłady użycia (Use Cases)
- Budowa modeli predykcyjnych dla finansów, sprzedaży, produkcji.
- Automatyzacja analizy danych i raportowania.
- Szybkie prototypowanie rozwiązań AI przez osoby nietechniczne (Designer).
- Wdrażanie modeli do aplikacji biznesowych i API.
- Monitorowanie jakości i wydajności modeli w produkcji.

## Przykład implementacji (C#)
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
[⟵ Poprzedni: Azure AI Foundry](16-azure-ai-foundry.md)
