I containerized my project from https://github.com/distance-m31/diabab. 
It is a small project related to type I diabetes carbohydarate calculations with a react front end and a node express backend. 
When running, the backend serves the built frontend. The system also uses a Postgres database located outside of the container.

In the docker file I used the node:21 image as a base image and separate build and production stages. I use GitHub workflows to
build the image, push it to GitHub registry and to deploy it to render.com with render specific action. GitHub secrets are used to 
convey the environtment variables required by the container, such as backend url and postgres url.

Currently the app is being server from: https://diabapp-v1-0.onrender.com. It appears to be very slow to start. The project itself is
work in progress so some tidying up is definetely required. 

NOTE: I still have a bug in the workflow file regarding the deployment automation, as the render.com deployment action should notify reder.com
via a webhook, but I have some error there. However the workflow pushes the new image to the registry and it can be manually deployed
via the render.com management interface to production.
