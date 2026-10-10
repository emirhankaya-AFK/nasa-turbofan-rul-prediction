## English

**Purpose**  
Predict remaining useful life (RUL) of turbofan engines from NASA's C-MAPSS FD001 dataset.

**Verified features**  
- 100 training engines, 100 official test engines  
- 3 operating settings, 21 sensor channels per cycle  
- Piecewise-linear training target capped at 125 cycles  
- Removal of constant/near‑constant sensors  
- Causal 5‑ and 10‑cycle rolling mean, std, trend features  
- GroupShuffleSplit validation by engine ID to avoid leakage  
- Models: Median RUL baseline, Histogram Gradient Boosting on current & causal rolling features, GRU sequence baseline (last 30 cycles)  
- Split‑conformal 90% prediction interval for the classical model  
- Evaluation metrics: MAE, RMSE, PHM08/NASA asymmetric score, late‑prediction rate, empirical coverage of 90% interval  

**Stack**  
Python‑based project; dependencies listed in `pyproject.toml` (scikit‑learn, PyTorch, etc.).

**Setup / Usage**  
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -e ".[dev,sequence]"
python scripts/download_data.py
ruff check .
pytest -q
python scripts/train_classical.py
python scripts/train_gru.py
```
Data are fetched from the official NASA C‑MAPSS Open Data page; the archive SHA‑256 and file list are stored in `data/manifest.json`.

**Testing**  
Run `pytest -q` after installing the dev dependencies.

**Limitations**  
- C‑MAPSS is a high‑fidelity simulation, not flight‑recorder data from operational aircraft.  
- FD001 contains one operating condition and one fault mode.  
- Results measure performance on this benchmark and do not validate maintenance decisions, flight safety, other engines, multiple fault modes or changing environmental conditions.

**License**  
Project code is MIT licensed. The dataset remains subject to its original publisher's terms; NASA's catalog currently does not specify a dataset license.

## Türkçe

**Amaç**  
NASA'nın C-MAPSS FD001 veri setinden turbofan motorlarının kalan kullanım ömrünü (RUL) tahmin etmek.

**Doğrulanmış özellikler**  
- 100 eğitim motoru, 100 resmi test motoru  
- 3 işletme ayarı, döngü başına 21 sensör kanalı  
- Eğitim hedefi piecewise-linear, 125 döngüyle sınırlı  
- Sabit veya neredeyse sabit sensörler model girdilerinden çıkarıldı  
- Nedensel 5‑ ve 10‑döngü ortalama, standart sapma ve trend özellikleri  
- Motor ID’sine göre GroupShuffleSplit kullanılarak sızma önlenen doğrulama  
- Modeller: Medyan RUL bazaltı, Histogram Gradient Boosting (mevcut ve nedensel kayan özellikler), 30‑döngü GRU dizisi bazaltı  
- Klasik model için bölünmüş‑konformal %90 tahmin aralığı  
- Değerlendirme metrikleri: MAE, RMSE, PHM08/NASA asimetrik skor, geç tahmin oranı, %90 aralığın emperik kapsamı  

**Yığın (Stack)**  
Python tabanlı proje; bağımlılıklar `pyproject.toml` dosyasında belirtilmiştir (scikit‑learn, PyTorch vb.).

**Kurulum / Kullanım**  
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -e ".[dev,sequence]"
python scripts/download_data.py
ruff check .
pytest -q
python scripts/train_classical.py
python scripts/train_gru.py
```
Veriler resmi NASA C‑MAPSS Açık Veri sayfasından indirilir; arşivin SHA‑256 özeti ve dosya listesi `data/manifest.json` içinde saklanır.

**Test**  
`pytest -q` komutunu geliştirme bağımlılıkları kurulduktan sonra çalıştırın.

**Sınırlamalar**  
- C‑MAPSS yüksek fidelite bir simülasyon olup gerçek uçuş kaydı verisi değildir.  
- FD001 tek bir işletme koşulu ve tek bir hata modu içerir.  
- Sonuçlar bu veri setine özgü bir benchmarktır; bakım kararları, uçuş güvenliği, diğer motorlar, çoklu hata modları veya değişen çevresel koşullar hakkında doğrulama sağlamaz.

**Lisans**  
Proje kodu MIT lisansıyla lisanslanmıştır. Veri seti orijinal yayıncısının koşullarına tabi kalır; NASA kataloğu veri seti lisansı belirtmez.

## Deutsch

**Zweck**  
Vorhersage der Restlebensdauer (RUL) von Turbinenmotoren anhand des NASA C‑MAPSS FD001 Datensatzes.

**Verifizierte Merkmale**  
- 100 Trainingsmotoren, 100 offizielle Testmotoren  
- 3 Betriebsbedingungen, 21 Sensorkanäle pro Zyklus  
- Stückweise lineares Trainingsziel, auf 125 Zyklen begrenzt  
- Konstant‑ oder nahezu konstant‑Sensoren wurden aus den Modell‑Eingängen entfernt  
- Kausale gleitende Mittelwerte, Standardabweichungen und Trends über 5 und 10 Zyklen  
- Validierung mittels `GroupShuffleSplit` nach Motoren‑ID, um Datenleckage zu vermeiden  
- Modelle: Median‑RUL‑Baseline, Histogram Gradient Boosting (aktuelle und kausale rollende Features), GRU‑Sequenz‑Baseline (letzte 30 Zyklen)  
- Das klassische Modell liefert ein geteiltes‑konformes 90 %‑Vorhersageintervall  
- Evaluationsmetriken: MAE, RMSE, PHM08/NASA asymmetrischer Score, Spät‑Vorhersage‑Rate, empirische Abdeckung des 90 %‑Intervalls  

**Stack**  
Python‑basiertes Projekt; Abhängigkeiten siehe `pyproject.toml` (z. B. scikit‑learn, PyTorch).

**Aufbau / Verwendung**  
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -e ".[dev,sequence]"
python scripts/download_data.py
ruff check .
pytest -q
python scripts/train_classical.py
python scripts/train_gru.py
```
Die Daten werden von der offiziellen NASA C‑MAPSS Open Data Seite heruntergeladen; die SHA‑256‑Prüfsumme und Dateiliste liegen in `data/manifest.json`.

**Test**  
Führe `pytest -q` nach Installation der Entwicklungsabhängigkeiten aus.

**Einschränkungen**  
- C‑MAPSS ist eine hochauflösende Simulation, keine echten Flugrekorderdaten.  
- FD001 umfasst lediglich einen Betriebszustand und einen Fehlermodus.  
- Die Ergebnisse dienen als Benchmark für dieses spezifische Dataset und validieren weder Wartungsentscheidungen, Flugsicherheit, andere Motoren, mehrere Fehlermodi noch wechselnde Umweltbedingungen.

**Lizenz**  
Der Projektcode steht unter der MIT‑Lizenz. Der Datensatz unterliegt den Bedingungen des ursprünglichen Herausgebers; der NASA‑Katalog spezifiziert keine Datensatzlizenz.
