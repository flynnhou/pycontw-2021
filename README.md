# pycontw-2021

## Get Started

```bash
$ npm ci
```

#### Develop with local data server

```bash
$ npm run json-server
$ npm run dev
```

#### Develop with staging/production API server

```bash
# staging
$ ENV=staging npm run dev
$
# production
$ ENV=production npm run dev
```

## Build Setup

```bash
# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

## Dependencies

#### nuxtjs

> Read the docs for more details: https://nuxtjs.org/docs/2.x/get-started/installation

#### tailwindcss

> Read the docs for more details: https://tailwindcss.com/docs

#### @nuxtjs/axios

> Read the docs for more details: https://go.nuxtjs.dev/axios

###### Usage

Use the plugged-in axios in `asyncData()` of a Vue instance in the need of an API call.

```vue
<template>
    <div>{{ resourceOneData.name }}</div>
    <div>{{ resourceTwoData.name }}</div>
</template>
<script>
export default {
    name: 'componentName',
    async asyncData({ $axios }) {
        const { data: resourceOneData } = await $axios.$get('/path/to/resource/one')
        const { data: resourceTwoData } = await $axios.$get('/path/to/resource/two')
        return {
            resourceOneData,
            resourceTwoData,
        }
    }
}
</script>
```

#### nuxt-i18n

> Read the docs for more details: https://i18n.nuxtjs.org/

###### Usage

For modularization, each page or component should create a `<component-name>.i18n.js` containing
the below format:

```js
export default {
    messages: {
        // utilize the the function in utils/i18n.util.js to reduce repetitive code
        'en-us': {
            nameToTranslate: '<Translation>',
        },
        'zh-hant': {
            nameToTranslate: '<翻譯>',
        },
    },
}
```

Then, import the i18n objects into the component for localization. Say if the file system looks like:

```bash
|-- pages/
|---- about/
|------ about.vue
|------ about.i18n.js
```

In the `pages/about.vue`, import the i18n to the Vue instance.

```vue
<template>...</template>

<script>
import i18n from './about.i18n'

export default {
    i18n,
    name: 'about',
    ...
}
</script>
```

## DevDependencies

#### json-server

The `json-server` is served as a mock data server so that frontend doesn't have to rely on the API
development. Rather, set up a mocked json formatted data payload in `db.json` with proper hierarchy
should accelerate the progress for data integration.

###### Usage

```bash
# use json-server (localhost:9876) as the backend for development
$ npm run json-server
$ BASE_URL=http://localhost:9876 npm run dev
```

#### prettier

Use `prettier` to opinionate the coding conventions. In short, this project has set with:

-   4 spaces as the indentation (for better readability)
-   always have trailing commas (needless to worry about the git changes and being easy to extend or
    move around the items in an array or object)
-   ending line without a semi-colon (align with the pythonist habit)

Please format code with `prettier` every once in a while to ensure the codebase consistency. 
