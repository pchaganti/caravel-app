FROM python:alpine AS build

RUN pip install --no-cache-dir starlette uvicorn

FROM python:alpine AS run

RUN adduser -S sampan -G root
USER sampan

COPY --from=build /usr/local/lib/python3.12/site-packages /usr/local/lib/python3.12/site-packages
COPY --chown=sampan:root python /home/sampan/python

EXPOSE 8080
WORKDIR /home/sampan
ENTRYPOINT ["python", "python/main.py"]
