


[⟵ Poprzedni: Podstawy uczenia maszynowego](03-machine-learning.md) | [Następny: Natural Language Processing ⟶](05-nlp.md)

# 4. **Computer Vision** na **Azure**

## Czym jest **Computer Vision**?
- **Computer Vision** to dziedzina AI zajmująca się analizą i interpretacją obrazów oraz wideo przez komputer. Pozwala na automatyczne rozpoznawanie, klasyfikowanie i interpretowanie zawartości wizualnej, co znajduje zastosowanie w wielu branżach.

## Typowe zadania
- **Przykładowy przepływ Computer Vision:**

![Computer Vision - przepływ](assets/computer-vision.svg)

- **Klasyfikacja obrazów (Image Classification)** – przypisywanie etykiet do całych obrazów (np. rozpoznawanie gatunku zwierzęcia na zdjęciu).
- **Detekcja obiektów (Object Detection)** – lokalizowanie i klasyfikowanie wielu obiektów na jednym obrazie (np. wykrywanie samochodów na drodze).
- **OCR (Optical Character Recognition)** – rozpoznawanie tekstu na obrazach, digitalizacja dokumentów papierowych (np. faktury, paragony, umowy).
- **Rozpoznawanie twarzy (Face Recognition)** – identyfikacja osób, analiza emocji, weryfikacja tożsamości.
- **Detekcja anomalii (Anomaly Detection)** – wykrywanie nietypowych wzorców lub defektów na obrazach (np. kontrola jakości w produkcji, wykrywanie uszkodzeń na liniach montażowych).

## Usługi **Azure**

- **Azure AI Vision** – kompleksowa usługa do analizy obrazów i wideo. Umożliwia:
	- Klasyfikację obrazów (Image Classification)
	- Detekcję obiektów (Object Detection)
	- OCR (rozpoznawanie tekstu na obrazach)
	- Analizę cech wizualnych (np. kolory, kształty, tagi)
	- Moderację treści (wykrywanie treści nieodpowiednich)
	- **Segmentację obrazów (Image Segmentation)** – wyodrębnianie obszarów pikseli przynależących do różnych obiektów na obrazie
	- **Analizę przestrzenną (Spatial Analysis)** – śledzenie ruchu osób, liczenie w strefach, mierzenie dystansów w czasie rzeczywistym z kamer
	- Wykrywanie marek (Brand Detection) i znanych osób (Celebrity Detection)

- **Azure AI Custom Vision** – trenowanie własnych modeli klasyfikacji i detekcji obiektów bez pisania kodu:
	- Wgrywanie i etykietowanie własnych zdjęć (data labeling)
	- Trenowanie modelu jednym kliknięciem
	- Eksport gotowego modelu do Edge/ONNX/CoreML/TensorFlow
	- Dwa tryby: **Image Classification** (co jest na zdjęciu?) i **Object Detection** (gdzie jest obiekt?)

- **Azure AI Document Intelligence** (dawniej Form Recognizer) – automatyczna ekstrakcja danych ze strukturyzowanych dokumentów:
	- Odczytywanie par klucz-wartość, tabel i pól formularzy
	- Gotowe modele: **Invoice** (faktury), **Receipt** (paragony), **ID Document** (dowody), **Business Card**
	- Możliwość trenowania własnych modeli na niestandardowych typach dokumentów

- **Azure AI Face** – specjalistyczna usługa do rozpoznawania i analizy twarzy. Pozwala na:

![Azure AI Face](assets/face.svg)

	- Detekcję i identyfikację twarzy na zdjęciach i wideo
	- Analizę emocji, wieku, płci, zarostu, okularów, pozycji głowy
	- Weryfikację tożsamości (np. logowanie biometryczne)
	- Grupowanie i porównywanie twarzy
	- **Face Liveness Detection** – wykrywanie żywej osoby (ochrona przed atakami z użyciem zdjęć lub wideo)
	- **Ograniczony dostęp (Limited Access)** – identyfikacja i weryfikacja twarzy wymagają formalnej akceptacji przez Microsoft

## Przykłady zastosowań
- **Automatyczna moderacja zdjęć** w mediach społecznościowych (usuwanie treści nieodpowiednich)
- **Weryfikacja tożsamości** w bankowości i systemach bezpieczeństwa (biometria twarzy)
- **Digitalizacja dokumentów** – automatyczne odczytywanie danych z faktur, paragonów, umów (OCR)
- **Wykrywanie defektów** na liniach produkcyjnych (detekcja anomalii, kontrola jakości)
- **Systemy monitoringu** – wykrywanie podejrzanych zachowań lub obiektów
- **Aplikacje dla osób niewidomych** – opisywanie otoczenia na podstawie obrazu z kamery

[⟵ Poprzedni: Podstawy uczenia maszynowego](03-machine-learning.md) | [Następny: Natural Language Processing ⟶](05-nlp.md)
