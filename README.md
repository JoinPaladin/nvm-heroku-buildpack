# nvm-heroku-buildpack

This custom Heroku buildpack is designed specifically for building Node.js applications with different versions 
using NVM (Node Version Manager). Unlike traditional runtime buildpacks, this buildpack is tailored for the application 
build process, ensuring flexibility in managing Node.js versions during the build phase.

In your `package.json` add `engines` section and declare versions of Node.js and NPM.

```json
{
  "engines": {
    "node": "20.10.x",
    "npm": "10.2.x"
  }
}
```

In the root of the project add `nvm-projects.json` and provide list of your Node.js applications

```json
[
  {
    "name": "Frontend (Legacy)",
    "package_path": "./assets/legacy-app/package.json"
  },
  {
    "name": "Frontend",
    "package_path": "./assets/app/package.json"
  }
]
```

Add buildpack to your Heroku app

```bash
$ heroku buildpacks:add https://github.com/Floship/nvm-heroku-buildpack
```