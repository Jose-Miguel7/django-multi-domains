# django-multi-domains

This Django App sets specific [URL Confs](https://docs.djangoproject.com/en/dev/topics/http/urls/) for configured domains.

After all, the app has only a small middleware.

## Installation

```bash
pip install git+https://github.com/Jose-Miguel7/PKG-20220924-MULTIDOMAIN-DJANGO.git
```

## Setup

The following configurations should be added in the [Django Settings](https://docs.djangoproject.com/en/dev/ref/settings/) Module.

1. Add `"django_domains"` to `INSTALLED_APPS`

   ```python
   INSTALLED_APPS = [
       "...",
       "django_domains",
   ]
   ```

2. Add middleware `"django_domains.middleware.MultiDomainsMiddleware"` to the beginning of the `MIDDLEWARE`

   ```python
   MIDDLEWARE = [
       "django_domains.middleware.MultiDomainsMiddleware",
       "...",
   ]
   ```

3. Define the mapping of domain and urlconf `MULTI_DOMAINS`

   ```python
   MULTI_DOMAINS = {
       "api.example.com": "api.urls",
       "shop.example.com": "shop.urls",
   }
   ```

If no mapping is set for a domain, `ROOT_URLCONF` is used as a fallback.