FROM python:3.10-slim-bullseye 

WORKDIR /usr/src/app

# Installer les dépendances système en premier
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt ./

RUN pip install --no-cache-dir --upgrade -r ./requirements.txt

COPY src/ ./src/

ENV PYTHONPATH="${PYTHONPATH}:/usr/src/app"

EXPOSE 8000

CMD ["uvicorn", "src.server:app", "--host", "0.0.0.0", "--port", "8000"]