# Deploying JSON Server on [render.com](http://render.com/) ( Heroku Alternative )
# Json document:- `https://www.npmjs.com/package/json-server`
We are gonna see how we can deploy `json-server` to [render.com](http://render.com/) which is a good alternative to heroku as heroku is gonna shut down it's free services in sometime.

You can read [json server documentation here](https://www.npmjs.com/package/json-server)

# Step 1 : Create a folder ( You can give it any name; I am gonna name my folder `mock-server-app`

```bash
mkdir mock-server-app
```

# Step 2 : Move into folder

```bash
cd mock-server-app
```

# Step 3 : Run the following command

```bash
npm init -y
```

When you run the above command. You should see something like this in your terminal. This will also create a `package.json` file which would look something like this

`package.json`

```bash
Wrote to /Users/abduljabbarpeer/Teach_Frontend/mock-server-app/package.json: #( package.json path in your system will be displayed )

{
  "name": "mock-server-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
}
```

# Step 4 : Install `json-server` library

```bash
npm i json-server
```

# Step 5 : For the next step; You need to create some files and add/change some code/data to it

PS : This is part of `json-server` documentation. Here's the [documentation link](https://www.npmjs.com/package/json-server)

1. Create a file called `db.json` and add the data that you want to host. I am adding the following fake users data which has been generated using  is super helpful if you want to generate fake data for any purpose ( I use it for dev purposes )

`db.json`

```bash
{
  "users": [
    {
      "id": 1,
      "name": "Gertrudis Tatterton",
      "age": 18,
      "email": "gtatterton0@ehow.com"
    },
    {
      "id": 2,
      "name": "Gail Newbatt",
      "age": 53,
      "email": "gnewbatt1@un.org"
    },
    {
      "id": 3,
      "name": "Walliw Wilstead",
      "age": 49,
      "email": "wwilstead2@tripadvisor.com"
    },
    {
      "id": 4,
      "name": "Abran Proback",
      "age": 29,
      "email": "aproback3@theglobeandmail.com"
    },
    {
      "id": 5,
      "name": "Roda Chappelow",
      "age": 31,
      "email": "rchappelow4@oaic.gov.au"
    },
    {
      "id": 6,
      "name": "Karney Wylie",
      "age": 22,
      "email": "kwylie5@miitbeian.gov.cn"
    },
    {
      "id": 7,
      "name": "Cammi Pimbley",
      "age": 63,
      "email": "cpimbley6@nyu.edu"
    },
    {
      "id": 8,
      "name": "Gavra Manning",
      "age": 43,
      "email": "gmanning7@lycos.com"
    },
    {
      "id": 9,
      "name": "Zachary Seward",
      "age": 45,
      "email": "zseward8@oracle.com"
    },
    {
      "id": 10,
      "name": "Chucho Norssister",
      "age": 20,
      "email": "cnorssister9@mayoclinic.com"
    }
  ]
}
```

1. Create a file called `server.js` and add the following code

`server.js`

```jsx
const jsonServer = require("json-server"); // importing json-server library
const server = jsonServer.create();
const router = jsonServer.router("db.json");
const middlewares = jsonServer.defaults();
const port = process.env.PORT || 3001; // you can use any port number here; i chose to use 3001

server.use(middlewares);
server.use(router);

server.listen(port);
```

1. Create a file called `.gitignore` and add the following code ( It ignores node_modules when the code is hosted on github )

```jsx
node_modules
```

1. Finally you need to make some changes to your `package.json` file that got created initially.

```json
{
  "name": "mock-server-app",
  "version": "1.0.0",
  "description": "mock server app",
  "main": "server.js",// since i want server.js to be entry point. I need to update the same here( if you have used index.js. then update your filename here )
  "scripts": {
    "start": "node server.js" // npm start command
  },
  "keywords": [],
  "author": "abdul",
  "license": "ISC",
  "dependencies": {
    "json-server": "^0.17.0"
  }
}
```

# Step 6 : Pushing the code to github

1. Create a repo on github

![Screenshot 2022-09-27 at 11.00.05 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd78c13d-8a14-4af0-a73a-7f8b85f739ed/Screenshot_2022-09-27_at_11.00.05_AM.png)

![Screenshot 2022-09-27 at 11.02.56 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43a58ae5-0517-46f7-8c22-dba2e3e2bea7/Screenshot_2022-09-27_at_11.02.56_AM.png)

1. Initialise Git Repo

```bash
git init
```

1. Add Origin

```bash
git remote add origin https://github.com/<your-github-username>/<your-repo-name>.git
```

1. Add

```bash
git add .
```

1. Commit

```bash
git commit -m "add-your-commit-message-here"
```

1. Push

```bash
git push origin main
```

just check your github repo whether it has been updated or not

![Screenshot 2022-09-27 at 11.38.18 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a7c06df-989f-49e8-b927-f00289840eb9/Screenshot_2022-09-27_at_11.38.18_AM.png)

# Step 7 : Now comes the part of deployment. For that please go to [https://render.com/](https://render.com/)

1. Click on signin

![Screenshot 2022-09-27 at 11.42.35 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5ce65f09-75d8-4a32-8d2f-b82dafacc871/Screenshot_2022-09-27_at_11.42.35_AM.png)

1. If you don’t have an account; Signup and then login. you have lot of options to signup and login. I personally went with using github credentials and I’d suggest you do the same ( I am gonna continue this with the assumption that you have done signup and login using github option )

PS : When you signup for the first time; You will be asked to verify your email and once verified you will able to start utilizing [render.com](http://render.com) services 

1. This is how the dashboard of [render.com](http://render.com) will look like once you sign in 

![ezgif-5-9809892062.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/17ff6509-73c0-40e8-97c1-048a483b1a2a/ezgif-5-9809892062.png)

and if you have already created a project in the past. It’d look like this

![ezgif-5-5444a9e5da.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/47f50d8d-9ab7-46fd-a2a3-44ad574b223f/ezgif-5-5444a9e5da.png)

Clicking on `New +` Button at the top also gives you the same options

1. Click on `New Service` button. You’ll see a page like this. Connect your github account

      

![ezgif-5-1d6e44af9f.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7832b6f9-28d3-4a21-839a-596e6a937e19/ezgif-5-1d6e44af9f.png)

1. You’ll see the following screen then

![Screenshot 2022-09-27 at 12.11.29 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ed08337-1eb1-494e-b7bc-de86f68e3ae0/Screenshot_2022-09-27_at_12.11.29_PM.png)

You can either give permission to select all your repositories or only selected repository. You’ll have to chose repository here if you go with only select repository option.

I have selected `All Repositories` and gave permission to access all repositories. Then click on `install` button

Now I will have to select the repository that I want to deploy

1. So I select the repo ( mock-server-app ) that I want to deploy

![ezgif-5-dd8374f299.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/584a837b-9f15-4f05-bdfa-4b619f798562/ezgif-5-dd8374f299.png)

1. You’ll get the following screen. Some of the input boxes here gets auto populated from the github repo itself which is great.

![220927-1.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9bf5452-6cf6-471d-9124-a5e2d0421d02/220927-1.png)

Give name to your application and you can leave root directory empty for this one

`Enviroment`, `Region`, `Branch`, `Build Command`, `Start Command` data was automatically picked which is fine as that’s correct. If you need to configure something in here; you can do so

The `Name` field here will be your application URL once it’s deployed. So I am gonna go ahead and give it some name

![220927-2.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe63816f-cac6-4758-8896-bdbd0a82ab5b/220927-2.png)

Plan I have selected is `Free`

You can go to `Advanced` and add `.env` variables and also you can chose `Auto-Deploy` option to either Yes or No. By default it’ll be yes.

And since I don’t have `.env` variables and I want to auto-deploy my changes on github repo. I am not gonna go to Advance and make any changes

8. I’ll then click on `Create Web Service` which will showcase the following screen.

![ezgif-5-d988166088.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de09578a-5a42-4650-8cfd-3475cb413d12/ezgif-5-d988166088.png)

 

1. Once deployment is successful. If you go check the same in browser. I am able to access data as expected

![Screenshot 2022-09-27 at 12.58.46 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fdd5f997-9b90-4485-80f3-8ec03311c466/Screenshot_2022-09-27_at_12.58.46_PM.png)

## Deployed Link:- `https://json-mock-4.onrender.com/users/`
