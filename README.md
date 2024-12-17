# 📂 YouTube Embedding Datasets (SeahorseDB)

This repository provides datasets containing **CLIP-generated embeddings** and metadata for YouTube video scenes. The embeddings are extracted based on **timestamps** indicating specific scenes within the videos. These datasets are part of the **SeahorseDB** collection, accessible on Hugging Face.

---

## 📊 Dataset Overview

| Dataset Name           | Size       | Description                                  |
|------------------------|------------|----------------------------------------------|
| `youtube-1M-dataset`   | 1 Million  | Contains CLIP embeddings and metadata for 1M YouTube video scenes. |
| `youtube-2M-dataset`   | 2 Million  | Contains CLIP embeddings and metadata for 2M YouTube video scenes. |
| `youtube-15M-dataset`  | 15 Million | Contains CLIP embeddings and metadata for 15M YouTube video scenes. |

All datasets are stored in **Parquet** format for efficient storage and processing.

---

## 🗃️ Dataset Structure

Each dataset includes the following fields:

| Field Name         | Data Type       | Description                                                                 |
|--------------------|-----------------|-----------------------------------------------------------------------------|
| `feature`          | sequence        | 1024-dimensional CLIP-generated embedding vector representing the scene.    |
| `title`            | string          | Title of the YouTube video.                                                 |
| `channel_name`     | string          | Name of the YouTube channel hosting the video.                              |
| `video_id`         | string          | Unique identifier for the YouTube video.                                    |
| `timestamp`        | string          | Timestamp indicating the specific scene in the video.                       |
| `id`               | int64           | Unique identifier for each row.                                             |
| `__index_level_0__`| int64           | Dummy field                                                                 |

---

## 📥 How to Access

The datasets can be downloaded directly from **Hugging Face**:

- [SeahorseDB - YouTube Embeddings (1M, 2M, 15M)](https://huggingface.co/datasets/dnotitia/SeahorseDB-dataset)

You can load the Parquet files using libraries like **Pandas** or **PyArrow**.

### Example in Python:

```python
import pandas as pd

# Load the 1M dataset
df = pd.read_parquet("path/to/youtube-1M-dataset.parquet")
print(df.head())

# Access embeddings and metadata
embeddings = df['feature'].tolist()  # 1024-dimensional embeddings for scenes
timestamps = df['timestamp'].tolist()
metadata = df['title'].tolist()
