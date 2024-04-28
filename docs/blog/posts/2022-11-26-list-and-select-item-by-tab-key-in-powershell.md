---
title: 讓 PowerShell 的可以用 tab 列出當下目錄選單並且選擇
tags: powershell, tab
---

# 讓 PowerShell 的可以用 tab 列出當下目錄選單並且選擇

1. 
安裝 `PSReadLine`

    Install-Module PSReadLine -AllowPrerelease -Force
    

2. 
編輯 `Microsoft.PowerShell_profile.ps1` 可以直接 `Write-Host $PROFILE` 取得位置，或者直接使用 `vscode` 開啟檔案:

    code $PROFILE
    

3. 
引入 `PSReadLine`，並設定 `tab` 的 KeyHandler:

    Import-Module PSReadLine
    Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
    

## 可以用的 Function

[Set-PSReadLineKeyHandler](https://learn.microsoft.com/en-us/powershell/module/psreadline/set-psreadlinekeyhandler) 可以設定的 `function` 可以使用 [Get-PSReadLineKeyHandler](https://learn.microsoft.com/en-us/powershell/module/psreadline/get-psreadlinekeyhandler) 取得，直接在 `PowerShell` 底下輸入 `Get-PSReadLineKeyHandler` 即可取得列表，列表中會直接列書有綁定以及未綁定的 `function`，以下列出所有可以使用的 `function` :

### Basic editing functions

    Function            Description
    --------            -----------
    AcceptLine          Accept the input or move to the next line if input is missing a closing token.
    AddLine             Move the cursor to the next line without attempting to execute the input
    BackwardDeleteChar  Delete the character before the cursor
    BackwardDeleteChar  Delete the character before the cursor
    BackwardDeleteInput Delete text from the cursor to the start of the input
    BackwardKillWord    Move the text from the start of the current or previous word to the cursor to the kill ring
    BackwardKillWord    Move the text from the start of the current or previous word to the cursor to the kill ring
    Copy                Copy selected region to the system clipboard.  If no region is selected, copy the whole line
    CopyOrCancelLine    Either copy selected text to the clipboard, or if no text is selected, cancel edit ing the line with CancelLine.
    Cut                 Delete selected region placing deleted text in the system clipboard
    DeleteChar          Delete the character under the cursor
    ForwardDeleteInput  Delete text from the cursor to the end of the input
    InsertLineAbove     Inserts a new empty line above the current line without attempting to execute the input
    InsertLineBelow     Inserts a new empty line below the current line without attempting to execute the input
    KillWord            Move the text from the cursor to the end of the current or next word to the kill ring
    KillWord            Move the text from the cursor to the end of the current or next word to the kill ring
    Paste               Paste text from the system clipboard
    Paste               Paste text from the system clipboard
    Redo                Redo an undo
    RevertLine          Equivalent to undo all edits (clears the line except lines imported from history)
    Undo                Undo a previous edit
    YankLastArg         Copy the text of the last argument to the input
    

### Cursor movement functions

    Function        Description
    --------        -----------
    BackwardChar    Move the cursor back one character
    BackwardWord    Move the cursor to the beginning of the current or previous word
    BeginningOfLine Move the cursor to the beginning of the line
    EndOfLine       Move the cursor to the end of the line
    ForwardChar     Move the cursor forward one character
    GotoBrace       Go to matching brace
    NextWord        Move the cursor forward to the start of the next word
    

### History functions

    Function              Description
    --------              -----------
    ClearHistory          Remove all items from the command line history (not PowerShell history)
    ForwardSearchHistory  Search history forward interactively
    HistorySearchBackward Search for the previous item in the history that starts with the current input - like PreviousHistory if the input is empty
    HistorySearchBackward Search for the previous item in the history that starts with the current input - like PreviousHistory if the input is empty
    HistorySearchForward  Search for the next item in the history that starts with the current input - like NextHistory if the input is empty
    HistorySearchForward  Search for the next item in the history that starts with the current input - like NextHistory if the input is empty
    ReverseSearchHistory  Search history backwards interactively
    

### Completion functions

    Function            Description
    --------            -----------
    MenuComplete        Complete the input if there is a single completion, otherwise complete the input by selecting from a menu of possible completions.
    MenuComplete        Complete the input if there is a single completion, otherwise complete the input by selecting from a menu of possible completions.
    MenuComplete        Complete the input if there is a single completion, otherwise complete the input by selecting from a menu of possible completions.
    TabCompletePrevious Complete the input using the previous completion
    

### Prediction functions

    Function             Description
    --------             -----------
    SwitchPredictionView Switch between the inline and list prediction views.
    

### Miscellaneous functions

    Function              Description
    --------              -----------
    ClearScreen           Clear the screen and redraw the current line at the top of the screen
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    DigitArgument         Start or accumulate a numeric argument to other functions
    ScrollDisplayDown     Scroll the display down one screen
    ScrollDisplayDownLine Scroll the display down one line
    ScrollDisplayUp       Scroll the display up one screen
    ScrollDisplayUpLine   Scroll the display up one line
    ShowCommandHelp       Shows help for the command at the cursor in an alternate screen buffer.
    ShowKeyBindings       Show all key bindings
    ShowParameterHelp     Shows help for the parameter at the cursor.
    WhatIsKey             Show the key binding for the next chord entered
    

### Selection functions

    Function              Description
    --------              -----------
    SelectAll             Select the entire line. Moves the cursor to the end of the line
    SelectBackwardChar    Adjust the current selection to include the previous character
    SelectBackwardsLine   Adjust the current selection to include from the cursor to the start of the line
    SelectBackwardWord    Adjust the current selection to include the previous word
    SelectCommandArgument Make visual selection of the command arguments.
    SelectForwardChar     Adjust the current selection to include the next character
    SelectLine            Adjust the current selection to include from the cursor to the end of the line
    SelectNextWord        Adjust the current selection to include the next word
    

### Search functions

    Function                Description
    --------                -----------
    CharacterSearch         Read a character and move the cursor to the next occurence of that character
    CharacterSearchBackward Read a character and move the cursor to the previous occurence of that character
    

---

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
