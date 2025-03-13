## Notes about IDE support for mill build files in a multi-file build.

This is using the example from the [official documentation](https://mill-build.org/mill/large/multi-file-builds.html#_helper_files)

Versions used :

* mill 0.12.8-9-95f1fe
* metals 1.5.1
* vscode 1.98.1
* IntelliJ 2024.3.4.1
* IntelliJ-Scala plugin 2024.3.42

## Vscode + BSP

* Jump to definition doesn't work when the definition is in another .mill file.
* Auto-completion points the the generated wrapper for definitions coming from other .mill files. See [screenshot](./screenshots/vscode-bsp-autocompletion.png).
* Error diagnostics do not disappear when errors are fixed (see https://github.com/com-lihaoyi/mill/issues/4721)
* Top level `defs` are reported as errors. See [screenshot](./screenshots/vscode-bsp-toplevel-def.png)

## Vscode + Bloop

* Jump to definition doesn't work when the definition is in another .mill file.
* Auto-completion doesn't seem to work at all for definitions coming from other .mill files.
* Non-syntactic error diagnostics do not seem to be displayed

## IntelliJ + BSP

* Jump to definition works across mill files ONLY when the files are in the same folder/package.
* IntelliJ shows errors for all `$file` imports, and all imported definitions from these imports. See [screenshot](./screenshots/intellij-bsp-genidea-red-imports.png)
* Auto-completion points the the generated wrapper for definitions coming from other .mill files. See [screenshot](./screenshots/intellij-bsp-autocompletion.png).

## IntelliJ + GenIdea

Experiencing the exact same symptoms as IntelliJ + BSP
