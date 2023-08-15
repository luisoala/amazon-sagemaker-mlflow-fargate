FROM python:3.10.12

RUN pip install \
    mlflow==2.5.0 \
    pymysql==1.0.2 \
    boto3 && \
    mkdir /mlflow/

EXPOSE 5000

CMD wget https://raw.githubusercontent.com/luisoala/amazon-sagemaker-mlflow-fargate/main/basic_auth.ini \
    && export MLFLOW_AUTH_CONFIG_PATH="${PWD}/basic_auth.ini" \
    && mlflow server \
    --host 0.0.0.0 \
    --port 5000 \
    --app-name basic-auth \
    --default-artifact-root ${BUCKET} \
    --backend-store-uri mysql+pymysql://${USERNAME}:${PASSWORD}@${HOST}:${PORT}/${DATABASE}
