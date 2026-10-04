\# ClipSense



> \*\*AI-powered video understanding and interactive Q\&A platform\*\*



ClipSense is a full-stack application designed to analyze video content using \*\*transcripts, automatic speech recognition (ASR), computer vision, OCR, and multimodal AI providers\*\*. It provides an interactive frontend for processing videos, viewing results, and asking questions about analyzed content.



\---



\## ✨ Features



\* 🎥 \*\*Video analysis workflow\*\*

\* 📝 \*\*YouTube transcript extraction\*\*

\* 🎙️ \*\*Automatic Speech Recognition (ASR) fallback\*\*

\* 👁️ \*\*Computer vision and visual evidence processing\*\*

\* 🔎 \*\*OCR-based visual analysis\*\*

\* 🤖 \*\*LLM-powered summarization and question answering\*\*

\* 💬 \*\*Interactive video Q\&A\*\*

\* ⏱️ \*\*Timestamp-aware results\*\*

\* 📊 \*\*Progress and result views\*\*

\* 🧪 \*\*Backend test suite and sample test data\*\*

\* 🔌 \*\*Configurable AI providers\*\*

\* 🖥️ \*\*React-based modern frontend\*\*

\* ⚡ \*\*FastAPI backend\*\*



\---



\## 🏗️ Architecture



```mermaid

flowchart TD

&#x20;   A\[User] --> B\[React + Vite Frontend]

&#x20;   B --> C\[FastAPI Backend]



&#x20;   C --> D\[Transcript Agent]

&#x20;   C --> E\[Vision Agent]



&#x20;   D --> F\[YouTube Transcript API]

&#x20;   D --> G\[Faster-Whisper ASR]



&#x20;   E --> H\[OpenCV]

&#x20;   E --> I\[EasyOCR]

&#x20;   E --> J\[Image Processing]



&#x20;   C --> K\[LLM Services]

&#x20;   K --> L\[Groq]

&#x20;   K --> M\[Google Gemini]



&#x20;   C --> N\[Job \& Result APIs]

&#x20;   N --> B

```



\---



\## 🛠️ Technology Stack



| Layer            | Technologies                     |

| ---------------- | -------------------------------- |

| Frontend         | React 19.1, TypeScript 5.8       |

| Build Tool       | Vite 7                           |

| Styling          | Tailwind CSS 4.1                 |

| Backend          | FastAPI                          |

| Server           | Uvicorn                          |

| Validation       | Pydantic                         |

| Configuration    | Pydantic Settings, python-dotenv |

| Transcript       | YouTube Transcript API           |

| ASR              | Faster-Whisper                   |

| Computer Vision  | OpenCV                           |

| OCR              | EasyOCR                          |

| Image Processing | Pillow, ImageHash, NumPy         |

| AI Providers     | Groq, Google Gemini              |

| Testing          | Pytest-based backend tests       |



\---



\## 📁 Project Structure



```text

ClipSense/

│

├── backend/

│   ├── app/

│   │   ├── agents/

│   │   │   ├── transcript.py

│   │   │   └── vision.py

│   │   │

│   │   ├── schemas/

│   │   │   ├── transcript.py

│   │   │   └── vision.py

│   │   │

│   │   ├── services/

│   │   │   ├── asr\_provider.py

│   │   │   ├── llm.py

│   │   │   └── vision\_provider.py

│   │   │

│   │   ├── utils/

│   │   │   ├── json\_utils.py

│   │   │   ├── media.py

│   │   │   ├── retry.py

│   │   │   └── timestamps.py

│   │   │

│   │   ├── config.py

│   │   └── main.py

│   │

│   ├── scripts/

│   ├── test\_data/

│   ├── tests/

│   ├── .env.example

│   └── requirements.txt

│

├── frontend/

│   ├── src/

│   │   ├── components/

│   │   ├── lib/

│   │   ├── pages/

│   │   ├── services/

│   │   └── types/

│   │

│   ├── .env.example

│   ├── package.json

│   ├── tsconfig.json

│   └── vite.config.ts

│

├── .gitignore

└── README.md

```



\---



\## 🔄 Application Workflow



| Step | Process     | Description                                                 |

| ---: | ----------- | ----------------------------------------------------------- |

|    1 | Input       | User provides video content                                 |

|    2 | Processing  | Backend creates an analysis job                             |

|    3 | Transcript  | Captions are retrieved when available                       |

|    4 | ASR         | Faster-Whisper can provide speech transcription fallback    |

|    5 | Vision      | Visual content can be processed through the vision pipeline |

|    6 | AI Analysis | Configured AI providers process available information       |

|    7 | Results     | Analysis results are returned to the frontend               |

|    8 | Q\&A         | User can ask questions about the processed content          |



\---



\## 🔌 Backend API



The FastAPI backend exposes the following application endpoints:



| Endpoint                    | Method | Purpose                             |

| --------------------------- | ------ | ----------------------------------- |

| `/api/health`               | GET    | Check backend health                |

| `/api/jobs`                 | POST   | Create an analysis job              |

| `/api/jobs/{job\_id}`        | GET    | Retrieve job information            |

| `/api/jobs/{job\_id}/result` | GET    | Retrieve analysis results           |

| `/api/jobs/{job\_id}/qa`     | POST   | Ask questions about an analyzed job |



\---



\## 💻 Local Development



\### Prerequisites



Make sure the following are installed:



\* Python 3.11+

\* Node.js

\* npm

\* Git



\### 1. Clone the repository



```bash

git clone <YOUR\_GITHUB\_REPOSITORY\_URL>

cd ClipSense

```



\### 2. Set up the backend



```powershell

cd backend



python -m venv .venv



.\\.venv\\Scripts\\Activate.ps1



python -m pip install --upgrade pip



pip install -r requirements.txt

```



\### 3. Configure backend environment



Create your local environment file from the example:



```powershell

Copy-Item .env.example .env

```



Add your required AI provider credentials to `.env`.



> \*\*Never commit `.env` or API keys to GitHub.\*\*



\### 4. Start the backend



```powershell

uvicorn app.main:app --reload

```



The backend will run at:



```text

http://127.0.0.1:8000

```



\### 5. Set up the frontend



Open another terminal:



```powershell

cd frontend



npm install

```



Create the frontend environment file if required:



```powershell

Copy-Item .env.example .env

```



\### 6. Start the frontend



```powershell

npm run dev

```



The Vite development server will provide the local frontend URL in the terminal.



\---



\## 🧪 Testing



Backend tests are located in:



```text

backend/tests/

```



Example:



```powershell

cd backend

pytest

```



Sample media and vision data are available under:



```text

backend/test\_data/

```



\---



\## 🔐 Environment Variables



ClipSense uses environment files for configuration and API credentials.



Example files are provided as:



```text

backend/.env.example

frontend/.env.example

```



The actual `.env` files are intentionally excluded from version control.



\### Security checklist



\* ✅ Keep API keys in `.env`

\* ✅ Keep `.env` out of Git

\* ✅ Use `.env.example` for placeholders

\* ❌ Never commit API keys

\* ❌ Never publish private credentials

\* ❌ Never hard-code production secrets



\---



\## 📦 Production Deployment



A recommended deployment architecture is:



```mermaid

flowchart LR

&#x20;   U\[User] --> V\[Vercel]

&#x20;   V --> F\[ClipSense Frontend]

&#x20;   F --> R\[Render]

&#x20;   R --> B\[FastAPI Backend]

&#x20;   B --> AI\[AI Providers]

```



\### Frontend



Recommended configuration:



| Setting           | Value           |

| ----------------- | --------------- |

| Framework         | Vite            |

| Root Directory    | `frontend`      |

| Build Command     | `npm run build` |

| Output Directory  | `dist`          |

| API Configuration | `VITE\_API\_BASE` |



\### Backend



Recommended configuration:



| Setting        | Value                                              |

| -------------- | -------------------------------------------------- |

| Platform       | Render                                             |

| Root Directory | `backend`                                          |

| Build Command  | `pip install -r requirements.txt`                  |

| Start Command  | `uvicorn app.main:app --host 0.0.0.0 --port $PORT` |



\---



\## 📌 Current Project Notes



\* Backend job storage is currently maintained in memory.

\* Production deployments should use persistent storage for durable job/result management.

\* AI providers are configurable through environment settings.

\* The frontend includes a demo/mock-data workflow when an API base URL is not configured.

\* The project is structured so transcript and vision functionality can evolve independently.



\---



\## 🚀 Future Improvements



Potential future enhancements include:



\* Persistent database-backed job storage

\* User authentication and accounts

\* Cloud media storage

\* More AI provider integrations

\* Advanced video search

\* Improved visual understanding

\* Speaker identification

\* Chapter generation

\* Exportable summaries

\* Production monitoring and logging

\* Background job queues for large videos

\* Scalable cloud deployment



\---



\## 📄 License



Add your preferred open-source license here before publishing the repository.



\---



\## 👤 Author



\*\*Talha Khan\*\*



Built with React, FastAPI, Python, TypeScript, and modern AI technologies.



