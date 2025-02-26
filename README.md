# clip

A command-line utility to copy text or PDF contents to the system clipboard.

## Description

`clip` is a simple yet powerful tool that allows you to quickly copy the contents of text files or PDFs to your clipboard. It supports multiple files, piped input, and automatically handles format conversion.

## Installation

### Dependencies

Make sure you have the following dependencies installed:

- `xclip` - for clipboard operations
- `pdftotext` - for PDF conversion (part of the Poppler tools)

On Debian/Ubuntu systems:
```bash
sudo apt install xclip poppler-utils
```

On Fedora/RHEL:
```bash
sudo dnf install xclip poppler-utils
```

On Arch Linux:
```bash
sudo pacman -S xclip poppler
```

### Installation Steps

1. Download the `clip` script
2. Make it executable:
   ```bash
   chmod +x clip
   ```
3. Move it to a directory in your PATH:
   ```bash
   sudo mv clip /usr/local/bin/
   ```

## Usage

```
clip                     # Read from stdin
clip file.txt            # Copy a single file
clip file1.txt file2.pdf # Copy multiple files
cat file.pdf | clip      # Pipe content to clip
```

## Features

- **Automatic Format Detection**: Automatically detects if a file is text or PDF
- **Format Conversion**: Converts PDFs to text before copying
- **Multiple File Support**: Copy the contents of multiple files at once
- **Input Flexibility**: Read from files or standard input
- **File Headers**: Includes filename headers in a format similar to the `head` command

## Supported File Types

- Text files (any text/* MIME type)
- PDF files

## Examples

### Copy a text file to clipboard

```bash
clip report.txt
```

### Copy a PDF file to clipboard

```bash
clip document.pdf
```

### Copy multiple files

```bash
clip notes.txt presentation.pdf reference.txt
```

### Copy output of a command

```bash
ls -la | clip
```

### Combine with other tools

```bash
grep "important" logfile.txt | clip
```

## Companion Utilities

The `clip` tool comes with two companion utilities that provide simpler clipboard operations:

### xc - Copy to Clipboard

A minimal utility to copy standard input to the clipboard.

#### Usage

```bash
echo "Hello World" | xc         # Copy text to clipboard
cat file.txt | xc               # Copy file contents to clipboard
xc                              # Read from stdin (type text, press Ctrl+D when done)
```

#### Description

`xc` is a simplified version of `clip` that focuses solely on copying standard input to the clipboard without any file format detection or conversion. It's perfect for quick copy operations when you don't need the additional features of `clip`.

### xo - Output Clipboard Contents

A utility to output the current contents of the clipboard to standard output.

#### Usage

```bash
xo                              # Print clipboard contents
xo > file.txt                   # Save clipboard contents to a file
xo | grep "search term"         # Search clipboard contents
```

#### Description

`xo` complements `clip` and `xc` by allowing you to retrieve and manipulate the content currently stored in your clipboard.

## Error Handling

The script will exit with an error message if:
- No input is provided (neither files nor stdin)
- A specified file doesn't exist
- A file has an unsupported format (not text or PDF)

## License

MIT

## Author

Erik Garrison