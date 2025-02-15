## Docker 사용 가이드

### Docker Desktop 설치

- Recommended 선택 → 설치 완료 후 재부팅
- WSL2 자동 설치 → 콘솔창에 `Linux용 Windows 하위 시스템 2.3.26 설치되었습니다`와 같은 메시지가 나타날 수 있

### Dockerfile에 사용할 Python 이미지 정보 확인

```powershell
docker manifest inspect python:3.10.11-slim
```
- 이후 Dockerfile (확장자 없음)을 생성하여 필요한 설정을 추가
- slim은 경량 버전
- python:3.10.11-slim-bookworm의 bookworm은 Debian 버전에 따른 이름

### Docker 이미지 빌드

```powershell
docker build -t <이미지 이름>[:<태그>] <Dockerfile 경로>
# ex) docker build -t myApp:latest .
```
- -t : --tag의 단축형. 이미지 이름과 태그를 지정하는 옵션
- latest가 기본 태그

### Docker 태깅
```powershell
docker tag <이미지명>:<버전> <hubID>/<이미지명>:<버전>
```
- <이미지명>:<버전> → <hubID>/<이미지명>:<버전>으로 태그 변경
- Docker Hub 업로드용 형식
- 태그는 **별칭(alias)**과 비슷한 개념이며, 기존 이미지를 수정하는 것이 아님

### Docker Hub에 이미지 업로드
```powershell
docker push hubID/myApp:v1.0
```
- Docker Hub에 로그인 필요 (docker login)

### Docker 컨테이너 생성

```powershell
docker run <이미지 이름>:<태그>
# ex) docker run my-python-app:latest
```

```powershell
docker run -d --name <컨테이너 이름 지정> <이미지 이름>:<태그>
# ex) docker run my-python-app:latest
```
- -d : 컨테이너를 백그라운드에서 실행 (터미널을 차지하지 않음. Ctrl+C로도 종료되지 않음. docker ps로 확)
- --name : 컨테이너 이름 지정 옵션. 미지정시 자동 생

### Docker 명령어 정리

- 설치 후 PATH 등록 → 터미널에서 Docker 명령어 사용 가능
- 기본 명령어
```powershell
docker images          # 로컬 저장된 Docker 이미지 목록 확인
docker ps -a           # 실행 중이거나 종료된 모든 컨테이너 목록 확인
docker ps              # 실행 중인 컨테이너만
docker inspect <컨테이너 Id> # 특정 컨테이너 상태
docker logs <컨테이너 ID>   # 특정 컨테이너 로그 확인
docker stop <컨테이너 ID>   # 실행 중인 컨테이너 중지
docker rm <컨테이너 ID>     # 컨테이너 삭제
docker rmi <이미지 이름>:<태그>  # 이미지 삭제
```

### Docker Image vs Container

- Docker Image = 템플릿
- Docker Container = 인스턴스

### Docker Image 배포

- 공개 Registry
-- Docker Hub, GitHub Packages, GitHub Container Registry
-- AWS ECR, Google Container Registry, Azure Container Registry
- 비공개 Registry : 내부망 등에서 사용

### 업로드/다운로드 순서

- 업로드: Docker build → (Hub에)Login → Tag → (Reg에)Push 
- 다운로드: Login → (Hub에서)Pull → Run

### Docker Image 내 취약점 해결

```dockerfile
RUN pip install --upgrade pip
RUN pip install --upgrade <패키지명1> <패키지명2>
```

### Docker 베이스 이미지 최신화

```powershell
docker pull python:3.10-slim  # 최신 버전 다운로드
docker build -t myapp .  # Dockerfile 실행
```

```dockerfile
FROM python:3.10-slim  # 베이스 이미지 지정
WORKDIR /app
COPY . .
CMD ["python", "app.py"]
```
docker build -t myapp .
- From은 현재 로컬에 있는 이미지 사용하겠다는 뜻
- 로컬에 해당 이미지가 없으면 docker pull python:3.10-slim 자동 실행

### OS 별 Docker 빌드

```powershell
docker build --build-arg OS_TYPE=windows -t myapp .
docker build --build-arg OS_TYPE=linux -t myapp .

# 최종 명령어
docker build --build-arg OS_TYPE=windows -t ai-triangle-validator .
```
