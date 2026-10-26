# Machine Error Code Reference

**Document:** DOC-ERR-001 | **Machines:** HP-200, CV-310, AC-450  
**Notice:** Synthetic sample data for training use.

Error codes are machine-specific. Always identify the machine ID first. Safety procedure: SOP-001.

## HP-200 Hydraulic Press
- **E12 — Low hydraulic oil level.** Meaning: tank below minimum. Possible causes: hose/fitting leak, oil not topped up after filter change, faulty level switch. Checks: inspect sight glass and leaks; after fixing leaks, top up with ISO VG 46 to midpoint; test level switch. **Severity: Medium.**
- **E45 — Hydraulic oil overheating.** Meaning: oil above 65 °C. Possible causes: clogged cooler fins, low oil, cooling fan failure, worn pump, faulty temperature sensor. Checks: stop and let oil cool for 20 minutes; check sight glass; clean cooler and check fan; compare sensor with handheld thermometer; inspect pump if overheating persists. **Severity: High. Do not restart until oil is below 55 °C.**
- **E51 — Pressure sensor fault.** Signal outside 4–20 mA. Possible causes: loose/damaged cable, failed sensor, power supply issue. Check connector/cable and signal; replace sensor if out of range. **Severity: Medium.**
- **E63 — Safety door interlock open.** Door/light curtain interlock not closed. Check door latch, switch alignment and continuity. **Never bypass the interlock. Severity: High (safety).**
- **E77 — Pump motor overload.** Current above rating. Possible causes: blocked return filter, oil too cold/thick, pump wear, loose electrical connection. Check filter indicator, oil temperature/grade, motor current and terminals. **Severity: High.**

## CV-310 Belt Conveyor
- **E20 — Motor overcurrent.** Current above 14 A. Possible causes: jammed belt/roller, overloaded belt, gearbox damage. Stop and lock out, clear jams, check load, rollers and gearbox oil. **Severity: High.**
- **E33 — Emergency stop activated.** Find the activated pull cord/button; reset and inspect switch/cable if it recurs. **Severity: Medium.**
- **E45 — Belt misalignment (tracking fault).** Belt drift greater than 25 mm. Possible causes: uneven loading, worn/seized idler, uneven take-up tension, material build-up. Lock out under SOP-001, compare belt edge with guide marks, inspect rollers and tension bolts, adjust in small steps and run empty for 10 minutes. **Severity: Medium; continued running can damage belt edge.**
- **E52 — Proximity sensor blocked.** Dust/object, misalignment or cable fault. Clean sensor, check alignment and cable. **Severity: Low.**
- **E60 — Gearbox oil level low.** Check level glass and seals; top up with ISO VG 220. **Severity: Medium.**

## AC-450 Air Compressor
- **E08 — Low oil pressure.** Below 2.0 bar. Possible causes: low oil, clogged oil filter, failing oil pump. Check oil level, filter and gauge. **Severity: High. Stop the compressor.**
- **E39 — Air filter clogged.** Check indicator and replace filter element. **Severity: Low.**
- **E45 — High vibration.** Vibration at least 7.1 mm/s. Possible causes: loose mounting bolts, worn coupling insert, worn motor/airend bearing, coupling misalignment. Stop and lock out under SOP-001; check mounting bolt torque (85 Nm), coupling insert, bearing noise/heat; re-measure after repair and ensure below 4.5 mm/s. **Severity: High.**
- **E58 — High discharge air temperature.** Above 105 °C. Check oil level, clean cooler and clear ventilation blockage. **Severity: High.**
- **E71 — Air dryer fault.** Possible refrigerant issue or blocked condensate drain. Check power, clean drain and call supplier if refrigerant fault suspected. **Severity: Low.**
