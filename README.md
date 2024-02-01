## 🧱 Pre-req’s

- Unix-based OS (if Windows, WSL2)
- Docker
- Node.js 18+

## Step-by-step

#### Install dependencies

First install NPM dependencies.

```bash
npm i
```

#### Setup Supabase stack

When developing a project in Supabase, you can choose to develop locally or directly on the cloud.


##### Cloud

1. Create a Supabase project at https://database.new, or via the CLI:

   ```shell
   npx supabase projects create -i "ChatGPT Your Files"
   ```

   Your Org ID can be found in the URL after [selecting an org](https://supabase.com/dashboard/org/_/general).

1. Link your CLI to the project.

   ```shell
   npx supabase link --project-ref <project-id>
   ```

   You can get the project ID from the [general settings page](https://supabase.com/dashboard/project/_/settings/general).

1. Store Supabase URL & public anon key in `.env.local` for Next.js.

   ```shell
   NEXT_PUBLIC_SUPABASE_URL=<api-url>
   NEXT_PUBLIC_SUPABASE_ANON_KEY=<anon-key>
   ```

   You can get the project API URL and anonymous key from the [API settings page](https://supabase.com/dashboard/project/_/settings/api).


1.  If you're developing directly on the cloud, set your `OPENAI_API_KEY` secret in the cloud:

    ```shell
    npx supabase secrets set OPENAI_API_KEY=<openai-key>
    ```

    Then deploy your edge function:

    ```shell
    npx supabase functions deploy
    ```

If you would like to jump directly to the completed app, simply checkout the `main` branch:

```shell
git checkout main
```

## 🚀 Going to prod

If you've been developing the app locally, follow these instructions to deploy your app to a production Supabase project.

1. Create a Supabase project at https://database.new, or via the CLI:

   ```shell
   npx supabase projects create -i "ChatGPT Your Files"
   ```

1. Link the CLI with your Supabase project.

   ```bash
   npx supabase link --project-ref=<project-ref>
   ```

   You can grab your project's reference ID in your [project’s settings](https://supabase.com/dashboard/project/_/settings/general).

1. Push migrations to remote database.

   ```bash
   npx supabase db push
   ```

1. Set Edge Function secrets (OpenAI key).

   ```bash
   npx supabase secrets set OPENAI_API_KEY=<openai-key>
   ```

1. Deploy Edge Functions.

   ```bash
   npx supabase functions deploy
   ```

1. Deploy to Vercel _(or CDN of your choice - must support Next.js API routes for authentication)_.

   - Follow Vercel’s [deploy instructions](https://nextjs.org/learn/basics/deploying-nextjs-app/deploy).
   - Be sure to set `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY` for your Supabase project.

     You can find these in your [project’s API settings](https://supabase.com/dashboard/project/_/settings/api).

