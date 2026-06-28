# SCHF Connectors

Universal database connectors for the SCHF Migration Framework.

Each connector implements `SCHF\SDK\Connector\ConnectorInterface` (defined in `schf-sdk`).

## Supported databases

| Connector       | Status      |
|-----------------|-------------|
| Firebird        | Implemented |
| MySQL           | Planned     |
| PostgreSQL      | Planned     |
| SQL Server      | Planned     |
| Oracle          | Planned     |
| SQLite          | Planned     |

## Usage

```php
use SCHF\Connectors\Firebird\FirebirdConnector;

$connector = new FirebirdConnector();
$connector->connect([
    'host'     => 'localhost',
    'port'     => 3050,
    'dbname'   => '/path/to/database.fdb',
    'username' => 'db_user',
    'password' => 'db_password',
]);

$schema = $connector->getSchema();

foreach ($connector->query('SELECT * FROM SOME_TABLE') as $row) {
    // process row
}

$connector->disconnect();
```

## Development

```bash
composer install
```
