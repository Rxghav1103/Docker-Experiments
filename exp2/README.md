# 🔹 Experiment 2: Run a Streamlit App with Docker

This experiment demonstrates how to use Docker to containerize and run a **Streamlit** application that draws a customizable spiral using sliders.

---

## 📁 Folder Structure

```
exp2/
├── Dockerfile
├── requirements.txt
├── streamlit_app.py
├── exp2 1.jpg         # Output screenshot
└── exp2 2.jpg         # VS Code project view
```

---

## 🧠 What This Does

- Builds a Streamlit app using `streamlit`, `altair`, and `pandas`.
- Allows the user to control the number of points and turns in a spiral.
- Containerizes the app with all necessary Python and system dependencies.

---

## 💻 `streamlit_app.py`

```python
from collections import namedtuple
import altair as alt
import math
import pandas as pd
import streamlit as st

st.header("Streamlit Docker")

with st.echo(code_location='below'):
    total_points = st.slider("Number of points in spiral", 1, 5000, 2000)
    num_turns = st.slider("Number of turns in spiral", 1, 100, 9)

    Point = namedtuple('Point', 'x y')
    data = []

    points_per_turn = total_points / num_turns

    for curr_point_num in range(total_points):
        curr_turn, i = divmod(curr_point_num, points_per_turn)
        angle = (curr_turn + 1) * 2 * math.pi * i / points_per_turn
        radius = curr_point_num / total_points
        x = radius * math.cos(angle)
        y = radius * math.sin(angle)
        data.append(Point(x, y))

    st.altair_chart(alt.Chart(pd.DataFrame(data), height=500, width=500)
        .mark_circle(color='#0068c9', opacity=0.5)
        .encode(x='x:Q', y='y:Q'))
```

---

## 📦 `requirements.txt`

```
streamlit==1.6.0
altair==4.2.0
pandas==1.3.3
protobuf==3.20.*
```

---

## 🐳 Dockerfile

```dockerfile
FROM python:3.9-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

# Copy local code
COPY . .

# Install Python dependencies
RUN pip install -r requirements.txt

EXPOSE 8501

# Health check to ensure app is live
HEALTHCHECK CMD curl --fail http://localhost:8501/_stcore/health

ENTRYPOINT ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

## 🚀 How to Run This App

### ✅ Step 1: Build the Docker Image

```bash
cd exp2
docker build -t streamlit-spiral .
```

### ▶️ Step 2: Run the Docker Container

```bash
docker run -p 8501:8501 streamlit-spiral
```

### 🌐 Open in Browser

Visit: [http://localhost:8501](http://localhost:8501)

---

## 🖼️ Screenshots

### ✅ Output Screenshot

![Working Streamlit App](exp2%201.jpg)

---

### 👨‍💻 VS Code Project Screenshot

![VS Code View](exp2%202.jpg)

---

## ✅ Requirements

- Docker installed → [Install Docker](https://docs.docker.com/get-docker/)
- Basic knowledge of Docker and Python

---

## 📢 License

MIT License

---

> 🌟 Learn how to serve interactive Python web apps in isolated containers using Streamlit and Docker!
```
