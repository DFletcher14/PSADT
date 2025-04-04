# Invoke-TaskSequence PowerShell Function

A custom PowerShell function that triggers a specific **SCCM Task Sequence** programmatically by interacting with WMI. This is best used with the likes of PSADT where you want to run an available task sequence from a deadline set in your Deploy-Application script.

---

## Features

- Finds and triggers a Task Sequence by name
- Modifies WMI policy to allow rerunning the sequence
- Sets the Task Sequence as mandatory (if required)
- Supports optional verbose logging
- Returns `$true` on success or `$false` if errors occur

---

## Requirements

- PowerShell (tested on Windows PowerShell 5.1)
- SCCM client installed and functioning
- Administrative privileges
- `Write-Log` function defined elsewhere in your script/module

---

## Usage

**Powershell**
`Invoke-TaskSequence -TaskSequenceName "Your TaskSequence Name Here"`

**With Verbose Logging**
`Invoke-TaskSequence -TaskSequenceName "Your TaskSequence Name Here" -VerboseLogging`

## Parameters
Name              	Type	    Required      	Description
TaskSequenceName	  String	  ✅	            The display name of the SCCM Task Sequence
VerboseLogging	    Switch	  ❌	            Enables detailed log output via Write-Log

## Example Output (Verbose)

`Found Task Sequence: PS100123 / AD100321
ScheduleID Found: {00000000-0000-0000-0000-000000000123}
RepeatRunBehavior set to RerunAlways
MandatoryAssignments are set to True
Task Sequence triggered successfully.`

## Notes
This function modifies WMI policy objects, so use with caution and always test before use in production.

This function requires a custom Write-Log function to handle logging.

## Author
Created by Dfletcher14


