# 실험 후 레포트: LAB1-07 1:8 디멀티플렉서

작성자: 엄상혁 (학번 ______) / 조: g조 / 실험일: 2026-09-14 / 소스 커밋: `7d89e2b` (https://github.com/dhawldnjs010-star/lab1_07_demux_1x8/commit/7d89e2bb86940d3a26fb05ab34fb946173bf776d) / 구현 도구·버전: Vivado 2026.1 (Build 6511674) / part: xc7s75fgga484-1 / top: `demux_1x8` (시뮬레이션 top `tb_demux_1x8`) / XDC: `constraints/pins.xdc`

경로: Vivado 경로로 수행했다.

## Vivado 시뮬레이션 — Vivado 경로

프로젝트 생성·등록: RTL(`src/demux_1x8.v`)은 Design Sources, TB(`sim/tb_demux_1x8.sv`)는 Simulation Sources, XDC(`constraints/pins.xdc`)는 Constraints에 추가했다(Copy sources 끔). 설계 top은 `demux_1x8`, 시뮬레이션 top은 `tb_demux_1x8`이다.

| 실행 | PASS 문구 | 검사 수 | 종료 시각 | 로그 |
|---|---|---|---|---|
| VS Code (Icarus) | `LAB1_PASS demux_1x8 cases=16` | 16개 | 160 ns | `evidence/simulation.txt` |
| Vivado xsim | `LAB1_PASS demux_1x8 cases=16` | 16개 | 160 ns | `evidence/vivado/xsim_simulate.log`, `evidence/vivado/console_lab1_07_sanghyeok_0920.txt` |

- Icarus와 Vivado xsim의 PASS 문구, 검사 수, 종료 시각이 같다.

- 파형: `evidence/wave.vcd`(Icarus VCD).

## 오픈소스 실행 환경 — CLI 경로

이 랩은 Vivado 경로로 수행했다. CLI 경로는 사용하지 않았다.

## 합성·구현·비트스트림

| 항목 | 결과 |
|---|---|
| Run Synthesis | 완료. `Synthesis finished with 0 errors, 0 critical warnings and 0 warnings.` |
| Run Implementation | 배치·배선 완료 |
| Generate Bitstream | `write_bitstream completed successfully` |
| 이용률 | Slice LUT 4 / Bonded IOB 12 (xc7s75: LUT 48,000 / IOB 338) |
| DRC | Checks found: 1 — CFGBVS-1(Warning) |
| Methodology | Checks found: 0 |
| 타이밍 | WNS/WHS = inf, 실패 endpoint 0. 사용자 타이밍 제약이 없는 조합회로라 통과 수치가 아니다(`Timing 38-313`). |
| 경고 | `Place 46-29`, `Power 33-232`, `Timing 38-313` |

- bit 경로: `vivado/demux_1x8.runs/impl_1/demux_1x8.bit` (Git 제외) / 크기: 3,687,012 bytes / SHA-256: `0446b6642e79e0ee2919a6a5305a11607a386cce7d550d2fd8aa3ac252a355b6`

- 보고서 원본: `evidence/vivado/`의 `synth_runme.log`, `impl_runme.log`, `drc_routed.rpt`, `methodology_drc_routed.rpt`, `timing_summary_routed.rpt`, `utilization_placed.rpt`.

- DRC의 `CFGBVS-1`은 CONFIG_VOLTAGE·CFGBVS 속성이 지정되지 않았다는 경고이다. 실제 보드의 구성 뱅크 전압과 대조해 해석하며 오류는 아니다.

## 실제 보드 기록·실측

연결된 장치: Spartan-7 XC7S75 교육용 보드(part `xc7s75fgga484-1`), 기록 도구: Vivado Hardware Manager (Open target → Program Device). 콘솔 로그: `evidence/board/console_lab1_07_teammate.txt`.

- Hardware Manager 콘솔에서 `program_hw_devices`가 2회 실행되었다.

- 배선·입력·출력이 보이는 영상: `evidence/board/videos/20260914_172207.mp4` (2026-09-14 17:22:07 촬영).


| 조건 | 예상 출력 | 실측 출력 | 사진/영상 시각 | 일치 여부·원인 |
|---|---|---|---|---|
| i=0 s=000 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=001 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=010 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=011 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=100 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=101 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=110 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=0 s=111 | o=00000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=000 | o=10000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=001 | o=01000000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=010 | o=00100000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=011 | o=00010000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=100 | o=00001000 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=101 | o=00000100 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=110 | o=00000010 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |
| i=1 s=111 | o=00000001 | 예상 출력과 같음 | `20260914_172207.mp4` (2026-09-14 17:22:07) | 일치 |


실측은 작성자가 보드에서 직접 확인한 결과이다.

## 비교·결론

- 예상값(진리표) → VS Code(Icarus) `LAB1_PASS demux_1x8 cases=16` → Vivado xsim `LAB1_PASS demux_1x8 cases=16`: 검사 16개 모두 일치하고 종료 시각 160 ns로 같다.

- 실측: 위 표의 모든 조건에서 예상 출력과 같았다. 불일치는 없었다.

- 구현 성공(bit 생성)만으로 동작을 확인한 것으로 보지 않고, 위 실측 표를 별도로 확인했다.

## 제출 링크

소스 커밋: https://github.com/dhawldnjs010-star/lab1_07_demux_1x8/commit/7d89e2bb86940d3a26fb05ab34fb946173bf776d / 실험 전 레포트: `reports/pre/lab1_07_pre_report.md` / 로그·VCD: `evidence/simulation.txt`, `evidence/wave.vcd`, `evidence/vivado/` / bit·해시: 위 3절 (SHA-256 `0446b6642e79e0ee2919a6a5305a11607a386cce7d550d2fd8aa3ac252a355b6`) / 영상: `evidence/board/videos/20260914_172207.mp4` / GitHub에서 링크 확인한 날짜: ______
