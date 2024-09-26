## Initial Setup
### Documentation
[R in Visual Studio Code](https://code.visualstudio.com/docs/languages/r#:~:text=To%20enhance%20the%20experience%20of,syntax%20highlighting%20and%20auto%2Dcompletion.)

### MacOS Setup Details
1. [Install R](https://cran.r-project.org/bin/macosx/) if it is not already installed on your system.
2. Install the [R extension for VSCode](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r)
3. Install [XQuartz](https://www.xquartz.org) prior to installing the httpgd package.
4. Install the following packages:
```
install.packages("httpgd")
```
```
install.packages("languageserver)
```
5. Type `CMD + ,` to open Settings. Type `httpgd`. Check the option to use httpgd for R plot viewing: ![image](https://github.com/user-attachments/assets/9debf4c1-f7f1-4795-8d64-ad76bf28e081)
6. Also in Settings, type `rpath`. Enter the following for macOS:
```
/usr/local/bin/R
```
7. If you plan to use R Markdown documents, install [Pandoc](https://github.com/jgm/pandoc/blob/main/INSTALL.md) and install the following packages:
```
install.packages("rmarkdown")
install.packages("knitr")
```
8. Add keybindings for arrow(<-) and pipe(|> or %>%) to your keybindings.json file.
Press `Cmd+Shift+P` to open the Command Palette. 
Type `Preferences: Open Keyboard Shortcuts (JSON)` and select it.
Add the following blocks between the [ ] brackets:
```
// Insert pipe-operator
{
  "description": "R Pipe Operator",
  "key": "ctrl+shift+m",
  "command": "type",
  "args": {"text": " |> "},
  "when": "editorTextFocus",
},
// Insert <- assignment
{
  "description": "R Assignment Arrow",
  "key": "alt+-",
  "command": "type",
  "args": {"text": " <- "},
  "when": "editorTextFocus",
}
```
Finally, in Settings, type `send keybindings` and check `Send Keybindings to Shell`.
9. Restart VSCode

## Daily Use

### How to open an R terminal
![image](https://github.com/user-attachments/assets/9f59d75a-cc22-46f2-8abc-59085dd1c8b5)

```
library("httpgd")
```

Run a line by using `CMD + ENTER`.

