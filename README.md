Instructions on how to work on this repo:

## Prereqs: 

I will assume you know how to clone a github repository.

### Latex setup

    1. Ensure you have a Latex engine (MikTeX recommended)

    2. Ensure your IDE of choice can compile latex
        - VS Code: Install the LaTeX extension
        - Conda should support Latex compilation by default
        - Jupyterlab: install `jupyterlab-latex` to allow PDF rendering
    
    3. (VSCode only): Ensure you have `Recipe: pdflatex -> biber -> pdflatex x2` under your build commands  
        - Configure command by going to `settings.json` (Ctrl OR Command + Shift + P), then open up `Preferences: Open User Settings (JSON)`  
        - Search for `latex-workshop.latex.tools` and add if not present:

        ```json
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "--shell-escape", // if you want to have the shell-escape flag
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }   

        {
            "name": "biber",
            "command": "biber",
            "args": [
                "%DOCFILE%"
            ]
        }
        ```  
        - Search for `latex-workshop.latex.recipes` and add:

        ```json
        {
            "name": "pdflatex ➞ biber ➞ pdflatex`×2",
            "tools": [
             "pdflatex",
             "biber",
             "pdflatex",
             "pdflatex"
            ]
        }
        ```  
        If you run into any trouble claude opus 5.5-medium is your friend.         