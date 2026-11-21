<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin sorting distinct leaves and singling out a lone specimen.">

# Richness

Count observed taxa and singletons from an abundance vector. This Blyx library is part of the geospatial and scientific computing collection.

Two surveys can have the same species count and very different abundance patterns. Report diversity alongside observed richness. [scikit-bio, Simpson dominance](https://scikit.bio/docs/latest/generated/skbio.diversity.alpha.dominance.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-richness.git
cd blyx-richness
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-richness) · [Package page](https://www.blyx-lang.space/packages/richness) · [Handbook](https://doc.blyx-lang.space/guide/egret)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-richness.git vendor/richness
```

```blyx
use vendor::richness::richness;

fn main() {
    let counts = [0, 1, 3, 1];
    let result = richness_observe(counts);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
3
2
5
```

## API

`richness_observe(counts)`

Returns [observed taxa, singletons, individuals]. Zero-count categories do not increase richness. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| counts | Vector of values, each a nonnegative exact integer |

## In use

[Egret](https://github.com/Rahulchaube1/blyx-egret) uses this module to summarize richness, singletons and dominance in an ecological field survey.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-richness/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
