# Sqlak

## Overview

The `sqlak` class is a simple PHP class designed to facilitate common MySQL database operations. It provides methods for executing SQL queries for tasks such as SELECT, INSERT, UPDATE, and DELETE, along with helper methods for fetching results and counting records.

## Installation

To use the `sqlak` class in your PHP project, include the class file and create an instance of the class. Ensure that the necessary MySQL extension is enabled in your PHP environment.

```php
<?php
require_once 'path/to/sqlak.php';

$config = [
    'host' => 'your_database_host',
    'user' => 'your_database_user',
    'pass' => 'your_database_password',
];

$dbName = 'your_database_name';
$options = [
    'port' => 3306,
    // Add more options if needed
];

$sqlak = new sqlak($config, $dbName, $options);
?>
```

## Class Methods

### `unique($len = 6): string`

Generates a random alphanumeric string of the specified length.

### `sqlize($value): string`

Escapes and sanitizes a string for safe use in SQL queries.

### `__construct($config, $db, $options = false)`

Class constructor for establishing a database connection. Takes an associative array `$config` containing database connection details, the database name `$db`, and optional `$options` for additional connection parameters.

### `db(): bool|mysqli`

Returns the established database connection.

### `do($query): mysqli_result|bool`

Executes a SQL query and returns the result set or `false` on failure.

### `set($table, $command, $where = false): bool|mysqli_result`

Updates records in the specified table based on the provided set of commands and optional WHERE clause.

### `sel($table, $col = false, $where = false): mysqli_result|bool`

Retrieves records from the specified table with optional column and WHERE clause.

### `fessoc($sel)`

Fetches a single row as an associative array from a result set.

### `sqlcount($sel)`

Returns the number of rows in a result set.

### `give($table, $where = false, $col = false): array`

Retrieves and returns an array of records from the specified table with optional WHERE clause and columns.

### `del($table, $where = false): mysqli_result|bool`

Deletes records from the specified table based on the optional WHERE clause.

### `put($table, $command): mysqli_result|bool`

Inserts a new record into the specified table based on the provided set of commands.

### `count($table, $where = false): int|string`

Returns the count of records in the specified table with an optional WHERE clause.

## Usage Examples

Here are some examples of how to use the `sqlak` class:

```php
<?php
// Example: Fetch records from 'users' table
$users = $sqlak->give('users', 'age > 18', 'id, name');

// Example: Insert a new user into 'users' table
$newUser = ['name' => 'John Doe', 'age' => 25, 'email' => 'john@example.com'];
$sqlak->put('users', $newUser);
?>
```

Feel free to explore and use the various methods provided by the `sqlak` class in your PHP projects.
