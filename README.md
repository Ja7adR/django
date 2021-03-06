# DEPRECATED

This image is officially deprecated in favor of [the standard `python` image](https://hub.docker.com/_/python/), and will receive no further updates after 2016-12-31 (Dec 31, 2016). Please adjust your usage accordingly.

For most usages of this image, it was already not bringing in `django` from this image, but actually from your project's `requirements.txt`, so the only "value" being added here was the pre-installing of `mysql-client`, `postgresql-client`, and `sqlite3` for various uses of the `django` framework.

For example, a `Dockerfile` similar to the following would be a good starting point for a Django project using PostgreSQL:

```dockerfile
FROM python:3.4

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
		postgresql-client \
	&& rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/app
COPY requirements.txt ./
RUN pip install -r requirements.txt
COPY . .

EXPOSE 8000
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

# About this Repo

This is the Git repo of the Docker [official image](https://docs.docker.com/docker-hub/official_repos/) for [django](https://registry.hub.docker.com/_/django/). See [the Docker Hub page](https://registry.hub.docker.com/_/django/) for the full readme on how to use this Docker image and for information regarding contributing and issues.

The full readme is generated over in [docker-library/docs](https://github.com/docker-library/docs), specifically in [docker-library/docs/django](https://github.com/docker-library/docs/tree/master/django).

See a change merged here that doesn't show up on the Docker Hub yet? Check [the "library/django" manifest file in the docker-library/official-images repo](https://github.com/docker-library/official-images/blob/master/library/django), especially [PRs with the "library/django" label on that repo](https://github.com/docker-library/official-images/labels/library%2Fdjango). For more information about the official images process, see the [docker-library/official-images readme](https://github.com/docker-library/official-images/blob/master/README.md).

---

-	[Travis CI:  
	![build status badge](https://img.shields.io/travis/docker-library/django/master.svg)](https://travis-ci.org/docker-library/django/branches)

<!-- THIS FILE IS GENERATED BY https://github.com/docker-library/docs/blob/master/generate-repo-stub-readme.sh -->
