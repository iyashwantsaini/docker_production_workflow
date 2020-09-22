
<h1 align="center">
  <br>
  <a href=""><img src="logo.png
" alt="Project_Logo" width="200"></a>
  <br>
  Docker Production Grade Workflow
  <br>
</h1>

<h4 align="center">Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.</h4>

## Phases

- DEV
  - develop, add ,test
  - DockerFile.dev
    - for development
    - first remove node_modules from root
    - this will make build faster
      ```
      > docker build -f DockerFile.dev .
      ```
    - now Run Server
      ```
      > docker run -it -p 3000:3000 image_id
      ```
    - to pass args in container
      ```
      > docker attach container_id
      ```
      ```
      > docker exec -it container_id sh 
      ```
- TEST
  - travis testing
- PROD
  - Deploy to cloud services like Elastic Beanstalk
  - DockerFile
    - for production
    ```
    > docker build .
    ```

## nginx

- nginx is a web server to serve our files
- We'll use a multistep build process
  - Run npm build
  - Use nginx  
  - Copy over result of npm run build
  - Start nginx

## travis-ci

- tell travis we need docker
- build img using DockerFile.dev
- tell travis to run test suite
- tell travis to deploy code to aws

## Elastic Beanstalk

- create web server env for docker platform

## Mapping

- Docker Volumes
  - Stores references instead of snapshots
  - Whenever any change occurs it automatically passes to container
- New Docker Running Command (to enable mapping)
  - run in GitBash
  - "-v $(pwd):/app" : mapping current dir to /app in container
  - "-v /app/node_modules" : bookmarking node_modules as we dont have node_modules in local env but they are still in container
    ```
    > docker run -it -p 3000:3000 -v /app/node_modules -v $(pwd):/app image_id
    ```
- Using Docker Compose
    ```
    > docker-compose up
    ```

## Branches

- master
  - clean working copy of code
  - changes here are automatically deployed
- feature
  - we make changes here
  - testing here
  - feature addition here
  - pull and push only from and to this branch
  - pull request to master when all tests passes from travis-ci

## Setup Project Base

```
> npm install -g create-react-app
> create-react-app workflow
> cd workflow
```

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## License

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

By [Yashwant](https://github.com/meyash)

## Contributors

<img src="https://avatars3.githubusercontent.com/u/21121279?s=460&u=f0450278b2b569c4443ab8ee03f9dff7015da5bf&v=4" width="100px;" alt="toofff"/><br />

<a href="https://meyash.xyz/" style="margin-right:30px;"><img src="https://meyash.xyz/assets/icons/siteicon.png" width="25"></a>
<a href="https://meyash.xyz/resume.pdf" style="margin-right:30px;"><img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/libreoffice.svg" width="25"></a> 
<a href="https://www.linkedin.com/in/meyash21/" style="margin-right:30px;"><img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" width="25"></a>
<a href="https://twitter.com/meyash21" style="margin-right:30px;"><img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" width="25"></a>
<a href="https://www.instagram.com/meyash21/" style="margin-right:30px;"><img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/instagram.svg" width="25"></a>
<a href="https://www.codechef.com/users/meyash21" style="margin-right:30px;"><img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/codechef.svg" width="25"></a>  