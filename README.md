# replit-database-oak
Replit Database for Oak (Oaklang.org).
## Oaklang Replit Database Client Documentation

### Introduction
This Oaklang code provides a client for interacting with the Replit Database. It allows you to read, write, delete, and list keys in the Replit Database from an Oaklang environment.

### Usage
To use the Replit Database client, you can follow the steps below:

1. Import Required Modules:
   - `fs`: File system module.
   - `std`: Standard library module.
   - `str`: String manipulation module.
   - `json`: JSON parsing and serialization module.
   - `http`: HTTP module.

2. Initialize the Replit Database Client:
   - Call `DBClient()` to create an instance of the database client. It will automatically fetch the Replit Database URL using the `getKey()` function.

3. Perform Database Operations:
   - You can use the following functions provided by the client:

#### `get(path, options)`
   - Retrieve a value from the Replit Database.
   - Parameters:
     - `path`: The path to the key.
     - `options`: Optional options object (e.g., `{ raw: true }` to get the raw value).
   - Returns the retrieved value.

#### `set(key, value)`
   - Set a key-value pair in the Replit Database.
   - Parameters:
     - `key`: The key to set.
     - `value`: The value to set for the key.
   - Returns the response from the database.

#### `delete(key)`
   - Delete a key from the Replit Database.
   - Parameters:
     - `key`: The key to delete.
   - No return value.

#### `list(prefix)`
   - List keys in the Replit Database with a specified prefix.
   - Parameters:
     - `prefix`: The optional prefix to filter keys.
   - Returns an array of keys.

#### `empty()`
   - Clear the entire database by deleting all keys.
   - No parameters or return value.

### Important Notes
- The Replit Database client handles fetching the Replit Database URL and performing API requests.
- Make sure to follow Replit's guidance on refreshing tokens every hour.

### Example Usage
```oak
r := import('spclib/replit/replit')

repl := r.DBClient()

res1 := repl.set('account', 'yeah') |>
	string()

print(res1 << '\n')

res2 := repl.get('account') |>
	string()

print(res2 << '\n')

repl.delete('account') |> string() |> print()

print(stat('main.oak'))
```

### Environment Variables
The `init()` function extracts and provides access to various environment variables related to your Replit environment, including cluster, owner, image, and more.

### Global Variable
- `replitDBFilename`: The path to the Replit Database file, which is '/tmp/replitdb' by default.

### Return Values
- The `DBClient` function returns an object with methods for interacting with the Replit Database.
- Most functions return values or responses from database operations.
