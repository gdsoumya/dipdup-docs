# Default hooks

There are special callbacks DipDup generates for all indexes; they fired on system-wide events and aren't linked to any index. Names of those hooks are reserved; you can't use them in config.

## `on_rollback`

It tells DipDip how to handle chain reorgs, a purely application-specific logic, especially if there are stateful entities. The default implementation does nothing if rollback size is one block and full reindexing otherwise.

See [5.3. Reindexing](../../advanced/reindexing.md) for details.

## `on_restart`

This hook executes right before starting indexing. It allows configuring DipDup in runtime based on data from external sources. Datasources are already initialized at the execution time and available at `ctx.datasources`. See [Handler context](../advanced/handler-context.md) for more details how to perform configuration.

## `on_reindex`

This hook fires after the database is re-initialized after reindexing (wipe).

Useful modify schema with arbitrary SQL. See [5.5. Executing SQL scripts](../sql.md) for details.

## `on_synchronized`

This hook fires when every active index reaches a realtime state.
