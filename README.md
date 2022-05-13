# rtmidi-jna: JNA-based RtMidi JVM binding

This project is set up to build a consumable Jar library that bundles built-in [rtmidi](https://github.com/thestk/rtmidi) binaries from the fairly up to date (i.e. not outdated) sources, and then bundle them within a Jar using jnaerator-gradle-plugin (of [my fork](https://github.com/atsushieno/gradle-jnaerator-plugin)).

I set this up primarily for [ktmidi](https://github.com/atsushieno/ktmidi) project.

## Using rtmidi-jna

If you use rtmidi-jna as a Maven package, use this line In `build.gradle`:

> implementation "dev.atsushieno:rtmidi-jna:+" // replace + with a specific version

The Maven package is built and packaged by the [GitHub Actions setup](.github/workflows/actions_package_reg.yml) in this repository, and contains prebuilt rtmidi binaries for Linux x86_64, Windows x86_64, and MacOS x86_64. <del>For anything else, you are supposed to prepare your own (lib)rtmidi shared/dynamic library. Also note that rtmidi does not seem to respect full ABI compatibility.</del>

An important note here is that with the current JNAerated package, those bundled libraries turned out to not get extracted and placed to any appropriate location. Therefore you will have to appropriately set up those shared libraries in the library paths for each platform (e.g. using `LD_LIBRARY_PATH`). Sadly JNAerator has been unmaintained and there is little chance to get this working.


## License

rtmidi-jna is distributed under the MIT licanse.

rtmidi is also distributed under the MIT license.
