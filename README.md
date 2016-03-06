# aspnet-coreclr-mvc
Docker base image which includes a bunch of asp.net core mvc packages already installed.

Docker hub: https://hub.docker.com/r/cl0sey/aspnet-coreclr-mvc/

To use:
```
docker pull cl0sey/aspnet-coreclr-mvc
```

In your Dockerfile:
```dockerfile
FROM aspnet-coreclr-mvc:latest
ADD . app/
WORKDIR app
RUN "dnu" "restore"
EXPOSE 5000
ENTRYPOINT ["dnx", "web"]
```

Also in your project.json, ensure your Kestrel server is allowing port 5000 out for all to see:
```json
...
"commands": {
  "web": "Microsoft.AspNet.Server.Kestrel --server.urls=http://*:5000/"
},
...
```
