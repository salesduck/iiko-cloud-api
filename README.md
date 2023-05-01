# iiko-cloud-api
The library describes the available methods, request and response bodies,<br> which allows you to make your own rest client based on it

> All types were generated automatically based on the [iiko open api schema](https://api-ru.iiko.services/api/1) using [generator](https://www.npmjs.com/package/openapi-typescript)

## Setup

Add package to your typescript package
```
yarn add @salesduck/iiko-cloud-api
```

## Usage

### With openapi-fetch

```ts
import createClient from "openapi-fetch";

import { paths } from "@salesduck/iiko-cloud-api";

const { get, post, put, patch, del } = createClient<paths>({
  baseUrl: "https://myserver.com/api/v1/",
  headers: {
    Authorization: `Bearer token`,
  },
});
```

### Directly

1. Import schemas and paths
```ts
import { paths, schemas } from "@salesduck/iiko-cloud-api";
```
 2. Define alias for types
```ts
 export type getRegionsIikoParameters = paths["/api/1/regions"]["post"]["parameters"];

export type getRegionsIikoBody = schemas["iikoTransport.PublicApi.Contracts.Address.RegionsRequest"];

export type getRegionsIikoResponse = schemas["iikoTransport.PublicApi.Contracts.Address.RegionsResponse"];
 ```


3. Use types in your code
```ts
const getRegionsIiko = async (
  parameters: getRegionsIikoParameters,
  data: getRegionsIikoBody
): Promise<getRegionsIikoResponse> => {
 // ... your code
};
```

 Run your code with type safety
```ts
getRegionsIiko({ header: { Authorization: "token" } }, { organizationIds: [] })
  .then((response) => {
    console.log(response.regions);
    console.log(response.correlationId);
  })
  .catch(console.error);
```
