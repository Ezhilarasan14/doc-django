# Infrastructure Layer

## File Storage


<p>

In Django, file storage is used to manage how and where files are stored and retrieved in a web application. Django comes with a default file storage system that stores files on the local filesystem

Extra : 
 but it also provides other storage backends for cloud services like Amazon S3, Google Cloud Storage, etc.


Here's a basic overview of file storage in Django:
</p>



<b>
Default File Storage (Local):
</b>

<p>
In your settings.py, the MEDIA_ROOT setting determines the base directory where media files (uploads) will be stored, and MEDIA_URL sets the base URL for serving media files.

but digid its customized configuation in settings:
1. File storage
2. AI Model Storage
3. Email template Storage
4. Static file Storage
</p>

```
FILE_STORAGE = conf('FILE_STORAGE')
MODEL_STORAGE = conf('MODEL_STORAGE')


STATIC_URL = '/static/'
STATICFILES_DIRS = [
    os.path.join (BASE_DIR, "__shared__" ),
]

STATIC_ROOT = os.path.join(FILE_STORAGE, 'static')
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(FILE_STORAGE, 'media')
FILE_UPLOAD_PERMISSIONS = 0o644

```
