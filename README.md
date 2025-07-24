# MidnightBSD VM GitHub Action

The MidnightBSD VM GitHub Action spins up a MidnightBSD virtual machine using QEMU, establishes an SSH connection, and executes specified commands within the VM.
A custom shell is also installed and can be used after the VM boots.

Currently, MidnightBSD 3.2.3 is used as the VM image.

### Inputs

| Input     | Description                              | Required | Default   |
|-----------|------------------------------------------|----------|-----------|
| `run`     | Commands to run inside the MidnightBSD VM | Yes      | `uname -a` |

### Examples

#### Basic usage

```yaml
name: Run on MidnightBSD

on: [push]

jobs:
  midnightbsd:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Run in MidnightBSD VM
        uses: bjia56/midnightbsd-vm@main
        with:
          run: |
            uname -a
```

#### Custom shell

```yaml
name: Run on MidnightBSD

on: [push]

jobs:
  midnightbsd:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Start MidnightBSD VM
        uses: bjia56/midnightbsd-vm@main

      - name: Run in MidnightBSD VM
        shell: midnightbsd {0}
        run: |
          uname -a
```
