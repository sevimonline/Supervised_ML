# Supervised_ML

**Purpose:**  
Scrape second-hand car listings from [Arabam.com](https://www.arabam.com/) for 20 popular car brands including Hyundai, Audi, BMW, Mercedes-Benz, etc.

**Libraries Used:**  
`requests`, `BeautifulSoup`, `pandas`, `time`, `fake_useragent`

**Target Features:**
### 📥 Hedeflenen Değişkenler

#### 🚗 Araç Temel Bilgileri
| Değişken Adı     | Açıklama                        | Örnek Değer              |
|------------------|----------------------------------|---------------------------|
| `marka`          | Araç markası                    | Citroen                   |
| `seri`           | Model serisi                    | C3                        |
| `model`          | Alt model ve donanım paketi     | 1.2 PureTech Feel Bold   |
| `yil`            | Model yılı                      | 2021                      |
| `kilometre`      | Araç kilometresi                | 56.000 km                 |
| `vites_tipi`     | Şanzıman türü                   | Düz / Otomatik            |
| `yakit_tipi`     | Yakıt türü                      | Benzin / Dizel / Hibrit   |
| `kasa_tipi`      | Araç kasa tipi                  | Hatchback / Sedan         |
| `cekis_tipi`     | Araç çekiş sistemi              | Önden Çekiş / 4x4         |
| `motor_hacmi`    | Motor hacmi (cc)                | 1199 cc                   |
| `motor_gucu`     | Motor gücü (hp)                 | 83 hp                     |
| `renk`           | Araç rengi                      | Gri                       |
| `fiyat`          | Araç satış fiyatı               | 728.000 TL                |
| `konum`          | Araç ilanının şehir bilgisi     | Sakarya / Adapazarı       |
| `kimden`         | Satıcı türü                     | Galeriden / Sahibinden    |

---

#### 📋 İlan ve Detay Bilgileri
| Değişken Adı     | Açıklama                        | Örnek Değer              |
|------------------|----------------------------------|---------------------------|
| `ilan_no`        | İlan numarası                   | 28145499                  |
| `ilan_tarihi`    | İlanın yayınlanma tarihi        | 20 Mart 2025              |
| `aciklama`       | Açıklama metni (opsiyonel)      | "Tramersiz, ilk elden..." |
| `boya_durumu`    | Araçta boya/değişen var mı      | Tamamı orijinal           |
| `hasar_kaydi`    | Tramer tutarı                   | Belirtilmemiş             |
| `takasa_uygun`   | Takas imkanı var mı             | Takasa Uygun              |

---

### 🛠️ Kullanılacak Araçlar & Kütüphaneler

- `requests` – Sayfa HTML içeriğini almak için  
- `BeautifulSoup` – HTML parsing ve veri çıkarımı  
- `pandas` – Veriyi tablo haline getirme ve kaydetme  
- `time`, `random` – Etik scraping ve zamanlama  
- `fake_useragent` – Bot tespiti riskini azaltmak için sahte tarayıcı başlıkları

---

### 📌 Notlar

- Veriler sayfa bazlı olarak gezilecek (`?page=1`, `?page=2`, ...)  
- Dönüşüm gerektiren sütunlar: `fiyat`, `kilometre`, `motor_hacmi` → sayıya çevrilecek  
- Eksik ya da "Belirtilmemiş" olan alanlar `NaN` olarak işaretlenecek  
- `marka` değişkeni URL’ye göre veya filtre sekmesinden dinamik alınabilir

---

### 💾 Örnek Kayıt (Scraped Row Formatı)

```json
{
  "marka": "Citroen",
  "model": "C3 1.2 PureTech Feel Bold",
  "yil": 2021,
  "kilometre": 56000,
  "vites_tipi": "Düz",
  "yakit_tipi": "Benzin",
  "motor_hacmi": 1199,
  "motor_gucu": 83,
  "cekis_tipi": "Önden Çekiş",
  "kasa_tipi": "Hatchback/5",
  "renk": "Gri",
  "konum": "Sakarya",
  "fiyat": 728000,
  "ilan_no": 28145499,
  "ilan_tarihi": "2025-03-20",
  "kimden": "Galeriden",
  "boya_durumu": "Tamamı orijinal",
  "hasar_kaydi": null,
  "takasa_uygun": "Evet"
}
---

## 🧼 2. Data Preprocessing & Feature Engineering

**Data Cleaning:**
- Handling missing or null values  
- Converting `object` types to numerical (via label encoding or one-hot encoding)  
- Formatting numeric columns (e.g., removing commas from prices, KM)

**Feature Engineering:**
- **Car Age:** `Car Age = 2025 - Year`
- **Engine Volume Category:** Grouping engine volumes into bins
- **Geographic Grouping:** Mapping cities to geographical regions (e.g., İstanbul → Marmara)

---

## 📊 3. Dependent Variable Analysis (Price)

**Normality Tests:**
- Shapiro-Wilk Test  
- Anderson-Darling Test  

**Transformations (if needed):**
- Log Transformation  
- Box-Cox Transformation  

**Multicollinearity Checks:**
- Pearson Correlation Heatmap  
- Variance Inflation Factor (VIF)

---

## 🔁 4. Model Validation Techniques

**Cross Validation:**
- **K-Fold CV** (k = 5 or 10)  
- **Leave-One-Out Cross Validation (LOOCV)**

**Bootstrap Sampling:**
- Bootstrapped estimation of performance metrics (e.g., R², RMSE)  
- Confidence intervals for predictions

---

## 📈 5. Regression Model Building

**Model Types:**
- Linear Regression  
- Ridge Regression  
- Lasso Regression

**Performance Metrics:**
- R², Adjusted R²  
- Mean Squared Error (MSE)  
- Root Mean Squared Error (RMSE)  
- Mean Absolute Error (MAE)

---

## ✅ 6. Regression Assumption Diagnostics

**Assumptions Checked:**
- **Normality of Residuals:** Q-Q Plot, Histogram of residuals  
- **Homoscedasticity:** Residuals vs Fitted Values Plot  
- **Multicollinearity:** VIF Scores  
- **Outliers & Influence Points:**  
  - Leverage Plots  
  - Cook’s Distance Analysis

**Bias-Variance Tradeoff:**  
- Model complexity vs error tradeoff visualization

**Endogeneity Evaluation:**  
- Discussed theoretically (e.g., possibility of omitted variable bias or IV needs)

---

## 📉 7. Prediction vs. Actual Comparison

- Scatter plot comparing actual vs predicted prices  
- Colored/marked by relevant segments (e.g., engine volume or brand)

---

## 💻 8. Streamlit Interface for Model Deployment

**Inputs:**
- Year  
- Mileage (KM)  
- Engine Volume  
- Fuel Type  
- Transmission  
- Region/City  

**Outputs:**
- Predicted Price  
- 95% Confidence Interval (via bootstrap or model's CI)

**Visual Feedback:**
- Model residual plot  
- Interactive pricing distribution based on user input

---

## 🎯 Optional Enhancements

- 🔍 Add XGBoost or LightGBM models for performance comparison  
- 🎯 SHAP or LIME for model interpretability  
- 🔁 Cron job setup for automatic data scraping and model retraining
