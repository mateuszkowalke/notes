# Pi pico

### Setting up vim(neovim) for development

I'm using neovim with coc.nvim for lsp support. The project setup is the one suggested by pi pico getting started pdf. I'm using coc-clangd. First thing to enable clangd support is to generate and link compile_commands.json. There are number of ways to do it, but since pi pico's SDK uses cmake for it's build system, the easiest way is to generate build with additional DCMAKE_EXPORT_COMPILE_COMMANDS flag, so the whole command looks like: cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1 .. .

Then we have to either copy or link the generated file to our project's root directory. To link it execute ln -s build/compile_commands.json . from your root directory. The last step is to tell clangd we're using different toolchain. In our case it is gcc-arm-none-eabi. To do that we need to create .vim folder with coc-settings.json file in it. In that file we need to set "clangd.arguments" array, and first element of it should be "-query-driver={our toolchain}". Be aware, that binary name might not be enough, and you might have to supply whole absolute path.

Highly recommend to check out:
- https://releases.llvm.org/10.0.0/tools/clang/tools/extra/docs/clangd/Configuration.html
- https://clangd.llvm.org/installation.html
- https://clangd.llvm.org/troubleshooting#cant-find-standard-library-headers-map-stdioh-etc
- https://github.com/clangd/coc-clangd

### Setting up vimspector for pi pico

### Using port monitor when using picoprobe

To use serial monitor without RPi our only option is to use usb. After uploading binary using picoprobe, openocd and gdb-multiarch we need to plug the pi pico using usb cable directly.
