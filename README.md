# My Notes

## General Code Structure

The flow of a program using this structure looks like this:
1. Someone calls the entrypoint
2. The entrypoint forwards the arguments to the processor
3. The processor asks instruction.rs to decode the instruction_data argument from the entrypoint function.Using the decoded data, the processor will now decide which processing function to use to process the request.
4. The processor may use state.rs to encode state into or decode the state of an account which has been passed into the entrypoint.

```
.
├─ src
│  ├─ lib.rs -> registering modules
│  ├─ entrypoint.rs -> entrypoint to the program
│  ├─ instruction.rs -> program API, (de)serializing instruction data
│  ├─ processor.rs -> program logic
│  ├─ state.rs -> program objects, (de)serializing state
│  ├─ error.rs -> program specific errors
├─ .gitignore
├─ Cargo.lock
├─ Cargo.toml
├─ Xargo.toml
```

## General Solana Reminders:

```
System program---owns---> User system acc
                            ^
                            |
              has owner attribute that points to...
                            |
                            |
Token program----owns---> User token acc


Escrow Program---owns--> Temporary escrow account <---via PDA-- Temp user token acc
```

The PDA allows the Escrow Program


## Credit To
https://paulx.dev/blog/2021/01/14/programming-on-solana-an-introduction/

### Environment Setup
1. Install Rust from https://rustup.rs/
2. Install Solana from https://docs.solana.com/cli/install-solana-cli-tools#use-solanas-install-tool

### Build and test for program compiled natively
```
$ cargo build
$ cargo test
```

### Build and test the program compiled for BPF
```
$ cargo build-bpf
$ cargo test-bpf
```
