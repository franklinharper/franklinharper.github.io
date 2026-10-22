---
layout: post
title: 'Create a PDF file for each Excel Worksheet'
---

Sometimes it's nececessary to generate a separate PDF file for each worksheet within an Excel workbook. This can be a big waste of time; especially if there are many sheets and/or you have to regenerate the PDFs every time the content changes!

If you are using Microsoft Office 2007 or later, the following VBA macro automates the process. The Fname variable can be used to customize the PDF file names that are generated. 

    Option Explicit
 
    Sub createPDFfiles()
        Dim ws As Worksheet
        Dim Fname As String
        For Each ws In ActiveWorkbook.Worksheets
            On Error Resume Next 'Continue if an error occurs

            ' Name PDF files based on the worksheet Index (e.g Annex 1.1.1, Annex 1.1.2, etc.)
            Fname = "Annex 1.1." & ws.Index & "_result"

            ' If you want to name the PDF files differently just change the Fname variable above to
            ' whatever you like. For example if you changed Fname to:
            '
            '  Fname =  “C:\myFolder\pdfs\” & ActiveWorkbook.Name & "-" & ws.Name
            '
            '  The files would be stored in C:\myFolder\pdfs, and named using the
            ' spreadsheet file name and the worksheet name.
            ' 
            ' WARNING: Using worksheet names may cause errors if the  names contain characters that Windows
            ' does not accept in file names. See below for a list of characters that you need to avoid.
            '
            ws.ExportAsFixedFormat _
                Type:=xlTypePDF, _
                Filename:=Fname, _
                Quality:=xlQualityStandard, _
                IncludeDocProperties:=True, _
                IgnorePrintAreas:=False
        Next ws
    End Sub

The following characters are not allowed in Windows file names, they will cause the macro to fail if you use them:

    < (less than)
    > (greater than)
    : (colon)
    ” (double quote)
    / (forward slash)
    \ (backslash)
    | (vertical bar or pipe)
    ? (question mark)
    * (asterisk)
