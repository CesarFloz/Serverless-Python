##Run

docker build -t serverless-python -f Dockerfile .

docker run -it -p 80:5000 serverless-python

docker run --env PORT=5000 -it -p  80:5000 serverless-python

##Push
####via Docker
docker build -t serverless_python -f Dockerfile .

docker tag serverless_python gcr.io/sodium-binder-341816/serverless-python

docker push gcr.io/sodium-binder-341816/serverless_python

gcloud builds submit --tag gcr.io/sodium-binder-341816/serverless-python .


gcloud run deploy serverless-python-v1 --image gcr.io/sodium-binder-341816/serverless-python:v1 --platform managed --region us-west1