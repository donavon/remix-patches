# remix-patches

This package contains various patches for Remix. It depends on [`patch-package`](https://github.com/ds300/patch-package) which you will need to install manually.

Once installed, you will need to add an entry to your `package.json`'s `post-install` script as follows:

```
"postinstall": "patch-package --patch-dir node_modules/remix-patches/{patch-name-here}"
```

where `{patch-name-here}` is the name of the patch you want to install.

For example, the following will patch Remix to allow Open Graph verticals support.

```
"postinstall": "patch-package --patch-dir node_modules/remix-patches/og-verticals"
```

## Patches

| Patch name                           | Description                                        |
| ------------------------------------ | -------------------------------------------------- |
| [mdx-data](./mdx-data)               | Exposes the `data` returned from Remark plugins    |
| [og-verticals](./og-verticals)       | Open Graph verticals support                       |
| [remix-config-ts](./remix-config-ts) | Adds TypeScript support for your Remix config file |

See the README file in each individual patches folder for more information.

## License

Copyright (c) 2022 Donavon West. Released under the [MIT License](./LICENSE).
