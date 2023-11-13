# qwik-warrant-js

## Overview

The Warrant React library provides components, hooks, and helper methods for controlling access to pages and components in Qwik using [Warrant](https://warrant.dev/). The library interacts directly with the Warrant API using short-lived session tokens that must be created server-side using your API key. Refer to [this guide](https://docs.warrant.dev/guides/creating-session-tokens) to see how to generate session tokens for your users.

## Installation

Use `npm` to install the core Warrant client module [`@warrantdev/warrant-js`](https://github.com/warrant-dev/warrant-js). This module includes methods shared across our client libraries (Vue, Angular, etc.) and additional types (for TypeScript users).

```sh
npm install @warrantdev/warrant-js
```

Use `npm` to install qwik-warrant-js`:

```sh
npm install qwik-warrant-js
```

## Usage

### `WarrantProvider`

Wrap your application with `WarrantProvider`, passing it your Client Key using the `clientKey` prop. `WarrantProvider` uses [Qwik Context](https://qwik.builder.io/docs/components/context/) to allow you to access utility methods for performing access checks anywhere in your app.

```jsx
// root.jsx
import {
  useContextProvider,
} from '@builder.io/qwik';


import Warrant from "@warrantdev/warrant-js";
import { WarrantContext } from "qwik-warrant-js";

// A valid session token is required to initialize the Client
const warrant = new Warrant({
  clientKey: "client_test_f5dsKVeYnVSLHGje44zAygqgqXiLJBICbFzCiAg1E=",
  sessionToken: "sess_test_f9asdfASD90mkj2jXZIaeoqbIUAIjsJAHSAnsndW=",
});

export default component$(() => {
  useContextProvider(WarrantContext, warrant);

  return (
    <QwikCityProvider>
      <head>
        <meta charSet="utf-8" />
        <link rel="manifest" href="/manifest.json" />
        <RouterHead />
        <ServiceWorkerRegister />
      </head>
      <body lang="en">
        <RouterOutlet />
      </body>
    </QwikCityProvider>
  );
});
```

## Notes

We’ve used a random Client Key in these code examples. Be sure to replace it with your
[actual Client Key](https://app.warrant.dev) to
test this code through your own Warrant account.

For more information on how to use the Warrant API, please refer to the
[Warrant API reference](https://docs.warrant.dev).

## TypeScript support

This package includes TypeScript declarations for Warrant.

Note that we may release new [minor and patch](https://semver.org/) versions of
`qwik-warrant-js` with small but backwards-incompatible fixes to the type
declarations. These changes will not affect Warrant itself.

## Warrant Documentation

- [Warrant Docs](https://docs.warrant.dev/)