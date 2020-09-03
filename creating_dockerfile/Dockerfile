FROM python:3.7.5-alpine

RUN mkdir /app
WORKDIR /app

# requirements.txt will be copied to /app/requiremnts.txt
COPY requirements.txt requirements.txt
RUN pip install -r  requirements.txt

#This command will copy all the files under docker file directory to /app folder
COPY . .

# Optional like tags
LABEL maintainer = "Naveenkumar <nawinkumar94@gmail.com>" \
      version = "1.0"

# mounted volume other container can communicate with this volume
VOLUME ["/app/public"]

# Copy the entrypoint to the root folder "/"
COPY docker-entrypoint.sh /

#Setting the previlage for the command
RUN chmod +x /docker-entrypoint.sh

#Making script for entrypoint (Entrypoint allows you to run custom scrips after image is built)
ENTRYPOINT ["/docker-entrypoint.sh"]

CMD flask run --host=0.0.0.0 --port=5000
