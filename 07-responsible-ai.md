[⟵ Poprzedni: Generatywna AI](06-generative-ai.md) | [Następny: Szybka ściąga i pułapki ⟶](08-last-minute-cram.md)

# 7. **Responsible AI (Odpowiedzialna AI)** – zasady i etyka

![Responsible AI](assets/responsible-ai.svg)

## Czym jest **Responsible AI**?
- **Responsible AI** to zbiór zasad, praktyk i narzędzi, które mają zapewnić, że systemy sztucznej inteligencji są tworzone i wdrażane w sposób etyczny, bezpieczny, przejrzysty i sprawiedliwy. Odpowiedzialna AI minimalizuje ryzyko błędów, uprzedzeń i negatywnego wpływu na użytkowników oraz społeczeństwo.

## Kluczowe zasady Responsible AI
![Zasady Responsible AI – sześć filarów](assets/responsible-ai-principles.svg)

- **Fairness (sprawiedliwość)** – równe traktowanie wszystkich użytkowników, eliminacja dyskryminacji i biasu.
- **Reliability & Safety (niezawodność, bezpieczeństwo)** – systemy AI muszą działać zgodnie z założeniami i być odporne na błędy oraz ataki.
- **Privacy & Security (prywatność, ochrona danych)** – ochrona danych osobowych i zapewnienie bezpieczeństwa informacji.
- **Inclusiveness (inkluzywność)** – projektowanie AI z myślą o dostępności dla różnych grup użytkowników.
- **Transparency (przejrzystość)** – możliwość wyjaśnienia, jak AI podejmuje decyzje, jasność działania algorytmów.
- **Accountability (odpowiedzialność)** – jasne określenie, kto odpowiada za decyzje i skutki działania AI.

## Przykłady zastosowań Responsible AI
- Eliminacja **biasu (Bias)** w danych – np. usuwanie tendencyjnych przykładów z danych treningowych.
- **Wyjaśnialność (Explainability)** decyzji AI – stosowanie narzędzi wyjaśniających, dlaczego model podjął daną decyzję (np. SHAP, LIME).
- **Ochrona prywatności użytkowników** – anonimizacja danych, stosowanie polityk prywatności.
- **Compliance** – zgodność z regulacjami prawnymi (np. RODO, GDPR, HIPAA).
- **Monitorowanie modeli** – śledzenie skuteczności i sprawiedliwości modeli po wdrożeniu.

## Narzędzia i usługi **Azure** wspierające Responsible AI
- **Azure Machine Learning Responsible AI dashboard** – panel do monitorowania, audytu, wykrywania biasu, wyjaśniania decyzji modeli:
	- **Fairness Assessment** – porównanie wydajności modelu dla różnych grup demograficznych (np. wiek, płeć, pochodzenie). Jeśli model radzi sobie lepiej dla jednej grupy niż drugiej, to jest bias.
	- **Error Analysis** – gdzie i dla kogo model robi wiele błędów?
	- **Explainability (SHAP/LIME)** – które cechy wpłynęły na daną decyzję modelu? (Feature Importance)
	- **Causal Analysis** – czy zmienna X rzeczywiście wpływa na Y, czy to korelacja?
- **Fairlearn** – open-source'owe narzędzie do oceny i poprawy sprawiedliwości modeli ML:
	- Automatycznie mierzy bias w modelach (Group Fairness, Individual Fairness).
	- Oferuje algorytmy do zmniejszania biasu (Reductions, Threshold Optimizer).
- **InterpretML (SHAP, LIME)** – wyjaśnianie decyzji modeli:
	- **SHAP** – wartości Shapleya pokazują wkład każdej cechy w predykcję.
	- **LIME** – lokalne wyjaśnienia – co by się stało, gdybyśmy zmienili pojedynczą cechę.

## Praktyczne użycie – Bias Detection & Mitigation

![Bias Detection & Mitigation](assets/bias-detection.svg)

- **Scenariusz**: Rekrutacyjny model AI faworyzuje mężczyzn kosztem kobiet do roli inżyniera (bias w danych treningowych).
- **Detekcja**:
  1. Wytrenuj model na danych historycznych (gdzie mężczyźni byli preferowani).
  2. W Azure ML Responsible AI Dashboard sprawdź Fairness Assessment.
  3. Wynik: Model radzi sobie z 85% dokładnością dla mężczyzn, ale tylko 65% dla kobiet → **BIAS DETECTED**.
- **Mitygacja**:
  - **Upstream**: Zbierz więcej CV od kobiet (data augmentation), usuń zmienne powiązane z płcią.
  - **Model level**: Użyj Class Weighting (wyższe kary za błędy dla mniejszości), zastosuj Fairlearn Reductions.
  - **Downstream**: Ustaw threshold decyzji inaczej dla różnych grup, by wyrównać FPR między grupami.
  - **Monitoring**: Co miesiąc sprawdzaj Fairness, czy nowe dane znowu nie wprowadzają biasu.

- **Azure AI Content Safety** – wykrywanie i blokowanie szkodliwych treści generowanych lub podawanych przez AI: mowa nienawiści, przemoc, treści seksualne, samookaleczenie. Dostępna jako osobna usługa API.

![Azure AI Content Safety](assets/content-safety.svg)

- **Monitorowanie modeli** – automatyczne śledzenie skuteczności, driftu danych i potencjalnych problemów etycznych.
- **Compliance Manager** – wsparcie dla zgodności z regulacjami prawnymi (ISO, GDPR, HIPAA, SOC).
- **Data Privacy Toolkit** – narzędzia do anonimizacji i ochrony danych.
- **Azure Policy i RBAC** – kontrola dostępu i egzekwowanie polityk zgodności w usługach AI.

[⟵ Poprzedni: Generatywna AI](06-generative-ai.md) | [Następny: Szybka ściąga i pułapki ⟶](08-last-minute-cram.md)
