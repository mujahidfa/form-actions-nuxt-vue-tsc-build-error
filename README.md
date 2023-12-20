# Reproduction for @hebilicious/form-actions-nuxt v0.3.0 vue-tsc error when type-checking is enabled at build time

`ERROR(vue-tsc)  ';' expected.` and ` ERROR(vue-tsc)  Expression expected.` in `.nuxt/types/loader-types.d.ts`.

To reproduce this error, install the following packages in a fresh Nuxt project:

```bash
npm install -D vue-tsc typescript
npm install @hebilicious/form-actions-nuxt
```

enable type-checking at build time:

```ts
// In nuxt.config.ts
export default defineNuxtConfig({
  modules: ['@hebilicious/form-actions-nuxt'],
  typescript: {
    // Enable type-checking at build time
    typeCheck: true,
  },
});
```

and run `npm run dev`. The following error surfaces:

```
 ERROR                                                                                                      5:13:40 PM
 ERROR(vue-tsc)  ';' expected.
 FILE  /home/mujahidfa/form-actions-nuxt-vue-tsc-build-error/.nuxt/types/loader-types.d.ts:18:16

    16 |           type LoaderUrl = 
    17 |
  > 18 |           type LoaderName = 
       |                ^^^^^^^^^^
    19 |
    20 |           
    21 |

 ERROR(vue-tsc)  Expression expected.
 FILE  /home/mujahidfa/form-actions-nuxt-vue-tsc-build-error/.nuxt/types/loader-types.d.ts:22:11

    20 |           
    21 |
  > 22 |           export interface Loaders {
       |           ^^^^^^
    23 |             
    24 |           }
    25 |

[vue-tsc] Found 2 errors. Watching for file changes.
```

## Setup

```bash
npm install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
npm run dev
```

## Production

Build the application for production:

```bash
npm run build
```

Locally preview production build:

```bash
npm run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
