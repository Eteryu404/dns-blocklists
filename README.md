# dns-blocklists 🛡️

Moja osobista, automatycznie aktualizowana i zoptymalizowana lista blokad DNS.

Pipeline na **GitHub Actions** cyklicznie pobiera źródła, czyści reguły z niepotrzebnych nakładek, usuwa redundantne poddomeny i generuje czysty plik gotowy dla resolvera DNS.

---

## Jak to działa?

* **Agregacja:** Pobiera listy ze `sources.txt` z walidacją pobierania.
* **Sanityzacja:** Odrzuca komentarze, reguły uBlocka, IP (`0.0.0.0`) oraz niepoprawne domeny.
* **Wyjątki:** Przepuszcza domeny zdefiniowane w `allowlist.txt`.
* **Deduplikacja (Python):** Automatycznie usuwa subdomeny, jeśli blokowana jest cała domena nadrzędna (np. usuwa `sub.bad.com`, gdy istnieje `bad.com`).
* **Deploy:** Generuje zoptymalizowany plik i automatycznie commituje zmiany.

---

## Plik wyjściowy

Gotowa lista do wdrożenia na poziomie resolvera (np. Cloudflare Worker `doh-worker`, Pi-hole, AdGuard Home):

* **Plik w repo:** `output/doh_combined.txt`
* **Raw URL:** `https://raw.githubusercontent.com/realeteryu/dns-blocklists/refs/heads/main/output/doh_combined.txt`
