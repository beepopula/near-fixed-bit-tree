<div align="center">

  <h1><code>near-fixed-bit-tree</code></h1>

  <p>
    <strong>Popula Library for fixed length binary tree and alternative key-value storage.</strong>
  </p>


  <p>
    <a href="https://crates.io/crates/near-fixed-bit-tree"><img src="https://img.shields.io/crates/v/near-fixed-bit-tree.svg?style=flat-square" alt="Crates.io version" /></a>
    <a href="https://crates.io/crates/near-fixed-bit-tree"><img src="https://img.shields.io/crates/d/near-fixed-bit-tree.svg?style=flat-square" alt="Download" /></a>
    <a href="https://docs.rs/near-fixed-bit-tree"><img src="https://docs.rs/near-fixed-bit-tree/badge.svg" alt="Reference Documentation" /></a>
  </p>

</div>

## Example


```rust
use near_fixed_bit_tree::BitTree;

#[near_bindgen]
impl Contract {
    #[init]
    pub fn new() -> Self {
        assert!(!env::state_exists(), "Already initialized");
        metadata.assert_valid();
        let mut this = Self {
            bit_tree: BitTree::new(28, vec![0], u16::BITS as u8),
        };
        this
    }
    
    pub fn get(&self, key: &[u8]) -> Option<u8> {
        self.bit_tree.get(key)
    }

    pub fn set(&mut self, key: &[u8], val: u8) {
        self.bit_tree.set(key, val)
    }

    pub fn del(&mut self, key: &[u8]) {
        self.bit_tree.del(key)
    }

    pub fn check(&self ,key: &[u8]) -> bool {
        self.bit_tree.check(key)
    }

    pub fn get_and_set(&mut self, key: &[u8], val: u8 ) -> Option<u8> {
        self.bit_tree.get_and_set(key, val)
    }

    pub fn check_and_set(&mut self, key: &[u8], val: u8 ) -> bool {
        self.bit_tree.check_and_set(key, val)
    }
}
```

## Features


## Versioning

### Semantic Versioning

This crate follows [Cargo's semver guidelines](https://doc.rust-lang.org/cargo/reference/semver.html). 

State breaking changes (low-level serialization format of any data type) will be avoided at all costs. If a change like this were to happen, it would come with a major version and come with a compiler error. If you encounter one that does not, [open an issue](https://github.com/near/near-fixed-bit-tree-rs/issues/new)!

### MSRV

The minimum supported Rust version is currently `1.56`. There are no guarantees that this will be upheld if a security patch release needs to come in that requires a Rust toolchain increase.
