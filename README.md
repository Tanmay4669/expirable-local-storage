# Expirable Local Storage

`expirable-local-storage` is a lightweight utility for managing browser local storage with built-in support for expiration times. This package allows you to easily set, retrieve, and remove items from local storage, while also providing the capability to automatically clear expired items.

## Features

- **Set items with expiration:** Store items in local storage with an optional expiration time.
- **Retrieve items considering expiration:** Automatically checks if an item has expired before returning it.
- **Remove individual items:** Delete specific items from local storage.
- **Clear all items:** Clear all items from local storage.

## Installation

You can install this package using npm:

```bash
npm install expirable-local-storage
```

## Usage

### 1. Importing the module

First, import the functions from the `expirable-local-storage` module:

```javascript
import { setItem, getItem, removeItem, clear } from "expirable-local-storage";
```

### 2. Setting an Item

You can set an item in the local storage with an optional expiration time (in milliseconds). If no expiration time is provided, the item will not expire.

```javascript
setItem("keyName", "value", 60000); // The item will expire in 60 seconds (60000 ms)
```

### 3. Getting an Item

Retrieve an item from local storage. If the item has expired, it will return `null` and remove the item from local storage.

```javascript
const value = getItem("keyName");
if (value !== null) {
  console.log("Value:", value);
} else {
  console.log("The item has expired or does not exist.");
}
```

### 4. Removing an Item

Remove a specific item from local storage:

```javascript
removeItem("keyName");
```

### 5. Clearing All Items

Clear all items from local storage:

```javascript
clear();
```

## API

- ### **_setItem(key, value, expirationTime)_**

  - **key** (string): The name of the key you want to create/update.
  - **value** (any): The value you want to store. This will be serialized to a string using `JSON.stringify`.
  - **expirationTime** (number | null): Optional expiration time in milliseconds. If not provided or set to `null`, the item will not expire.

- ### **_getItem(key)_**

  - **key** (string): The name of the key you want to retrieve.
  - **returns** (any | null): The stored value, or `null` if the item has expired or does not exist.

- ### **_removeItem(key)_**

  - **key** (string): The name of the key you want to remove.

- ### **_clear()_**

  - **clear all** items from local storage.

## Example

```javascript
import { setItem, getItem, removeItem, clear } from "expirable-local-storage";

// Set an item with a 10-second expiration
setItem("username", "alex_doe", 10000);

// Retrieve the item (within 10 seconds)
console.log(getItem("username")); // Output: 'alex_doe'

// Wait for 10 seconds, then try to retrieve the item again
setTimeout(() => {
  console.log(getItem("username")); // Output: null
}, 10000);

// Remove an item
removeItem("username");

// Clear all items from local storage
clear();
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contribution

Feel free to contribute to this project by submitting issues or pull requests.

## Acknowledgements

This package is inspired by the need for a simple way to manage local storage with expiration handling in modern web applications.
