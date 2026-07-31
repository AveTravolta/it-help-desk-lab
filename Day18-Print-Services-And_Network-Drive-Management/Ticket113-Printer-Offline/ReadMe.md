🎫 Ticket #113 — Printer Offline

## Issue
User reported they were unable to print. Printer appeared unavailable.

## Investigation
    • Verified HR-Printer existed on DC01
    • Checked printer status through Print Management
    • Verified Print Spooler service was running
    • Found printer was paused on the print server
    
## Root Cause
Printer was manually paused, preventing print jobs from processing.

## Resolution
Resumed printing on HR-Printer through Print Management.

## Verification
    • Confirmed printer returned to an available state
    • Verified client could access HR-Printer
    • Confirmed print queue was functional
