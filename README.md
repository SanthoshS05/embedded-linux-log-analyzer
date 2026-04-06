# Embedded Linux Log Analyzer

![Python](https://img.shields.io/badge/python-3.8+-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## Overview

**Embedded Linux Log Analyzer** is a Python-based CLI tool designed to analyze **boot logs from embedded systems** and automatically detect:

* Errors
* Warnings
* Failures
* Critical issues

It helps engineers quickly debug **boot sequences, driver issues, and system failures** during development and validation.

---

## 🎯 Key Features

* Regex-based intelligent log parsing
* Categorizes logs into multiple severity levels
* Tracks line numbers for each issue
* Generates summary report
* Handles large log files efficiently
* Works as a CLI tool (`logphraser`)

---

## Supported Log Types

* U-Boot logs
* Linux kernel (`dmesg`) logs
* Embedded Linux boot logs
* Driver initialization logs
* Yocto-based system logs

---

## Project Structure

```text id="p4v7vl"
embedded-linux-log-analyzer/
│
├── logphraser           # Main CLI tool (executable script)
├── logs/                # Generated output logs (auto-created)
│   ├── error.log
│   ├── warning.log
│   ├── failure.log
│   └── critical.log
│
├── input/               # Sample input log files
│   ├── sample.log
│   └── big_log.txt
│
├── README.md
```

### Structure Explanation

* **logphraser** → Core script that processes logs
* **logs/** → Output directory (created automatically during execution)
* **input/** → Sample logs for testing
* **README.md** → Project documentation

---

## Setup & Installation

### 1 Make Script Executable

```bash id="k7aj0v"
chmod +x logphraser
```

---

### 2 Add Tool to `$PATH`

 This allows running `logphraser` from anywhere

```bash id="0uqy3z"
export PATH="$PATH:/full/path/to/project"
```

#### Example:

```bash id="1rmn8n"
export PATH="$PATH:/home/santhosh/embedded-linux-log-analyzer"
```

---

### 3 Make PATH Permanent

#### For Bash:

```bash id="aqaxlr"
echo 'export PATH="$PATH:/home/santhosh/embedded-linux-log-analyzer"' >> ~/.bashrc
source ~/.bashrc
```

#### For Zsh:

```bash id="s9r9hf"
echo 'export PATH="$PATH:/home/santhosh/embedded-linux-log-analyzer"' >> ~/.zshrc
source ~/.zshrc
```

---

## Usage

### Basic Command

```bash id="r41jrn"
logphraser <log_file>
```

---

### Example (From build folder)

```bash id="m01mhc"
cd build
logphraser ../../../log.txt
```

---

### Example (Absolute Path)

```bash id="q0d0yw"
logphraser /home/santhosh/logs/boot.log
```

---

## Sample Output

```text id="g8r1jx"
===== LOG VALIDATION SUMMARY =====
Error: 10
Warning: 5
Failure: 3
Critical: 2
```

---

## Generated Output

After execution, categorized logs are stored in:

```id="61y9co"
logs/
├── error.log
├── warning.log
├── failure.log
└── critical.log
```

Each file contains:

```text id="7d9uy5"
[Line 45] ERROR: DDR initialization failed
```

---

## Pattern Matching Logic

| Category | Regex Pattern         | Example Match    |
| -------- | --------------------- | ---------------- |
| Error    | `\berror\b`           | error occurred   |
| Failure  | `\bfail(ed)?\b`       | driver failed    |
| Warning  | `\bwarning\b`         | warning detected |
| Critical | `cannot \| get.*fail` | cannot get clk   |

---

## How It Works

1. Reads log file line-by-line
2. Applies regex patterns
3. Identifies issue category
4. Writes categorized logs
5. Generates summary

---

## Use Cases

* Embedded Linux bring-up debugging
* Kernel and driver issue detection
* Boot failure analysis
* Automated log validation

---

## Troubleshooting

### Command not found

```bash id="9o1yk9"
echo $PATH
```

Ensure your project path is included.

---

### Permission denied

```bash id="y2z87d"
chmod +x logphraser
```

---


## Contributing

Contributions are welcome!
Feel free to raise issues or submit pull requests.

---

##  Author

**Santhosh Suresh**
Embedded Software Engineer | Embedded Linux | System Programming

---
