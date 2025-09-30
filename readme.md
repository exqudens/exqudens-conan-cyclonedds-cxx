# cyclonedds-cxx

## cmake-vars
- `-DBUILD_DDSLIB=0`: to disable DDS lib build, useful in crosscompiling scenarios where you only need the generator and use the DDS lib from another build.
- `-DBUILD_IDLLIB=0`: to disable IDL preprocessor lib build
- `-DBUILD_DOCS=1`: to build the documentation
- `-DBUILD_TESTING=1`: to build the testing tree
- `-DBUILD_EXAMPLES=1`: to build examples
- `-DENABLE_LEGACY=1`: to enable legacy c++11 mode, adds boost as dependency (otherwise it uses c++17)
- `-DENABLE_ICEORYX=1`: to enable Iceoryx tests
- `-DENABLE_TYPELIB=1`: to enable type library support
- `-DENABLE_TOPIC_DISCOVERY=1`: to enable topic discovery support
- `-DENABLE_COVERAGE=1`: to enable coverage build

## how-to-configure
1. `cmake --preset ${preset}` where `${preset}` is one of `cmake --list-presets`

## how-to-build
1. follow `how-to-configure`
2. `cmake --build --preset ${preset}`
3. `cmake --build --preset ${preset} --target cmake-install`

## how-to-export
1. follow `how-to-configure`
2. `cmake --build --preset ${preset} --target conan-remove`
3. `cmake --build --preset ${preset}`
4. `cmake --build --preset ${preset} --target conan-export`

## how-to-export-all-packages
1. `conan remove -c cyclonedds`
2. `git clean -xdf`
3. `cmake --list-presets | cut -d ':' -f2 | xargs -I '{}' echo '{}' | xargs -I '{}' bash -c "cmake --preset {} || exit 255"`
4. `cmake --list-presets | cut -d ':' -f2 | xargs -I '{}' echo '{}' | xargs -I '{}' bash -c "cmake --build --preset {} || exit 255"`
5. `cmake --list-presets | cut -d ':' -f2 | xargs -I '{}' echo '{}' | xargs -I '{}' bash -c "cmake --build --preset {} --target conan-export || exit 255"`

### examples

#### build-example
1. `cmake --preset windows.ninja.msvc-x64-x64.debug.shared`
2. `cmake --build --preset windows.ninja.msvc-x64-x64.debug.shared`
3. `cmake --build --preset windows.ninja.msvc-x64-x64.debug.shared --target cmake-install`
