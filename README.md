# Potato Disease Classification

This repository contains a project for classifying potato diseases using a deep learning model. Follow the steps below to set up and run the project.

## Prerequisites

Ensure you have the following installed on your system before proceeding:

- **Python 3.9.20**
- **Docker**

## Setup Instructions

### 1. Install Required Software

Install the following software versions if not already installed:

- **Python 3.9.20**: [Download Python 3.9.20](https://www.python.org/downloads/release/python-3920/)
- **Docker**: [Download Docker](https://www.docker.com/products/docker-desktop/)

Additionally, pull the TensorFlow Serving image using Docker:

```bash
docker pull tensorflow/serving
```

### 2. Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/Lokesh-DataScience/Potato-disease-classification.git
cd Potato-disease-classification
```

### 3. Create and Activate Virtual Environments

#### Backend (Python Environment)

1. Navigate to the project’s root directory.
2. Create a Python virtual environment:
    ```bash
    python -m venv venv
    ```
3. Activate the environment:
    - On Windows (Command Prompt):
      ```bash
      venv\Scripts\activate
      ```
    - On Windows (PowerShell):
      ```bash
      .\venv\Scripts\Activate.ps1
      ```
    - On Linux/Mac:
      ```bash
      source venv/bin/activate
      ```
4. Install required Python packages:
    ```bash
    cd api
    pip install -r requirements.txt
    ```

### 4. Configure and Run TensorFlow Serving

Run TensorFlow Serving with Docker using the following command (ensure you run this in **Windows PowerShell as Administrator**):

```bash
docker run -t --rm -p 8502:8502 -v D:\ML-projects\Potato-disease:/Potato-disease tensorflow/serving --rest_api_port=8502 --model_config_file=/Potato-disease/models.config
```

> **Note:** Adjust the volume path (`D:\ML-projects\Potato-disease`) to your local directory where the `models.config` file is stored.

### 5. Run the Backend

1. Navigate to the `api` directory:
    ```bash
    cd api
    ```
2. Start the FastAPI backend:
    ```bash
    python main.py
    ```

### 6. Run the Streamlit Frontend

1. Navigate to the project’s root directory:
    ```bash
    cd ..
    ```
2. Start the Streamlit app:
    ```bash
    streamlit run streamlit_app.py
    ```

## Notes for Other Users

- **Administrator Privileges:** Ensure Docker commands are run in Windows PowerShell with Administrator privileges.
- **Directory Adjustments:** Modify paths for volume mounting (`D:\ML-projects\Potato-disease`) to match your local system setup.
- **Environments:** Always ensure the respective environments (Python) are activated before running backend and frontend commands.