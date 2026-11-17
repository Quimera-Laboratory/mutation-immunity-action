# Quimera Kinetic Mutation Immunity (1.58-Bit AI)

Sub-10s AI-powered Semantic Mutation Testing directly in GitHub Actions using **Q-KineQuant 1.58-Bit** Fisher-guided SLMs, **Tree-sitter** AST algebraic invariants, **Zygote Copy-on-Write** parallel swarms, and **Closed-Loop RL Homeostasis** — zero GPU required.

## Quick Start

```yaml
name: Quimera Mutation Guard

on:
  pull_request:
  push:
    branches: [main]

permissions:
  contents: read
  security-events: write
  pull-requests: write

jobs:
  mutation-immunity:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Quimera Kinetic Mutation Immunity
        id: quimera
        uses: Quimera-Laboratory/mutation-immunity-action@v1
        with:
          target: 'src/'
          probe: 'quimera-sonda-rust'
          max-mutants: 256
          app-code: 'APP-LEDGER-01'
          license-key: ${{ secrets.QUIMERA_LICENSE_KEY }}

      - name: Check Outputs
        run: |
          echo "Immunity Score: ${{ steps.quimera.outputs.immunity-score }}%"
          echo "Surviving Mutants: ${{ steps.quimera.outputs.surviving-mutants }}"
          echo "License Tier: ${{ steps.quimera.outputs.license-tier }}"
```

## Commercial Licensing (Fail-Closed)

Execution requires a valid `QUIMERA_LICENSE_KEY` issued for your exact:
- **GitHub Organization** (`GITHUB_REPOSITORY_OWNER`)
- **Repository** (`GITHUB_REPOSITORY`)
- **Application Code** (`app-code`)

| Tier | Max Mutants | Parallelism | Features |
| :--- | :--- | :--- | :--- |
| **Pro** | Up to `128` | Zygote CoW (`all cores`) | Encrypted `.kineq` In-RAM, SARIF 2.1.0, PR Auto-Comment |
| **Enterprise** | Up to `1024` | Zygote CoW + AVX2/VNNI | Full Q128/Schreier/Euclidean Orbits, Closed-Loop RL Homeostasis |

## Inputs

| Input | Required | Default | Description |
| :--- | :--- | :--- | :--- |
| `app-code` | **Yes** | — | Application identifier bound to your license |
| `license-key` | **Yes** | — | Commercial `QUIMERA_LICENSE_KEY` secret |
| `target` | No | `src/` | Target source file or directory |
| `probe` | No | `quimera-sonda-rust` | Language probe extension (`quimera-sonda-*`) |
| `max-mutants` | No | `128` | Maximum mutants per run |
| `timeout-ms` | No | `50` | Watchdog timeout per mutant (ms) |
| `engine-version` | No | `v1.0.0` | Pre-built engine release version |
| `upload-sarif` | No | `true` | Upload SARIF 2.1.0 to GitHub Code Scanning |

## Outputs

| Output | Description |
| :--- | :--- |
| `immunity-score` | Kinetic Mutation Immunity score (`0.00` to `100.00`) |
| `surviving-mutants` | Count of surviving mutants (blind spots) |
| `sarif-path` | Path to generated SARIF 2.1.0 file |
| `license-tier` | Validated commercial tier (`pro` or `enterprise`) |
