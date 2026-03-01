# apcupsd_exporter

Command `apcupsd_exporter` provides a Prometheus exporter for the
[apcupsd](http://www.apcupsd.org/) Network Information Server (NIS). MIT
Licensed.

## Credits

This project is derived from the original
[apcupsd_exporter](https://github.com/mdlayher/apcupsd_exporter) by
[Matt Layher](https://github.com/mdlayher). All credit for the original design
and implementation goes to the original author.

## Development

### Prerequisites

- [Go](https://go.dev/) 1.26 or later

### Build

From the repository root:

```bash
go build ./cmd/apcupsd_exporter
```

This produces an `apcupsd_exporter` binary in the current directory. To run without building:

```bash
go run ./cmd/apcupsd_exporter --help
```

### Tests

Run the full test suite (unit and integration):

```bash
go test ./...
```

Run the linter before committing:

```bash
go vet ./...
go fmt ./...
```

### Running locally

When testing without a real apcupsd NIS, use `-telemetry.addr :0` so the exporter picks an available port and avoid conflicts with other instances.

## Usage

Available flags for `apcupsd_exporter` include:

```
$ ./apcupsd_exporter -h
Usage of ./apcupsd_exporter:
  -apcupsd.addr string
        address of apcupsd Network Information Server (NIS) (default ":3551")
  -apcupsd.network string
        network of apcupsd Network Information Server (NIS): typically "tcp", "tcp4", or "tcp6" (default "tcp")
  -telemetry.addr string
        address for apcupsd exporter (default ":9162")
  -telemetry.path string
        URL path for surfacing collected metrics (default "/metrics")
```
