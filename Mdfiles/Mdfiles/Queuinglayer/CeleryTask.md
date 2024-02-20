# Queuing Layer

## Celery Task

<p>
Create tasks in your Django app
</p>

### tasks.py in your app

```
from celery import shared_task

@shared_task
def your_task():
    # Your task logic here
    pass

```

<p>
Run Celery: 
</p>

```
celery -A your_project worker -l info
```

<p>
To run the  digid app queues:
</p>

```
celery -A TC_CELERY.DI.detect_image worker  --pool=solo --loglevel=INFO -n worker1.%h
celery -A TC_CELERY.IV.id_verfication worker  --pool=solo --loglevel=INFO -n worker2.%h
celery -A TC_CELERY.LD.liveness_detection worker  --pool=solo --loglevel=INFO -n worker2.%h
celery -A TC_CELERY.TM.template_matching worker  --pool=solo --loglevel=INFO -n worker3.%h
celery -A TC_CELERY.OCR.ocr worker  --pool=solo --loglevel=INFO -n worker4.%h
celery -A TC_CELERY.NT.sms worker -Q queue_sms --pool=solo --loglevel=INFO -n worker6.%h
celery -A TC_CELERY.NT.email worker -Q queue_email --pool=solo --loglevel=INFO -n worker7.%h

```