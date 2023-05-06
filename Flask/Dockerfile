FROM python:3.9-slim

WORKDIR /Flask

RUN  apt update && apt -y install curl

COPY requirements.txt /Flask
RUN curl https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 > /usr/local/bin/cloud_sql_proxy && chmod +x /usr/local/bin/cloud_sql_proxy
# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Copy the rest of the application code into the container at /app
COPY . /Flask
GOOGLE_ENTRYPOINT ["python", "main.py"]
# Expose the port that the application will run on
EXPOSE 8080

# Start the application