# fyp-grading-config

Shared configuration for the Assay services, served by
[fyp-grading-config-server](https://github.com/FirasKhalife/fyp-grading-config-server).

- `application.yml` applies to every service. It only holds what must be identical everywhere: which actuator
  endpoints are exposed (health, info and prometheus), which tokens are accepted (issuer `AUTH_ISSUER_URI` and
  client `assay-spa`) and log levels.
- `application-dev.yml` applies with the `dev` profile.
- Each service's own `application.yml` is complete, so a service also starts without the config server.

Values served from here **override** a service's own defaults. Never widen the actuator exposure here, and never
put secrets in this repository: it is public. Secrets come from the environment.

To try an unpushed branch locally, run the config server with the `native` profile and mount this folder at
`/config` (the docker-compose repo does this).
