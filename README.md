# Lost & Found AI

An AI-powered prototype that classifies photographs of lost or found college campus items, maps them to campus Lost & Found categories, and displays the prediction confidence score through a Gradio web interface.

## Problem Statement
In colleges, students frequently lose or find everyday items such as water bottles, bags, headphones, shoes, books, mobile phones, and laptops. Sorting and searching through lost-and-found items manually is slow and difficult.

## Objective
Build a lightweight AI-powered Lost & Found prototype where a user can upload a photograph of an item, identify the object using a pre-trained Vision Transformer (ViT) model, map it to a Lost & Found category, and view the model's confidence score.

## Features
- **Automated Object Identification:** Classifies uploaded item photos using a pre-trained Vision Transformer (`google/vit-base-patch16-224`).
- **Category Mapping:** Maps raw ImageNet predictions into 7 campus Lost & Found categories (`Electronics`, `Bags & Wallets`, `Bottles & Containers`, `Books & Stationery`, `Clothing & Footwear`, `Personal Accessories`, `Sports & Musical Gear`).
- **Confidence Score Display:** Shows the softmax probability percentage and warns the user if confidence is below 40%.
- **Simple Web UI:** Clean Gradio interface with image upload and `Lost Item` / `Found Item` status selection.

## AI/ML Approach & Model Used
- **Model:** `google/vit-base-patch16-224` (Vision Transformer by Google Research via Hugging Face `transformers`).
- **Pre-trained Knowledge:** Pre-trained on ImageNet-21k (14 million images) and fine-tuned on ImageNet-1k (1,000 everyday object categories).
- **Why Pre-trained:** Training a Vision Transformer from scratch requires millions of labeled images and heavy GPU compute. Using pre-trained inference provides reliable recognition of common items while keeping the project lightweight.

## Technologies Used
- **Language:** Python 3
- **Environment:** Google Colab
- **AI/ML Libraries:** Hugging Face `transformers`, PyTorch (`torch`), Pillow (`PIL`)
- **Interface:** Gradio
- **Version Control:** Git & GitHub

## Application Workflow
```text
User
 ↓
Upload item image
 ↓
Image preprocessing (Convert to RGB, resize to 224x224, normalize)
 ↓
Pre-trained Vision Transformer (ViT) model inference
 ↓
Object prediction + Softmax confidence score
 ↓
Map prediction to a Lost & Found category
 ↓
Display Object + Category + Confidence + Status in Gradio UI

## Example Results

| Uploaded Image | Predicted Object | Category | Confidence |
| :--- | :--- | :--- | :--- |
| `backpack.jpg` | Backpack | Bags & Wallets | 98.54% |
| `headphones.jpg` | Headphone | Electronics | 94.12% |
| `water_bottle.jpg` | Water Bottle | Bottles & Containers | 96.80% |

---

## Repository Structure

```text
Lost-and-Found-AI/
│
├── README.md
├── Lost_and_Found_AI.ipynb
├── requirements.txt
├── screenshots/
└── sample_images/
```

---

## How to Run the Project

### Method 1: Google Colab (Recommended)
1. Open `Lost_and_Found_AI.ipynb` in Google Colab.
2. Run all cells sequentially from top to bottom (`Shift + Enter`).
3. Click the public Gradio link (`*.gradio.live`) generated in the final cell to open the interface and test with sample images.

### Method 2: Run Locally on Laptop
1. Clone this repository:
   ```bash
   git clone [https://github.com/HARISH-BN890/Lost-and-Found-AI.git](https://github.com/HARISH-BN890/Lost-and-Found-AI.git)
   cd Lost-and-Found-AI
   ```
2. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Open and run `Lost_and_Found_AI.ipynb` in Jupyter Notebook or VS Code.

---

## Limitations

- A general pre-trained image classifier may not recognise every college lost-and-found item correctly (for example, college ID cards or specific lab manuals that are not part of the 1,000 ImageNet classes).
- The confidence score represents mathematical probability across known classes and is not an absolute guarantee of correctness.
- Similar-looking objects or cluttered backgrounds may confuse the model.
- This is an educational student prototype, not a production-level college management system.

---

## Future Improvements

- Create a custom dataset of common college lost-and-found objects and **fine-tune** the Vision Transformer model.
- Implement **image similarity matching** using feature embeddings to automatically match a "Lost" item photo with visually similar "Found" item reports.
- Connect a database (such as SQLite or PostgreSQL) to store item reports along with **campus location and date/time** details.

---

## Author

**Harish Naidu BN**  
3rd-Year B.Tech — Computer Science & Engineering (AI & ML)  
Built as a practical AI/ML mini-project demonstrating pre-trained model inference, image classification, and Gradio deployment.
