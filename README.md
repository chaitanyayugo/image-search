# 📸 Elite Serverless Reverse Image Search Engine

A high-performance, completely serverless reverse image search engine built entirely on GitHub infrastructure. It utilizes deep learning vector embeddings to run visual matching workflows without requiring external databases or paid cloud infrastructure.

🚀 **[Live Demo Link](https://github.io)** *(Replace with your actual GitHub Pages URL)*

---

## 🛠️ System Architecture

The engine splits computational loads efficiently between automated cloud processes and client-side browser execution:

1. **The Vector Storage Asset (`images/`)**: Houses target image libraries.
2. **The Cloud Indexer Engine (`GitHub Actions`)**: An automated Python pipeline that boots up on code pushes. It uses OpenAI's pre-trained **CLIP** model (`clip-vit-base-patch32`) to extract visual features from new assets and writes them into a unified, flat vector cache file.
3. **The Web Client Interface (`GitHub Pages`)**: A responsive UI utilizing `Transformers.js` to extract semantic features from user-uploaded queries directly inside the user's browser, matching vectors locally via **Cosine Similarity**.

---

## ✨ Features

* **Zero Hosting Cost**: Runs entirely inside GitHub actions, static file repositories, and native browser instances.
* **Incremental Processing Caching**: The pipeline skips older, pre-processed files to minimize processing runtimes and avoid API throttling.
* **Flip-Invariant Processing**: The backend script duplicates database vectors into mirrored options, accommodating reversed product photos seamlessly.
* **Multi-Angle Rotation Support**: The frontend generates 4-stage rotational canvas variations (0°, 90°, 180°, 270°) at query time to correct skewed user images automatically.

---

## 🚀 How to Add New Assets to the Index

To grow your visual search catalog, follow these simple steps:

1. Place your new product images inside the `./images/` directory.
2. Ensure images are clean and saved in standard formats (`.jpg`, `.png`, `.webp`).
3. Commit and push the files directly to your `main` branch:
   ```bash
   git add images/
   git commit -m "add: new product variations to search inventory"
   git push origin main
   ```
4. Navigating to your repository's **Actions** tab will show the automation script compiling the mathematical update instantly.

---

## 💻 Local Setup and Development

If you want to run this project on your local machine for modifications:

1. Clone this repository:
   ```bash
   git clone https://github.com
   cd your-repo-name
   ```
2. Spin up a local static server to circumvent CORS browser blocks:
   ```bash
   # If you have Python installed
   python -m http.server 8000
   ```
3. Open your browser and navigate to `http://localhost:8000`.
