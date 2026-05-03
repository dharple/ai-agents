Random, possibly useful AI agents.

### Analyze 3rd Party Dependency Updates

`dependency-security-auditor.md` - Agent for reviewing 3rd party dependencies.
Tuned for PHP and NPM.  Initially created using Claude.

---

After installing the agent, use the following processes:

---

Process for composer:

1. Install the agent.
2. Copy `vendor` to `vendor-old`, e.g. `cp -a --reflink=auto vendor vendor-old`.
3. Run `composer update --no-install`.
4. Run `composer install --no-scripts --no-plugins`.
5. Run `claude --agent dependency-security-auditor`.
6. Tell the agent:

   I have made a backup copy of vendor in vendor-old, and I ran composer
   install without scripts or plugins.  Please review the changes between
   vendor-old and vendor, using composer.lock as a reference, and look for any
   potential security risks.

7. Review the agent's report.
8. If needed, review the changes yourself, e.g. `diff -rNwBb vendor-old vendor`.
9. Run `composer install`, to let any scripts and plugins run as needed.
10. Commit your changes.
