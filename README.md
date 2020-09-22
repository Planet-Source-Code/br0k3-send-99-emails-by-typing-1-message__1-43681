<div align="center">

## Send 99 Emails By Typing 1 Message


</div>

### Description

This Email Bomber sends the user 99 email messages. Sometimes (I don't know why) it sends more than 99. Simple cut and paste code.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Br0k3](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/br0k3.md)
**Level**          |Beginner
**User Rating**    |1.8 (24 globes from 13 users)
**Compatibility**  |VB 6\.0
**Category**       |[Internet/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-html__1-34.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/br0k3-send-99-emails-by-typing-1-message__1-43681/archive/master.zip)





### Source Code

```

Add 6 text boxes. Call them txtToEmailAddress, txtFromEmailAddress, txtFromName, txtEmailSubject, txtEmailServer, txtMessage
Add 1 label called StatusTxt
Add Winsock. Project>Components>Microsoft Winsock Control 6.0 and check the box.
And last of all add 1 command button called CmdSendMail Now just insert the code below and run your program.
Dim Response As String
Dim Start As Single, Tmr As Single
Sub SendEmail(MailServerName As String, FromName As String, FromEmailAddress As String, ToName As String, ToEmailAddress As String, EmailSubject As String, EmailBodyOfMessage As String)
Dim DateNow As String
Dim first As String, Second As String, Third As String
Dim Fourth As String, Fifth As String, Sixth As String
Dim Seventh As String
With Winsock1
 If .State = sckClosed Then ' Check to see if socket is closed
  DateNow = Format(Date, "Ddd") & ", " & Format(Date, "dd Mmm YYYY") & " " & Format(Time, "hh:mm:ss") & "" & " -0600"
  first = "mail from: " & FromEmailAddress & vbCrLf ' Get who's sending E-Mail address
  Second = "rcpt to: " & ToEmailAddress & vbCrLf ' Get who mail is going to
  Third = "Date: " & DateNow & vbCrLf ' Date when being sent
  Fourth = "From: """ & FromName & """ <" & FromEmailAddress & ">" + vbCrLf ' Who's Sending
  Fifth = "To: " & ToNametxt & vbCrLf ' Who it going to
  Sixth = "Subject: " & EmailSubject & vbCrLf ' Subject of E-Mail
  Seventh = EmailBodyOfMessage & vbCrLf ' E-mail message body
  Ninth = "X-Mailer: STMP Sender" & vbCrLf ' What program sent the e-mail, customize this
  .LocalPort = 0 ' Must set local port to 0 (Zero) or you can only send 1 e-mail per program start
  .Protocol = sckTCPProtocol ' Set protocol for sending
  .RemoteHost = MailServerName ' Set the server address
  .RemotePort = 25 ' Set the SMTP Port
  .Connect ' Start connection
  WaitFor ("220")
  StatusTxt.Caption = "Connecting...."
  .SendData ("HELO EnterComputerNameHere" & vbCrLf)
  WaitFor ("250")
  StatusTxt.Caption = "Connected"
  .SendData (first)
  StatusTxt.Caption = "Sending Message"
  WaitFor ("250")
  .SendData (Second)
  WaitFor ("250")
  .SendData ("data" & vbCrLf)
  WaitFor ("354")
  .SendData (Fourth & Third & Ninth & Fifth & Sixth & vbCrLf)
  .SendData (Seventh & vbCrLf)
  .SendData ("." & vbCrLf)
  WaitFor ("250")
  .SendData ("quit" & vbCrLf)
  StatusTxt.Caption = "Disconnecting"
  WaitFor ("221")
  .Close
 Else
  MsgBox (Str(.State))
 End If
End With
End Sub
Sub WaitFor(ResponseCode As String)
 Start = Timer ' Time event so won't get stuck in loop
 While Len(Response) = 0
  Tmr = Start - Timer
  DoEvents ' Let System keep checking for incoming response **IMPORTANT**
  If Tmr > 50 Then ' Time in seconds to wait
   MsgBox "SMTP service error, timed out while waiting for response", 64, MsgTitle
   Exit Sub
  End If
 Wend
 While Left(Response, 3) <> ResponseCode
  DoEvents
  If Tmr > 50 Then
   MsgBox "SMTP service error, impromper response code. Code should have been: " + ResponseCode + " Code recieved: " + Response, 64, MsgTitle
   Exit Sub
  End If
 Wend
 Response = "" ' Sent response code to blank **IMPORTANT**
End Sub
Private Sub CmdSendMail_Click()
 MsgBox ("Please wait while the emails are sent... This could take serveral minutes!")
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 SendEmail txtEmailServer.Text, txtFromName.Text, txtFromEmailAddress.Text, txtToEmailAddress.Text, txtToEmailAddress.Text, txtEmailSubject.Text, txtMessage.Text
 StatusTxt.Caption = "Mail Sent"
 Beep
 Close
End Sub
Private Sub Winsock1_DataArrival(ByVal bytesTotal As Long)
 Winsock1.GetData Response ' Check for incoming response *IMPORTANT*
End Sub
```

