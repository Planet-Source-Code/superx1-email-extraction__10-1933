<div align="center">

## Email Extraction


</div>

### Description

The is the first of its kind that i have seen. It extracts emails from the c:\program files directory and subdirectorys please vote for me if this is of use to you.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[sUPErX1](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/superx1.md)
**Level**          |Beginner
**User Rating**    |4.0 (20 globes from 5 users)
**Compatibility**  |VB\.NET
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__10-33.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/superx1-email-extraction__10-1933/archive/master.zip)





### Source Code

```
' This programme was created by Damien Hally
' Please if you find this programme useful Vote For Me
'
'This programme searches for emails in the programs folder and subfolders
' for emails and sxtracts them into a file on the c:\ drive called name.txt
Imports System.IO
Imports System
Imports Microsoft.VisualBasic
Imports System.Text.RegularExpressions
Module Module1
  Sub main()
    On Error Resume Next
    Dim fname As String
    Dim tx As String
    Dim dname As String
    Dim hd As New FileStream("c:\name.txt", FileMode.OpenOrCreate, FileAccess.Write)
    Dim dh As New StreamWriter(hd)
    For Each dname In Directory.GetDirectories("c:\program files")
      For Each fname In Directory.GetFiles((dname), "*.txt")
        Dim sr As New FileStream((fname), FileMode.Open, FileAccess.Read)
        Dim str As New StreamReader(sr)
        str.BaseStream.Seek(0, SeekOrigin.Begin)
        tx = str.ReadToEnd()
        Dim re As New Regex("[\w\-]+\@[\w\-]+\.\b[\S\-]+\b", RegexOptions.IgnoreCase)
        Dim m As Match = re.Match(tx)
        Do While m.Success
          dh.WriteLine(m)
          m = m.NextMatch
        Loop
        str.Close()
      Next
    Next
    dh.Close()
  End Sub
End Module
```

