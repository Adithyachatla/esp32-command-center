# Security

JARVIS is a **hobby / educational project. Its access control is not production-grade.** Do not use it to guard anything
where a failure could cause harm, loss or safety risk (for example mains-powered equipment).

## Security model

```text
Laptop ──Wi-Fi (WPA2, password you choose)──▶ ESP32 SoftAP ──HTTP (no TLS)──▶ web server
```

**What is implemented (from the source code):**

- Credentials are verified **in the firmware** (`src/auth.cpp`); the browser never holds them. The password field is cleared on submit and nothing is kept in `localStorage`/`sessionStorage`.
- Constant-time comparison; username **and** password are always both evaluated.
- Session tokens: 128 bits from the hardware RNG (`esp_random()`), sent in an `HttpOnly`, `SameSite=Strict` cookie (`JARVIS_SID`).
- Sessions: RAM only, 30-minute idle timeout, at most 3 at once (least-recently-used is replaced).
- Per-IP lockout: 5 wrong tries → 60 s lock, doubling on repeats up to ×8.
- Every data/control route needs a valid session; POST routes additionally require `Origin` (when sent) to match `Host`.
- Hardware safety: only pins listed in `include/config.h` **and** on the safe-pin allow-list can be driven.
- The repository contains no credentials; `include/secrets.h` is git-ignored and `include/secrets.example.h` holds placeholders.

**Limitations (design limits, not hidden bugs):**

- **Plain HTTP.** Anyone able to capture the Wi-Fi traffic *and* who knows the access-point password could read the session cookie or the login. WPA2 on the access point is the real protection — choose a long, unique AP password.
- Credentials are **compiled into the firmware** (no hashing, no change-password screen). Anyone who can read the chip's flash can extract them.
- The login lockout is per IP; an attacker who changes IP can keep guessing slowly. Sessions are lost on reboot.
- The HTML/CSS/JavaScript are public to anyone on the network; only the data and controls are protected.
- Not hardened: no HTTPS, no CSRF tokens beyond `SameSite=Strict` and the `Origin` check, no audit log.
- The code has **not** had an independent security review, and the firmware has not been fully verified on hardware.

## Configure your own credentials safely

```bat
copy include\secrets.example.h include\secrets.h
```

1. Put your own SSID/passwords in `include/secrets.h` (AP password: 8–63 characters). Use long, unique values.
2. Never commit, post or screenshot `secrets.h`. Check `git status` before every push.
3. Re-flash the **firmware** after changing it (`pio run -t upload`).
4. Do not leave the template placeholders (`CHANGE-ME-…`) on a device you actually use.

## If you published a secret by mistake

`.gitignore` only affects *future* commits — a password already pushed stays in Git history and in forks/clones.

1. **Treat it as compromised.** Change the Wi-Fi and dashboard passwords in `secrets.h` and re-flash.
2. Remove it from history, e.g. with [`git filter-repo`](https://github.com/newren/git-filter-repo) (or recreate the repository), then force-push.
3. Remember that cached copies, forks and clones may still exist — rotating the secret is what actually protects you.

## Reporting a vulnerability

Please **do not** open a public issue with exploit details.

1. Use GitHub's private vulnerability reporting (repository **Security** tab → *Report a vulnerability*) if it is enabled, **or**
   contact the maintainer privately through the Instagram profile in the README
   ([@aditechsmith](https://www.instagram.com/aditechsmith?obrf=MXZlOWpub2k2M3RrbQ==)).
2. Include what you found, steps to reproduce, the firmware version and, if you have one, a suggested fix.
3. **Never include real credentials, tokens or personal network details** in a report.

Responses are best-effort; there is no guaranteed timeline and no bug bounty. Only the latest commit on the default branch is maintained.
