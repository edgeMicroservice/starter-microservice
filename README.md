# starter-microservice
---

This is a starter microservice that allows you to start developing an edge microservice.

# How to use it?
---

#### If this is your first time developing an edge microservice, please follow the [developer documentation quick start guide](https://devdocs.mimik.com/tutorials/01-submenu).

#### Before you use it, you must build the microservice and later deploy it to mim OE.

# Build Process
---

The build script **default.yml** is specified under **config** directory.

1. Install dependencies: ```npm install```
2. Run the build script: ```npm run build```
3. Package to container: ```npm run package```

# Deployment
---

For **mobile application development**, deployment is programmatically by **Android or iOS Client Libraries**, learn more about it:

- Android: [Link](https://devdocs.mimik.com/key-concepts/11-index)
- iOS: [Link](https://devdocs.mimik.com/key-concepts/10-index) [github](https://github.com/mimikgit/cocoapod-EdgeCore?tab=readme-ov-file#mimik-client-library-cocoapods)

For **microservice development**, things you will need:

- mim OE running on the deployment targeted device.
- Obtained edge Access Token and associated the device from **[mimik-edge-cli](https://www.npmjs.com/package/@mimik/mimik-edge-cli)** that is installed:```npm install -g @mimik/mimik-edge-cli```. For more information, go [here](https://devdocs.mimik.com/api/01-index).
- Run the following commands under the same directory of your containerized microservice file:

```
curl -i -H 'Authorization: Bearer <edge Access Token>' -F "image=@<file name>.tar" http://<target IP address>:8083/mcm/v1/images
```

- To run the microservice after successful deployment, with environment variables:

```
curl -i -H 'Authorization: Bearer <edge Access Token>' -d '{"name": <file name>, "image": <image name>, "env": {"MCM.BASE_API_PATH": "<request base path>", "MCM.WEBSOCKET_SUPPORT": "true", "<add your environment variable name>": "<add your environment variable>"} }' http://<target IP address>:8083/mcm/v1/containers
```

- For more information and explanation, you can visit our [command line tool reference](https://devdocs.mimik.com/api/01-index) and [general guide on packaging, deployment, and exporting microservice](https://devdocs.mimik.com/key-concepts/02-index).
