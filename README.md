<div align="center">

# Анализ отзывов отелей Booking.com

**Предсказание рейтинга отелей Европы · Kaggle [sf-booking](https://www.kaggle.com/competitions/sf-booking)**

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

Построение модели, предсказывающей рейтинг отеля (`reviewer_score`) по табличным и инженерным признакам. Если предсказание сильно расходится с фактическим рейтингом, объект можно отправить на дополнительную проверку.

---

## Результаты

| Этап | Ноутбук | MAPE |
|------|---------|------|
| Baseline (без feature engineering) | `EDA_Project_3_model.ipynb` | 0.141 |
| После EDA, FE и отбора признаков | `EDA_Feature_Engineering_Отели_Европы_Соревнов.ipynb` | 0.139 |

MAPE считается через `sklearn.metrics.mean_absolute_percentage_error` (доля, не проценты).

---

## Структура проекта

```text
eda-feature-engineering-europe-hotels-kaggle/
├── data/
│   └── hotels.csv          # не в git, см. раздел «Данные»
├── kaggle_version/
│   ├── hotels-of-europe.ipynb   # версия для Kaggle (train/test + submission)
│   └── my_submit.csv            # пример submission-файла
├── EDA_Feature_Engineering_Отели_Европы_Соревнов.ipynb   # основной ноутбук
├── EDA_Project_3_model.ipynb   # baseline до предобработки
├── README.md
├── LICENSE
├── .gitignore
└── requirements.txt
```

### Ноутбуки

- **`EDA_Project_3_model.ipynb`** — baseline: удаление object-колонок, `RandomForestRegressor`, MAPE ≈ 0.141.
- **`EDA_Feature_Engineering_Отели_Европы_Соревнов.ipynb`** — полный pipeline: EDA → очистка → `country` / `is_foreign` → encoding → VIF → chi² → модель, MAPE ≈ 0.139.
- **`kaggle_version/hotels-of-europe.ipynb`** — та же логика для Kaggle (`hotels_train.csv`, `hotels_test.csv`, submission).

---

## Данные

Исходный датасет большой (>170 МБ), в репозиторий не включён.

1. Скачайте данные: [Google Диск](https://drive.google.com/drive/folders/1rZdq635ZjQZr_6nwKiouQrfpc_6bdOaI) или [Kaggle sf-booking](https://www.kaggle.com/competitions/sf-booking/data).
2. Создайте папку `data/`.
3. Для локального ноутбука положите **`hotels.csv`** в `data/`.
4. Для Kaggle-версии нужны `hotels_train.csv`, `hotels_test.csv`, `submission.csv` (пути в ноутбуке — `/kaggle/input/...`).

**Признаки в сыром CSV:** `hotel_address`, `review_date`, `average_score`, `reviewer_nationality`, `negative_review`, `positive_review`, word counts, `reviewer_score` (таргет), `tags`, `days_since_review`, `lat`, `lng` и др.

**Инженерные признаки в модели:** `country`, `is_foreign`, one-hot по стране и nationality (после `BinaryEncoder`).

---

## Как запустить

```bash
git clone https://github.com/theKerimKerimov/eda-feature-engineering-europe-hotels-kaggle.git
cd eda-feature-engineering-europe-hotels-kaggle
```

```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/macOS:
source venv/bin/activate

pip install -r requirements.txt
jupyter lab
```

Откройте `EDA_Feature_Engineering_Отели_Европы_Соревнов.ipynb` и выполните **Run All** (нужен `data/hotels.csv`).

---

## Зависимости

См. [`requirements.txt`](requirements.txt). Минимальная версия Python: **3.11**.

---

## Автор

**Karim** · [k.kerimow@yandex.ru](mailto:k.kerimow@yandex.ru)
