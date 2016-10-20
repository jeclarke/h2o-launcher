# h2o Launcher

## Overview

This project runs the h2o data science platform as an application on PNDA.

*** Note ***
The sparkStreaming deployment component is being re-used to launch this application as a PoC. If it works OK then a new h2o component type will be created to be more consistent.

## Requirements

* [Maven](https://maven.apache.org/docs/3.0.5/release-notes.html) 3.0.5

## h2o Distribution

Download a version of h2o that is compatible with the target PNDA verson and place it in `app-package/src/main/resources/sparkStreaming/h2o`

## Build

To build the h2o application use:

````
mvn clean package
````

This command should be run at the root of the repository and will build the application package to `app-package/target/h2o-launcher-{version}.tar.gz`.

## Files in the package

- `application.properties`: unused but required for compatability with the deployment manager.
- `log4j.properties`: unused but required for compatability with the deployment manager.
- `properties.json`: contains default properties that may be overriden at application creation time.
- `upstart.conf`: runs h2o using the hadoop jar command.
- `yarn-kill.py`: kills the yarn job associated with this application.

## Deploying the package and creating an application

The PNDA console can be used to deploy the application package to a cluster and then to create an application instance. The console is available on port 80 on the edge node.

To make the package available for deployment it must be uploaded to a package repository. The default implementation is an OpenStack Swift container. The package may be uploaded via the PNDA repository manager which abstracts the container used, or by manually uploading the package to the container.

## How to access h2o after running the app

TODO: Fill this in