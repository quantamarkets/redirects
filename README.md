# Domain Redirection

Simple Caddy app to send a 301 redirect to the domain set in the `REDIRECT_TO` service variable.

The URI of the incoming request is preserved upon redirection, for example:

```
REDIRECT_TO = www.domain.com

https://domain.com/page/num/1?limit=5 -> https://www.domain.com/page/num/1?limit=5
```
```
REDIRECT_TO = www.domain.com/api

https://domain.com/page/num/1?limit=5 -> https://www.domain.com/api/page/num/1?limit=5
```

**To disable URI preservation remove `{uri}` from the `redir` directive in the Caddyfile** 

Accepted `REDIRECT_TO` variable formats:

- railway.app
- docs.railway.app
- docs.railway.app/develop/variables

The `REDIRECT_TO` variable value must not include:
- any schema `http, https, etc`
- a query string `?hello=world`
- a fragment `#important-text-block`

**Note: If URI preservation is disabled you may specify your own query and or fragment in the redir directive**

Relevant Caddy documentation:

- [The Caddyfile](https://caddyserver.com/docs/caddyfile)
- [Caddyfile Directives](https://caddyserver.com/docs/caddyfile/directives)
- [redir](https://caddyserver.com/docs/caddyfile/directives/redir)
