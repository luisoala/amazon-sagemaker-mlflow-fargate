FROM python:3.10.12

RUN pip install \
    mlflow==2.5.0 \
    pymysql==1.0.2 \
    boto3 && \
    mkdir /mlflow/

EXPOSE 5000

CMD mlflow server \
    --host 0.0.0.0 \
    --port 5000 \
    --app-name basic-auth \
    --default-artifact-root ${BUCKET} \
    --backend-store-uri mysql+pymysql://${USERNAME}:${PASSWORD}@${HOST}:${PORT}/${DATABASE}
    sed -i 's/default_permission = READ/default_permission = NO_PERMISSIONS/' mlflow/server/auth/basic_auth.ini
