# PLC Code Reader

PLC Code Reader opens an exported PLC program and shows its logic, tags and hardware in your browser.
It only reads the file. It never connects to a PLC or controller, and nothing about the program leaves your computer.

Get the latest build from the [Releases page](../../releases?q=plc-code-reader) (tagged `plc-code-reader-v<version>`).

## Files it opens

- Schneider EcoStruxure Control Expert exports: `.zef` or `.xef`
- Rockwell RSLogix / Studio 5000 exports: `.L5K`

A file named `.L5X` is read as L5K text. The XML L5X format is not yet supported, so export L5K from Studio 5000.

## Start it (Windows)

1. Unzip `plc-code-reader-<version>.zip` anywhere, for example in `Documents`.
2. Double-click `plcreader.exe`. A console window opens, and your browser opens at <http://127.0.0.1:8000>.
   The program is not code-signed, so the first time Windows SmartScreen may stop it. Choose *More info*, then *Run anyway*.
3. Drag an export onto the page, or click *Choose file*. Files up to 256 MB are accepted.

To stop it, close the console window or press `Ctrl+C` in it.

To start it without opening a browser, run `plcreader.exe --no-open` from a command prompt, then open <http://127.0.0.1:8000> yourself.

## What you can look at

- Sections: every routine or section, grouped by task (and by program, for Rockwell). Ladder, FBD and Structured Text are drawn as readable schematics. In ladder, click a `JSR` target to open that routine.
- Tags / IO: the full tag list with type, address and description. Search it, filter it to tags used in logic or never referenced, and export it to CSV or Markdown.
- Cross-ref: where a tag is read and where it is written, and a trace of what drives it.
- Types: user-defined types (UDTs, DDTs) and function blocks (AOIs, DFBs) with their parameters and internal logic. A protected block shows its interface only.
- Hardware: the CPU, racks, remote drops and modules.
- Document: the whole program on one page. Use *Print / Save as PDF* to hand it off.

If the reader cannot draw part of a section, the section shows a "Partial" warning with the number of elements it skipped.

Click *Close file* to unload the program and open another one.

## If something goes wrong

- "Port 8000 is already in use": another copy is running. Open <http://127.0.0.1:8000>, or close the other copy and start again.
- "Unsupported file type": the file is not `.zef`, `.xef`, `.L5K` or `.L5X`.
- "File does not look like..." or "Archive contains no .xef payload": the file is not the export its name says it is.
- "Failed to parse (HTTP 500)": the file is damaged or is not well-formed XML. Export it again.
- "File is too large": the file is over 256 MB.
- The browser did not open: open <http://127.0.0.1:8000> yourself.

## Your data

The program listens only on `127.0.0.1` and makes no network calls.
An uploaded file is read in memory and discarded after it is parsed; nothing is written to disk.
Your browser keeps the parsed program until you close the tab or load another file.

## Use responsibly

Use it only for program exports you are authorized to hold. It is provided as-is, with no warranty.

## License

Apache License 2.0 — see [LICENSE](LICENSE). Third-party components used to build this binary are listed in [NOTICE](NOTICE).
