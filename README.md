# typeorm-naming-strategy-rails

Rails-like naming strategy for [TypeORM](https://github.com/typeorm/typeorm).

This package overrides TypeORM’s default naming strategy, giving you pluralized table names and snake-case column names, i.e. `users` and `email_address` instead of `user` and `emailAddress`.

Using this naming strategy with a database system such as PostgreSQL prevents you from having to put many of your column names in quotes when writing queries: `SELECT ip_address, last_seen_at` compared to `SELECT "ipAddress", "lastSeenAt"`.

## Installation

After installing TypeORM, then

    npm i typeorm-naming-strategy-rails

or

    yarn add typeorm-naming-strategy-rails

## Usage

In your `ormconfig.js`:

    const namingStrategy = require('typeorm-naming-strategy-rails')

    module.exports = {
        // …

        namingStrategy,
    }

## Known issues

- Not yet complete; only transforms table names, column names, join column names, and join table column names for now. More methods from the default naming strategy will be overridden in the future.
- Table names are pluralized naïvely, simply appending an ‘s’. You can manually name your entity, e.g. `@Entity({ name: 'cities' })`, as a workaround.
- Lodash dependency should be removed.
