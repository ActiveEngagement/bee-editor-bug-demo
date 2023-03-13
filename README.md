# Bee Editor Bug Demo

## How to use this repo

1. Run `pnpm install` in the root of the repo.
2. Create a file called `.env` at the root of the project.
3. Paste in the follow and replace with real API keys.
   
      VITE_BEE_PLUGIN_CLIENT_ID=client-id \
      VITE_BEE_PLUGIN_CLIENT_SECRET=client-secret
4. Run `pnpm run dev`
5. Paste in the following code in a text block and save:
   
      </#if>
6. Reload the page, and see the `</#if>` is missing, despite being properly encoded and contained in the payload, which is viewable in `console.log`.