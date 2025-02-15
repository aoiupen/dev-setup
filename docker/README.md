## Docker 사용 가이드

### Docker Desktop 설치

- Recommended 선택 → 설치 완료 후 재부팅
- WSL2 자동 설치 → 콘솔창에 `Linux용 Windows 하위 시스템 2.3.26 설치되었습니다` 확인

### Dockerfile 만들기 (확장자 없음)

```powershell
docker manifest inspect python:3.10.11-slim
```

- Python 이미지 있는지 확인
- slim은 경량 버전
- bookworm 등 별칭은 Debian 버전에 따른 이름

### Docker 이미지 빌드

```powershell
docker build -t <이미지 이름>[:<태그>] <Dockerfile 경로>
# ex) docker build -t myApp:latest .
```
- -t : 이미지 이름과 태그를 지정하는 --tag 옵션

### Docker 컨테이너 생성

```powershell
docker run <이미지 이름>:<태그>
# ex) docker run my-python-app:latest
```
- latest가 기본 태그

### Docker 명령어 정리

- 설치 후 PATH 등록 → 터미널에서 Docker 명령어 사용 가능
- 기본 명령어
```powershell
docker images          # 로컬 저장된 Docker 이미지 목록 확인
docker ps -a           # 실행 중이거나 종료된 모든 컨테이너 목록 확인
docker logs <컨테이너 ID>   # 특정 컨테이너 로그 확인
docker stop <컨테이너 ID>   # 실행 중인 컨테이너 중지
docker rm <컨테이너 ID>     # 컨테이너 삭제
docker rmi <이미지 이름>:<태그>  # 이미지 삭제
```

### Docker Image vs Container

- Docker Image = 객체
- Docker Container = 인스턴스

### Docker Image 배포

- 공개 Registry
-- Docker Hub, GitHub Packages, GitHub Container Registry
-- AWS ECR, Google Container Registry, Azure Container Registry
- 비공개 Registry : 내부망 등에서 사용

### 업로드/다운로드 순서

- 업로드: Docker build → Login → Tag → Push
- 다운로드: Login → Pull → Run

### Docker Image 내 취약점 해결

```dockerfile
RUN pip install --upgrade <패키지명1> <패키지명2>
```

### Docker 베이스 이미지 최신화

```powershell
docker pull python:3.10-slim
```
- 실행 순서: pull → build(FROM)

### OS 별 Docker 빌드

```powershell
docker build --build-arg OS_TYPE=windows -t myapp .
docker build --build-arg OS_TYPE=linux -t myapp .

# 최종 명령어
docker build --build-arg OS_TYPE=windows -t ai-triangle-validator .
```