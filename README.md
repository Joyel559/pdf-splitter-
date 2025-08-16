# PDF Chapter Chunker – splitter.py

PDF Chapter Chunker is a command-line tool for splitting PDF files into smaller, organized chunks by chapters or by a fixed number of pages. It automatically detects chapters from the table of contents (TOC) or uses a page-based method if no TOC is found.

***

## Features

- Smart chapter detection using various TOC formats  
- Page-based splitting as a fallback  
- Creates organized output folders with clear filenames  
- Adds bookmarks and metadata  
- Efficient memory usage and fast processing  
- Robust error handling and quiet mode option

***

## Requirements

- Python 3.7 or higher  
- pip package manager  
- [pypdf](https://pypi.org/project/pypdf/)

***

## Installation

Install the required dependency with:
```bash
pip install pypdf
```
Download the script with:
```bash
git clone https://github.com/newjordan/PDF-Chapter-Chunker.git
cd PDF-Chapter-Chunker
# Or download directly
wget https://raw.githubusercontent.com/newjordan/PDF-Chapter-Chunker/main/splitter.py
```

***

## Usage

Basic commands:
```bash
# Split by chapters (default mode)
python splitter.py habits.pdf

# Split by chapters explicitly
python splitter.py habits.pdf --mode chapters

# Split by pages (99 pages per chunk)
python splitter.py habits.pdf --mode pages

# Split by pages with custom chunk size
python splitter.py habits.pdf --mode pages --size 50

# Custom output directory
python splitter.py habits.pdf --output ./chunks

# Quiet mode (minimal output)
python splitter.py habits.pdf --quiet

# Get help
python splitter.py --help
```

***

## Command Line Options

| Option                 | Description                                 | Default       |
|------------------------|---------------------------------------------|---------------|
| input_pdf              | Path to input PDF file                      | Required      |
| --mode {chapters,pages}| Chunking mode: chapters or pages            | chapters      |
| --output, -o OUTPUT    | Output directory for chunks                 | Same as input |
| --size, -s SIZE        | Pages per chunk (pages mode only)           | 99            |
| --quiet, -q            | Run without verbose output                  | False         |
| --help, -h             | Show help message and exit                  | -             |
| --version              | Show program's version number and exit      | -             |

***

## Output Structure

### Chapter Mode
```
habits_chapters/
├── 001_1 percent better or.pdf (3 pages)
├── 002_3 How to Build Better Habits in.pdf (33 pages)
├── 003_1 percent better each day, you’ll end up with.pdf (163 pages)
├── 004_170 to a lean.pdf (57 pages)
```

### Page Mode
```
habits_pages/
├── habits_chunk_001.pdf (N pages)
├── habits_chunk_002.pdf (N pages)
...
```

***

## Examples

Split `habits.pdf` by chapters:
```bash
python splitter.py habits.pdf
```
_Output: 4 chapter PDF files in habits_chapters/._

Split by pages (99 per chunk, default):
```bash
python splitter.py habits.pdf --mode pages
```
_Output: 3 PDF files: 99, 99, 58 pages in habits_pages/._

Split by custom chunk size (50 per chunk):
```bash
python splitter.py habits.pdf --mode pages --size 50
```
_Output: 6 PDF files: five with 50 pages each, one with 6 pages._

Split to a custom output directory:
```bash
python splitter.py habits.pdf --output ./custom_chunks
```

Run without verbose output:
```bash
python splitter.py habits.pdf --quiet
```

Show help:
```bash
python splitter.py --help
```

***

## Troubleshooting

- If no table of contents is detected, the tool uses page-based chunking.
- Ensure your PDF is not corrupted and you have proper file permissions.
- For very large PDFs, consider splitting in stages for optimal performance.

***

## License

MIT License. See the LICENSE file in the repository for details.

***

Made for efficient and organized PDF document management.
