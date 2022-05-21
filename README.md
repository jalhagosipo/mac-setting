# mac-setting

## 기본 세팅
- 트랙패드 설정: 시스템 환경설정 > 트랙패드 > 탭하여 클릭하기 활성화
- 메뉴 막대 아이콘 설정: 시스템 환경설정 > Dock 및 메뉴 막대 > Bluetooth(메뉴 막대에서 보기), 사운드(메뉴 막대에서 보기, 항상), 배터리(퍼센트 보기)
- 부팅 소리 없애기: 시스템 환경설정 > 사운드 > 시작 시 사운드 재생 비활성화
- 사운드 효과 없애기: 시스템 환경설정 > 사운드 > 사용자 인터페이스 사운드 효과 재생 비활성화, 경고음량 최소한으로
- 독 가리기: 시스템 환경설정 > Dock 및 메뉴 막대 > 자동으로 Dock 가리기와 보기 활성화, Dock에서 최근 사용한 응용 프로그램 보기 비활성화
- 세 손가락으로 창 옮기기: 시스템 환경설정 > 손쉬운 사용 > 포인터 제어기 > 트랙패드 옵션 > 드래그 활성화 > 세 손가락으로 드래그하기
- 아이콘 정렬: Finder > 우클릭 보기옵션 > 정렬 이름으로 변경
- 폴더 경로 막대, 상태 막대 보기: Finder > 보기 > 폴더 경로 막대, 상태 막대 보기
- 시스템 환경설정 > 문서를 닫을 때 변경사항을 저장할지 묻기 활성화
- 화면 모드 설정: 시스템 환경설정 > 일반 > 라이트모드 or 다크모드
- 키보드 연속 입력: 시스템 환경설정 > 키보드 > 반복지연시간 짧게, 키 반복 빠르게


## 프로그램 세팅
- [크롬](https://www.google.co.kr/chrome/?brand=CHBD&gclsrc=aw.ds&gclid=Cj0KCQjwspKUBhCvARIsAB2IYus25zswGahCX5nDvdgUz8wLFS1nxHRTNhcFBHB5b3pLKSJcDH1_8vEaAhItEALw_wcB)
- 카카오톡: 앱스토어
- [인텔리제이](https://www.jetbrains.com/idea/)
- 슬랙 : 앱스토어
- [포스트맨](https://www.postman.com/downloads/)
- [Docker](https://docs.docker.com/desktop/mac/apple-silicon/)
    - (m1) `softwareupdate --install-rosetta` 후 설치

## CLI 세팅
- Homebrew
    - macOS 용 패키지 관리자. 터미널(Terminal)에서 명령어를 작성하여 자신이 필요한 프로그램을 설치, 삭제, 업데이트를 손쉽게 관리할 수 있음.
    - (intell mac)`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
    - (m1 mac)
        - `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` 
        - `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/[user]/.zprofile` # [user] 주의!
        - `eval "$(/opt/homebrew/bin/brew shellenv)"`
        - `brew --version`


- tig
    - Text-mode interface for git
    - `brew install tig`

- git
    - `brew install git`
    - ```
      git config --global user.name "jalhagosipo"
      git config --global user.email "email"
      git config --list
      ```
    - `ssh-keygen -t rsa -b 4096 -C "email@example.com"`  
    - `cat ~/.ssh/id_rsa.pub` 통해 Github page > Settings >SSH keys 등록
    - `ssh -T git@github.com` > `yes` 입력 >> 계속 git 사용할 수 있게 

- [iTerm2](https://iterm2.com/)
    - 맥의 기본 Terminal을 대체할 수 있는 터미널 에뮬레이터
    - `brew cask install iterm2`
    - preferences(command+,) > keys > key bindings에 추가
        - 줄 삭제: ⌘ + Backspace / Send Hex Code / 0x15
        - 단어 삭제: ⌥ + Backspace / Send Hex Code / 0x17
        - 커서 맨 앞 이동: ⌘ + ← / Send Escape Sequence / OH
        - 커서 맨 뒤 이동: ⌘ + → / Send Escape Sequence / OF
    - Profiles -> Keys -> Key Mappings -> ⌥ + ← 더블 클릭
        - 커서 단어 왼쪽 이동: ⌥ + ← / Send Escape Sequence / b
        - 커서 단어 오른쪽 이동: ⌥ + → / Send Escape Sequence / f


    - oh-my-zsh
        - `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
        
    - 사용자이름 설정
      ```
      vi ~/.zshrc
      
      prompt_context() {
        if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
          prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
        fi
      }

      #
      source ~/.zshrc
      ```
      
    - agnoster 테마 설치: 현재 디렉토리에서 Git의 상태를 알려주는 테마로 현재 마스터 브랜치인지 개발 브랜치인지 알려주는 기능
      ```
      # zshrc 파일 수정
      vi ~/.zshrc 또는 opne ~/.zshrc

      # 설정파일 진입 후 5~15번째줄에 있는 ZSH_THEME=”robyrussell” 부분을 agnoster로 수정하기 
      ZSH_THEME=”agnoster”

      # 설정 파일에서 나간 후 zshrc 파일 적용
      source ~/.zshrc
      ```
    - [D2 폰트](https://github.com/naver/d2codingfont)로 변경
        -  Profile > Text에서 Font D2Coding로 변경. 13으로 사이즈 변경
    - 줄 바꾸기: 줄바꿈된 라인에서 명령어 입력이 되도록 함
        - `vi ~/.oh-my-zsh/themes/agnoster.zsh-theme`
          ```
          build_prompt() {
            RETVAL=$?
            prompt_status
            prompt_virtualenv
            prompt_context
            prompt_dir
            prompt_git
            prompt_bzr
            prompt_hg
            prompt_newline //이부분을 추가 꼭 순서 지켜서
            prompt_end
          }
          prompt_newline() {
            if [[ -n $CURRENT_BG ]]; then
              echo -n "%{%k%F{$CURRENT_BG}%}$SEGMENT_SEPARATOR
          %{%k%F{blue}%}$SEGMENT_SEPARATOR"
            else
              echo -n "%{%k%}"
            fi
            echo -n "%{%f%}"
            CURRENT_BG=''
          }

          ```
    - 하이라이트: 사용할 수 없는 명령어라면 초록색으로 하이라이팅 되지 않으며 잘못된 명령어를 쉽게 거를 수 있음
        - `brew install zsh-syntax-highlighting`
        - `vi ~/.zshrc`
          ```
          (M1)
          source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
          (intel Mac)
          source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
          ```

    - 자동완성
        - 하이라이트랑 설정 적용하는 방법 비슷함
        - `brew install zsh-autosuggestions`
        - `source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh`


    - [color theme](https://iterm2colorschemes.com/) 적용
        - ```
          # curl이 설치되어 있지 않은 경우
          brew install curl

          # util이라는 이름의 directory를 생성하고 이동
          mkdir util && cd util

          # snazzy color theme를 download
          # 만약 다른 color 테마를 다운로드 할 경우 curl -LO 이후에 해당 URL을 넣으면 됨
          curl -LO https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Snazzy.itermcolors
          ```
        - Profiles > colors > color presets > import 통해 snazzy 가져오고 snazzy 설정해주면 됨
