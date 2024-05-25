# zip-extract

zip-extract's primary goal is simple: Automate tedious zip extraction. Ever wanted to just unpack
an archive somewhere? Well, here you go.

## Forked!

This is a forked project. The main changes are:

- Add support of file name encoding detection, for SHIFT-JIS or other non-UTF8 encoded file names.
- Use up-to-date `zip` crate. Mainly for `deflate64`.

## Usage

```rust
let archive: Vec<u8> = download_my_archive()?;
let target_dir = PathBuf::from("my_target_dir"); // Doesn't need to exist

// The third parameter allows you to strip away toplevel directories.
// If `archive` contained a single directory, its contents would be extracted instead.
zip_extract::extract(Cursor::new(archive), &target_dir, true)?;
```

## Features

All features are passed through to `zip`. Visit `zip` for detail: https://github.com/zip-rs/zip2?tab=readme-ov-file#features

default features are:

- `aes-crypto`
- `bzip2`
- `deflate`
- `deflate64`
- `zstd`
