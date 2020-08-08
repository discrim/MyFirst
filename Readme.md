# Miscellaneous
1. [GitHub Markdown](#github-markdown)
	1. [Insert LaTeX formula in GitHub Markdown](#insert-latex-formula-in-github-markdown)
1. [Vim](#vim)
	1. [How to make Vim python friendly (with minimum effort, minimum function)](#how-to-make-vim-python-friendly-with-minimum-effort-minimum-function)
1. [GPIO](#gpio)
	1. [GPIO Zero Dependency](#gpio-zero-dependency)
		1. [Why do I get PinFactoryFallback warnings when I import gpiozero?](#why-do-i-get-pinfactoryfallback-warnings-when-i-import-gpiozero)
1. [Excel](#excel)
	1. [Make and Use Grid Template 엑셀 셀 정사각형 (그리드)로 만들고 템플릿으로 사용하기](#make-and-use-grid-template-엑셀-셀-정사각형-그리드로-만들고-템플릿으로-사용하기)
1. [MinGW](#mingw)
	1. [How to Install MinGW Development Environment](#how-to-install-mingw-development-environment)
	1. [How to Uninstall MinGW](#how-to-uninstall-mingw)
## GitHub Markdown
`*Itallic*` -> *Itallic*  
`**Bold**` -> **Bold**
### Insert LaTeX formula in GitHub Markdown
Source: [#GitHub Gist](https://gist.github.com/a-rodin/fef3f543412d6e1ec5b6cf55bf197d7b)  
`<img src="https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1">`  
Also use https://alexanderrodin.com/github-latex-markdown/ to generate the URL-friendly formula.
## Vim
### How to make Vim python friendly (with minimum effort, minimum function)
- Source: [Here](https://realpython.com/vim-and-python-a-match-made-in-heaven/)
1. Install [Vundle](https://realpython.com/vim-and-python-a-match-made-in-heaven/#vundle), the VIM's pip.
1. Install Plugins for [Syntax Checking/Highlighting](https://realpython.com/vim-and-python-a-match-made-in-heaven/#syntax-checkinghighlighting).
1. Done!
- Colorschemes? Do it on your own.
## GPIO
### GPIO Zero Dependency
#### Why do I get PinFactoryFallback warnings when I import gpiozero?
- Source: [Here](https://gpiozero.readthedocs.io/en/stable/faq.html#why-do-i-get-pinfactoryfallback-warnings-when-i-import-gpiozero)  

` $ pip3 install rip.gpio `
## Excel
### Make and Use Grid Template 엑셀 셀 정사각형 (그리드)로 만들고 템플릿으로 사용하기
Source: [클리앙](https://www.clien.net/service/board/lecture/8390021), [ExtendOffice](https://www.extendoffice.com/documents/excel/2419-excel-grid)
1. Make a rectangle  
직사각형 만들기
1. Make it square by changing its width and height to your desired size of grid at Ribbon 'Drawing Format -> Size'.  
리본 메뉴 중 '도형 서식 -> 크기'에서 가로와 세로 길이를 원하는 그리드 크기를 입력하여 정사각형으로 만들기.
1. Move the square to the top left corner, i.e. in cell A1.  
정사각형을 화면 가장 왼쪽 위, 즉 A1 셀로 옮기기.
1. Right click the square and select 'Size and Properties'.  
정사각형을 오른쪽 클릭하고 '크기 및 속성' 클릭.
1. Under 'PROPERTIES', select 'Don't move or size with cells'.  
'속성' 아래에서 '변하지 않음' 선택.
1. Select the whole worksheet.  
모든 셀 선택하기.
1. Click and drag the border of headers 1/2 and A/B to see and change the height/width. Use both your bare eyes and pixel indication while letting the height/weight of A1 and the sides of the square match.  
헤더 1/2와 A/B의 경계를 클릭하고 드래그하여 높이/너비를 조절. 눈대중과 픽셀표시를 모두 활용하여 A1 셀의 높이/너비가 정사각형과 맞도록 조절.
1. Save as `.xltx` file to use it as a user template.  
`.xltx` 형식으로 저장하여 사용자 템플릿으로 사용하기.
## MinGW
### How to Install MinGW Development Environment
1. Download and install MinGW. You can google it or use the link below:  
https://osdn.net/projects/mingw/downloads/68260/mingw-get-setup.exe/  
You can change the installation path if you want, but be sure to note it because we need the path itself at the later step.
1. We just installed 'package manager', and now we need to install some packages. After the installation is complete, the `MinGW Installation Manager` pops up. From there, mark four things:  
	```
	mingw-developer-toolkit-bin
	mingw32-base-bin
	mingw32-gcc-g++-bin
	msys-base-bin
	```
	Be patient: it takes ~5 sec after you select a package and click 'Mark for Installation'.
1. Go to the top left of the window and click `Installation -> Apply Changes`. Then the installation automatically starts. This will take a while. If something fails, just click `Installation -> Apply` Changes again.
1. Go to system environmental variable setting, i.e. hit the Windows key on your keyboard and type 'environmental variable' then select 'System Environmental Variable' (it may differ since I don't exactly know the term in English Windows).
1. Click `Environmental Variable` button.
1. Under `System Variables`, find `Path`. Click it and click `Edit`.
1. Double-click an empty new line and type in the path of your `bin` folder of MinGW. EX) If you installed MinGW in `C:\MinGW`, then `C:\MinGW\bin` should be written.
1. One more to add; double-click an empty new line and type in the path of your `bin` folder of msys. EX) If you installed MinGW in `C:\MinGW`, then `C:\MinGW\msys\1.0\bin` should be written. The version of mine is 1.0 but it may differ, so please explore to your folders and write your version.
1. Now you can use gcc, make, etc. in your cmd.
### How to Uninstall MinGW
Source: [YouTube](https://www.youtube.com/watch?v=WWSK8wYvs2w)
1. In `MinGW Installation Manager`, uninstall every individual packages you have installed.
1. Delete the folder that `MinGW` is installed.
1. Remove `MinGW` related directories from `System Variables - Path`.
