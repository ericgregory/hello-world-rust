# "Hello World" in Rust for Cosmonic Control

This is a simple Rust-based WebAssembly (Wasm) component intended to run on [Cosmonic Control](https://cosmonic.com/), an enterprise control plane for managing WebAssembly (Wasm) workloads in cloud native environments. The component responds with a "Hello World" message for each request. 

Additionally, the repository includes a generic GitHub Workflow for building a Wasm component from Rust and pushing it to an OCI registry. The component is available as an OCI artifact at TK

While this component was written for Cosmonic Control, you can run it with any WebAssembly runtime that supports the Component Model and the WebAssembly System Interface (WASI) HTTP API. 

Cosmonic Control is built on [wasmCloud](https://wasmcloud.com/), an Incubating project at the Cloud Native Computing Foundation (CNCF).

## Install Cosmonic Control

Sign up for Cosmonic Control's [free trial](https://cosmonic.com/trial) to get a `cosmonicLicenseKey`.

```shell
helm install cosmonic-control oci://ghcr.io/cosmonic/cosmonic-control --version 0.2.0 --namespace cosmonic-system --create-namespace --set cosmonicLicenseKey="<insert license here>"
```
```shell
helm install hostgroup oci://ghcr.io/cosmonic/cosmonic-control-hostgroup --version 0.2.0 --namespace cosmonic-system --set http.enabled=true
```

## Deploy with Cosmonic Control

TK

## Contents

In addition to the standard elements of a Rust project, the template directory includes the following files and directories:

- `wit/`: Directory for WebAssembly Interface Type (WIT) packages that define interfaces
- `./github/workflows`: Directory for GitHub Workflows 

## Build Dependencies

Before starting, ensure that you have the following installed:

- [`cargo`](https://www.rust-lang.org/tools/install) 1.82+ for the Rust toolchain
- [Wasm Shell (`wash`)](https://github.com/cosmonic-labs/wash) for component development

### Developing with `wash`

Clone the [cosmonic-labs/control-demos repository](https://github.com/cosmonic-labs/control-demos): 

```shell
git clone https://github.com/cosmonic-labs/control-demos.git
```

Change directory to `hello-world-rust`:

```shell
cd hello-world-rust
```

Start a development loop:

```shell
wash dev
```

The component is accessible at localhost:8000. View the code and make changes in `src/lib.rs`.

### Clean Up

You can cancel the `wash dev` process with `Ctrl-C`.

## Building with `wash`

To build the component:

```shell
wash build
```

## Further Reading

For more on building components, see the [Developer Guide](https://cosmonic.com/docs/developer-guide/developing-webassembly-components) in the Cosmonic Control documentation. 

To learn how to extend this example with additional capabilities, see the [Adding Capabilities](https://wasmcloud.com/docs/tour/adding-capabilities?lang=rust) section of the wasmCloud documentation.