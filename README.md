# `#[derive(ToTokens)]`

[![Crates.io](https://img.shields.io/crates/v/derive-quote-to-tokens)](https://crates.io/crates/derive-quote-to-tokens)
[![Downloads](https://img.shields.io/crates/d/derive-quote-to-tokens.svg)](https://crates.io/crates/derive-quote-to-tokens)
[![Documentation](https://docs.rs/derive-quote-to-tokens/badge.svg)](https://docs.rs/derive-quote-to-tokens)
[![License](https://img.shields.io/crates/l/derive-quote-to-tokens)](https://crates.io/crates/derive-quote-to-tokens)
[![Dependency Status](https://deps.rs/repo/github/aatifsyed/derive-quote-to-tokens/status.svg)](https://deps.rs/repo/github/aatifsyed/derive-quote-to-tokens)

`#[derive(ToTokens)]`, calling [`quote::ToTokens`](https://docs.rs/quote/1.0.33/quote/trait.ToTokens.html#tymethod.to_tokens) on each field.
Nothing more, nothing less.

```rust
use derive_quote_to_tokens::ToTokens;
use quote::{ToTokens, quote};
use proc_macro2::Span;
use syn::{Token, Ident};

#[derive(ToTokens)]
struct Tag {
    lt: Token![<],
    inner: Ident,
    gt: Token![>],
}

let tag = /* snip */
assert_eq!(
    tag.to_token_stream().to_string(),
    quote! { <main> }.to_string(),
);
```

Enums work too.
```rust
#[derive(ToTokens)]
enum Arrow {
     Left(Token![<], Token![-]),
    Right(Token![-], Token![>]),
}
```

<!-- cargo-rdme end -->
