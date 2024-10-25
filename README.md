# php-dbml-core

> [!WARNING]
> Caution: This package is a WIP and is not intended for usage yet.

`php-dbml-core` is a PHP library designed to parse, convert, and manage different database formats. It provides essential functionality for handling DBML (Database Markup Language) and SQL, allowing developers to seamlessly transition between these formats.

## Features

- **Parse DBML and SQL**: Convert DBML or SQL files into a `Database` object for easier manipulation.
- **Export SQL and DBML**: Generate SQL and DBML files from a `Database` object.
- **Convert Formats**: Easily convert between DBML and SQL, both ways.
- **Generate DBML**: Create DBML from a `DatabaseSchema` object for clear, readable documentation.

## Installation

You can install the package via Composer:

```bash
composer require mysticseagull/php-dbml-core --dev --with-all-dependencies
```

## Usage

### Parse DBML or SQL

To parse a DBML or SQL string into a `Database` object:

```php
use MysticSeagull\PhpDbmlCore\Parser;

$dbml = """
Table users {
  id int [pk]
  name varchar
}
""";

$database = Parser::fromDBML($dbml);
```

Similarly, for SQL:

```php
$sql = """
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(255)
);
""";

$database = Parser::fromSQL($sql);
```

### Export SQL or DBML

You can export your `Database` object to DBML or SQL:

```php
use MysticSeagull\PhpDbmlCore\Exporter;

// Export to DBML
$dbmlOutput = Exporter::toDBML($database);

// Export to SQL
$sqlOutput = Exporter::toSQL($database);
```

### Convert Between DBML and SQL

To convert directly between DBML and SQL:

```php
use MysticSeagull\PhpDbmlCore\Converter;

// DBML to SQL
$sql = Converter::dbmlToSql($dbml);

// SQL to DBML
$dbml = Converter::sqlToDbml($sql);
```

### Generate DBML from DatabaseSchema

To generate DBML from a `DatabaseSchema` object:

```php
use MysticSeagull\PhpDbmlCore\Generator;

$databaseSchema = new MysticSeagull\PhpDbmlCore\DatabaseSchema();
// Define your database schema here

$dbml = Generator::fromDatabaseSchema($databaseSchema);
```

## Requirements

- PHP 8.0 or higher
- Composer

## Contributing

Contributions are welcome! Please submit a pull request or create an issue to get started.

## License

This package is open-sourced software licensed under the [MIT license](LICENSE).

## Contact

For any inquiries, please contact [justinborzi@gmail.com](mailto:justinborzi@gmail.com).
