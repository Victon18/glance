---
id: server
aliases: []
tags: []
---
# serverless
### cloudflare workers
```bash
# initialization
npm create cloudflare -- my-app
# start worker locally
npm run dev
```
---
Wrangler
--
```bash
#login
npx wrangler login
# deploying my worker
npm run deploy
```
- returning json
```ts
export default {
	async fetch(request: Request, env: Env, ctx: ExecutionContext): Promise<Response> {
		return Response.json({
			message: "hi"
		});
	},
};
```
Routing
---
```ts
export interface Env {}
export default {
	async fetch(request: Request, env: Env, ctx: ExecutionContext): Promise<Response> {
		console.log(request.body);
		console.log(request.headers);

		if (request.method === 'GET') {
			return Response.json({
				message: 'you sent a get request',
			});
		} else {
			return Response.json({
				message: 'you did not send a get request',
			});
		}
	},
};
```
### hono
for adding express like syntax
```bash
npm create hono@latest my-app
```
1. getting inputs from user
```ts
import { Hono } from 'hono'

const app = new Hono()

app.get('/', async (c) => {
  const body = await c.req.json()
  console.log(body);
  console.log(c.req.header("Authorization"));
  console.log(c.req.query("param"));

  return c.text('Hello Hono!')
})

export default app
```
---
2, auth
```ts
import { Hono, Next } from "hono";
import { Context } from "hono/jsx";

const app = new Hono();
async function authMiddlewares(c: any, next: any) {
  if (c.req.header("Authorization")) {
    // Do validation
    await next();
  } else {
    return c.text("You dont have acces");
  }
}

app.get("/", authMiddlewares, async (c) => {
  const body = await c.req.parseBody();
  console.log(body);
  console.log(c.req.header("Authorization"));
  console.log(c.req.query("param"));

  return c.json({ msg: "as" });
});

export default app;
```
3. auth middleware
```ts
import { Hono, Next } from 'hono'
import { Context } from 'hono/jsx';

const app = new Hono()

app.use(async (c, next) => {
  if (c.req.header("Authorization")) {
    // Do validation
    await next()
  } else {
    return c.text("You dont have acces");
  }
})

app.get('/', async (c) => {
  const body = await c.req.parseBody()
  console.log(body);
  console.log(c.req.header("Authorization"));
  console.log(c.req.query("param"));

  return c.json({msg: "as"})
})

export default app
```
### connection pooling
1.
```bash
# installing prisma
npm install --save-dev prisma
# initialization
npx prisma init
```
2.
```ts
/*creating basic schema*/
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id       Int    @id @default(autoincrement())
  name     String
  email    String
	password String
}
```
3.
```bash
# creating migration
npx prisma migrate dev --name init
# signup to prisma accelarate
# enable accelarate and generate api key
# replace that in .env file
# DATABASE_URL="prisma://accelerate.prisma-data.net/?api_key=your_key"
# adding accelerate
npm install @prisma/extension-accelerate
# generating accelerate client
npx prisma generate --no-engine
```
4.
```ts
import { Hono, Next } from 'hono'
import { PrismaClient } from '@prisma/client/edge'
import { withAccelerate } from '@prisma/extension-accelerate'
import { env } from 'hono/adapter'

const app = new Hono()

app.post('/', async (c) => {
  // Todo add zod validation here
  const body: {
    name: string;
    email: string;
    password: string
  } = await c.req.json()
  const { DATABASE_URL } = env<{ DATABASE_URL: string }>(c)

  const prisma = new PrismaClient({
      datasourceUrl: DATABASE_URL,
  }).$extends(withAccelerate())

  console.log(body)

  await prisma.user.create({
    data: {
      name: body.name,
      email: body.email,
      password: body.password
    }
  })

  return c.json({msg: "as"})
})

export default app
```
# aws backend(Ec2) server
1. creating server
---
- create new instance
- add name
- add os
- select size
- create key-pair
- custom size allocation
- allowing traffic on http-https
---
2. ssh into server
```bash
# give ssh permission
chmod 700 kirat-class.pem
# ssh into machine
ssh -i kirat-class.pem ubuntu@ec2-65-0-180-32.ap-south-1.compute.amazonaws.com
# create server
# connect to internet
# https://www.tecmint.com/resolve-temporary-failure-in-name-resolution/
# install node js
sudo dnf install node
npm install
# start backend
node index.js
# hit the server and open/close ports from security group
# http://your_domain:8080
```
### ngnix
reverse proxy
```bash
# installing
sudo apt update
sudo apt install nginx
# creating a reverse proxy
sudo rm sudo vi /etc/nginx/nginx.conf
sudo vi /etc/nginx/nginx.conf
```
```
events {
    # Event directives...
}

http {
	server {
    listen 80;
    server_name be1.100xdevs.com;

    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
	}
}
```
```bash
# load config
sudo nginx -s reload
# start backend
node index.js
# visit site
```
### certificate management
Certbot
```bash
# install
sudo snap install --classic certbot
# create symblink
sudo ln -s /snap/bin/certbot /usr/bin/certbot
# autocreate certificate and config changes
sudo certbot --nginx
# renewal
sudo certbot renew --dry-run
```
# aws frontend
- object store (S3)
- CDNs (cloudfront)
1. initial
```bash
# Access your aws (S3) and cloudfront account
# go to your react project
# build project
npm run build
# serve locally
npm i -g serve
serve
# create object store (bucket) from website
# upload assets files to aws
# access your site
```
2. OAC
---
- create cloudfront distribution
- select your bucket on origin domain
- enable Origin Access Control (OAC)
- create a new OAC
---
3. own domain
---
- select edit on root page
- attach domain name to the distributon
- create certificate
- Add a CNAME record for the website to point to your cloudfront URL
---
4. error pages
---
- create a error page
- create a custom error response
- customize error respnse which will direct to error page
---
