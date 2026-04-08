[⟵ Poprzedni: Azure OpenAI](15-azure-openai.md) | [Następny: Azure Machine Learning ⟶](17-azure-machine-learning.md)

# Azure AI Foundry


![Azure AI Foundry](assets/azure-ai-foundry.svg)

## Opis usługi
Azure AI Foundry to platforma do zarządzania, katalogowania i wdrażania modeli AI w środowisku Azure. Umożliwia organizacjom centralne przechowywanie modeli, zarządzanie ich wersjami, udostępnianie modeli zespołom oraz monitorowanie ich wykorzystania i wydajności. Foundry wspiera zarówno modele własne, jak i modele open source oraz komercyjne.

## Kluczowe funkcje
- **Katalog modeli (Model Catalog)** – centralna baza modeli AI: modele Microsoft (GPT-4, Phi-3), open source (Llama, Mistral, Falcon), modele partnerów. Umożliwia przeglądanie, ewaluację i szybkie wdrażanie.
- **Prompt Flow** – narzędzie do orkiestracji przepływów AI: budowa pipeline’ów łączących LLM, narzędzia, retrieval i logikę. Używane do RAG i wielostopniowych aplikacji AI.
- **AI Hub i AI Project** – środowisko pracy zespołowej: zarządzanie połączeniami, zasobami, dostępem i eksperymentami.
- **Ewaluacja modeli (Evaluation)** – porównywanie jakości modeli i promptów na własnych danych testowych (metryki: coherence, groundedness, fluency, relevance).
- **Wersjonowanie modeli** – śledzenie zmian i historii modeli.
- **Wdrażanie modeli** – szybkie publikowanie modeli jako endpointy REST API (managed online endpoints).
- **Zarządzanie dostępem** – kontrola RBAC, kto może korzystać z danego modelu lub projektu.
- **Monitorowanie wydajności** – analiza wykorzystania, skuteczności i błędów modeli po wdrożeniu.
- **Integracja z Azure Machine Learning** – płynne wdrażanie i zarządzanie cyklem życia modeli (MLOps).
- **Responsible AI** – wbudowane dashboardy Responsible AI, content safety i ewaluacja fairness.

## Azure Foundry Agent Service – budowanie agentów AI

![AI Agent Lifecycle](assets/agent-lifecycle.svg)

- **Co to jest agent**: Aplikacja AI, która używa LLM do rozumowania i podejmowania autonomicznych decyzji. Różni się od chatbota – agent może korzystać z narzędzi, uzyskiwać dostęp do danych i wykonywać wielokrokowe zadania.
- **Komponenty agenta**:
  - **Model (LLM)** – GPT-4, Llama, DeepSeek (wybierz z katalogów Foundry)
  - **Instructions** – prompt systemowy, cele, ograniczenia
  - **Tools** – wyszukiwarka, dostęp do plików, API, Azure DevOps, kod interpreter
- **Trzy typy agentów**:
  - **Prompt Agents** – bez kodu, tylko instrukcje + narzędzia, szybkie prototypowanie
  - **Workflow Agents** – deklaratywna orkiestracja, wielokrokowe procesy, YAML, decyzje logiczne
  - **Hosted Agents** – kod-based (Agent Framework, LangGraph), pełna kontrola nad logiką
- **Lifecycle agenta**:
  1. **Create** – definiuj w portalu lub kodzie
  2. **Test** – chat playground, testuj narzędzia, waliduj logikę
  3. **Trace** – inspekcja każdego wywołania modelu i tool-call
  4. **Evaluate** – automatyczne oceny jakości (coherence, fluency, relevance)
  5. **Publish** – stable endpoint, versioning
  6. **Monitor** – dashboard metryki, performance monitoring, błędy
- **Built-in Tools**: web search, file search, memory, code interpreter, MCP (Model Context Protocol) servers
- **Integration**: Foundry IQ (knowledge base dla agentów), Azure AI Search (vector store), Microsoft 365 Copilot
- **Security**: Microsoft Entra identity, content filters, XPIA (Cross-Prompt Injection Attacks) protection, private networking

## Przykłady użycia (Use Cases)
- Udostępnianie modeli AI zespołom deweloperskim i analitycznym.
- Zarządzanie cyklem życia modeli w dużych organizacjach.
- Monitorowanie skuteczności modeli wdrożonych w produkcji.
- Szybkie wdrażanie modeli open source do środowiska chmurowego.
- Zapewnienie zgodności i bezpieczeństwa modeli AI.

## Przykład implementacji (C#)
```csharp
// Azure AI Foundry – wywołanie modelu z Model Catalog (SDK: Azure.AI.Inference)
using Azure;
using Azure.AI.Inference;

var endpoint = new Uri("https://<your-project>.services.ai.azure.com/models");
var credential = new AzureKeyCredential(Environment.GetEnvironmentVariable("AZURE_AI_FOUNDRY_KEY")!);

var client = new ChatCompletionsClient(endpoint, credential);

var options = new ChatCompletionsOptions
{
    Messages =
    {
        new ChatRequestSystemMessage("Jesteś ekspertem AI. Odpowiadaj zwięźle po polsku."),
        new ChatRequestUserMessage("Wyjaśnij czym jest Prompt Flow w Azure AI Foundry.")
    },
    Model = "gpt-4o", // lub Phi-3, Llama, Mistral z Model Catalog
    Temperature = 0.7f,
    MaxTokens = 500
};

var response = await client.CompleteAsync(options);
Console.WriteLine(response.Value.Content);
Console.WriteLine($"Model: {response.Value.Model}, Tokeny: {response.Value.Usage.TotalTokens}");
```

## Ważne informacje
- Ułatwia zarządzanie dużą liczbą modeli w organizacji.
- Wspiera standardy MLOps i automatyzację wdrożeń.
- Integracja z narzędziami CI/CD i monitorowaniem.
- Zapewnia zgodność z regulacjami i bezpieczeństwo danych.
- Rozliczanie za wykorzystanie zasobów i liczbę endpointów.

---
[⟵ Poprzedni: Azure OpenAI](15-azure-openai.md) | [Następny: Azure Machine Learning ⟶](17-azure-machine-learning.md)
