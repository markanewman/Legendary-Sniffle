FROM python:3.12
WORKDIR /app

COPY ./requirements.txt .
RUN pip install --no-cache-dir --upgrade -r requirements.txt

#COPY ./app /app/app

EXPOSE 80
#CMD ["fastapi", "run", "app/main.py", "--port", "80"]
