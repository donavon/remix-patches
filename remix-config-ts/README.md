# remix-config-ts

Patch Remix to allow you to specify a `remix.config.ts` config file (i.e. TypeScript).

It also allows the for the default export to be an async function that returns a configuration.

## Peer Dependencies

In order to use `remix-config-ts`, you must install the following peer dependencies:

```bash
npm i bundle-require
```

## Example Usage

```ts
import { AppConfig } from '@remix-run/dev/config';

type ConfigFunction = () => Promise<AppConfig>;

export const readConfig: ConfigFunction = async () => {
  // some async operation here

  return {
    serverBuildTarget: 'netlify',
    server: './server.js',
    ignoredRouteFiles: ['.*'],
  };
};

export default readConfig;
```
