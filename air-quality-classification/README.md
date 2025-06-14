### Task description

1. Prediction of air quality (Good/Moderate/Hazardous/Poor) based on the data of the given weather indicators (Temperature/Humidity/PM2.5/PM10/NO2/SO2/CO/Proximity to Industrial Areas/Population Density).
2. Give the model training code (Python 3.11), and the trained model.
3. Support with docker image build and `docker compose up` one click to start the backend service (Python 3.11).
4. You can use the browser to open the page and then enter the value of each indicator (allowed to be empty), submit and return to the prediction results.

### Dataset

[dataset](./updated_pollution_dataset.csv)

### App Testing 

#### 1. Unpack the tar file

```bash
tar -xvf aqc.tar.gz
```

#### 2. Build an image

```shell
cd air-quality-classification
docker build -t evaluation/aqc .
```

#### 3. Start docker service:

```shell
cd docker
docker compose up -d
```
#### 4. Visit the Web Interface

👉 http://localhost:1111/aqc

<p align="center">
  <img src="https://github.com/HenryCZhang/coding-tasks/blob/main/air-quality-classification/README%20images/aqc%20form.png"  width="400" alt="aqc form">
</p>

#### 5. Stop the App When You're Done

```bash
docker compose down
```

### App Packaging (Development)

#### 1. Pull the required python image
(in aqc directory)
```bash
docker pull python:3.11-slim
```

#### 2. Build an image and train the model in the image:
(in aqc directory)
```bash
docker build -t aqc-builder .
docker run -v "$PWD/app":/app -w /app -it aqc-builder python train.py dataset.csv
```

#### 3. Start the App with Docker Compose
(in aqc/docker directory)
```bash
cd docker
docker compose up --build
```

#### 4. Visit the Web Interface

👉 http://localhost:1111/aqc

#### 5. Stop the App When You're Done

```bash
docker compose down
```
#### 6. Tar the project:
(outside aqc directory)
```bash
cd ../../
tar -czvf aqc.tar.gz air-quality-classification/
```


