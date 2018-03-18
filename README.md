## Docker containter for Angular 5 development

From ubuntu:16.04

**Requirements:** 

* docker >= 17.12.0-ce
* docker-compose >=  1.18.0


**Includes:**

 - node 8 
 - npm 5
 - git
 - ng (angular-cli)

**Instructions**

Edit docker-compose.yml and set the volume path to your project

```
services:
  angular5:
    image: bancuadrian/angular5
    container_name: "angular5"
    ports:
      - "4200:4200"
    # mount your project folder to container
    # ensure that project folder is shared in docker
    volumes:
      - /Users/bancuadrian/Projects/myAngularProject:/home/project
```

Start container

```
docker exec -it angular5 /bin/sh -c "(cd /home/project;ng serve --host 0.0.0.0 --port 4200)"
```

You can then browse to `http://127.0.0.1:4200`

If you would like to generate files using angular-cli, simply bash to the container, and use it there.

```
docker exec -it angular5 bash

root@1de171fceab9:/home/node# cd /home/project
root@1de171fceab9:/home/project# ng --version

    _                      _                 ____ _     ___
   / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
  / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
 / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
/_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
               |___/

Angular CLI: 1.6.8
Node: 8.10.0
OS: linux x64
Angular: 5.2.9
... animations, common, compiler, compiler-cli, core, forms
... http, language-service, platform-browser
... platform-browser-dynamic, router

@angular/cli: 1.6.8
@angular-devkit/build-optimizer: 0.0.42
@angular-devkit/core: 0.0.29
@angular-devkit/schematics: 0.0.52
@ngtools/json-schema: 1.1.0
@ngtools/webpack: 1.9.8
@schematics/angular: 0.1.17
typescript: 2.5.3
webpack: 3.10.0
```