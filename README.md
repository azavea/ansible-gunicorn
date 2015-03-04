# ansible-gunicorn

An Ansible role for installing and configuring gunicorn. Provides the `Restart gunicorn` handler to reload gunicorn when you install/update your app.

## Role Variables

- `develop` - is a develop environment. If set, will reload after each request (default: `false`)
- `test` - is a test environment. If set, will reload after each request (default: `false`)
- `gunicorn_version` - version of gunicorn to install (default: `"19.2.1"`)
- `gunicorn_user` - user to run gunicorn as. will create if doesn't exist. (default: `"gunicorn"`)
- `gunicorn_app_name` - name of app which will be used as the name of the service (default `"gunicorn"`)
- `gunicorn_workers` - number of workers to pre-fork (default: `8`)
- `gunicorn_log` - log file location (default: `"/home/gunicorn/gunicorn.log"`)
- `gunicorn_bind` - address and port to bind to (default: `"127.0.0.1:8000"`)
- `gunicorn_app_dir` - where to chdir into before loading app (*required*)
- `gunicorn_wsgi` - module to import containing application (*required*)

## Example Playbook

See the [examples](./examples/) directory. Example will serve a small app at http://localhost:8000/.
