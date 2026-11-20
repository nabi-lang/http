# Changelog

All notable changes to this package. Versions follow semver, independent of the Nabi toolchain.

## 0.1.0 (unreleased)

First release.

- HTTP/1.1 (RFC 9110 / 9112) and HTTP/2 (RFC 9113, HPACK RFC 7541), over
  plaintext or TLS 1.3, on `std::net` with no other dependencies.
- Message model: `Request`, `Response`, `Method`, `StatusCode`, `HeaderMap`,
  `Body`, `Uri` with percent and form encoding, cookies (`SetCookie`).
- `Client` with connection pooling, and `get` for one request.
- Async `Server`: one `async fn(Request) -> Response` handler, through
  `serve` / `serve_tls`.
- Strict parsing where leniency would allow request smuggling or response
  splitting.
- Features `http1`, `http2` and `tls`, all on by default.
- Needs Nabi 0.1 or later.
