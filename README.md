; ---- Déclaration et Includes ----
#NoTrayIcon
#include <Misc.au3>
#include <ButtonConstants.au3>
#include <EditConstants.au3>
#include <GUIConstantsEx.au3>
#include <TabConstants.au3>
#include <WindowsConstants.au3>
#include <File.au3>
#include <Date.au3>

; ---- GUI ----
$Form1 = GUICreate("WizzTools", 346, 266, 100, 70)
$Tab1 = GUICtrlCreateTab(8, 8, 329, 249)

; ---- Tab 1 (Switcher) ----
$TabSheet1 = GUICtrlCreateTabItem("Switcher")
$Button1 = GUICtrlCreateButton("Choisir F1", 20, 69, 75, 25)
$Button2 = GUICtrlCreateButton("Choisir F2", 20, 101, 75, 25)
$Button3 = GUICtrlCreateButton("Choisir F3", 20, 133, 75, 25)
$Button4 = GUICtrlCreateButton("Choisir F4", 20, 165, 75, 25)
$Button5 = GUICtrlCreateButton("Choisir F5", 100, 69, 75, 25)
$Button6 = GUICtrlCreateButton("Choisir F6", 100, 101, 75, 25)
$Button7 = GUICtrlCreateButton("Choisir F7", 100, 133, 75, 25)
$Button8 = GUICtrlCreateButton("Choisir F8", 100, 165, 75, 25)
$ButtonHide = GUICtrlCreateButton("Minimiser", 195, 220, 121, 25)
$Edit1 = GUICtrlCreateEdit("", 195, 50, 121, 161, BitOR($ES_AUTOVSCROLL, $ES_MULTILINE, $ES_WANTRETURN, $ES_READONLY))
GUiCtrlSetState(-1, $GUI_DISABLE)

; ---- Tab 2 (Raccourci) ----
$TabSheet2 = GUICtrlCreateTabItem("Raccourci")
$Group1 = GUICtrlCreateGroup("Fichier à Charger", 24, 40, 121, 89)
$Input1 = GUICtrlCreateInput("Default", 32, 64, 105, 22)
$Button10 = GUICtrlCreateButton("Charger", 48, 96, 75, 25)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$Edit2 = GUICtrlCreateEdit("", 208, 48, 105, 161, BitOR($ES_AUTOVSCROLL, $ES_MULTILINE, $ES_WANTRETURN, $ES_READONLY))
GUiCtrlSetState(-1, $GUI_DISABLE)
$Group2 = GUICtrlCreateGroup("Assigner", 24, 136, 169, 105)
$Button11 = GUICtrlCreateButton("A", 32, 160, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button12 = GUICtrlCreateButton("Z", 32, 184, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button13 = GUICtrlCreateButton("E", 32, 208, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button14 = GUICtrlCreateButton("R", 72, 160, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button15 = GUICtrlCreateButton("T", 72, 184, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button16 = GUICtrlCreateButton("Y", 72, 208, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button17 = GUICtrlCreateButton("U", 112, 160, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button18 = GUICtrlCreateButton("I", 112, 184, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button19 = GUICtrlCreateButton("O", 112, 208, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
$Button20 = GUICtrlCreateButton("P", 152, 184, 35, 17)
GUiCtrlSetState(-1, $GUI_DISABLE)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$Button9 = GUICtrlCreateButton("Help", 208, 216, 107, 25)

; ---- Tab 3 (Autres) ----
$TabSheet3 = GUICtrlCreateTabItem("Autres")
$Edit3 = GUICtrlCreateEdit("", 24, 40, 209, 201, BitOR($ES_AUTOVSCROLL, $ES_MULTILINE, $ES_WANTRETURN, $ES_READONLY))
GUiCtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetData(-1, "")
GUICtrlSetFont(-1, 7)
$Button21 = GUICtrlCreateButton("Clear", 248, 48, 75, 25)
$Button22 = GUICtrlCreateButton("Save", 244, 208, 75, 25)


GUICtrlCreateTabItem("")
GUISetState(@SW_SHOW)


; ---- Variables ----
Global $Handle1, $Handle2, $Handle3, $Handle4, $Handle5, $Handle6, $Handle7, $Handle8
Global $para1, $para2, $para3, $para4
Global $Hide = 0
Global $lock = 0
Global $data[3]
Global $Path = GUICtrlRead($Input1)

; ---- PreConfig ----
HotKeySet("{F9}", "HideH")
GUICtrlSetData($Edit1, "Console du Switcher :" & @CRLF, 1)
GUICtrlSetData($Edit2, "Console des Raccourcis :" & @CRLF, 1)
_Journal3("Lancement du Tools")

; ---- Boucle Principal ----
While 1
	$nMsg = GUIGetMsg()
	Switch $nMsg
		Case $GUI_EVENT_CLOSE
			_Journal3("Fermeture")
			Exit
		Case $Button1
			GUICtrlSetData($Edit1, "MultiCompte 1 :" & @CRLF, 1)
			MultiCompte("$Handle1", "{F1}")
			_Journal3("Touche F1 = " & $Handle1)
		Case $Button2
			GUICtrlSetData($Edit1, "MultiCompte 2 :" & @CRLF, 1)
			MultiCompte("$Handle2", "{F2}")
			_Journal3("Touche F2 = " & $Handle2)
		Case $Button3
			GUICtrlSetData($Edit1, "MultiCompte 3 :" & @CRLF, 1)
			MultiCompte("$Handle3", "{F3}")
			_Journal3("Touche F3 = " & $Handle3)
		Case $Button4
			GUICtrlSetData($Edit1, "MultiCompte 4 :" & @CRLF, 1)
			MultiCompte("$Handle4", "{F4}")
			_Journal3("Touche F4 = " & $Handle4)
		Case $Button5
			GUICtrlSetData($Edit1, "MultiCompte 5 :" & @CRLF, 1)
			MultiCompte("$Handle5", "{F5}")
			_Journal3("Touche F5 = " & $Handle5)
		Case $Button6
			GUICtrlSetData($Edit1, "MultiCompte 6 :" & @CRLF, 1)
			MultiCompte("$Handle6", "{F6}")
			_Journal3("Touche F6 = " & $Handle6)
		Case $Button7
			GUICtrlSetData($Edit1, "MultiCompte 7 :" & @CRLF, 1)
			MultiCompte("$Handle7", "{F7}")
			_Journal3("Touche F7 = " & $Handle7)
		Case $Button8
			GUICtrlSetData($Edit1, "MultiCompte 8 :" & @CRLF, 1)
			MultiCompte("$Handle8", "{F8}")
			_Journal3("Touche F8 = " & $Handle8)
		Case $ButtonHide
			MsgBox(0, "WizzTools", "Appuyez sur F9 pour Cacher/Montrer la fenêtre")

		Case $Button10
			Charger()
		Case $Button11
			AssiLock("1", "A")
		Case $Button12
			AssiLock("2", "Z")
		Case $Button13
			AssiLock("3", "E")
		Case $Button14
			AssiLock("4", "R")
		Case $Button15
			AssiLock("5", "T")
		Case $Button16
			AssiLock("6", "Y")
		Case $Button17
			AssiLock("7", "U")
		Case $Button18
			AssiLock("8", "I")
		Case $Button19
			AssiLock("9", "O")
		Case $Button20
			AssiLock("10", "P")
		Case $Button9
			Help()

		Case $Button21
			Guictrlsetdata($Edit3,"")
		Case $Button22
			Save()
			_Journal3('Console enregistré dans "Log.txt"')

	EndSwitch
	If $lock = 1 Then
		ModeLock()
	EndIf
WEnd


; ---- Fonction Tab1 ----
Func MultiCompte($para1,$para2)
	ToolTip("Cliquez sur votre fênetre pour la mettre au premier plan, puis, appuyez sur C", 0, 0)
	While 1
		If _IsPressed("43") Then
			Tooltip("")
			$GetHandle = WinGetHandle("")
			GUICtrlSetData($Edit1, "Handle : " & $GetHandle & @CRLF, 1)
			ToolTip($GetHandle,0,0)
			Sleep(1000)
			ToolTip("")
			HotKeySet($para2, "Start")
				If $para1 = "$Handle1" Then
					$Handle1 = $GetHandle
				ElseIf $para1 = "$Handle2" Then
					$Handle2 = $GetHandle
				ElseIf $para1 = "$Handle3" Then
					$Handle3 = $GetHandle
				ElseIf $para1 = "$Handle4" Then
					$Handle4 = $GetHandle
				ElseIf $para1 = "$Handle5" Then
					$Handle5 = $GetHandle
				ElseIf $para1 = "$Handle6" Then
					$Handle6 = $GetHandle
				ElseIf $para1 = "$Handle7" Then
					$Handle7 = $GetHandle
				ElseIf $para1 = "$Handle8" Then
					$Handle8 = $GetHandle
				EndIf
		Return
		EndIf
	WEnd
EndFunc

Func Start()
	$SaveClip = ClipGet()

switch @HotKeyPressed
  Case "{F1}"
	WinActivate($Handle1)
	_Journal3("F1 Pressé")
  Case "{F2}"
	WinActivate($Handle2)
	_Journal3("F2 Pressé")
  Case "{F3}"
	WinActivate($Handle3)
	_Journal3("F3 Pressé")
  Case "{F4}"
	WinActivate($Handle4)
	_Journal3("F4 Pressé")
  Case "{F5}"
	WinActivate($Handle5)
	_Journal3("F5 Pressé")
  Case "{F6}"
	WinActivate($Handle6)
	_Journal3("F6 Pressé")
  Case "{F7}"
	WinActivate($Handle7)
	_Journal3("F7 Pressé")
  Case "{F8}"
	WinActivate($Handle8)
	_Journal3("F8 Pressé")
EndSwitch
EndFunc

Func HideH()
	If $Hide = 0 Then
	GUISetState(@SW_HIDE, $Form1)
	_Journal3("GUI Caché (F9)")
	$Hide = 1
	Else
	GUISetState(@SW_SHOW, $Form1)
	_Journal3("GUI Montrée (F9)")
	$Hide = 0
	EndIf
EndFunc

; ---- Fonctions Tab2 ----
Func Charger()
	Global $Path = GUICtrlRead($Input1)
	FileOpen($Path)
	$Read = FileRead($Path, 100)
	_Journal3("Fichier " & $Path & " chargé")
	If $Read > 0 Then
		GUICtrlSetData($Edit2, $Read & @CRLF, 1)
		GUiCtrlSetState($Button10, $GUI_DISABLE)
		GUiCtrlSetState($Input1, $GUI_DISABLE)
		GUiCtrlSetState($Button11, $GUI_ENABLE)
		GUiCtrlSetState($Button12, $GUI_ENABLE)
		GUiCtrlSetState($Button13, $GUI_ENABLE)
		GUiCtrlSetState($Button14, $GUI_ENABLE)
		GUiCtrlSetState($Button15, $GUI_ENABLE)
		GUiCtrlSetState($Button16, $GUI_ENABLE)
		GUiCtrlSetState($Button17, $GUI_ENABLE)
		GUiCtrlSetState($Button18, $GUI_ENABLE)
		GUiCtrlSetState($Button19, $GUI_ENABLE)
		GUiCtrlSetState($Button20, $GUI_ENABLE)

	Else
		GUICtrlSetData($Edit2, "Fichier "& $Path & " est vide ou Inexistant.." & @CRLF, 1)
		GUICtrlSetData($Edit2, "Vous pouvez maintenant Assigner les touches!" & @CRLF, 1)
		FileDelete($Path)
		_FileCreate($Path)
		GUiCtrlSetState($Button10, $GUI_DISABLE)
		GUiCtrlSetState($Input1, $GUI_DISABLE)
		GUiCtrlSetState($Button11, $GUI_ENABLE)
		GUiCtrlSetState($Button12, $GUI_ENABLE)
		GUiCtrlSetState($Button13, $GUI_ENABLE)
		GUiCtrlSetState($Button14, $GUI_ENABLE)
		GUiCtrlSetState($Button15, $GUI_ENABLE)
		GUiCtrlSetState($Button16, $GUI_ENABLE)
		GUiCtrlSetState($Button17, $GUI_ENABLE)
		GUiCtrlSetState($Button18, $GUI_ENABLE)
		GUiCtrlSetState($Button19, $GUI_ENABLE)
		GUiCtrlSetState($Button20, $GUI_ENABLE)
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
		FileWriteLine($Path, " ")
	EndIf
	FileClose($Path)
	HotKeySet("²", "LockR")
EndFunc

Func ModeLock()
	If _IsPressed("41") Then
		ModeLock2("1")
	ElseIf _IsPressed("5A") Then
		ModeLock2("2")
	ElseIf _IsPressed("45") Then
		ModeLock2("3")
	ElseIf _IsPressed("52") Then
		ModeLock2("4")
	ElseIf _IsPressed("54") Then
		ModeLock2("5")
	ElseIf _IsPressed("59") Then
		ModeLock2("6")
	ElseIf _IsPressed("55") Then
		ModeLock2("7")
	ElseIf _IsPressed("49") Then
		ModeLock2("8")
	ElseIf _IsPressed("4F") Then
		ModeLock2("9")
	ElseIf _IsPressed("50") Then
		ModeLock2("10")
	EndIf
EndFunc

Func ModeLock2($ParL1)
	FileOpen($Path)
	$data = FileReadLine($Path, $ParL1)
		If $data >0 Then
			$data = StringSplit($data, ";")
			$PosIni = MouseGetPos()
			MouseClick("Left", $data[1], $data[2],1,0)
			MouseMove($PosIni[0], $PosIni[1], 0)
			_Journal3("Touche " & $data[3] & " Pressé")
			Sleep(100)
		EndIf
	FileClose($Path)
EndFunc

Func AssiLock($paral1, $paral2)
	FileOpen($Path)
	ToolTip("Choissiez la position du raccourci à enregistrer, puis appuyez sur C", 0, 0)
	While 1
		If _IsPressed("43") Then
			$PosLock = MouseGetPos()
			_FileWriteToLine($path, $paral1, $PosLock[0] & ";" & $PosLock[1] & ";" & $paral2, True)
			GUICtrlSetData($Edit2, $paral2 & " : " & $PosLock[0] & ";" & $PosLock[1] & @CRLF, 1)
			ToolTip("")
			FileClose($Path)
			_Journal3("Touche " & $paral2 & " = " & $PosLock[0] & ";" & $PosLock[1] & " (Positions)")
			Return
		EndIf
	FileClose($Path)
	WEnd
EndFunc

Func LockR()
	If $lock = 0 Then
		$lock = 1
		ToolTip("Mode Raccourci", 0,0)
		_Journal3("Mode Raccourci : ON")
	Else
		$lock = 0
		ToolTip("")
		_Journal3("Mode Raccourci : OFF")
	EndIf
EndFunc

Func Help()
	MsgBox(0, "WizzTools", "A venir !")
EndFunc

; ---- Fonctions Tab3 ----
Func _Journal3($Msg)
	GUICtrlSetData($Edit3, "[" & _NowTime() & "] " & $Msg & @CRLF, 1)
EndFunc

Func Save()
	$Edit3Read = GUICtrlRead($Edit3)
	FileOpen("Log.txt")
	FileWriteLine("Log.txt", "")
	FileWriteLine("Log.txt", _Now())
	FileWriteLine("Log.txt", $Edit3Read)
	FileClose("Log.txt")
EndFunc
