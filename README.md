# GraphQL Examples

https://countries.trevorblades.com/

## Simple 
https://graphql.org/learn/queries/#fields
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

## Arguments 
https://graphql.org/learn/queries/#arguments
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

## Aliases 
https://graphql.org/learn/queries/#aliases
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

## Aliases Complex 
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

## Operation Name 
https://graphql.org/learn/queries/#operation-name
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

## Variables 
https://graphql.org/learn/queries/#variables
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

## Directives 
https://graphql.org/learn/queries/#directives
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
