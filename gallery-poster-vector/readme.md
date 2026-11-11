기하학적 형상(Shape)과 시각 예술 양식(Art Style)을 결합하여 순수 SVG 코드로 벡터 그래픽 포스터를 생성하고, 리퀴드 글래스(Liquid Glass) 3D 인터랙티브 카탈로그로 전시하는 프로젝트.

## Specification

### 1. SVG 포스터 출력 제약
- 캔버스 규격: `viewBox="0 0 600 900"` (2:3 세로 비율) 고정.
- 순수 벡터 구현: 외부 이미지 래스터 참조(`href`, `image`)나 웹폰트 `@import` 없이, 기본 시스템 폰트(`system-ui`, `sans-serif`, `serif`)와 순수 SVG 요소(`<polygon>`, `<path>`, `<circle>`, `<line>`, `<text>`, `<defs>`)만 사용.
- 레이아웃 구성: 상·하단 인덱스 가이드 라인, 세련된 타이포그래피, 작가 표기(`ARTIST: GITSAM`)를 포함한 포스터 양식.
- 파일 네이밍 규칙: `assets/{shape}_{style_art}_{version}.svg`

### 2. 데이터 구조
- `preset.json`: 선별된 형상 및 예술 스타일 프리셋 정의.
- `posters.json`: 생성된 포스터 메타데이터(id, shape, style_art, version, file_path, title, artist, created_at)를 관리하는 정적 파일 기반 데이터베이스.

---

## Presets

### Shape 7선
1. Heart (하트): 곡면과 꼭짓점의 대비, 중앙 대칭 분할
2. Diamond (다이아몬드): 다각도 파셋 분할과 직선적 입체 조형
3. Sphere (구형): 동심원, 호(arc), 절단면 슬라이스 구조
4. Crescent Moon (초승달): 내외부 호 곡률 차이와 음각 여백의 긴장감
5. Eye (아이콘형 눈): 타원 윤곽선, 중심 원, 방사형 시선 집중
6. Hourglass (모래시계): 상하 대칭 역삼각형과 중앙 수렴 구조
7. Hexagon (육각형): 등각투영 큐브 및 테셀레이션 그리드 확장

### Style 7선
1. Bauhaus Constructivism (바우하우스 구성주의): 삼원색과 기하학적 면, 호의 비대칭 균형
2. Swiss Style (스위스 스타일): 엄격한 모듈 그리드, 정밀 보조선, 절제된 산세리프 레이아웃
3. Technical Schematic (엔지니어링 청사진): 좌표축 보조선, 치수선, 단색 와이어프레임 도면
4. Low Poly Origami (로우 폴리 오리가미): 폴리곤 파셋의 명암 대비와 흰 접힘선 강조
5. Memphis Pattern (멤피스 패턴): 굵은 도트·지그재그 패턴, 파스텔 톤, 80년대 포스트모던 그래픽
6. Gradient Mesh (벡터 그라디언트): 다중 선형·방사형 그라디언트와 부드러운 빛·그림자 볼륨감
7. Sumi Ink Wash (수묵 잉크 워시): 먹물의 유기적 번짐, 거친 필선 질감, 비백의 여백과 붉은 낙관 인장

---

## 인터랙티브 카탈로그 (`index.html`)

Three.js 및 GSAP 기반의 3D 리퀴드 글래스(Liquid Glass) 무한 캐러셀 카탈로그.

- Zero-Build & CDN: 빌드 도구 없이 브라우저에서 즉시 실행 (UnoCSS Runtime, Three.js r128, GSAP 3.12.5).
- 모노크롬 다크 테마: `#09090b` 배경과 실버 화이트 굴절 조명.
- 고해상도 텍스처 렌더링: SVG를 1200×1800 해상도 Canvas 2D로 래스터화하여 WebGL 텍스처로 바인딩.
- WebCodecs GIF 애니메이션: `ImageDecoder` API를 활용하여 GIF 프레임 실시간 재생 동기화.
- 사용자 인터랙션: 포인터 드래그, 마우스 휠 관성 스크롤, 방향키 탐색, 클릭 포커스 줌인 및 재클릭 복귀.
