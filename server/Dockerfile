FROM python:3.12.0-slim-bookworm

ENV PYTHONUNBUFFERED=1 \
    PYTHONWRITEBYTECODE=1 \
    APP=/app

WORKDIR $APP

COPY requirements.txt $APP
RUN pip install --upgrade pip \
    && pip install -r requirements.txt

COPY . $APP

RUN chmod +x /app/entrypoint.sh

EXPOSE 8000

ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]
