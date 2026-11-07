Random, possibly useful AI agents.

### Analyze 3rd Party Dependency Updates

`dependency-security-auditor.md` - Agent for reviewing 3rd party dependencies.
Tuned for PHP and NPM.  Initially created using Claude.

---

Install the agent:

1. Symlink the markdown file to `~/.claude/agents/`.
2. Consider adding `diff` and `find` to allowedTools in `~/.claude/settings.json`.

---

Process for composer:

1. Install the agent.
2. Copy `vendor` to `vendor-old`, e.g. `cp -a --reflink=auto vendor vendor-old`.
3. Run `composer update --no-install`.
4. Run `composer install --no-scripts --no-plugins`.
5. Run `claude --agent dependency-security-auditor`.
6. Give the agent the Composer prompt from [`prompts.md`](prompts.md), filling
   in any notes from previous runs.
7. Review the agent's report.
8. If needed, review the changes yourself, e.g. `diff -rNwBb vendor-old vendor`.
9. Run `composer install`, to let any scripts and plugins run as needed.
10. Commit your changes.
11. Clean up `vendor-old`.

---

Process for npm:

1. Install the agent.
2. Copy `node_modules` to `node_modules-old`, e.g.
   `cp -a --reflink=auto node_modules node_modules-old`.
3. Run `npm update --package-lock-only`.
4. Run `npm ci --ignore-scripts`.
5. Run `claude --agent dependency-security-auditor`.
6. Give the agent the npm prompt from [`prompts.md`](prompts.md), filling in
   any notes from previous runs.
7. Review the agent's report.
8. If needed, review the changes yourself, e.g.
   `diff -rNwBb node_modules-old node_modules`.
9. Run `npm rebuild`, to let any install scripts run as needed.
10. Commit your changes.
11. Clean up `node_modules-old`.

### Analyze Security Findings

`security-auditor.md` - Agent for reviewing the code itself.  Tuned for PHP,
JavaScript, Bash, and C.  Initially created using Claude.

---

Install the agent:

1. Symlink the markdown file to `~/.claude/agents/`.
