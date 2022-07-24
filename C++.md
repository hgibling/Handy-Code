```
size_t					// unsigned integer
const std::string&			// reference to a string that's constant
%c, %s. %zu				// character, string, size_t
std::map				// search tree/dictionary (key and value)
```

print string while iterating over a set:
```
for (auto iter = x.begin(); iter != x.end(); ++iter) {
        fprintf(stderr, "%s\n", iter->c_str());
}
// -> is shortcut for dereference and dot notation, i.e. (*iter).c_str()
```

in functions, parameters will almost always be const
& means pass by reference--instead of copying full object, just reference it. use for large items like strings, maps, sets. dont need for small things like integers or doubles

using gdb:
```
$ gdb --args /path/to/gbkc arg1 arg2 arg3
(gdb) run
```
