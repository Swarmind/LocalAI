# pkg/xsync/map.go  
## Package: xsync  
  
Imports:  
```  
"sync"  
```  
  
External data, input sources: None  
  
TODOs: None  
  
### SyncedMap  
  
This code defines a `SyncedMap` struct, which is a thread-safe wrapper around a standard Go map. It uses a `sync.RWMutex` to protect the underlying map from concurrent access.  
  
The `SyncedMap` struct has the following methods:  
  
- `NewSyncedMap()`: Creates a new `SyncedMap` instance.  
- `Map()`: Returns the underlying map.  
- `Get(key K)`: Returns the value associated with the given key.  
- `Keys()`: Returns a slice containing all the keys in the map.  
- `Values()`: Returns a slice containing all the values in the map.  
- `Len()`: Returns the number of key-value pairs in the map.  
- `Iterate(f func(key K, value V) bool)`: Iterates over the map, calling the given function for each key-value pair.  
- `Set(key K, value V)`: Sets the value associated with the given key.  
- `Delete(key K)`: Deletes the key-value pair associated with the given key.  
- `Exists(key K)`: Checks if a key exists in the map.  
  
This `SyncedMap` implementation provides a convenient way to use a map in a concurrent environment without worrying about data races or other synchronization issues.  
  
  
  
