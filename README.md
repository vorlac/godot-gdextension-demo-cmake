# Godot GDExtension C++ CMake Demo Project

1. Install Python and Visual Studio 2022 Community Edition (including the C++ toolchain and cmake build features)
1. run `pip install scons` (needed to build the godot editor/engine with debug symbols)
1. Clone this repo
1. Run `git submodule update --init` from the root directory of this repo to populate the godot engine submodule
1. run `./scripts/build_engine.sh` from the root directory of this repo to build the engine.
1. Open the root directory of this repo from Visual Studio 2022 (open as folder).
1. Configure the CMake project ("Project"->"Configure gdext_example" from within Visual Studio 2022)
1. Select the "MSVC Debug" build configuration in the drop down in Visual Studio, then build the project. Clang doesn't seem to build successfully on windows, and I haven't fully tested GCC yet so I'd recommend sticking with the MSVC build to start with.
    1. When the build completes, select the startup item option labeled "example lib (debug editor)".
    1. Toss a breakpoint in `void GDExample::_process(double delta)`
    1. Hit F5 or go to "Debug"->"Start Debugging".

If everything worked correctly, the editor should automatically open, and the breakpoint should hit. The debug build of the editor should allow you to inspect a complete callstack into the engine.

If you don't want to build the engine, you can just edit the "example lib (release editor)" entry in the `.vs/launch.vs.json` file to point to a release installation of the editor, then select that as your debug launch target. You'll still be able to debug the GDExtension demo code, but won't be able to debug into the engine.
