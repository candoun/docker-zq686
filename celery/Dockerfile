FROM python:2.7
RUN groupadd user && useradd --create-home --home-dir /home/user -g user user
WORKDIR /home/user

RUN pip install redis

ENV CELERY_VERSION 3.1.19

RUN pip install celery=="$CELERY_VERSION"

RUN { \
	echo 'import os'; \
	echo "BROKER_URL = os.environ.get('CELERY_BROKER_URL', 'redis://')"; \
} > celeryconfig.py

# --link some-rabbit:rabbit "just works"
ENV CELERY_BROKER_URL redis://guest@redis

# USER user
CMD ["celery", "worker"]