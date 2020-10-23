# zpages

Standard z-page health check methods to be imported as needed.

## Usage

- Configure Health Check drivers for each dependency
- Register drivers with healthz
- Register HTTP handlers
- Start application server

## HTTP Handlers

By default, `HTTPHandlers` will add the following routes to your HTTP handler.

`/healthz`: Basic healthy check	

`/readyz`: Readiness check for start up dependencies

`/livez`: Liveness check for continual checking for uptime

`/statusz`: Application status object which returns the output of a first class function which returns `map[string]interface{}`. See language-specific package for configuration example.

If you need to cusomize the endpoints or use a custom `http` library, the health check methods can be imported directly.

## Supported Drivers

See [docs/drivers.md](docs/drivers.md) for supported drivers and configurations.

## Supported Languages

- Golang
- NodeJS

### API Parity

There is full API parity across supported languages.

API Parity must be guaranteed in any feature addition / change to one language package.

Each package exports a a language-specific standard library `HTTPHandlers` method.

API parity diverges to support popular HTTP frameworks for each language.

For example, `go-zpages` exports `HTTPHandlersMux` for `gorilla/mux`, and `node-zpages` exports `HTTPHandlersKoa` for `koa` framework.
