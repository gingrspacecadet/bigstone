# 🔌 Component Port Standards

Bigstone components communicate using standardized I/O ports. These ports follow strict naming conventions to ensure clarity, compatibility, and automation across the ecosystem.

## 📦 Port Naming Convention

All ports must be named using the following format:

```

\[Port Type]–\[Direction]–\[Label]

```

### 🔠 Segments

| Segment      | Description                              | Example             |
|--------------|------------------------------------------|---------------------|
| `STP`        | **Standard Transfer Port** (binary)      | `STP-O-CLK`         |
| `DTP`        | **Data Transfer Port** (hexadecimal)     | `DTP-I-ADDR`        |
| `I` / `O`    | **Direction**: Input or Output           | `STP-I-1`, `DTP-O-DATA` |
| `Label`      | **Label or index** (numeric or semantic) | `1`, `DATA`, `READY` |

> Example: `STP-I-CLK` = a **Standard (binary) input port** for the **clock signal**.

### 🔁 Port Type Definitions

| Port Type | Full Name               | Signal Type   | Typical Use                |
|-----------|-------------------------|---------------|----------------------------|
| `STP`     | Standard Transfer Port  | Binary (0/1)  | Control lines, toggles     |
| `DTP`     | Data Transfer Port      | Hex (0–F)     | Address buses, data lanes  |

Each component must define all active ports in its documentation using this naming scheme.

---

## 🎛️ Port Layout Guidelines

- **All ports must connect via the 16×16×16 grid interface** using clearly marked dust or interface blocks.
- **Inputs and outputs must be consistently placed** according to Bigstone's wiring standards:
  - **Inputs** typically enter from the north or west.
  - **Outputs** typically exit to the south or east.
- **Bidirectional connections** (if any) must use separate STP-I and STP-O ports.

---

## 📘 Example: Clocked Register

| Port Name     | Type | Direction | Description            |
|---------------|------|-----------|------------------------|
| `STP-I-CLK`   | STP  | Input     | Clock signal           |
| `STP-I-WE`    | STP  | Input     | Write enable           |
| `DTP-I-DATA`  | DTP  | Input     | 4-bit data input       |
| `DTP-O-Q`     | DTP  | Output    | 4-bit stored output    |

This register accepts clocked binary control signals and hexadecimal data input/output.

---

## 🔧 Notes

- Port names are **case-sensitive**.
- If a port is not used in a given component variation, it should be clearly marked as **unused** in documentation.
- Avoid ambiguous labels like `STP-I-X` unless `X` is defined elsewhere in the system.