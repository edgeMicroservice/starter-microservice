# starter-microservice
---

This is a starter microservice that allows you to start developing an edge microservice.

# How to use it?
---

#### If this is your first time developing an edge microservice, please follow the edge microservice development quick start guide from [mimik's developer portal](https://devdocs.mimik.com/tutorials/01-submenu).

#### Before you use it, you must build the microservice and later deploy it to mimOE.

# Build Process
---

The build script **default.yml** is specified under **config** directory.

1. Install dependencies: ```npm install```
2. Run the build script: ```npm run build```
3. Package to container: ```npm run package```

# Deployment
---

For **mobile application development**, deployment is programmatically by **Android or iOS Wrappers**, learn more about it:

- Android: [Link](https://developer.mimik.com/resources/documentation/latest/wrappers/android-wrapper)
- iOS: [Link](https://developer.mimik.com/resources/documentation/latest/wrappers/ios-wrapper)

For **microservice development**, things you will need:

- mimOE running on the deployment targeted device.
- Obtained edge Acess Token and associated the device from **mimik OAuth Tool**.
- Run the following commands under the same directory of your containerized microservice file:

```
curl -i -H 'Authorization: Bearer <edge Access Token>' -F "image=@<file name>.tar" http://<target IP address>:8083/mcm/v1/images
```

- To run the microservice after successful deployment, with environment variables:

```
curl -i -H 'Authorization: Bearer <edge Access Token>' -d '{"name": <file name>, "image": <image name>, "env": {"MCM.BASE_API_PATH": "<request base path>", "MCM.WEBSOCKET_SUPPORT": "true", "<add your environment variable name>": "<add your environment variable>"} }' http://<target IP address>:8083/mcm/v1/containers
```

- For more information and explanation, you can visit our [mCM container management API references](https://developer.mimik.com/resources/documentation/latest/getting-started/quick-start) and [general guide on packaing, deployment, and exporting microservice](https://developer.mimik.com/resources/documentation/latest/apis/mcm).
