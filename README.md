<a href="https://markprompt.com">
  <img alt="Markprompt – Open-source GPT-4 platform for Markdown, Markdoc and MDX with built-in analytics" src="https://user-images.githubusercontent.com/504893/227404383-62737a47-72ab-4426-b7b3-83db5b836ebb.png">
  <h1 align="center">Markprompt</h1>
</a>

Markprompt is a platform for building GPT-powered prompts. It scans Markdown, Markdoc and MDX files in your GitHub repo and creates embeddings that you can use to create a prompt, for instance using the companion [Markprompt React](https://github.com/motifland/markprompt/blob/main/packages/markprompt-react/README.md) component. Markprompt also offers analytics, so you can gain insights on how visitors interact with your docs.

<br />

<p align="center">
  <a href="https://twitter.com/markprompt">
    <img src="https://img.shields.io/twitter/follow/markprompt?style=flat&label=%40markprompt&logo=twitter&color=0bf&logoColor=fff" alt="Twitter" />
  </a>
  <a aria-label="NPM version" href="https://www.npmjs.com/package/markprompt">
    <img alt="" src="https://badgen.net/npm/v/markprompt">
  </a>
  <a aria-label="License" href="https://github.com/motifland/markprompt/blob/main/LICENSE">
    <img alt="" src="https://badgen.net/npm/license/markprompt">
  </a>
</p>

## Self-hosting

Markprompt is built on top of the following stack:

- [Next.js](https://nextjs.org/) - framework
- [Vercel](https://vercel.com/) - hosting
- [Typescript](https://www.typescriptlang.org/) - language
- [Tailwind](https://tailwindcss.com/) - CSS
- [Upstash](https://upstash.com/) - Redis and rate limiting
- [Supabase](https://planetscale.com/) - database and auth
- [Stripe](https://stripe.com/) - payments
- [Plain](https://plain.com/) - support chat
- [Fathom](https://usefathom.com/) - analytics

### Supabase

You'll need a Supabase account and the [supabase CLI](https://supabase.com/docs/guides/cli). 
To set up a new Supabase project with this repo, follow these instructions:
If you haven't already, sign up at Supabase and create a new project.

1. Clone this repo
2. `yarn install` (This repo uses yarn)
3. (The repo has already been initialized to use Supabase, so no need to `supabase init`)
4. If you haven't already, sign up at Supabase and create a new project.
5. `supabase project create`
6. `supabase start`
7. Once the project is created, go to the Project Settings and find the API URL and Public API Key. 

### UpStash

1. Create an account at [Upstash](https://upstash.com/).

### Environment variables:

1. In the root of the repo, copy `.env.example` to `.env` and fill in the supabase and UpStash and OpenAI environment variables.

### Database Schema

You need to create the local database schema and apply migrations:
1. `yarn run supabase_db_reset`
(The schema is defined as the first migration step in `supabase/migrations/20230401212256_init.sql`.)

2. To update the types after making a schema change:
```sh
yarn run supabase_create_types_local
```

#### Auth provider

Authentication is handled by Supabase Auth. Follow the [Login with GitHub](https://supabase.com/docs/guides/auth/social-login/auth-github) and [Login with Google](https://supabase.com/docs/guides/auth/social-login/auth-google) guides to set it up.

### Setting environment variables

A sample file containing required environment variables can be found in [example.env](https://github.com/motifland/markprompt/blob/main/example.env). In addition to the keys for the above services, you will need keys for [Upstash](https://upstash.com/) (rate limiting and key-value storage), [Plain.com](https://plain.com) (support chat), and [Fathom](https://usefathom.com/) (analytics).

## Using the React component

Markprompt React is a headless React component for building a prompt interface, based on the Markprompt API. With a single line of code, you can provide a prompt interface to your React application. Follow the steps in the [Markprompt React README](https://github.com/motifland/markprompt/blob/main/packages/markprompt-react/README.md) to get started using it.

Also, check out the [Markprompt starter template](https://github.com/motifland/markprompt-starter-template) for a fully working Next.js + Tailwind project.

## Usage

Currently, the Markprompt API has basic protection against misuse when making requests from public websites, such as rate limiting, IP blacklisting, allowed origins, and prompt moderation. These are not strong guarantees against misuse though, and it is always safer to expose an API like Markprompt's to authenticated users, and/or in non-public systems using private access tokens. We do plan to offer more extensive tooling on that front (hard limits, spike protection, notifications, query analysis, flagging).

## Data retention

OpenAI keeps training data for 30 days. Read more: [OpenAI API data usage policies](https://openai.com/policies/api-data-usage-policies).

Markprompt keeps the data as long as you need to query it. If you remove a file or delete a project, all associated data will be deleted immediately.

## Community

- [Twitter @markprompt](https://twitter.com/markprompt)
- [Twitter @motifland](https://twitter.com/motifland)
- [Discord](https://discord.gg/MBMh4apz6X)

## Authors

Created by the team behind [Motif](https://motif.land)
([@motifland](https://twitter.com/motifland)).

## License

MIT
