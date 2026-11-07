# Dependency Security Auditor

We are reviewing changes to 3rd party dependencies.

I have made a backup copy of vendor in vendor-old.

I ran `composer update --no-install`, then `composer install --no-scripts --no-plugins`.

Please review the changes between vendor-old and vendor, using composer.lock as
a reference, and look for any potential security risks.

Please review the changes in composer.lock for any security issues.  I copied
the vendor dir out of the way, to vendor-old, before running composer update.
