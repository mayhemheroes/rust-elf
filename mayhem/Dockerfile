FROM fuzzers/cargo-fuzz:0.11.0 as builder

ADD . /rust-elf
WORKDIR /rust-elf

RUN cd fuzz/ && cargo fuzz build

FROM ubuntu:20.04

COPY --from=builder /rust-elf/fuzz/target/x86_64-unknown-linux-gnu/release/common /
COPY --from=builder /rust-elf/fuzz/target/x86_64-unknown-linux-gnu/release/notes /
COPY --from=builder /rust-elf/fuzz/target/x86_64-unknown-linux-gnu/release/stream /
COPY --from=builder /rust-elf/fuzz/target/x86_64-unknown-linux-gnu/release/symbol_table /
COPY --from=builder /rust-elf/fuzz/target/x86_64-unknown-linux-gnu/release/symver /
