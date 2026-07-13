# myguard labs

Security-focused infrastructure software: hardened nginx/Angie modules, a
mail-filtering stack in Go, and OWASP CRS hardening plugins — everything
packaged and served as ready-to-install Debian/Ubuntu packages at
**[deb.myguard.nl](https://deb.myguard.nl)**.

## Package repository — [deb.myguard.nl](https://deb.myguard.nl)

Our APT repository ships [nginx](https://deb.myguard.nl/nginx-modules/) and
[Angie](https://deb.myguard.nl/angie-modules-optimized-extended/) builds with
HTTP/3, compile-time hardening, and a large set of dynamic modules, plus
supporting packages (rspamd, dovecot, clamav, libmodsecurity, lua-resty, and
more) for Debian and Ubuntu on amd64 + arm64. Install instructions, the full
package index, and in-depth articles live on the site. Full directive
reference for every module: [modules synopsis](https://deb.myguard.nl/nginx/modules-synopsis/).
Bugs and requests go to the
[deb.myguard.nl issue tracker](https://github.com/myguard-labs/deb.myguard.nl).

## nginx / Angie modules

Dynamic modules, all shipped pre-built in the APT repo:

- [nginx-cache-turbo-module](https://github.com/myguard-labs/nginx-cache-turbo-module) — edge page cache: shared-memory cache, stale-while-revalidate, probabilistic single-flight refresh
- [nginx-strip-filter-module](https://github.com/myguard-labs/nginx-strip-filter-module) — smart HTML/CSS/JS/JSON response-body minifier
- [nginx-error-abuse-module](https://github.com/myguard-labs/nginx-error-abuse-module) — rate-limits clients that hammer your site with 404s
- [nginx-autocert-module](https://github.com/myguard-labs/nginx-autocert-module) — automatic certificates via the ACME protocol
- [nginx-zstd-module](https://github.com/myguard-labs/nginx-zstd-module) — Zstandard compression, fixed and maintained
- [nginx-http-shield-module](https://github.com/myguard-labs/nginx-http-shield-module) — *upcoming*: legacy-exploit floor, ~400 compiled-in signatures (Log4Shell, Shellshock, SQLi, traversal, RCE chains, SSRF) in one Aho-Corasick pass, ~1 µs/request. Not a WAF — ModSecurity/Coraza + CRS stay the front line; this is the last line of defense for hosters who don't control what their customers install
- [nginx-http-sentinel-module](https://github.com/myguard-labs/nginx-http-sentinel-module) — *experimental*: client reputation + JA4+ fingerprinting + AI-scraper tarpit

## Mail security stack

Out-of-process attachment analysis and hash-clearinghouse clients, built for
busy rspamd/SpamAssassin pipelines:

- [mailstrix](https://github.com/myguard-labs/mailstrix) — the owl that finds malware hiding in your mail: recursively unwraps OLE2/OOXML, VBA, RTF, PDF, and nested archives until YARA rules can see the dangerous bits
- [gozer](https://github.com/myguard-labs/gozer) — standalone Go binary bundling DCC/Razor/Pyzor with an HTTP backend
- [gazor](https://github.com/myguard-labs/gazor) / [gyzor](https://github.com/myguard-labs/gyzor) / [gdcc](https://github.com/myguard-labs/gdcc) — pure-Go clients for Razor 2, Pyzor, and DCC — each a library, CLI, and daemon
- [rspamd-dcc-razor-pyzor](https://github.com/myguard-labs/rspamd-dcc-razor-pyzor) — rspamd plugin + Docker image wiring the Go clients in, with optional Redis caching
- [rspamd-olefy](https://github.com/myguard-labs/rspamd-olefy) — front-end wrapping oletools VBA-macro scanning for rspamd
- [rspamd-kam-rules](https://github.com/myguard-labs/rspamd-kam-rules) — SpamAssassin KAM rules transpiled to rspamd

## OWASP CRS / ModSecurity plugins

False-positive exclusions plus opt-in positive-security allowlists for apps
behind [OWASP CRS](https://coreruleset.org/) 4.x:

- [wordpress-hardening-plugin](https://github.com/myguard-labs/wordpress-hardening-plugin) — harden WordPress behind CRS
- [vimbadmin-crs-plugin](https://github.com/myguard-labs/vimbadmin-crs-plugin) — CRS plugin for ViMbAdmin
- [vaultwarden-crs-plugin](https://github.com/myguard-labs/vaultwarden-crs-plugin) — CRS plugin for Vaultwarden (Bitwarden), JSON-API aware

## Also here

- [ViMbAdmin](https://github.com/myguard-labs/ViMbAdmin) — modernised 2026 fork of the virtual mailbox admin panel
- [dockerized](https://github.com/myguard-labs/dockerized) — the Docker stacks we run in production; images on [Docker Hub](https://hub.docker.com/u/eilandert)
- [build_psol](https://github.com/myguard-labs/build_psol) — build scripts for the PageSpeed Optimization Library (PSOL) (archived)

## Links

- APT repo + blog: [deb.myguard.nl](https://deb.myguard.nl)
- nginx stack + modules: [deb.myguard.nl/nginx-modules](https://deb.myguard.nl/nginx-modules/)
- Angie stack + modules: [deb.myguard.nl/angie-modules-optimized-extended](https://deb.myguard.nl/angie-modules-optimized-extended/)
- Module directive reference: [deb.myguard.nl/nginx/modules-synopsis](https://deb.myguard.nl/nginx/modules-synopsis/)
- Package issues: [myguard-labs/deb.myguard.nl](https://github.com/myguard-labs/deb.myguard.nl)
- Docker Hub: [hub.docker.com/u/eilandert](https://hub.docker.com/u/eilandert)
- Find us on Discord: [deb.myguard.nl/contact](https://deb.myguard.nl/contact/)
