# Анализ отзывов отелей Booking.com

Проект по соревнованию [Kaggle sf-booking](https://www.kaggle.com/competitions/sf-booking): построение модели, предсказывающей рейтинг отеля (`reviewer_score`) по табличным и инженерным признакам. Цель — выявлять объекты, у которых фактический рейтинг существенно расходится с предсказанным.

**Стек:** Python 3.11+, pandas, scikit-learn, category-encoders, statsmodels, Jupyter.

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

- **`EDA_Project_3_model.ipynb`** — быстрый baseline: удаление object-колонок, `RandomForestRegressor`, MAPE ≈ 0.141.
- **`EDA_Feature_Engineering_Отели_Европы_Соревнов.ipynb`** — полный pipeline: EDA → очистка → `country` / `is_foreign` → encoding → VIF → chi² → модель, MAPE ≈ 0.139.
- **`kaggle_version/hotels-of-europe.ipynb`** — та же логика для формата Kaggle (`hotels_train.csv`, `hotels_test.csv`, submission).

---

## Данные

Исходный датасет большой (>170 МБ), в репозиторий не включён.

1. Скачайте данные: [Google Диск — данные проекта](https://drive.google.com/drive/folders/1rZdq635ZjQZr_6nwKiouQrfpc_6bdOaI) или [Kaggle sf-booking](https://www.kaggle.com/competitions/sf-booking/data).
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

Karim Kerimov — 2025–2026. Учебный проект (SkillFactory / Kaggle sf-booking).
