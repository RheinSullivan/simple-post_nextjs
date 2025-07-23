# Day 1 : Start Setup Project

Before you start and running this project, you need to install the following tools:

1. Make sure you already have or install node.js/npm.
2. Clone this project [https://github.com/RheinSullivan/simple-post_nextjs.git](https://github.com/RheinSullivan/simple-post_nextjs.git).
3. Install the dependencies by running `npm install`.
4. Renaming the `.env.example` component to `.env` is mandatory.
5. Run `npm run dev` to start the development server.

## Clerk Setup

1. Sign up for a account at [https://clerk.com](https://clerk.com).
2. Create a new project application.
3. Once the app is created, get the following values from the Clerk Dashboard:
   1. Publishable Key
   - `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
   2. Secret Key
   - `CLERK_SECRET_KEY`

Add them to the `.env` file.

```.env
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
```

## Supabase Setup

1. Register for an account at [https://supabase.com](https://supabase.com).
2. Create a new project.
3. In the Supabase dashboard, click on your project name in the topbar.
4. Click the **Connect** button on the top right.
5. Open the **ORMs** tab.
6. Copy the .env.local file provided, and insert it into the variable below.
7. Don't forget to replace `YOUR_PASSWORD` in the string with your database password (can be found in **Project Settings > Database**).

Add them to the `.env` file:

```env
# Connect to Supabase via connection pooling
DATABASE_URL=your_supabase_connection_pooling_url

# Direct connection to the database. Used for migrations
DIRECT_URL=your_supabase_direct_connection_url
```

>

## Migrate & Push Database

1. Run the `npx prisma migrate dev` command to create a new table in the database.
2. Run the `npm run db:push` command to push the changes to the database.

# Day 2 :

1. Open the database that you have created.
2. Notice on the left sidebar, there is a **Settings** menu.
3. Click the **Settings** menu, then in the `Project Settings` section, click the `API Keys` menu.
4. In the `service_role` `secret` section, copy and save the `secret` value.
5. Place the `secret` value in the `SUPABASE_ROLE_KEY` variable in the `.env` file.
6. Notice in the header, to the right of your database menu, there is a **Connect** menu, click the menu.
7. Click the `App Frameworks` section, make sure to select the `Next.js` framework, using `Pages Router`, and with `Supabase-Js`.
8. Then copy everything in the `.env.local` column, to get `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_AMON_KEY`.
9. Don't forget to install the `Supabase-Js` depedency, with the prompt `npm install @supabase/supabase-js`.
10. Open the Supabase sidebar again, in the **Storage** menu section, create a storage inside the supabase named `product-images` (optional name) make sure to enable `Public bucket`, so that the images uploaded to the Supabase database, will appear in the Product Management frontend, align it with the `bucket.ts` component.

Add them to the `.env` & `bucket.ts` file:

_.env_

```.env
NEXT_PUBLIC_SUPABASE_URL=your_api_key
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_api_key
SUPABASE_ROLE_KEY=your_api_key
```

_bucket.ts_

```bucket.ts
  export enum Bucket {
    ProductImages = "product-images", //optional
  }
```

_Activity Result :_

- [x] Create product  
- [x] Read Product
- [x] Include file uploads with signed URL
- [x] Forms -> RHF (React Hook Form)
- Update Product
- Filter products by category
- Delete Product

PRE-SIGNED URL -> POST https://.......

1. Send a request to the backend to get a presigned URL
2. Upload the image to the presigned URL
3. Retrieve the object URL (product image)
4. Send the image URL to the tRPC mutation

Cons
- Requires two requests
- The uploaded image might not be used

Pros
- Does not burden the server

# Day 3

- [x] Read products (filter by category)
- [x] Add to cart (global state with Zustand)
- [x] Generate QRIS (Xendit)
- [x] Handle payment (webhook -> NGROK | localtunnel)

Webhook -> POST request from Xendit sent to the Next.js API when a payment is made

tRPC -> Tanstack Query / React Query
- Handle caching

# Create T3 App

This is a [T3 Stack](https://create.t3.gg/) project bootstrapped with `create-t3-app`.

## What's next? How do I make an app with this?

We try to keep this project as simple as possible, so you can start with just the scaffolding we set up for you, and add additional things later when they become necessary.

If you are not familiar with the different technologies used in this project, please refer to the respective docs. If you still are in the wind, please join our [Discord](https://t3.gg/discord) and ask for help.

- [Next.js](https://nextjs.org)
- [NextAuth.js](https://next-auth.js.org)
- [Prisma](https://prisma.io)
- [Drizzle](https://orm.drizzle.team)
- [Tailwind CSS](https://tailwindcss.com)
- [tRPC](https://trpc.io)

## Learn More

To learn more about the [T3 Stack](https://create.t3.gg/), take a look at the following resources:

- [Documentation](https://create.t3.gg/)
- [Learn the T3 Stack](https://create.t3.gg/en/faq#what-learning-resources-are-currently-available) — Check out these awesome tutorials

You can check out the [create-t3-app GitHub repository](https://github.com/t3-oss/create-t3-app) — your feedback and contributions are welcome!

## How do I deploy this?

Follow our deployment guides for [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify) and [Docker](https://create.t3.gg/en/deployment/docker) for more information.
