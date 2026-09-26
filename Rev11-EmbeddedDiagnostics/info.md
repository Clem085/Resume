# Rev11 Target Fit and Evidence Notes

## Target

Snap-on Diagnostics — Sr. Embedded Software Engineer, San Jose, CA, Job ID 2026-20708. User-supplied posting seeks real-time automotive diagnostic and vehicle-interface software, protocol reverse engineering, schedules/documentation/global releases, collaboration with OBD/application engineers, application validation, and competitive scan-tool analysis. Required: BSCS/BSEE/BSSE, at least three years of relevant firmware experience, fluent C/C++, real-time development, strong communication. Preferred: automotive/OBD/scan-tool experience, ST/ARM, Windows and Ethernet.

## Evidence Mapping

| Posting need | Selected evidence | Boundary |
| --- | --- | --- |
| C and real-time firmware | Bare-metal TMS320 converter control; PIC32/FreeRTOS; current embedded C; academic periodic C tasks | Linux/POSIX coursework is not an RTOS kernel or an automotive production application |
| C++ | Professional host programmer and TI flasher customization; academic cache/predictor/pipeline simulators | Distinguish host C++ tools from embedded C; no embedded C++ production runtime or unrecorded language-standard expertise claimed |
| Protocol reverse engineering | Summer 2024 RS-232 load/relay command transactions, serial captures and checksums | Test-equipment protocol work, not reverse engineering vehicle ECUs or proprietary automotive diagnostics |
| Vehicle-facing relevance | CAN/J1939 professional experience and team-built EV STM32 sensor adapter | No OBD/UDS/ISO-TP, diagnostic trouble codes, ECU service routines, or scan-tool stack claimed |
| ST / ARM | STM32G474 academic firmware; ARM Cortex-M platform; professional TI AM62 integration | ST work is academic; no sole CAN middleware/message ownership or entire-board design |
| Windows / Ethernet | Shared Windows/Linux engineering tools, Ethernet/TCP/IP troubleshooting and firmware transport | No Windows driver, native Windows GUI, Win32, or handheld product ownership claimed |
| Validation | Protocol/electrical diagnostics, corrective-action verification, IPMI interface validation, trace-driven academic tests | No vehicle certification, automotive qualification, or complete product-validation leadership claimed |
| Communication / releases | Distributed firmware-team coordination, build/flashing/validation documentation, teaching | Supporting releases is not owning global releases or project schedules |

Sources: [AEGIS](../experience/aegis-power-systems.md), [senior design](../experience/senior-design.md), [projects](../experience/personal-projects.md), [GitHub evidence](../experience/github-projects.md), [TEAM](../experience/team-industries.md), [teaching](../experience/teaching-leadership.md).

## Significant Gaps / Application Advice

1. **Three-year firmware minimum and senior scope:** Documented AEGIS work comprises May–August 2024, May–August 2025, and May 2026–present. As of September 2026 this is roughly one year of employment even counting both entire internships; not all 2024 work was firmware. TEAM internships and academic projects do not establish three years of relevant professional firmware development. This is a stretch application; do not convert calendar span or four internships into three years of firmware experience.
2. **Direct automotive diagnostics:** No established OBD/scan-tool development, vehicle-specific diagnostic application, UDS/ISO-TP implementation, ECU diagnostics, or competitive scan-tool evaluation. CAN, J1939, EV sensing, and serial reverse engineering are relevant transferable experience, not substitutes for these claims.
3. **Senior delivery ownership:** No established end-to-end project-schedule ownership, worldwide product-release accountability, or collaboration specifically with a global OBD organization. Existing documentation, Git release workflows, and distributed-team work are supporting evidence only.
4. **Degree wording:** Actual degree is B.S. Computer Engineering; the posting explicitly lists CS, EE, or SE. Keep the true degree. Employer acceptance of a related discipline is not guaranteed by this posting.
5. **C++ depth:** Strongest professional evidence is host-side development/customization plus academic systems projects. Be prepared to explain personal implementation, debugging, memory ownership, and design choices; do not claim embedded C++ or fluency beyond what can be demonstrated.
6. **Location:** Current contact location remains Murphy, NC; job is San Jose. Relocation willingness and work arrangement are unspecified. Add relocation wording only if Connor confirms it.

Potential additional evidence that would materially strengthen this application, if it exists: actual OBD/ECU/UDS/ISO-TP work, delivered vehicle-interface software, Windows application/driver ownership, automated regression-test ownership, measured real-time constraints, and personally managed schedules/releases. These are evidence questions, not skills to add speculatively.

## Attribution and Wording Decisions

- Converter control and TI serial flasher are summer 2025. Protocol reverse engineering and SCB301 CLI are summer 2024.
- Connected PIC32/TMS320 update work is supported but its exact summer remains unresolved. The combined internship heading preserves that uncertainty.
- Current VPX/IPMI, TI AM62, cross-platform tooling, and distributed engineering remain under May 2026–present.
- Senior design retains Connor's sensing, state-machine, LED, error-logging, and BQ UART work. CAN stays a general integration mention at Connor's request; no CAN middleware/message authorship.
- Do not infer FreeRTOS or ADC DMA in senior design, production vehicle deployment, or safety certification.
- All gaps belong in these notes, not in the application résumé. No new experience facts were added to the source library by tailoring this revision.
