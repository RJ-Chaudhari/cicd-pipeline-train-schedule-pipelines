# cicd-pipeline-train-schedule-pipelines

This is a simple train schedule app written using nodejs. It is intended to be used as a sample application for a series of hands-on learning activities.

## Running the app on local

You need a Java JDK 7 or later to run the build. You can run the build like this:

    ./gradlew build

You can run the app with:

    ./gradlew npm_start

Once it is running, you can access it in a browser at [http://localhost:3000](http://localhost:3000)

----------------------------------------------------------------------------------

## cicd-pipeline-train-schedule-pipelines with Jenkins CI/CD using docker-compose: Flow 

Developer (Push Code)
   ↓
GitHub
   ↓
Jenkins (EC2-1)
   ↓
Docker Hub
   ↓
App Server (EC2-2)
   ↓
Docker Compose (App + Nginx)
   ↓
Users

