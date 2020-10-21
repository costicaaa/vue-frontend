
### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
Application is expected to run in docker. When building, provide `ARG_VUE_APP_API_URL` - the public service endpoint where the backend 
can be accessed.
```
docker build -t raducostin/vue-frontend:v2 --build-arg ARG_VUE_APP_API_URL=http://localhost:44345 .
```

Local development is done using host `npm run serve`. This is not ideal, but I am so tired of configuring n-th windows host to compile in docker
and serves no one.

The application knows what to display in case the backend is not available. 
We are going to add end-to-end tests in order to test that the application displays the backend response or the error if the backend is not 
available.