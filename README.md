# ansible-gunicorn

An Ansible role for installing and configuring gunicorn. Provides the `Restart gunicorn` handler to reload gunicorn when you install/update your app.

## Role Variables

- `gunicorn_start_on` - start on string for upstart (default: `"local-filesystems and net-device-up IFACE!=lo"`)
- `gunicorn_version` - version of gunicorn to install (default: `"19.2.1"`)
- `gunicorn_user` - user to run gunicorn as. will create if doesn't exist. (default: `"gunicorn"`)
- `gunicorn_app_name` - name of app which will be used as the name of the service (default `"gunicorn"`)
- `gunicorn_dynamic_workers` - dynamically generate workers based on the number of CPUs. This overrides the value of `gunicorn_workers` (default: `False`).
- `gunicorn_cpu_coefficient` - Coefficient for scaling workers based on CPU. When this value is set along with `gunicorn_dynamic_workers`, gunicorn will fork `(gunicorn_cpu_coefficient * # of CPUs) + 1` workers (default: `2`).
- `gunicorn_workers` - number of workers to pre-fork. This value will be overridden if `gunicorn_dynamic_workers` is True (default: `8`).
- `gunicorn_accesslog` - access log file location (default: `"-"`)
- `gunicorn_errorlog` - error log file location (default: `"-"`)
- `gunicorn_syslog` - send `stdout` and `stderr` output to syslog (default: `True`)
- `gunicorn_bind` - address and port to bind to (default: `"127.0.0.1:8000"`)
- `gunicorn_reload` - reload after each request (default: `False`)
- `gunicorn_loglevel` - log level (default: `"info"`)
- `gunicorn_app_dir` - where to chdir into before loading app (*required*)
- `gunicorn_wsgi` - module to import containing application (*required*)

## Example Playbook

See the [examples](./examples/) directory. Example will serve a small app at http://localhost:8000/.
