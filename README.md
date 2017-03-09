# NHSBSA Docker Build Files: owasp-zap

This docker file is basically a wrapper of `owasp/zap2docker-weekly`.  For more information about the upstream images, see this wiki entry:

[ZAP Proxy - Docker](https://github.com/zaproxy/zaproxy/wiki/Docker)

The bits we add are:

```docker
EXPOSE 8080
ENTRYPOINT ["zap.sh"]
CMD ["-daemon", "-port", "8080", "-host", "0.0.0.0", "-config", "api.disablekey=true"]
```

This is because the gitlab-ci service requires a listening port and service rather than passing in commands with `docker run`.
