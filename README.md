# CIP-A106 Lab 04 — Lokibot Trojan Decompilation & Controlled Debug Analysis

**Student:** Loveth Adebayo
**Course:** CIP-A106 — Malware Analysis
**Date:** 7 October 2026

---

## Overview

Static and dynamic analysis of an AutoIt-packaged Lokibot Trojan (`sample.bin`) inside an isolated Windows 10 VM with no external network connectivity.

Analysis combined Exe2Aut decompilation, Ghidra static review, x32dbg debugger observation, and memory acquisition via OllyDumpEx. Family attribution to **Lokibot** is **high confidence** based on converging evidence across decompiled, static, and memory artifacts.

---


---

## Key Findings

| Attribute | Value |
|---|---|
| Source SHA-256 | `00A91175E7D72A7FF2BCB3F09D3F2BA7BBE4045F9C4DEE5C9685C7FDF6DA622A6` |
| Decompiled `.au3` SHA-256 | `D6BBA866165DDE476D26466526F0E35DC6D72CB47C7303233D7639906C44B695` |
| Memory dump SHA-256 | `CA9854EF63799E66386586217D4AA926C61FFC848F4E725FABDF0CCA0D167D9F` |
| Source size | 1,217,024 bytes |
| Entry Point | `00FA7CDC` |
| AutoIt signature | `AU3!` confirmed |
| Anti-debug | Sample self-terminated under x32dbg |

**Capabilities confirmed (static + memory):** HTTP C2 (`HttpSendRequestW`), FTP exfiltration (`FtpPutFileW`), all 5 registry hives, Startup folder persistence, self-deletion via `cmd /c Del`.

---

## Tools Used

Exe2Aut · Ghidra 12.1.2 · x32dbg · OllyDumpEx · Process Hacker 2.39.124 · Sysinternals strings

---

## Limitations

Sample self-terminated under debugger (hardware breakpoint not observed). No live C2 traffic captured (network isolated by design). `.au3` output treated as analytical lead; capability conclusions asserted only where corroborated by Ghidra and memory evidence.

---

## Safety Note

All analysis performed inside an isolated VM (Host-Only network, clipboard and drag-drop disabled, shared folders removed during execution). **No live malware included**; memory dump retained for grading only — do not redistribute.

---

## Academic Integrity

All observations traceable to evidence artifacts. Hypotheses clearly labelled. No bypass code developed or applied.
