# BAR 생산 계산기 v1.0 — Windows 데스크톱 앱

전체 시트 N, 1BAR의 S2 개수 a, S3 개수 b를 입력하면 BAR 수, 층수, 사용 시트, 잔여 시트가 실시간으로 계산되는 오프라인 프로그램입니다.

## Windows에서 설치 프로그램 만들기 (가장 간단한 방법)

1. Windows PC에 [Node.js LTS](https://nodejs.org/)를 설치합니다. 이미 설치되어 있다면 생략합니다.
2. `Windows에서_설치파일_만들기.bat`를 더블클릭합니다. 인터넷 연결이 필요합니다.
3. 빌드가 성공하면 `dist/BAR-Calculator-Setup-1.0.0.exe`가 생성되고 폴더가 열립니다.
4. 해당 설치 파일을 실행하면 설치 과정에서 바탕화면 바로가기를 생성합니다.

## GitHub에서 Windows 설치 파일 자동 제작

프로젝트 전체(.github 폴더 포함)를 GitHub 저장소에 올리고 Actions > Build Windows Installer > Run workflow를 실행합니다. 실행 완료 시 Artifacts에서 Windows installer를 다운로드할 수 있습니다.

## 다운로드 페이지 배포

`website/index.html`과 실제 생성된 `BAR-Calculator-Setup-1.0.0.exe` 파일을 **같은 폴더**에 놓고 Netlify Drop 등에 함께 업로드하세요. 사이트의 설치 파일 다운로드 버튼이 작동합니다. 업로드하지 않으면 링크는 작동하지 않습니다.

## 계산식

- 1BAR 필요 시트 P = 2a + 3b
- 완성 BAR B = floor(N / P)
- S2 총개수 = aB, S3 총개수 = bB
- 사용 시트 = PB, 잔여 시트 = N - PB
- 완성 층수 = (a+b)B

기본값 N=1500, a=10, b=53이면 완성 BAR 8개, S2 80개, S3 424개, 사용 시트 1432개, 잔여 시트 68개입니다.

## 제한사항

이 배포본에는 `.exe` 파일이 **포함되지 않습니다**. Windows에서 빌드하거나 GitHub Actions로 생성해야 합니다. 앱 배포용 코드 서명 인증서가 없으므로 Windows SmartScreen 경고가 나올 수 있습니다.
