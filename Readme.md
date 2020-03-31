# Miscellaneous
## Markdown test
`*Itallic*` -> *Itallic*  
`**Bold**` -> **Bold**
### How to make VIM python friendly (with minimum effort, minimum function)
- Source: [Here](https://realpython.com/vim-and-python-a-match-made-in-heaven/)
1. Install [Vundle](https://realpython.com/vim-and-python-a-match-made-in-heaven/#vundle), the VIM's pip.
1. Install Plugins for [Syntax Checking/Highlighting](https://realpython.com/vim-and-python-a-match-made-in-heaven/#syntax-checkinghighlighting).
1. Done!
- Colorschemes? Do it on your own.
### GPIO Zero Dependency
#### Why do I get PinFactoryFallback warnings when I import gpiozero?
- Source: [Here](https://gpiozero.readthedocs.io/en/stable/faq.html#why-do-i-get-pinfactoryfallback-warnings-when-i-import-gpiozero)  

` $ pip3 install rip.gpio `
### Linux용 Windows 하위 시스템 / Windows Subsystem for Linux 's actual directory
- Source: [Windows 10 - Ubuntu on Windows 10 서로간 파일 시스템 접근하기](https://snowdeer.github.io/windows/2018/01/07/windows10-ubuntu-file-directory/)  
`C:\Users\<username>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\rootfs`
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
