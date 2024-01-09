# cyclonedds-cxx

##### Variables:

* `-DBUILD_DDSLIB=NO`: to disable DDS lib build, useful in crosscompiling scenarios where you only need the generator and use the DDS lib from another build.
* `-DBUILD_IDLLIB=NO`: to disable IDL preprocessor lib build
* `-DBUILD_DOCS=ON`: to build the documentation
* `-DBUILD_TESTING=ON`: to build the testing tree
* `-DBUILD_EXAMPLES=ON`: to build examples
* `-DENABLE_LEGACY=ON`: to enable legacy c++11 mode, adds boost as dependency (otherwise it uses c++17)
* `-DENABLE_ICEORYX=ON`: to enable Iceoryx tests
* `-DENABLE_TYPELIB=ON`: to enable type library support
* `-DENABLE_TOPIC_DISCOVERY=ON`: to enable topic discovery support
* `-DENABLE_COVERAGE=ON`: to enable coverage build

##### Build:

```
cmake --preset windows.ninja.msvc-16-x64-x64.release.shared
cmake --build --preset windows.ninja.msvc-16-x64-x64.release.shared
cmake --build --preset windows.ninja.msvc-16-x64-x64.release.shared --target conan-export
```

##### Examples:

* Build `idlcxx`:
    * `cmake -DBUILD_IDLLIB=ON --preset windows.ninja.msvc-16-x64-x64.debug.shared`
    * `cmake --build --preset windows.ninja.msvc-16-x64-x64.debug.shared --target idlcxx`
    * `cmake --build --preset windows.ninja.msvc-16-x64-x64.debug.shared --target cmake-install`
