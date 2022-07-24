# Golang-migrate

### Installation

For Go>1.15 it's best to use go get:

```bash
go install -tags 'postgres' github.com/golang-migrate/migrate/v4/cmd/migrate@latest
```

### Running migrations

The force command enables resolving of the dirty state.

```bash
migrate -path migrations -database "postgresql://testuser:testpass@localhost:5432/falcon_manager?sslmode=disable" -verbose up

migrate -path migrations -database "postgresql://testuser:testpass@localhost:5432/falcon_manager?sslmode=disable" -verbose down

migrate -path migrations -database "postgresql://testuser:testpass@localhost:5432/falcon_manager?sslmode=disable" -verbose force <migration no>
```
