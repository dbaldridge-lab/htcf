## Initial Setup
### Documentation
[R in Visual Studio Code](https://code.visualstudio.com/docs/languages/r#:~:text=To%20enhance%20the%20experience%20of,syntax%20highlighting%20and%20auto%2Dcompletion.)

### MacOS Setup Details
1. [Install R](https://cran.r-project.org/bin/macosx/) if it is not already installed on your system.
2. Install the [R extension for VSCode](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r)
3. Install [XQuartz](https://www.xquartz.org) prior to installing the httpgd package.
4. Install the following packages:
```
## start R
R

## Install packages to allow plot viewing
install.packages("httpgd")
install.packages("languageserver)
install.packages("lintr")
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
[See here](https://gist.github.com/strengejacke/a84caf94095f498fb552988edf4ee23a) for other useful keybindings.

9. Restart VSCode

### HTCF Seput
1. Connect via SSH
2. Start an interactive session
```
sml
```
4. Install the VSCode R extension here as well.
5. In Settings, type `rpath`. Enter the path to the lab R installation for linux:
```
/ref/dblab/software/spack-0.21.0/opt/spack/linux-rocky8-x86_64/gcc-8.5.0/r-4.3.0-3ggwaqrtfpe2t627qhwaknvsifz6dk5n/rlib/R/bin/R
```
Type `R: Lib Paths` and enter `/ref/dblab/software/r-envs/4.1.3`. Check the `Use Renv Lib Path` checkbox.

Type `Terminal integrated profiles` and update the settings.json for Linux.
```
{
    "terminal.integrated.profiles.linux": {
        "R": {
            "path": "/bin/bash",
            "args": ["-c", "eval `spack load --sh /3ggwaqr` && R"]
        }
    },
    "terminal.integrated.defaultProfile.linux": "R"
}
```
3. Install XQuartz prior to installing the httpgd package.
4. Install the following packages:
```
## Start R
labr
runr

## Install packages to allow plot viewing
install.packages("httpgd")
install.packages("languageserver)
install.packages("lintr")

```
## Daily Use
### Load R
```
labr
runr
```

### Open an R terminal
![image](https://github.com/user-attachments/assets/9f59d75a-cc22-46f2-8abc-59085dd1c8b5)

### Start the plot viewer
```
# Load the httpgd library
library(httpgd)

# Start the httpgd graphics device
hgd()
```

Copy the URL. Type `R Plot: Open Httpgd URL` and select it. Paste in the URL and press enter.

Open the Command Palette (Cmd+Shift+P).
Type `R: Show Plot Viewer` and select it to open the httpgd viewer.

Run a line by or selection using `CMD + ENTER`.

## Troubleshooting
### How do I make this work with a different R installation? 
1. Install R using spack (it has already been installed in the lab spack instance using the following commands):
```
spack create env r_430
spack install r@4.3.0 X=True
spack env activate r_430
spack add r@4.3.0 X=True
```
2. Enter the following commands, replacing r@4.3.0 with your spec name:
```
spack location -i r@4.3.0
```
Add `/rlib/R/bin/R` to the path that is returned to get the path to the R executable. Update the rpath Linux setting with this path.
