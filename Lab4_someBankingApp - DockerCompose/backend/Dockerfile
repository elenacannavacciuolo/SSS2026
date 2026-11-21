FROM python:3.12-slim

RUN apt-get update && apt-get install -y git
RUN git clone https://github.com/mmenapace/SomeBankingApp.git /app

WORKDIR /app/backend
RUN pip install -r requirements.txt
RUN pip install --no-cache-dir fastapi
EXPOSE 8000

ENTRYPOINT ["python", "-m", "uvicorn", "main:app",  "--host", "0.0.0.0", "--port", "8000"]

