# DISCUSSION FORUM

### How To Setup Discussion Forum MW

This section will help the developer ( or third-party vendors ) to set up and use Discussion-middleware.

#### Background: <a href="#background" id="background"></a>

This discussions-middleware works like an API proxy. All the discussions-forum related APIs will go via this proxy.

#### Git Repository: <a href="#git-repository" id="git-repository"></a>

[https://github.com/Sunbird-Ed/discussions-middleware](https://github.com/Sunbird-Ed/discussions-middleware)

#### Prerequisite: <a href="#prerequisite" id="prerequisite"></a>

1. Local nodebb should be installed ( or for a particular environment )\
   _**Note:**_ Refer to this link for easy installation: [https://docs.nodebb.org/installing/os/](https://docs.nodebb.org/installing/os/)
2. all the necessary plugins to be installed and activated for the nodebb to access certain APIs,

#### Steps to set up DMW locally : <a href="#steps-to-set-up-dmw-locally" id="steps-to-set-up-dmw-locally"></a>

**Step-1 : Git clone:**

`1> git clone git@github.com:Sunbird-Ed/discussions-middleware.git 2> nvm use 12 (min node version 12) 3> cd discussion-middleware 4> yarn`

**Step-2: Add the following configuration in environmentVariablesHelper.js**

`1'use strict' 2const env = process.env 3const __envIn = 'dev'; 4 5let localEnv = { 6 NODEBB_SERVICE_URL: 'http://localhost:4567', 7 Authorization: <master token>, 8 nodebb_api_slug: env.nodebb_api_slug || '/api' 9} 10 11module.exports = localEnv;`

Replace the ‘\<mater token>’ with your local NodeBB master token.

**Q1. How to generate/get master token?**\
Ans. Local NodeBB should be running fine. Install the [Write-API NodeBB plugin](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1981546511/Discussion+Forum+Deployment#Install-nodebb-plugins).\
After successfull installation, generate the master token by refering below link.\
[Discussion Forum: Deployment | Step-5:-Creating-Nodebb-Token](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1981546511/Discussion+Forum+Deployment#Step-5:-Creating-Nodebb-Token)\
\
Start the application

1. `1> npm run start`

middleware will be running on port **3002**\
URL: **http”//localhost:3002**

#### &#x20;DMW setup using script

if you are doing the discussion middleware local setup for the first time, you can use the below script file.

1.  Create `discussion_dmw.sh` file with below script and run the script with the command `bash discussion_dmw.sh`.

    ``1red=`tput setaf 1` 2green=`tput setaf 2` 3 4read -p 'Branch name: ' branch_name 5git clone -b $branch_name https://github.com/Sunbird-Ed/discussions-middleware.git discussions-middleware || echo -e "$(tput setaf 1)Error: incorrect branch name " $branch_name 6cd discussions-middleware 7npm install 8npm run start``

here you have give branch name to clone the repo. You see all available branch names here [DMW-Branchs](https://github.com/Sunbird-Ed/discussions-middleware/branches). Then follow this steps [Step-2](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2259812379/Developer+s+Doc+How+to+setup+and+use+Discussions-middleware#Step-2:--Add-the-following-configuration-in-environmentVariablesHelper.js)

### How To Setup Discussion Forum UI

This section will help to set up and use the Discussion-UI library.

#### Background: <a href="#background" id="background"></a>

Discussion-UI library is an angular base library that will help any platform to configure and use a discussion forum.

In the Sunbird use case, any of the learning sections can have a discussion forum attached to it like Courses, Groups, etc. This is being achieved by this library.

#### Git Repository: <a href="#git-repository" id="git-repository"></a>

[https://github.com/Sunbird-Ed/discussions-UI](https://github.com/Sunbird-Ed/discussions-UI)

#### Peer dependencies: <a href="#peer-dependencies" id="peer-dependencies"></a>

* [@project-sunbird/client-services](https://github.com/Sunbird-Ed/sunbird-client-services)
* lodash-es
* ngx-chips
* ngx-infinite-scroll

#### Prerequisite: <a href="#prerequisite" id="prerequisite"></a>

1. [**NodeBB:** ](https://docs.nodebb.org/installing/os/)Local setup
2. [**Discussion middleware**](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2259812379/Developer+s+Doc+How+to+setup+and+use+Discussions-middleware): Local setup

#### Discussions-UI library local set-up: <a href="#discussions-ui-library-local-set-up" id="discussions-ui-library-local-set-up"></a>

Git clone the discussion-ui library:

`1> git clone git@github.com:Sunbird-Ed/discussions-UI.git 2> cd discussion-UI 3> yarn`

Now change the configuration of library/application to communicate with local NodeBB & Discussion-middleware.

Note: Make sure Local discussion-middeware & NodeBB is running.

`1Open "url.config.ts" file 2Change the property "host" to local discussion-middleware setup 3=> host: 'http://localhost:3002'`

Build the discussion-UI library project. The build will get created in `dist` folder.

`1> ng build --watch=true`

Now run the demo application

`1> npm run demo`
