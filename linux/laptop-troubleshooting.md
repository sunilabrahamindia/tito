# Linux laptop troubleshooting notes

**Date:** 20 November 2026

These notes record the troubleshooting work carried out on the HP laptop. The purpose is to keep a dated technical history of the symptoms, tests, changes and findings, so that future investigations can continue from the available evidence rather than repeat earlier work.

This is an ongoing record. New investigations should be added as dated entries, and confirmed findings should be kept separate from possible explanations.

## Laptop details

The laptop used during these investigations was recorded as:

- **Model:** HP 15s-eq2xxx
- **Operating system:** Ubuntu 24.04
- **RAM:** 8 GB
- **Storage:** Samsung 512 GB NVMe SSD
- **Graphics:** AMD Lucienne
- **Wi-Fi:** Realtek RTL8821CE

These details should be checked again if the hardware or operating system configuration changes.

## Problem history

The reported problems included intermittent system freezes, unexpected shutdowns or restarts, kernel panics and occasions when the laptop failed to detect the boot drive.

Errors seen during the troubleshooting history included:

- `Attempted to kill init`
- HP boot error `3F0`
- `No hard drive installed`

The problems were not conclusively attributed to one cause. The investigations covered both hardware and Ubuntu software/driver behaviour.

## Tests and hardware checks

The following results were recorded during earlier troubleshooting:

| Check | Recorded result |
|---|---|
| SSD SMART health | PASSED |
| SSD media/data integrity errors | 0 |
| SSD error log errors | 0 |
| HP Memory Quick Test | PASSED |
| HP SSD Quick Test | PASSED |
| HP SSD Long DST | PASSED |

An earlier SSD health check reported approximately 3% life used and a temperature of 36°C at the time of that check.

Passing these tests did not rule out an intermittent physical connection problem. A drive can pass its health tests while its connection is unreliable.

## Physical inspection

A diagnostic centre identified a loose NVMe/SSD connection inside the laptop.

This is an important finding because an intermittent connection could explain occasions when the SSD was not detected by the firmware or operating system, including the reported `3F0` and `No hard drive installed` messages.

The precise repair or reseating work carried out at the centre, and whether the connection has remained stable since then, should be recorded when confirmed.

## BIOS, firmware and kernel work

The recorded BIOS version was **F.34**, dated **29 July 2024**.

Firmware and Ubuntu kernel/firmware updates were part of the troubleshooting work. The exact package versions, update dates and any BIOS changes should be added when the relevant system records are available. Do not assume that an update fixed the underlying problem unless this is supported by subsequent observations.

## Ubuntu logs and driver investigation

### Realtek Wi-Fi messages

During the November 2026 investigation, Ubuntu logs showed recurring messages associated with the Realtek RTL8821CE Wi-Fi driver, including:

```text
rtw88_8821ce: firmware failed to leave lps state
unhandled firmware c2h interrupt
```

These messages indicate a problem involving communication between the Wi-Fi driver and its firmware. They are worth tracking, but the investigation did not establish that they caused the complete system freezes or kernel panics.

### Boot history

The command below was used to inspect the recorded boot history:

```bash
journalctl --list-boots
```

The output examined on 19 November 2026 showed nine recorded boots for that date.

### Kernel panic

The error `Attempted to kill init` was also part of the reported kernel-panic history. Its root cause was not established by the log review described here.

The logs examined at that stage did not establish corresponding NVMe I/O errors, AMD graphics errors, memory errors or machine-check exceptions. This is limited to the logs reviewed; it is not proof that those components can never be involved.

## Findings so far

| Area | What is known |
|---|---|
| SSD health | Earlier SMART and HP SSD tests passed. |
| SSD connection | A diagnostic centre identified a loose NVMe/SSD connection. |
| RAM | HP Memory Quick Test passed. |
| BIOS/firmware | BIOS version F.34 was recorded; firmware and Ubuntu kernel/firmware updates were performed. |
| Realtek Wi-Fi | Recurring driver/firmware messages were found in November logs. Their relationship to the freezes is unconfirmed. |
| Kernel panics | `Attempted to kill init` was reported; its cause remains unresolved. |
| AMD graphics | No specific fault was established in the logs reviewed. |

## Current assessment

There is evidence of a physical NVMe connection issue identified during inspection, as well as a separate, unresolved investigation into Ubuntu kernel and Realtek Wi-Fi driver messages.

It would be premature to attribute every freeze, restart or kernel panic to either one of these findings. Further observations and logs are needed to establish whether the problems share a cause or are separate issues.

## Troubleshooting timeline

### 20 November 2026

This entry consolidates earlier hardware checks, the physical inspection finding and the Ubuntu log investigation into one starting record for future troubleshooting. Some of the underlying tests and events took place before this date; the date here marks when this record was created, not when every test was performed.

### Future entries

For each new investigation, record:

- Date and approximate time.
- Symptom observed, including whether the laptop froze, restarted or failed to boot.
- Command or diagnostic test used.
- Relevant output or exact error message.
- Any change made to the system.
- Whether the issue occurred again after the change.

Keep the original output where practical. Distinguish a test result from an interpretation, and mark anything not yet verified as unconfirmed.
