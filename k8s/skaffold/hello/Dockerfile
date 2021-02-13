FROM python:3-alpine

ENV FLASK_APP=hello.py

WORKDIR /app

# Install from requirements first, and have
# separate COPY . line at end for rest. This allows
# docker caching of layers to avoid the 'pip' rebuild
# when we change a single python file
RUN pip3 install flask

ENTRYPOINT ["/usr/local/bin/python", "-m", "flask", "run", "--host", "0.0.0.0"]
COPY hello.py /app
