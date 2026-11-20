# http

[![CI](https://github.com/nabi-lang/http/actions/workflows/ci.yml/badge.svg)](https://github.com/nabi-lang/http/actions/workflows/ci.yml) [![packages.nabi-lang.org](https://img.shields.io/github/v/tag/nabi-lang/http?label=packages.nabi-lang.org&sort=semver)](https://packages.nabi-lang.org/packages/http) [![License: MIT OR Apache-2.0](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue)](#license)

HTTP/1.1 and HTTP/2 for Nabi: a message model, a pooling client and an async
server, over plaintext or TLS 1.3. Built on `std::net` with no other
dependencies. Parsing is strict where leniency would allow request smuggling or
response splitting.

## Add it

```sh
nabi add http
```

Needs Nabi 0.1 or later.

Features `http1`, `http2` and `tls` are on by default; turn off what you do not
need with `default_features: false`.

## Usage

```nabi,norun
// One-off request with a default client.
async fn main() throws {
    let r = try await http::get("http://example.com/");
    println(f"{r.status} {r.headers.get("content-type") ?? "-"}");
    println(try await r.body.text());
}
```

The server is router-free: one `async fn(Request) -> Response` handler, served
with `http::serve` / `http::serve_tls`. See the API docs for the client, server
and TLS details.

## Docs

https://packages.nabi-lang.org/packages/http/latest/docs

## License

Licensed under either of [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE), at
your option.
