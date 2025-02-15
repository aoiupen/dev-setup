## GPU 지원 PyTorch 설치 가이드



---

### 1. CPU 지원 PyTorch 삭제

처음 설치된 torch는 cpu 버전일 확률이 있으므로 지우고 새로 설치해준다

```powershell
pip uninstall torch torchaudio torchvision
```
Pytorch GPU 버전명은 마지막에 +cu124 같은 것이 붙는데, Cuda 12.4 버전과 호환된다는 뜻이다

```powershell
torch==2.6.0+cu124
torchaudio==2.6.0+cu124
torchvision==0.21.0+cu124
```

### 2. GPU 지원 PyTorch 설치

```powershell
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124
```

### 3. 설치 확인

```powershell
import torch
print(f"PyTorch Version: {torch.__version__}")
print(f"CUDA available: {torch.cuda.is_available()}")
if torch.cuda.is_available():
    print(f"CUDA version: {torch.version.cuda}")
    print(f"GPU Device: {torch.cuda.get_device_name(0)}")
```

### 4. CUDA_PATH Cuda 실행 경로 추가
참고) Cuda 버전을 2개 이상 운용 시
- 메인으로 사용하는 Cuda 버전을 CUDA_PATH에 등록
- 서브로 사용하는 Cuda 버전은 프로그램 실행 시 임시로 CUDA_PATH를 변경해주는 코드를 활용
- set PATH는 해당 세션에서만 적용, setx PATH는 영구 적용
  
  ```powershell
  set PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin;%PATH%
  ```
  
