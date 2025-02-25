
<div align="center">
    <img alt="GofeR logo" src="https://raw.githubusercontent.com/nasan016/gofer/main/res/logo.png">
</div>

![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)
# GofeR
A **Go** reactive library inspired by [Vue.js](https://vuejs.org/guide/extras/reactivity-in-depth.html).


## Install
use `go get` to install this package 

```shell
go get github.com/nasan016/gofer
```

## Getting Started
To start, define the GofeR package and import the library.

```go
package main

import(
    gf "github.com/nasan016/gofer"
)
```

## Usage
GofeR brings the following reactive primitives from Vue to Go:
* [ref](https://vuejs.org/api/reactivity-core.html#ref)
* [computed](https://vuejs.org/api/reactivity-core.html#computed)
* [watchEffect](https://vuejs.org/api/reactivity-core.html#watcheffect)

## Example

```go
package main

import (
    "fmt"
    gf "github.com/nasan016/gofer"
)

func main() {
    price := gf.Ref(2)
    quantity := gf.Ref(1000)

    revenue := gf.Computed(func() int {
        return price.GetValue() * quantity.GetValue()
    })

    gf.WatchEffect(func() {
        fmt.Println("revenue:", revenue.GetValue())
    })

    price.SetValue(price.GetValue() / 2)
    price.SetValue(price.GetValue() * 10)
    quantity.SetValue(quantity.GetValue() + 500)
}

```

**Output**

```shell
revenue: 2000
revenue: 1000
revenue: 10000
revenue: 15000
```
---
Checkout [Effekt](https://github.com/bendgk/effekt) by [bendgk](https://github.com/bendgk) :heart:
