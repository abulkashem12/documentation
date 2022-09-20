---
title: WP-CLI on the Pantheon Platform
subtitle: SQL Queries, PHP Code, and Subcommands with WP-CLI
description: Learn how to run SQL queries, PHP code, and subcommands on WP-CLI.
cms: "WordPress"
categories: [develop]
tags: [wp-cli, cli]
layout: guide
showtoc: true
permalink: docs/guides/wp-cli/wp-cli-sql-php-subcommands
anchorid: wp-cli-sql-php-subcommands
---

This section provides information on how to run SQL queries, PHP code, and subcommands on WP-CLI.

## Run SQL Queries Using WP-CLI on Pantheon

Use `echo` to pipe (or _redirect_) a SQL query through WP-CLI via [Terminus](/terminus):

```bash{promptUser: user}
echo "SELECT * FROM wp_users WHERE ID=1;" | terminus wp $site.$env -- db query
```

## Execute PHP Code Using WP-CLI on Pantheon

The [`wp eval`](https://developer.wordpress.org/cli/commands/eval/) command is not supported on Pantheon, but you can still run the interactive shell [`wp shell`](https://developer.wordpress.org/cli/commands/shell/) to execute PHP commands:

```bash
terminus wp $site.$env -- shell
var_dump($_ENV);
```

## Extending WP-CLI With Subcommands

WP-CLI has a framework for users to write their own commands. Learn about the [anatomy of a subcommand](https://make.wordpress.org/cli/handbook/commands-cookbook/#anatomy-of-a-command) to solve your thorny problems with WP-CLI.

Keep in mind that WP-CLI commands are subject to platform PHP memory limits, which are optimized for serving webpages and not necessarily running development tools. Commands that utilize Composer, such as `wp package install`, are generally best run on your local machine or on a CI service.