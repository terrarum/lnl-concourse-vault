# Vault Concourse Demo

# To Do

- [x] Get vault and concourse running
- [x] Connect vault and concourse
- [] Create a pipeline for the app
- [] Have it pass a secret in to the app

Vault: http://localhost:8200
Concourse: http://localhost:8080

## TfL API

Line Status

https://api-portal.tfl.gov.uk/api-details#api=Line&operation=Line_StatusByModeByPathModesQueryDetailQuerySeverityLevel

`https://api.tfl.gov.uk/Line/Mode/tube,dlr/Status?app_key=2213d8123faa4f2b8feb5e0c1838db93`

# Notes

Launch Vault
Launch Concourse

## How do we link them?
concourse docker compose

    - CONCOURSE_VAULT_URL=http://localhost:8200
    - CONCOURSE_VAULT_CLIENT_TOKEN=root_token

Terminal into Vault box

`vault login` -> root_token
`vault secrets enable -version=2 -path=concourse kv`

go to vault UI
create a policy called `concourse`
```hcl
path "concourse/*" {
  policy = "read"
}
```

# Concourse
target: local, team name: main
admin/admin

`fly -t local login -n main -c http://127.0.0.1:8080`
