# Environment Variables Demo

This is a repro demonstrating that Next.js replaced the `process.env.NODE_ENV`
with `production` no matter what is set during build (even if it's set to `test`
which is documented as [a supported env](https://nextjs.org/docs/basic-features/environment-variables#test-environment-variables)).

To reproduce the issue, do the following:
1. Install dependencies:

```
$ yarn install
```

2. Build the app using the `test` environment:

```
$ yarn test:build
```

3. Start the app using the `test` environment:

```
$ yarn test:start
```

4. Visit the API route at http://localhost:3000/api/env and notice that the JSON
   response contains `production` instead of `test`. This is because Next.js
   hardcodes (i.e. replaces) the `process.env.NODE_ENV` variable to `production`
   when running `next build`. This is not ideal when you want to use the
   `NODE_ENV` variable to trigger certain behavior during tests (e.g. accessing
   different Algolia search indexes).

## Getting Started

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/import?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
