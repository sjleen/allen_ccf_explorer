# Allen CCF Explorer — Quick Start Guide

## 시작하기 전에 (기본 사항)

- 모든 **좌표 단위는 mm**이며, 원점은 **bregma**입니다. 좌표는 ML / AP / DV 순으로 표시됩니다.
- 앱을 처음 열면 mesh 데이터를 불러오는 동안 **로딩 화면**이 잠깐 나타났다가, **별도의 폴더 선택 없이 곧바로 뷰어**가 열립니다. (데이터가 앱에 임베드되어 있어 오프라인에서도 동작합니다.)
- **최신 웹브라우저**(Chrome / Edge, 또는 2023년 이후의 Firefox · Safari)에서 실행하세요. mesh 압축 해제에 브라우저 내장 기능을 사용하므로 오래된 브라우저에서는 열리지 않을 수 있습니다.

---

## 주요 기능 (Features)

1. **Allen CCFv3 (2017) mesh dataset**을 기반으로 3D · 2D 구조를 탐색합니다. 본 앱은 Allen CCFv3 mesh를 그대로 사용하지 않고, **각 축별 크기와 뇌 전체 각도를 flat skull 위치로 보정**한 상태를 기본값으로 하여 전통적인 stereotaxic surgery에서 익숙한 좌표계를 제공합니다. (보정을 끄고 원본 좌표로 보려면 **Coordinates** 탭의 **Preset**을 **Raw CCF**로 바꾸고, 직접 조정하려면 **Custom**으로 전환하면 됩니다.)

2. **Bregma personalization** — Allen CCF의 bregma와 개인의 bregma 사이 상대거리를 보정해 개인에게 맞는 좌표계를 설정합니다. **Bregma–Lambda 거리**도 함께 커스터마이즈할 수 있습니다.

3. **Point 등록 및 probe path 분석** — 임의의 point를 등록해 3D · 2D 상에서 확인하고, 그 point에 도달하는 probe의 path를 시각화할 수 있습니다. 나아가 그 path로 probe를 삽입할 때 **통과하는 다른 region들의 목록**까지 확인할 수 있습니다.

4. **Path 시뮬레이션** — path에 **Tilt와 Azimuth**를 적용해 target에 도달하는 최적 경로를 시뮬레이션합니다. 좌표 계산에 쓰이는 XYZ 좌표계와 tilt · azimuth의 **적용 순서를 실제 기기의 물리적 순서에 맞춰** 커스터마이즈할 수 있습니다.

5. **View 저장 / 공유** — 현재 설정과 point 정보를 "view"로 저장해 나중에 다시 불러오거나 다른 사람과 공유할 수 있습니다.

6. **오프라인 · 크로스플랫폼** — Allen CCFv3 dataset이 앱에 임베드되어 있어 offline에서 작동하며, 단일 HTML로 작성되어 OS와 상관없이 최신 웹브라우저에서 실행됩니다.

---

## 튜토리얼 (Tutorial)

### 1. **Ontology** 창
앱을 실행하면 왼쪽에 **Ontology** 창이 나타납니다. 이 창에서 원하는 region을 켜고 끌 수 있고, 검색창으로 region을 찾을 수도 있습니다.

### 2. Bregma 보정 (**Coordinates** 탭)
왼쪽 창의 탭 목록에서 **Coordinates**로 이동합니다. **Bregma / Lambda personalization** 섹션에서 Allen CCF의 bregma를 본인의 bregma에 맞출 수 있습니다. **새로운 사용자는 이 과정을 반드시 먼저 수행**하세요. AP axis 방향으로 좁게 존재하는 target에 미량의 dye를 injection한 뒤 histology로 bregma 위치를 보정합니다. 예를 들면:

1. ML = mid ± 1 mm 부근의 **anterior commissure**를 target해 미량의 dye(예: Trypan Blue 2–5 nL)를 injection합니다.
2. 사용한 좌표값을 point로 등록합니다. (point 등록은 아래 5번 참고)
3. histology 결과와 등록한 point가 같은 위치에 오도록 **Bregma AP**와 **Bregma DV** 값을 조절합니다.
4. 이렇게 얻은 값을 기록해 두거나 현재 view를 저장해 개인 프로파일처럼 사용합니다.

### 3. **Manipulator convention** (**Coordinates** 탭)
**Coordinates** 창의 **Manipulator convention** 섹션에서는 실제 실험 셋업에 맞춰 XYZ axis와 tilt · azimuth의 순서를 지정할 수 있습니다. 기본 순서와 값은 널리 쓰이는 stereotaxic arm의 구성과 일치합니다.

### 4. 3D / 2D 뷰 조작
화면 가운데 위쪽에 **3D 뷰**가, 그 아래에 **3개의 2D 뷰**가 있습니다.

- **3D 뷰**: 왼쪽 버튼 드래그로 회전, 휠로 확대/축소.
- **2D 뷰**: 왼쪽 버튼 드래그로 이동, 휠로 확대/축소.
- 각 2D 창 아래의 **스크롤바**는 드래그하거나, 휠을 굴리거나, 값을 직접 입력해 다른 좌표의 2D section으로 이동할 수 있습니다. 이때 **Ctrl을 누른 채 휠**을 굴리면 이동 단위가 0.1에서 0.01로 바뀌어 **10배 더 정교하게** 움직입니다.

### 5. Point 등록 (오른쪽 창)
오른쪽 창에서 point를 등록합니다.

- **New point**를 클릭해 새 point를 만듭니다. 이름과 좌표는 물론, infusion 시 diffusion 범위를 가늠할 수 있는 **반지름**도 설정할 수 있습니다.
- point를 **더블클릭**하면 2D 뷰가 그 point 위치로 이동합니다.
- 여러 좌표를 한꺼번에 넣으려면 **CSV import**로 일괄 등록하면 됩니다.

### 6. Path 분석
각 point의 path를 체크하면 그 point에 접근하는 경로를 볼 수 있습니다. path를 체크하면 **Path analysis** 항목이 생기고, 이를 클릭해 창을 열면 해당 path가 지나는 모든 region을 확인할 수 있습니다.

- **Path analysis** 창은 좌표와 각도 변경에 **실시간으로 반응**합니다.
- 각도를 입력하면 표시되는 **manip 값**은, bregma를 X=Y=Z=0으로 set 했을 때 해당 point 좌표에 도달하기 위해 manipulator에 설정해야 하는 값입니다.
- 창 상단의 버튼으로 **SVG**(시각화용) 또는 **CSV**(데이터 분석용)로 export할 수 있습니다.

> **참고:** Allen CCF mesh dataset의 특성상, 두 개 이상의 region에 동시에 속하는 지역이 있습니다. 이런 지역은 두 region이 함께 표시되며, **Path analysis** 창에서 **가로 길이가 절반인 사각형**이 바로 다른 region과 겹쳐 함께 표현된 region입니다.

### 7. View 저장 / 공유
앱 왼쪽 최상단, 앱 이름 옆의 **Save view**를 클릭하면 현재 설정값과 입력한 정보를 저장할 수 있습니다. 저장된 view는 `.json` 파일로 내려받아지며 **Load view**로 다시 불러옵니다. 이 `.json` 파일(또는 앱 html)을 건네주면 같은 앱을 쓰는 다른 사용자가 동일한 상태를 그대로 재현할 수 있습니다.

---

### (선택) 시각화 조절
- **Mesh opacity** — mesh 투명도를 조절해 내부 구조를 함께 볼 수 있습니다.
- **Slice plane** — 2D 단면을 클리핑해 원하는 단면만 볼 수 있습니다.
