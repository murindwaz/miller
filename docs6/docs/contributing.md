<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# How to contribute

## Community

You can ask questions -- or answer them! -- following the links on the [Community](community.md) page.

## Documentation improvements

Pre-release Miller documentation is at [https://github.com/johnkerl/miller/tree/main/docs6](https://github.com/johnkerl/miller/tree/main/docs6).

Instructions for modifying, viewing, and submitting PRs for these are in the [docs6/README.md](https://github.com/johnkerl/miller/blob/main/docs6/README.md).

While Miller 6 is in pre-release, these docs are not viewable at
[https://miller.readthedocs.io](https://miller.readthedocs.io) which shows Miller 5 docs.
For now, I'll push Miller-6 docs to my ISP space at
[https://johnkerl.org/miller6](https://johnkerl.org/miller6) after your PR is merged.

<!---
TODO: after Miller6 release when these are on RTD

Once PRs are merged, readthedocs creates [https://miller.readthedocs.io](https://miller.readthedocs.io) using the following configs:

* [https://readthedocs.org/projects/miller](https://readthedocs.org/projects/miller)
* [https://readthedocs.org/projects/miller/builds](https://readthedocs.org/projects/miller/builds)
* [https://github.com/johnkerl/miller/settings/hooks](https://github.com/johnkerl/miller/settings/hooks)
-->

## Testing

As of Miller-6's current pre-release status, the best way to test is to either build from source via [Building from source](build.md), or by getting a recent binary at [https://github.com/johnkerl/miller/actions](https://github.com/johnkerl/miller/actions), then click latest build, then *Artifacts*. Then simply use Miller for whatever you do, and create an issue at [https://github.com/johnkerl/miller/issues](https://github.com/johnkerl/miller/issues).

Do note that as of mid-2021 a few things have not been ported to Miller 6 -- most notably, including localtime DSL functions and other issues.

## Feature development

Issues: [https://github.com/johnkerl/miller/issues](https://github.com/johnkerl/miller/issues)

Developer notes: [https://github.com/johnkerl/miller/blob/main/go/README.md](https://github.com/johnkerl/miller/blob/main/go/README.md)

PRs which pass regression test ([https://github.com/johnkerl/miller/blob/main/go/regtest/README.md](https://github.com/johnkerl/miller/blob/main/go/regtest/README.md)) are always welcome!
