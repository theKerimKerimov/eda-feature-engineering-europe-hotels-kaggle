<div align="center">

# Анализ отзывов отелей Booking.com

**EDA + Feature Engineering · Отели Европы · [Kaggle sf-booking](https://www.kaggle.com/competitions/sf-booking)**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![pandas](https://img.shields.io/badge/pandas-2.3-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-2.3-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.7-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)](https://matplotlib.org/)
[![Statsmodels](https://img.shields.io/badge/Statsmodels-0.14-006BA6?style=for-the-badge)](https://www.statsmodels.org/)
[![Kaggle](https://img.shields.io/badge/Kaggle-sf--booking-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/competitions/sf-booking)

[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![MAPE](https://img.shields.io/badge/MAPE-0.139-blue?style=for-the-badge)](README.md#результаты)

</div>

---

Модель предсказывает рейтинг отеля (`reviewer_score`) по табличным и инженерным признакам. Сильное расхождение предсказания с фактом — сигнал для дополнительной проверки объекта.

---

## Результаты

| Этап | Ноутбук | MAPE |
|------|---------|------|
| Baseline (без feature engineering) | [`notebooks/baseline_hotel_rating.ipynb`](notebooks/baseline_hotel_rating.ipynb) | 0.141 |
| EDA + FE + отбор признаков | [`notebooks/eda_feature_engineering_hotels_europe.ipynb`](notebooks/eda_feature_engineering_hotels_europe.ipynb) | 0.139 |

MAPE — `sklearn.metrics.mean_absolute_percentage_error` (доля, не проценты).

---

## Структура проекта

```text
eda-feature-engineering-europe-hotels-kaggle/
│
├── notebooks/                              # все ноутбуки
│   ├── baseline_hotel_rating.ipynb         # baseline-модель
│   ├── eda_feature_engineering_hotels_europe.ipynb   # основной pipeline
│   └── kaggle/                             # версия для Kaggle
│       ├── hotels_europe_kaggle.ipynb
│       └── my_submit.csv                   # пример submission
│
├── data/                                   # данные (не в git)
│   └── hotels.csv
│
├── README.md
├── LICENSE
├── requirements.txt
└── .gitignore
```

### Ноутбуки

| Файл | Описание |
|------|----------|
| [`notebooks/baseline_hotel_rating.ipynb`](notebooks/baseline_hotel_rating.ipynb) | Baseline: удаление object-колонок, `RandomForestRegressor` |
| [`notebooks/eda_feature_engineering_hotels_europe.ipynb`](notebooks/eda_feature_engineering_hotels_europe.ipynb) | Полный pipeline: EDA → FE → VIF → chi² → модель |
| [`notebooks/kaggle/hotels_europe_kaggle.ipynb`](notebooks/kaggle/hotels_europe_kaggle.ipynb) | Тот же pipeline для Kaggle (`hotels_train` / `hotels_test`, submission) |

---

## Данные

Датасет >170 МБ, в репозиторий не входит.

1. Скачать: [Google Диск](https://drive.google.com/drive/folders/1rZdq635ZjQZr_6nwKiouQrfpc_6bdOaI) или [Kaggle sf-booking](https://www.kaggle.com/competitions/sf-booking/data).
2. Положить **`hotels.csv`** в папку **`data/`** (в корне репозитория).
3. Для Kaggle-версии: `hotels_train.csv`, `hotels_test.csv`, `submission.csv` (пути в ноутбуке — `/kaggle/input/...`).

---

## Как запустить

```bash
git clone https://github.com/theKerimKerimov/eda-feature-engineering-europe-hotels-kaggle.git
cd eda-feature-engineering-europe-hotels-kaggle

python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate   # Linux / macOS

pip install -r requirements.txt
jupyter lab
```

Откройте **`notebooks/eda_feature_engineering_hotels_europe.ipynb`** → **Run All**.

> Jupyter запускайте из **корня** репозитория — ноутбуки читают данные из `../data/hotels.csv`.

---

## Зависимости

См. [`requirements.txt`](requirements.txt). Python **3.11+**.

---

## 👤 Автор

**Karim** · 2026

[![GitHub](https://img.shields.io/badge/GitHub-theKerimKerimov-181717?logo=github)](https://github.com/theKerimKerimov)<br>
[![Kaggle](https://img.shields.io/badge/Kaggle-kerimkerimov-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/kerimkerimov)<br>
[![LinkedIn](https://img.shields.io/badge/LinkedIn-kerim--kerimov-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kerim-kerimov-79323b400)<br>
[![LeetCode](https://img.shields.io/badge/LeetCode-KerimK-FFA116?logo=leetcode&logoColor=black)](https://leetcode.com/u/KerimK)<br>
[![Email](https://img.shields.io/badge/Email-k.kerimow%40yandex.ru-EA4335?logo=gmail&logoColor=white)](mailto:k.kerimow@yandex.ru)<br>
[![Telegram](https://img.shields.io/badge/Telegram-@theDagestani-26A5E4?logo=telegram&logoColor=white)](https://t.me/theDagestani)<br>

📍 Москва
