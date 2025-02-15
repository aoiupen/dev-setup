# Git 설치 시 설정


| **페이지**                          | **옵션**                                               | **설명**                                                         | **추천 여부**            |
|---------------------------------------------|--------------------------------------------------------------|----------------------------------------------------------------|-------------------------|
| **Choosing the default editor**              | Default Editor                                                | Git에서 기본으로 사용할 텍스트 에디터 선택 (기본: Vim)        | VS Code 또는 기본 Vim   |
|                                               | Custom branch name                                            | 초기 브랜치 이름을 사용자 지정                                   | 필요 시 설정             |
| **Adjusting the name of the initial branch**  | Default branch name                                           | 새로운 리포지토리 생성 시 초기 브랜치 이름 설정 (기본: main)    | **main 추천**               |
| **Adjusting your PATH environment**           | Git from the command line and 3rd-party software               | 모든 커맨드 라인과 3rd-party 소프트웨어에서 Git 사용 가능      | **권장**                  |
|                                               | Git from the command line only                                 | Git Bash에서만 Git 사용 가능                                    | 필요시 선택             |
|                                               | Do not add Git to PATH                                        | Git을 PATH에 추가하지 않음, Git Bash에서만 사용 가능          | 비추천                   |
| **Choosing the SSH executable**               | Use bundled OpenSSH                                            | Git에 포함된 OpenSSH 사용                                       | **권장**                     |
|                                               | Use external OpenSSH                                           | 시스템(Windows) 기본 SSH 클라이언트를 사용                    | 환경에 따라 선택        |
| **Configuring the line ending conversions**   | Checkout Windows-style, commit Unix-style line endings        | Windows에서 CRLF로 체크아웃, Unix 스타일로 커밋                | **권장**                     |
|                                               | Checkout as-is, commit Unix-style line endings                | 체크아웃 시 그대로, Unix 스타일로 커밋                         | 필요시 선택             |
|                                               | Checkout and commit as-is                                      | 모든 줄바꿈 형식을 변경하지 않고 그대로 유지                  | 혼합 환경에서 비추천    |
| **Configuring the terminal emulator to use**  | Use MinTTY                                                    | Git Bash의 기본 터미널로 MinTTY 사용                           | **기본 권장**               |
|                                               | Use Windows' default console window                            | Windows 기본 CMD 터미널 사용                                    | 필요시 선택             |
| **Choose the default behavior of git pull**   | Default (fast-forward or merge)                               | 기본 동작으로 git pull이 병합(Merge) 또는 빠른 병합(Fast-forward) 방식을 사용 | **대부분의 경우 권장**       |
|                                               | Rebase                                                       | git pull 시 자동으로 리베이스(Rebase)를 수행해 더 깔끔한 커밋 기록을 유지 | 리베이스 전략 사용 시 선택 |
|                                               | Only fetch                                                    | git pull이 기본적으로 가져오기(fetch)만 수행하고 병합은 하지 않음 | 필요시 선택             |
| **Configuring extra options**                 | Enable file system caching                                    | 파일 시스템 캐싱을 활성화하여 성능 향상                        | **권장**                     |
|                                               | Enable symbolic links                                         | 기호 링크 활성화 (Windows 관리자가 아닌 경우 비활성화)         | 필요한 경우만 선택      |
| **Choose credential helper**                  | Git Credential Manager (GCM)                                  | Git 자격 증명 관리자를 활성화하여 자격 증명 저장 및 관리      | **권장**                    |
|                                               | None                                                         | 자격 증명을 저장하지 않고 매번 수동 입력                      | 필요시 선택             |
| **Configuring experimental options**          | Enable experimental features                                  | Git에서 실험적인 기능을 사용할 수 있도록 허용                | 고급 사용자용, 신중히 선택 |
