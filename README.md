# carpenter 🔨

[![Package Version](https://img.shields.io/hexpm/v/carpenter)](https://hex.pm/packages/carpenter)
[![Hex Docs](https://img.shields.io/badge/hex-docs-ffaff3)](https://hexdocs.pm/carpenter/)

Bindings for Erlang's [ETS tables](https://www.erlang.org/doc/man/ets.html). Forked and updated from [gts](https://github.com/Lunarmagpie/gts). 

If you aren't familiar with ETS tables, [this](https://elixirschool.com/en/lessons/storage/ets) is a good introduction.


## Quick start

```gleam
import gleam/io
import carpenter/table

pub fn main() {
  // Set up and configure an ETS table
  let example: table.Set(String, String) =
    table.build("table_name")
    |> table.set
    |> table.privacy(table.Private)
    |> table.write_concurrency(table.AutoWriteConcurrency)
    |> table.read_concurrency(True)
    |> table.decentralized_counters(True)
    |> table.compression(False)

  // Insert a value
  example
  |> table.insert("hello", "world")

  // Retrieve a key-value tuple
  example
  |> table.lookup("hello")
  |> set.debug

  // Delete an object
  example
  |> table.delete("hello")

  // Delete a table
  example
  |> table.drop
}
```

## Installation

This package is available on hex:

```sh
gleam add carpenter
```

Its documentation can be found at <https://hexdocs.pm/carpenter>.
