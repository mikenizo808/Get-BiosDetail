# Get-BiosDetail
A PowerShell function for Linux to report system information from dmidecode

## Outputs

Very simple screen output by default, or see the examples to copy the resulting report (text blob) to your clipboard.


## DESCRIPTION
    Gets the the system information from the local Linux device by using `dmidecode`.
    This requires sudo access by default (i.e. you will be prompted).To run without sudo 
    see the `UseSudoElevation` parameter which is a boolean value that defaults to $true
    unless you manully set it false (i.e. -UseSudoElevation:$false).

## NOTES

    Script:       Get-BiosDetail.ps1
    Author:       Hyper Mike Labs
    Github:       site:github.com user:mikenizo808
    Requirements: Requires Linux and PowerShell.
    Tested On:    This script was tested on Ubuntu 24.04 which includes `dmidecode` by default. Many other distros should run this fine as well. 

## EXAMPLE

    #import the module if needed. Adjust path based on where you saved it.
    Import-Module ~/Scripts/Get-BiosDetail.ps1 -Force -Verbose

## EXAMPLE

    Get-BiosDetail -ReportType Memory | Out-String | Set-Clipboard

    This example gathered a report for only "Memory" and sent the information to the clipboard.

## EXAMPLE

    Get-BiosDetail -ReportType All | Out-String | Set-Clipboard

    This example gathered a report for "All" possible report types and sent the information to the clipboard.

## EXAMPLE

    #optionally start a transcript log first
    start-Transcript -Path ~/outputs-before-bios-maintenance.txt
    Get-BiosDetail -ReportType All
    Stop-Transcript

## EXAMPLE

    Get-BiosDetail -ReportType bios

## EXAMPLE

    #this example warms up sudo before running, which means you will not be prompted.
    sudo -v
    Get-BiosDetail

## EXAMPLE

    Get-BiosDetail -ReportType bios -UseSudoElevation:$false

    This example showed the syntax for systems that do not require sudo.

## EXAMPLE

    code -d "path-to-file-1" "path-to-file2"

    This example does not use the script herein, but is an example for users of
    Visual Studio Code (a.k.a. code), you can use the diff feature with `code -d`
    to compare two text files. This assumes you have saved the desired info into
    text files, for example one before your maintenance and one after.
    
