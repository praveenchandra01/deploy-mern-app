# Deploy MERN apps for free
Deploying single react applications and full-stack web applications using Heroku and Netlify/Github.

# Deploying Full-Stack Apps

1) Create a Heroku app.
2) Change your Node app port to
```
process.env.PORT || <any port number>
```
3) Move your front-end app inside the Node app.
4) Add these codes inside your main JS file in your Node app.
```
app.use(express.static(path.join(__dirname, "/<front end app folder name>/build")));

app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, '/<front end app folder name>/build', 'index.html'));
});
```

5) Add this script to your package.json in the Node app.

```
"heroku-postbuild": "cd client && npm install && npm run build"
```

6) Change your API URL in your React app.

7) Set your environment variables on Heroku

8) Run these codes.
```bash
heroku login
```
```bash
git init
```
```bash
heroku git:remote -a <app-name>
```
```bash
git add .
```
```bash
git commit -am "my first commit"
```
```bash
git push heroku master
```
---
# Deploying a React App to GitHub Pages

> [reference deployment guide](https://github.com/gitname/react-gh-pages),
> [official deployment guide](https://create-react-app.dev/docs/deployment/#github-pages)


### 1. Create an **empty** repository on GitHub

### 2. Create a React app

1. Create a React app named `my-app`:
  
    ```shell
    $ npx create-react-app my-app
    ```

    > That command will create a React app written in JavaScript. To create one written in [TypeScript](https://create-react-app.dev/docs/adding-typescript/#installation), you can issue this command instead:
     ```shell
     $ npx create-react-app my-app --template typescript
     ```
    
2. Enter the newly-created folder:
  
    ```shell
    $ cd my-app
    ```


### 3. Install the `gh-pages` npm package

 
    ```shell
    $ npm install gh-pages --save-dev
    ```


### 4. Add a `homepage` property to the `package.json` file


 Add a `homepage` property in this format\*: `https://{username}.github.io/{repo-name}`

    ```diff
    {
      "name": "my-app",
      "version": "0.1.0",
    + "homepage": "https://gitname.github.io/react-gh-pages",
      "private": true,
    ```


### 5. Add deployment scripts to the `package.json` file


    ```diff
    "scripts": {
    +   "predeploy": "npm run build",
    +   "deploy": "gh-pages -d build",
        "start": "react-scripts start",
        "build": "react-scripts build",
    ```


### 6. Add a "remote" that points to the GitHub repository

    
    ```shell
    $ git remote add origin https://github.com/{username}/{repo-name}.git
    ```


### 7. Deploy the React app to GitHub Pages

    ```shell
    $ npm run deploy
    ```


**That's it!** The React app has been deployed to GitHub Pages! :rocket:
    

### 8. (Optional) Store the React app's _source code_ on GitHub


    ```shell
    $ git add .
    $ git commit -m "Configure React app for deployment to GitHub Pages"
    $ git push origin master
    ```

> I recommend exploring the GitHub repository at this point. It will have two branches: `master` and `gh-pages`. The `master` branch will contain the React app's source code, while the `gh-pages` branch will contain the distributable version of the React app.

----
## Single React App on Heroku

1) Create a Heroku account.
2) Create your app.
3) Download Heroku CLI from [here](https://devcenter.heroku.com/articles/heroku-cli#download-and-install).
4) Run these codes.
```bash
heroku login
```
```bash
git init
```
```bash
heroku git:remote -a <app-name>
```
```bash
heroku create -b https://github.com/mars/create-react-app-buildpack.git
```
```bash
git add .
```
```bash
git commit -am "my first commit"
```
```bash
git push heroku master
```
----
## Single React App on Netlify

### Deploy using the browser

1) Build your application
```bash
yarn build
```
2) Drag and drop your build folder to Netlify manual upload section.

### Deploy using Github

1) Connect to the Github
2) Choose your repository/branch
3) Change the deployment code to
```
CI= npm run build
```
