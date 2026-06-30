# Smart Waste Disposal Guide 🌍♻️

An AI-powered web application that helps users categorize waste, find safe disposal methods, learn key safety precautions, and discover recycling options. Powered by **Google Gemini API** (`gemini-2.5-flash-lite`) and built with **Flask** and **Vanilla HTML/CSS/JS**.

---

## 🚀 Key Features

*   **Intelligent Classification:** Uses Google Gemini to analyze user-provided waste descriptions and categorize them (e.g., hazardous, electronic, organic, recyclable).
*   **Structured Disposal Methods:** Provides clear, step-by-step guidance on how to properly discard the waste.
*   **Safety Precautions:** Warns users about risks (such as swollen batteries, toxic components) and details how to handle them safely.
*   **Recycling Options:** Suggests appropriate recycling programs, bins, or centers where applicable.
*   **Clean & Responsive UI:** Built with a user-friendly interface that adapts to both desktop and mobile devices.

---

## 🛠️ Tech Stack

*   **Backend:** Python, Flask, Flask-CORS
*   **AI Integration:** Google Generative AI Python SDK (`google-generativeai`)
*   **Frontend:** HTML5, CSS3, JavaScript (Fetch API)
*   **Configuration:** python-dotenv (for API Key management)

---

## 📁 Project Structure

```text
├── templates/
│   └── index.html      # Main application page (UI and styling)
├── static/
│   └── styles.css      # Static stylesheet
├── app.py              # Flask server, route handlers, and Gemini API integration
├── .env.example        # Reference file for environment variables
├── .gitignore          # Git exclusion rules
├── README.md           # Project documentation (this file)
└── requirements.txt    # Python package dependencies
```

---

## ⚙️ Setup and Installation

### 1. Clone the Repository
```bash
git clone https://github.com/Akshai-Baiju/Smart-Waste-Disposal.git
cd Smart-Waste-Disposal
```

### 2. Set Up a Virtual Environment (Recommended)
Create and activate a Python virtual environment to manage dependencies:

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
Install all required Python modules:
```bash
pip install flask flask-cors google-generativeai python-dotenv
```
*(Alternatively, create a `requirements.txt` file and run `pip install -r requirements.txt`)*

### 4. Configure Environment Variables
Create a `.env` file in the root of the project:
```env
GEMINI_API_KEY=your_actual_gemini_api_key_here
```
> ⚠️ **Important:** Never commit your `.env` file containing secrets to version control.

---

## 🖥️ Running the Application

1. Start the Flask local development server:
   ```bash
   python app.py
   ```
2. Open your web browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```

---

## 💡 How it Works Under the Hood

1. **User Description:** The user submits a description of their waste (e.g., *"An old laptop battery that's swollen"*).
2. **Gemini Query:** The Flask backend constructs a prompt instructing `gemini-2.5-flash-lite` to evaluate the waste and return a response strictly in the following JSON format:
   ```json
   {
       "classification": "category_name",
       "disposal_methods": ["method1", "method2"],
       "safety_precautions": ["precaution1", "precaution2"],
       "recycling_options": ["option1", "option2"]
   }
   ```
3. **Response Parsing:** The backend extracts and validates the JSON content from the LLM response.
4. **UI Update:** The frontend receives the JSON payload asynchronously and renders it inside structured card components.
