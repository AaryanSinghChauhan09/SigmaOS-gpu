# SigmaOS GPU

Rust library containing GPU and graphics modules. The crate exports GPU
manager and vendor-specific state types alongside graphics APIs; its source
includes frequency-scaling, power-profile, vector, display, and rendering
models.

## Current implementation limits

Several GPU control methods update in-memory values and describe sysfs or
vendor-tool writes as future work. For example, the frequency controller's
clock and power setters do not program a physical device. Default clock,
temperature, and power values are model defaults, not hardware readings. The
crate has no published hardware support matrix here, so API presence must not
be read as working AMD, Intel, or NVIDIA support.

## Integration

The crate depends on `SigmaOS-kernel` through a sibling path dependency. The
CI workflow resolves SigmaOS path dependencies and runs Rust checks. Keep
capability detection, hardware access, and fallback behavior explicit before
integrating a control path into a desktop or power policy.

## Development

Run `cargo check` to compile the library and `cargo test` to run its unit
tests. A successful host build alone does not validate physical GPU control.
