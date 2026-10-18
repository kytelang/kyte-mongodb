# kyte-mongodb

MongoDB driver for Kyte (OP_MSG, BSON, SCRAM). A Kyte package - fetch with:

```sh
kyte get https://github.com/kytelang/kyte-mongodb
```

```kyte
import mongodb;
```

## Design

Split by responsibility; consumers only touch the driver interface (`MongoDriver` / `MongoConnection`).

| Module     | Responsibility                                                                                      |
| ---------- | --------------------------------------------------------------------------------------------------- |
| `mongodb`  | Driver interface: `MongoConnection impl Connection` + `MongoDriver impl Driver` + connect/handshake/SCRAM auth. |
| `codec`    | OP_MSG wire codec (`encodeOpMsg`, `decodeOpMsg`, `frameLength`).                                    |
| `commands` | BSON command builders (hello/insert/find/saslStart/saslContinue) + `commandError`.                  |
