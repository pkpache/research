# Research

A working library of historical DOS specifications and references useful for implementing and studying **memory managers**, **DOS extenders**, and **DPMI hosts**.

The documents under [`docs/dos/`](docs/dos/) cover the classic interfaces that 386+ DOS environments glue together: EMS/XMS memory services, VCPI and DPMI protected-mode entry, DMA virtualization (VDS), vendor memory-manager APIs, and related OpenDOS/DR-DOS protected-mode and multitasking material.

These are archival copies of public-era specs and manuals (or faithful transcriptions). Prefer the PDF when both a PDF and text extract exist; the `.txt` / `.doc` copies are kept for grepping and diffing.

## Documents

| Document | Description |
| --- | --- |
| [DPMI 0.9](docs/dos/dpmispec09.txt) ([PDF](docs/dos/dpmispec09.pdf)) | DOS Protected Mode Interface specification version 0.9 — the widely implemented Int 31h host/client API for protected-mode DOS programs (descriptor, memory, interrupt, and mode-switch services). |
| [DPMI 1.0](docs/dos/dpmispec10.txt) ([PDF](docs/dos/dpmispec10.pdf)) | DPMI specification version 1.0 (March 1991) — extends 0.9 with additional host services (shared memory, improved exception handling, and related 1.0-only calls). Rarely fully implemented by commercial hosts. |
| [MS-DOS API Extensions for DPMI Hosts 0.04](docs/dos/msdos_dpmi_extensions_0.04.txt) ([PDF](docs/dos/msdos_dpmi_extensions_0.04.pdf)) | Microsoft pre-release 0.04 describing how DPMI hosts (notably Windows Enhanced Mode) expose protected-mode DOS/BIOS interrupt reflection and a small “MS-DOS” extension entry point. |
| [MS-DOS API Extensions for DPMI Hosts 0.02](docs/dos/msdos_dpmi_extensions_0.02.txt) | Earlier October 1990 draft of the same MS-DOS-in-protected-mode extensions document. |
| [VCPI 1.0](docs/dos/vcpi.doc) | Virtual Control Program Interface — lets DOS extenders run in protected mode under a VCPI-capable 386 EMS/memory manager (the pre-DPMI industry interface). |
| [XMS 2.0](docs/dos/xms20.txt) | eXtended Memory Specification 2.0 — HMA, A20 control, and extended-memory block allocate/move/lock services for real-mode DOS. |
| [XMS 3.0](docs/dos/xms30.txt) | XMS 3.0 — adds large free/total query and related 3.x functions (up to 4 GB class machines); UMB calls remain optional. |
| [XMS 3.5 / 3.51](docs/dos/xms35.txt) | Informal super-extended XMS notes (beyond 4 GB): query/allocate/lock/move extensions used by some modern DOS memory managers. |
| [HIMEM notes](docs/dos/himem.txt) | Short Microsoft notes on `HIMEM.SYS` as an XMS 2.0 provider and how it interacts with other extended-memory users. |
| [LIM EMS 3.2](docs/dos/limems32.txt) | Lotus/Intel/Microsoft Expanded Memory Specification 3.2 — classic bank-switched EMS via a page frame and Int 67h. |
| [LIM EMS 4.0](docs/dos/limems40.txt) | EMS 4.0 — larger capacity and richer mapping/OS features that absorbed much of the earlier EEMS work. |
| [EMS 4.0 vs EMS/EEMS 3.2](docs/dos/ems_vs_eems.txt) | Stephen Satchell’s comparison of EMS 4.0 against EMS 3.2 and AST/Quadram/Ashton-Tate EEMS 3.2. |
| [VDS](docs/dos/vds.txt) | Virtual DMA Services (Microsoft PW0519) — API for DMA-using drivers under memory managers / Windows Enhanced Mode that remaps physical pages. |
| [QPI](docs/dos/qpi.txt) | Ralf Brown / Dr. Dobb’s write-up of QEMM-386’s undocumented QPI programming interface (memory maps and related manager services). |
| [DPMS (OpenDOS)](docs/dos/dpms_opendos.pdf) | Caldera OpenDOS DPMS 1.0 API guide — DOS Protected Mode Services for relocating drivers/TSRs into extended memory while leaving a small real-mode stub. |
| [Multitasking API (OpenDOS)](docs/dos/multitask_opendos.pdf) | Caldera DR-DOS/OpenDOS Multitasking API guide — modules and `X_*` / `Z_*` services of the 386 multitasking core used with `EMM386 /MULTI` and Task Manager. |
| [PC DOS 7 Technical Update](docs/dos/pc_dos7_technical_update.pdf) | IBM GG24-4459 PC DOS 7 programmer-oriented technical update, including Appendix E on DPMS and Appendix F on task-swapping. |

## Open-source projects

Popular projects used in FreeDOS / SvarDOS and related communities. Links point at the primary source repository when one exists.

Typical FreeDOS-style stack: an **XMM** (HimemSX or XMGR, or JemmEx alone) → optional **EMM/VCPI** (Jemm) → a **DPMI host** when needed (CWSDPMI, HDPMI, or DPMIONE). DOS extenders such as DOS/32A or HX may supply their own DPMI server instead of a separate host TSR.

| Project | Role | Repository |
| --- | --- | --- |
| [XMGR](https://gitlab.com/FreeDOS/drivers/xmgr) | Compact XMS 3.0 manager (up to ~4 GB); works with UMBPCI / Jemm | [FreeDOS/drivers/xmgr](https://gitlab.com/FreeDOS/drivers/xmgr) |
| [Jemm](https://github.com/Baron-von-Riedesel/Jemm) | EMM / V86 monitor: EMS, UMBs, VCPI, VDS (`Jemm386` needs an XMM; `JemmEx` embeds one) | [Baron-von-Riedesel/Jemm](https://github.com/Baron-von-Riedesel/Jemm) |
| [FreeDOS EMM386](https://github.com/FDOS/emm386) | FreeDOS packaging / mirror of Jemm (upstream is Baron-von-Riedesel/Jemm) | [FDOS/emm386](https://github.com/FDOS/emm386) |
| [HimemSX](https://github.com/Baron-von-Riedesel/HimemSX) | XMS host (XMM), HimemX fork with XMS 3.5 super-extended memory (beyond 4 GB, up to ~1 TB); often paired with Jemm386 | [Baron-von-Riedesel/HimemSX](https://github.com/Baron-von-Riedesel/HimemSX) |
| [386MAX](https://github.com/sudleyplace/386MAX) | Qualitas 386 memory manager (XMS/EMS/VCPI, GEMMIS); source release by the DPMIONE author | [sudleyplace/386MAX](https://github.com/sudleyplace/386MAX) |
| [Open386MAX](https://github.com/geosone/Open386MAX) | Active fork of 386MAX: Linux/open-toolchain rebuild, modern fixes, QPI / XMS 3.5 / DPMI work | [geosone/Open386MAX](https://github.com/geosone/Open386MAX) |
| [CWSDPMI](https://github.com/jayschwa/cwsdpmi) | Classic free DPMI 0.9 host used with DJGPP (unofficial git mirror) | [jayschwa/cwsdpmi](https://github.com/jayschwa/cwsdpmi) · [upstream site](https://sandmann.dotster.com/cwsdpmi/) |
| [HDPMI](https://github.com/Baron-von-Riedesel/HX) | Standalone DPMI 0.9 host with many 1.0 features (`HDPMI16` / `HDPMI32`); part of HX | [Baron-von-Riedesel/HX](https://github.com/Baron-von-Riedesel/HX) |
| [DPMIONE](https://github.com/sudleyplace/DPMIONE) | Standalone DPMI **1.0** host (from the 386MAX lineage) | [sudleyplace/DPMIONE](https://github.com/sudleyplace/DPMIONE) |
| [DOS/32A](https://github.com/amindlost/dos32a) | Open DOS/4GW-compatible extender with built-in DPMI 0.9 server | [amindlost/dos32a](https://github.com/amindlost/dos32a) |
| [HX DOS Extender](https://github.com/Baron-von-Riedesel/HX) | Win32 PE-on-DOS runtime built on HDPMI | [Baron-von-Riedesel/HX](https://github.com/Baron-von-Riedesel/HX) |