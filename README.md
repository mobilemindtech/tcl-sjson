# TCL Simple JSON

### Encode dict

```tcl
set data {
    id 1
    name {Ricardo Bocchi}
    age 37
    enabled true
    group {
        id 1
        description {Developer}
    }
    friends {
        {id 1 name jonh}
        {id 2 name jully}
        {id 3 name fred}
    }
}

set tpl {
    id int
    name str
    age str
    enabled bool
    group {
        dict {id int description str}
    }
    friends {
        list {id int name str}
    }
}

::sjson::encode $data -tpl $tpl
```
### Encode list

```tcl
set data {
    {
        id 1
        name {Ricardo Bocchi}
        age 37
        enabled true
        group {
            id 1
            description {Developer}
        }
        friends {
            {id 1 name jonh}
            {id 2 name jully}
            {id 3 name fred}
        }
    }
    {
        id 2
        name {Jones Manoel}
        age 26
        enabled true
        group {
            id 1
            description {Developer}
        }
        friends {
            {id 1 name jonh}
            {id 2 name jully}
            {id 3 name fred}
        }
    }
}

set tpl {
    id int
    name str
    age str
    enabled bool
    group {
        dict {id int description str}
    }
    friends {
        list {id int name str}
    }        
}

::sjson::encode-list $data -tpl $tpl
```

### Decode

```
::sjson::decode {{"x": 1}}
```