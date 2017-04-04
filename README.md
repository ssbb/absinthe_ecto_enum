# Ansible.EctoEnum

Provides some helper fucnions for [EctoEnum](https://github.com/gjaldon/ecto_enum)
integration with [Absinthe](https://github.com/absinthe-graphql/absinthe).

This function makes it easy to integrate enums defined with EctoEnum
with GraphQL API build with Absinthe.

## Installation

Add `absinthe_ecto_enum` to `mix.exs`:

```elixir
def deps do
  [{:absinthe_ecto_enum, "~> 0.1.0"}]
end
```

## Basic Usage

```elixir
import EctoEnum

defenum StatusEnum, :status, [:active, :pending, :failed]
```

```elixir
defmodule MyApp.Web.Schema.Enums do
  use Absinthe.EctoEnum

  ecto_enum StatusEnum
end
```

`ecto_enum` macro will produce this code:

```elixir
enum :status do
  value :active
  value :pending
  value :failed
end
```
