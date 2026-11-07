# Dependency Security Auditor — Composer

I'm reviewing updates to 3rd party PHP dependencies. Before updating, I copied
`vendor` to `vendor-old`. I then ran `composer update --no-install` followed by
`composer install --no-scripts --no-plugins`, so no package scripts or plugins
have executed yet.

Please:

1. Use `git diff composer.lock` to identify added, removed, and updated packages.
2. Review the changes between `vendor-old` and `vendor` for those packages.
   Treat newly added packages (including new transitive dependencies) with
   extra scrutiny.
3. Check any `scripts` or `plugin` entries in the updated packages'
   composer.json, since they will run when I do a normal `composer install`.

Report one line per changed package (old → new version, verdict:
safe / needs review / do not install), followed by details for anything that
isn't "safe".

Notes from previous runs:
[INSERT NOTES OR DELETE THIS SECTION]

# Dependency Security Auditor — npm

I'm reviewing updates to 3rd party npm dependencies. Before updating, I copied
`node_modules` to `node_modules-old`. I then ran
`npm update --package-lock-only` followed by `npm ci --ignore-scripts`, so no
package lifecycle scripts have executed yet.

Please:

1. Use `git diff package-lock.json` to identify added, removed, and updated
   packages.
2. Review the changes between `node_modules-old` and `node_modules` for those
   packages. Treat newly added packages (including new transitive
   dependencies) with extra scrutiny.
3. Check the `preinstall`, `install`, `postinstall`, and `prepare` scripts in
   the updated packages' package.json, since they will run when I do a normal
   install or `npm rebuild`. Also check any new or changed `bin` entries, since
   those get linked into `node_modules/.bin` and can shadow commands used by
   my own npm scripts.

Report one line per changed package (old → new version, verdict:
safe / needs review / do not install), followed by details for anything that
isn't "safe".

Notes from previous runs:
[INSERT NOTES OR DELETE THIS SECTION]
