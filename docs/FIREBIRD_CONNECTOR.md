# Firebird Connector

The Firebird connector implements `SCHF\SDK\Connector\ConnectorInterface` in `src/Firebird/FirebirdConnector.php`.

## Config Keys

Required:

- `dbname`: Firebird database path or alias.
- `username`: Firebird user.
- `password`: Firebird password.

Optional:

- `host`: defaults to `localhost`.
- `port`: defaults to `3050`.
- `charset`: defaults to `UTF8`.

Example lab config:

```php
$connector->connect([
    'host' => 'firebird-lab',
    'port' => 3050,
    'dbname' => '/var/lib/firebird/data/lab_schf.fdb',
    'username' => 'schf_lab_user',
    'password' => 'schf_lab_password_change_me',
    'charset' => 'UTF8',
]);
```

The credentials above are fake local lab credentials only.

## Methods

- `connect(array $params): void`
- `disconnect(): void`
- `getDriverName(): string`
- `getSchema(): array`
- `query(string $sql, array $params = []): Iterator`
- `fetchAll(string $sql, array $params = []): array`

## Testing

Unit tests mock PDO and do not require a running Firebird server:

```bash
composer install
vendor/bin/phpunit --configuration phpunit.xml.dist
```

Use the `schf-migration` Firebird Lab compose override for real local integration checks.
