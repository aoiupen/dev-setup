##**원격 Repo 생성 후 로컬과 연결**

```powershell
# 로컬 초기화
git init

# 원격 레포 연결
git remote add origin https://github.com/<userID>/<RepoName>.git

# (1_1. 등록된 origin url을 지우고 싶다면)
git remote remove origin

# (1_2. 등록된 origin url을 교체하고 싶다면)
git remote set-url origin https://github.com/<userID>/<RepoName>.git

# 원격 브랜치 등록 조회
git remote -v

# 로컬을 원격으로 Push
git push --set-upstream origin main
# 축약하여
git push -u origin main

# 원격에서 .gitignore 가져오기
# .venv의 add 방지
git fetch origin main
git checkout origin/main .gitignore

# 브랜치 이름을 main으로 변경
git branch -M main

# 스테이징 하고 push
git add .
git commit -m "커밋메세지"
git push origin main
# git push origin main --force
```
