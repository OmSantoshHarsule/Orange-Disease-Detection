FROM python:3.9-slim

WORKDIR /app

# Copy requirements first for better layer caching
COPY ./requirements.txt /requirements.txt

# Install dependencies in virtual environment
RUN python -m venv /py && \
    /py/bin/pip install --upgrade pip && \
    /py/bin/pip install -r /requirements.txt && \
    rm -rf /root/.cache && \
    adduser --disabled-password --no-create-home appuser

# Copy app files
COPY ./Application /app

# Only need to expose port once
EXPOSE 5000

USER appuser

# Use the Python from the virtual environment
CMD ["/py/bin/python", "app.py"]