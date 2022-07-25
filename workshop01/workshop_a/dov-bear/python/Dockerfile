FROM python:3.9-slim-buster

WORKDIR /app

COPY requirements.txt .

RUN pip3 install -r requirements.txt

COPY . .


ENV PORT=5000
ENV INSTANCE_NAME="We Python Bears"
ENV INSTANCE_HASH="5py2"
ENV FLASK_APP=main.py

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]

