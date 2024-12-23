# Simple GitOps ML Project

This repository provides a minimal setup for:
- A training script (`train.py`) that saves a model to `model/model.pkl`
- A FastAPI-based inference service (`app.py`)
- Kubernetes manifests for GitOps (`manifests/`)
- GitHub Actions CI/CD workflow in `.github/workflows/ci-cd.yml`

## Step-by-Step Usage

1. **Clone the repo**:

   ```bash
   git clone https://github.com/kingabzpro/GitOps-Project.git
   cd GitOps-Project
   ```

2. **Install dependencies**:

    ```bash
    Copy code
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

3. **Run the training script**:

    ```bash
    python src/train.py
    ```

4. **Run the inference service**(optional test):

    ```bash
    uvicorn src.app:app --reload --host 0.0.0.0 --port 80
    ```

5. **Build and run via Docker**:

    ```bash
    docker build -t ml-service:latest .
    docker run -p 80:80 ml-service:latest
    ```
6. **Deploy to Kubernetes**:

    ```bash
    kubectl apply -f manifests/deployment.yaml
    kubectl apply -f manifests/service.yaml
    ```
7. **GitOps**:
- If you're using a GitOps tool (Argo CD, Flux, etc.), point it to this repo (or a specific directory/branch).
- Any commit changes to the `manifests/` folder will be automatically picked up and deployed.