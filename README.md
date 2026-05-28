# 🛋️ SpaceSync — Benchmarking MARL in Augmented Reality

SpaceSync is a multi-agent reinforcement learning (MARL) system that benchmarks collaborative furniture placement in simulated augmented reality rooms. Three specialized agents — layout, style, and budget — work together using real IKEA product data to furnish rooms while optimizing for space efficiency, aesthetic fit, and cost. Built with PettingZoo, the system benchmarks agent specialization quality using cosine similarity scoring across five room types.

---

## 🚀 Features

* **Three Specialized Agents working collaboratively:**
   * `layout_agent` — optimizes for space coverage, placing larger anchor furniture first
   * `style_agent` — optimizes for aesthetic coherence, selecting complementary pieces
   * `budget_agent` — optimizes for cost efficiency, staying within a configurable spending limit
* **Real IKEA Dataset Integration:** Furniture placement uses actual IKEA product dimensions and prices from two merged datasets (4,000+ items across 17 categories)
* **Cosine Similarity Benchmarking:** Each episode is scored against an ideal room profile vector, measuring how well the agents' collaborative output matches a well-furnished room
* **Target Utilization System:** Episodes run until 50%+ of floor space is covered, with dynamic reward shaping to encourage dense, realistic layouts
* **Room-Aware Filtering:** Furniture is filtered by room type (Living Room, Bedroom, Kitchen, Bathroom, Dining Room) so agents only place contextually appropriate items
* **Reward Visualization:** Automatically generates a 6-chart summary after every run covering agent rewards, space utilization, cosine similarity scores, and total spend

---

## 🧩 Tech Stack

* Python 3.12
* PettingZoo
* NumPy / Pandas
* Matplotlib
* YOLOv8
* OpenCV
* Hugging Face (`clip-vit-base-patch32`)
* IKEA Dataset (Kaggle)

---

## ⚙️ Installation & Setup

1. Clone the repository

```
git clone https://github.com/b-Karthikeya-reddy/Marl-ar-benchmark.git
```

2. Create and activate a virtual environment

```
python3 -m venv venv
source venv/bin/activate       # Mac
venv\Scripts\activate          # Windows
```

3. Install dependencies

```
pip install -r requirements.txt
```

4. Add datasets to the `datasets/` folder

```
datasets/
├── ikea_furniture.csv          # original dimensions dataset
└── ikea_new_w_prices.csv       # Kaggle IKEA dataset with prices
```

5. Run the test

```
python env/run_ikea_test.py
```

---

## 📁 Project Structure

```
Marl-ar-benchmark/
├── datasets/
│   ├── ikea_furniture.csv
│   └── ikea_new_w_prices.csv
├── env/
│   ├── ikea_furniture_env.py   # PettingZoo MARL environment (3 agents)
│   ├── room_similarity.py      # Cosine similarity scorer
│   ├── furniture_env.py        # Original prototype environment
│   └── run_ikea_test.py        # Main test runner + visualizations
├── reward_visualization.png    # Auto-generated after each run
└── README.md
```

---

## 📊 Benchmark Metrics

| Metric | Description |
|---|---|
| Space Utilization | % of room grid covered by placed furniture |
| Cosine Similarity | Similarity of placed categories to ideal room profile (0–1) |
| Agent Reward | Cumulative reward per agent per episode |
| Total Spend | Sum of all placed furniture prices vs. budget cap |

---

## 👥 Authors

* **Hamim Choudhury** — PettingZoo environment, dataset integration, agent design, testing
* **Karthikeya Reddy Basavanagoudgari** — Space utilization logic, dataset preprocessing, visualization
