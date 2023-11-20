FROM python
LABEL authors="siva sankar reddy bogala"

RUN mkdir /service
COPY protobufs/ /service/protobufs/
COPY marketplace/ /service/marketplace/
WORKDIR /service/marketplace
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
RUN python -m grpc_tools.protoc -I ../protobufs --python_out=. --pyi_out=. \
           --grpc_python_out=. ../protobufs/recommendations.proto

EXPOSE 4000
ENV FLASK_APP=marketplace.py
ENTRYPOINT [ "flask", "run", "--host=0.0.0.0", "--port=4000"]