# GraphQL Examples

https://countries.trevorblades.com/

#Simple
```
{
  continents {
    code
    name
    countries {
      name
    }
  }
}
```

#Parameters
```
{
  continent(code: "AF") {
    code
    name
    countries {
      name
    }
  }
}
```

#Aliases
```
{
  africa: continent(code: "AF") {
    code
    name
    countries {
      name
    }
  }
}
```

#Aliases Complex
```
{
  africa: continent(code: "AF") {
    countries {
      name
    }
  },
  antarctica: continent(code: "AN") {
    countries {
      name
    }
  },
  asia: continent(code: "AS") {
    countries {
      name
    }
  }
}
```

#Explicitly Name Query 
```
query ContinentsStartingWithA {
  africa: continent(code: "AF") {
    countries {
      name
    }
  }
  antarctica: continent(code: "AN") {
    countries {
      name
    }
  }
  asia: continent(code: "AS") {
    countries {
      name
    }
  }
}
```

#Named Operation 
```
query ContinentsStartingWithA {
  africa: continent(code: "AF") {
    countries {
      name
    }
  }
  antarctica: continent(code: "AN") {
    countries {
      name
    }
  }
  asia: continent(code: "AS") {
    countries {
      name
    }
  }
}
```

#Named Operation with variables. 
Cleaner and easier to hand off to someone else since the don't have to modify the query, just the variables
```
query ContinentWithCode($continentCode: String){
  africa: continent(code: $continentCode) {
    code
    name
    countries {
      name
    }
  }
}
```

variables
```
{
  "continentCode": "AS"
}
```

#Fancy variables
```
query ContinentWithCode($continentCode: String!, $includeCountries: Boolean!){
  africa: continent(code: $continentCode) {
    code
    name
    countries @include(if: $includeCountries){
      name
    }
  }
}
```

variables
```
{
  "continentCode": "AS",
  "includeCountries": true
}
```
