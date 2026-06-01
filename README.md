# MeasureCount

모바일 웹(Chrome/Safari)에서 동작하는 **거리/넓이 측정** 및 **사물 개수 카운팅** 프로토타입.

- 단일 `index.html` (외부 빌드 도구 없음)
- TensorFlow.js + COCO-SSD (CDN)
- DeviceOrientation API + 카메라 높이 기반 삼각측량
- 후면 카메라(`facingMode: environment`), Canvas 오버레이

## 실행

`https`로 서빙해야 카메라/방향 권한이 열립니다.

```bash
# 예시 (Python)
python -m http.server 8443

# 또는 ngrok / vercel / netlify / github pages 정적 배포
```

iOS Safari는 첫 진입 시 화면의 **"기울기 권한 요청"** 버튼을 한 번 눌러야 DeviceOrientation 이 활성화됩니다.

## 거리 측정 사용법

1. **카메라 높이(m)** 입력 (지면에서 카메라 렌즈까지의 높이, 기본 1.50m).
2. 카메라를 지면 쪽으로 기울여, 화면 중앙 조준점(Reticle)을 측정할 첫 위치에 맞춤.
3. **시작점 찍기** 버튼 또는 화면 탭 → 두 번째 점 동일 방법.
4. 두 점: 거리 표시 · 세 점 이상: 다각형 넓이/둘레 표시.

> 단순 삼각측량(`d = h / tan(β-90°)`) 기반의 추정치입니다. 평평한 바닥, 안정적인 자세에서 가장 정확합니다.

## 개수 세기

상단 탭에서 **물건 개수 세기** 선택 → 최초 1회 모델 로딩(수 초) 후 실시간 박스/라벨/카운트 표시.

## 라이선스

MIT (필요 시).
