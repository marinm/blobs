# Blobs

CRUD endpoint for large binary objects

```
Index   GET    /blobs
Create  POST   /blobs
Read    GET    /blobs/:id
Update  PUT    /blobs/:id
Delete  DELETE /blobs/:id
```

List all blobs:

```
curl http://localhost:3000/blobs
```

The response will be something like:

```json
[
  {
    "id": "221e0386-eef1-4874-b953-eb0492e194f3	",
    "size": 70829
  },
  {
    "id": "33b339c6-1aa8-4b52-8e23-0980994bf764",
    "size": 31412
  },
  {
    "id": "89151edd-1a57-4cc1-989a-58b331d4aef4",
    "size": 187016
  }
]
```

Create a blob:

```
curl -X POST http://localhost:3000/blobs --data-binary 'hello world';
```

The response will be something like:

```
{"id":"1d72ac22-480d-4ef8-8adf-1cd483d893c1"}
```

Read a blob:

```
curl http://localhost:3000/blobs/:id
```

Update a blob:

```
curl -X PUT http://localhost:3000/blobs/:id --data-binary 'hello world updated';
```

Delete a blob:

```
curl -X DELETE http://localhost:3000/blobs/:id
```

## Example usage

```js
import express from "express";
import cors from "cors";
import { createBlobsRouter } from "@marinm/express-blobs";

express()
  .use(cors())
  .use(createBlobsRouter("./blobs", "10mb"))
  .listen(3001, () => console.log("Listening..."));
```
