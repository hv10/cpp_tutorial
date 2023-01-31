# A repository following along the W3 School C++ Tutorial

> using VSCode

# Running CPP Files

We can create a new task within VSCode to enable a quick compile + run action.

Create a file `.vscode/task.json`
Add the following task to the `task.json`:

```json
{
  "tasks": [
    {
      "type": "cppbuild",
      "label": "C/C++: clang++ build active file",
      "command": "/usr/bin/clang++",
      "args": [
        "-fcolor-diagnostics",
        "-fansi-escape-codes",
        "-g",
        "${file}",
        "-o",
        "${workspaceFolder}/out/${fileBasenameNoExtension}"
      ],
      "options": {
        "cwd": "${fileDirname}"
      },
      "problemMatcher": ["$gcc"],
      "group": {
        "kind": "build",
        "isDefault": false
      },
      "detail": "Compile the currently active cpp file."
    }
  ],
  "version": "2.0.0"
}
```

This creates a "building" (compiling) task we can run.

Within the "tasks" array add another task:

```json
{
  "type": "shell",
  "label": "Run Compiled File",
  "command": "${workspaceFolder}/out/${fileBasenameNoExtension}",
  "group": {
    "kind": "test",
    "isDefault": true
  },
  "options": {
    "cwd": "${fileDirname}"
  },
  "problemMatcher": ["$gcc"],
  "detail": "Run the currently active cpp file.",
  "dependsOn": ["C/C++: clang++ build active file"]
}
```

We can now compile and run any cpp file by calling the command palette `Ctrl/Cmd + Shift + P` and searching / selecting `Run Task` then `Run Compiled File`.

This will run the file in a Task View, without any commandline arguments,
with the current working directory being the location of the original cpp file.

# Hello World

> hello_world.cpp

We can run the file by using a c++ compatible compiler (like GCC / Clang++) in the terminal.

```bash
$ clang++ hello_world.cpp -o out/hello_world
$ ./out/hello_world
> Hello World
```
