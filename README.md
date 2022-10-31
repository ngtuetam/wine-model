# wine-model
Deploy a ML model with fastAPI and Docker

## Set up
Install Python dependencies
```bash
pip install -r requirements.txt
```
## Build the image
```bash
docker build -t wine-model-nb:no-batch .
```
## Run the container
```bash
docker run --rm -p 80:80 wine-model-nb:no-batch
```
## Make requests to the server
```bash
curl -X POST http://localhost:80/predict \
    -d @./wine-examples/1.json \
    -H "Content-Type: application/json"
```
## Result
```
{"Prediction":1}
```

# Adding batch
## Build the image
```bash
docker build -t wine-model-wb:with-batch .
```
## Run the container
```bash
docker run --rm -p 81:80 wine-model-wb:with-batch
```
## Make requests to the server
```bash
curl -X POST http://localhost:81/predict \
    -d @./wine-examples-withbatch/batch_1.json \
    -H "Content-Type: application/json"
```
## Result
```
{"Prediction":[2,1,1,0,1,0,0,1,0,0,2,1,1,1,0,1,1,1,2,2,0,1,2,2,1,1,0,1,2,2,1,2]}
```