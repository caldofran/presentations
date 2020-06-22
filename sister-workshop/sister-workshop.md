# Sister workshop

![](mordor.gif)

---

# Sister

- BFF
- Playground for mobile
- Create endpoints, schemas and send fake data... or even more
- Let backend developers focus on important staff

---

# Why this workshop?

---

# No mobile dev is actually doing so

### (Well, only few of them)

---

## Because the language?

## Because the framework?

## Because just backend fear?

---

# Why me?

---

![](boromir.gif)

---

# It's not that bad

### It's actually easy

---

## ~~Because the language?~~

## ~~Because the framework?~~

## ~~Because just backend fear?~~

---

# Agenda

- Setup
- IDEs
- Create endpoint
- Test and run
- Create documentation

---

# Setup

[Sister readme](https://github.com/jobandtalent/sister)

---

# IDEs

- VSCode + [ElixirLS](https://marketplace.visualstudio.com/items?itemName=JakeBecker.elixir-ls)
- Rubymine + [Elixir plugin](https://plugins.jetbrains.com/plugin/7522-elixir)
- Whatever you feel comfortable with

---

# Let's code

---

# Create endpoint

- Router
- Controller
- View

---

## Router

- `sister_web/router.ex`
- Scopes

```elixir
scope "/v3/worker", SisterWeb do
end
```

- Resource

```elixir
 resources("/workers", Workers.WorkerController, only: [:index, :show])
```

- `mix phx.routes`

---

## Controller

- `Router` -> `WorkerController`
- Gather data and perform tasks before rendering
- Action

```elixir
@spec index(Plug.Conn.t(), any) :: Plug.Conn.t()
def index(conn, params)
```

- conn: Bunch of request data
- params: Request parameters

---

## Views

- `WorkerController` -> `WorkerView`
- Render data: `html/json`
- By default Phoenix will look for a view with the same name as the controller:
  - `SisterWeb.Workers.WorkerController`
  - `SisterWeb.Workers.WorkerView`
- Render Errors: `SisterWeb.ErrorView`

---

# Test and run

- Locally
- Staging
- Tests
- Kitt

---

## Locally

![](4-5897563204959078055-unscreen \(1\).gif)

- **Devkit/Devcloud**
- **No easier way**

---

## Staging

![](curling.gif)

---

## Testing (preferred way)

![140%](https://media.giphy.com/media/3orieKKmYyvUdR3RkY/giphy.gif)

- **`mix test`**

- **`valid-one`**

```elixir
get(conn, Routes.worker_path(conn, :index, auth_token: "valid-one"))
```

---

## Kitt

![](hackerman.gif)

**`kitt -e s console ecs ecs-shell sister-http:latest sh`**

---

# Create documentation

- Schemas
- Assert against schemas
- Yaml

---

## Schemas

- `doc/api/v3/schemas`

---

## Assert against schemas

- `import JsonSchema.Assertions`
- `assert_schema("worker/workers/index.json", response)`
- Validates our fake data
- When real backend developers do their job, they can be sure that they are not breaking the contract

---

## Yaml

- `doc/api/v3/api.yaml`
- `doc/api/v3/paths/worker/workers/index.yaml`
- Add examples on schemas
  `"example": { "$ref": "index.example.json" }`
- `mix docs`
  - docker installed and running
  - It validates schemas and generates documentation

---

# Bonus track

- Localization
  - `mix phraseapp`
  - `dgettext("leaves", "leave-detail-subtitle")`
- `mix format`
- `mix dyalizer`

---

# References

[Request life-cycle](https://hexdocs.pm/phoenix/request_lifecycle.html) (Recomended)
[Phoenix framework](https://www.phoenixframework.org/)
[Phoenix docs](https://hexdocs.pm/phoenix/Phoenix.html)
Slack #elixir
[@fertapric](https://twitter.com/fertapric)

---

![175%](finished.gif)
