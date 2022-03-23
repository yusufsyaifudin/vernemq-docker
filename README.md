# VERNEMQ DOCKER

This is non-official image of VerneMQ, use only for local testing or development.

## How to run

Clone this repo and then just run `docker compose up`. Then connect using username `admin` and password `admin` when connect to MQTT with port 1883.


### Changing password

Read this https://docs.vernemq.com/configuring-vernemq/file-auth or TLDR below:

```bash
docker run -it --platform linux/amd64 vernemq/vernemq:1.12.3-alpine /bin/bash
```

Then inside Docker bash, run:

```bash
vmq-passwd -c {your-file-path} {username}
```

For example,

```bash
vmq-passwd -c generated.passwd myusername
```

Then type your password after that command and re-enter it.

```bash
cat generated.passwd
```

Will return something as follow:

```
myusername:$6$G6OKsoFfVbtBFz2O$fMx0pug+rjebL1JnSmQqjPqtR+9vnFfErHAMx1efmmP2FlB32YSKHaTINRqggkjZDWyt4AXBX+N1Fq6Bff1hVQ==
```

Copy paste that line into file `vernemq_conf/vmq.passwd`.

`exit` from Docker bash and re-run `docker compose`.
