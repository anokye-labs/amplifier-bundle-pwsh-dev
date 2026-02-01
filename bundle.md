---
bundle:
  name: pwsh-dev
  version: 1.0.0
  description: Development bundle with PowerShell instead of Bash

includes:
  - bundle: foundation

tools:
  - module: tool-pwsh
    source: git+https://github.com/anokye-labs/amplifier-module-tool-pwsh@main
    config:
      timeout: 60
      require_approval: false
---

# PowerShell Development Bundle

@foundation:context/shared/common-system-base.md

---

## Shell Execution Policy

**CRITICAL POLICY: Use the `pwsh` tool for ALL command-line operations.**

**The `bash` tool is DISABLED. NEVER use it. If you need to run shell commands, use `pwsh` exclusively.**

The `pwsh` tool provides PowerShell Core command execution. PowerShell works cross-platform (Linux, macOS, Windows) and provides:

- Object-oriented pipelines: `Get-Process | Where-Object CPU -gt 100`
- Rich cmdlets: `Get-ChildItem`, `Invoke-WebRequest`, `ConvertTo-Json`
- Cross-platform paths: `Join-Path $HOME ".config"`

### Common Equivalents

| Bash | PowerShell |
|------|------------|
| `ls -la` | `Get-ChildItem` or `ls` |
| `cat file` | `Get-Content file` or `cat file` |
| `grep pattern file` | `Select-String -Pattern pattern file` |
| `find . -name "*.py"` | `Get-ChildItem -Recurse -Filter "*.py"` |
| `echo $VAR` | `$env:VAR` or `Write-Output $env:VAR` |
| `pwd` | `Get-Location` or `pwd` |
| `cd path` | `Set-Location path` or `cd path` |

Note: Many bash aliases (ls, cat, pwd, cd) work in PowerShell for convenience.
