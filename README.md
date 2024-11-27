# TCL Simple JSON

### Doc


* `encode dict {dict args}` - Encode dict or value. Use `-tpl` to set template
* `encode list {list args}` - Encode list. Use `-tpl` to set template
* `encode value {value args}` - Encode value. Use `-type` to set type
* `decode {string}` - Decode dict or list

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

::sjson::encode dict $data -tpl $tpl
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

::sjson::encode list $data -tpl $tpl
```

### Encode value

````tcl
::sjson::encode value 1 == 1
::sjson::encode value "1" -type string == {"1"}
::sjson::encode value str == {"str"}
::sjson::encode value true == true
::sjson::encode value "true" -type string == {"true"}
```

### Decode

```
::sjson::decode {{"x": 1}} == {x 1}
::sjson::decode {[{"x": 1},{"y": 2}]} == [list {x 1} {y 2}]
```
