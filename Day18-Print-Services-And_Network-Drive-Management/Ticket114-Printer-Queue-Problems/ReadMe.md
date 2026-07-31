## Ticket #114 – Print Queue Problems

### Issue

User states “My Document is stuck printing.”

## Investigation 
- Verified HR-Printer was available 
- Opened print queue through Print Management 
- Identified stuck print job 
- Confirmed printer was paused and preventing job completion 

## Root Cause 
-A stuck print job was preventing normal queue processing. 

## Resolution 
- Removed stuck print job from the print queue 
- Resumed printer operation 

## Verification 
- Confirmed queue was empty 
- Verified HR-Printer returned to Ready status 
- Confirmed new print jobs could be submitted 
