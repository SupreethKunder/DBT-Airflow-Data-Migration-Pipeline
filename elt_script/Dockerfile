FROM python:3.13.0b2-slim

# Install PostgreSQL command-line tools
RUN apt-get update && apt-get install -y postgresql-client cron

WORKDIR /app

# Copy the entrypoint script for cronjob 
COPY start.sh .
# Copy the ELT script 
COPY elt_script.py .

RUn echo "0 3 * * * python /app/elt_script.py" | crontab -
# Set the default command to run the ELT script
CMD ["python", "elt_script.py"]