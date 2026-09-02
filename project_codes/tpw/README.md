# TPW 프로젝트

위성 관측 기반 **총가강수량(Total Precipitable Water, TPW)** 분석 프로젝트입니다.

- **담당 팀:** `project-tpw`
- **대상 영역:** 아시아–태평양
- **기간:** 1988–현재

## 사용 자료

| 자료 | 형식 | 비고 |
|------|------|------|
| SSMI 3-day averaged TPW | bytemap (`.gz`) | 1988–2024 |
| Blended TPW (bTPW) | netCDF / HDF4 | |
| KMA GK2A/AMI TPW | HDF5 | 월별 파일 |
| ERA5 (GPH, q, SLP) | netCDF / pickle | 기압면 자료 |

## 실행 환경

```bash
conda env create -f ../../environment.yml
conda activate sml
```

## 코드 구성

*(코드 추가 후 작성)*

## 주의

- 원자료와 중간 캐시(`.pkl`, `.h5`, `.nc`)는 **커밋하지 않습니다.**
- 자료 경로는 각 스크립트 상단에 변수로 정의합니다.
