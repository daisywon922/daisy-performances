# Daisy Performance History

## GitHub 업로드와 배포

1. 저장소를 만들고 이 폴더 안의 파일과 폴더를 저장소 루트에 업로드합니다. ZIP 파일 자체를 업로드하지 않습니다.
2. Settings → Pages → Build and deployment에서 Source를 Deploy from a branch로 선택합니다.
3. Branch는 main, Folder는 /(root)를 선택하고 Save를 누릅니다.
4. 배포가 완료되면 Pages에 표시된 주소를 엽니다. 루트 주소는 performances/로 연결됩니다.

GitHub 공식 안내: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 폴더 구조

| 경로 | 용도 |
|---|---|
| index.html | 현재는 공연 이력으로 이동. 나중에 새 메인 페이지로 교체 |
| performances/index.html | 공연 이력 화면 |
| data/performance_history.csv | 공연 정보 |
| data/performance_interviews.csv | 공연별 인터뷰 답변 |
| data/performance_links.csv | 링크 한 건당 한 행 |
| data/performance_posters.csv | 공연 ID와 포스터 경로 연결 |
| assets/posters/ | 공연 ID로 이름을 맞춘 포스터 |

## 데이터 수정

인터뷰는 data/performance_interviews.csv에서 해당 performance_id 행의 답변 칸을 수정합니다. 작성된 질문만 표시하고, 모든 답변이 비면 인터뷰 탭을 숨깁니다. 누락되어 있던 P0023의 빈 답변 행을 추가했습니다.

CSV 파일을 수정하여 커밋하면 Pages 배포 후 새로고침 시 반영됩니다. 공연 ID는 고정하며, 이후 과거 공연을 추가해도 기존 ID를 다시 매기지 않습니다. 새 공연은 다음 ID를 부여합니다.

유형·역할·레퍼토리의 복수 값은 ;로 구분합니다. CSV에서 쉼표·줄바꿈·큰따옴표가 들어간 답변은 CSV 편집기로 저장하세요. 엑셀이나 구글 시트로 편집 후 UTF-8 CSV로 내보내면 됩니다.

링크는 performance_id, link_type, link_title, link_source, link_url로 관리합니다. 링크 유형은 자유롭게 입력하고 동일 표기를 사용합니다. URL은 http 또는 https 주소로 입력합니다.

포스터는 assets/posters/에 업로드하고 performance_posters.csv에 저장소 루트 기준 경로를 입력합니다. 한 공연 ID당 포스터 한 행만 사용합니다. 파일 확장자는 실제 형식과 맞춰야 합니다.

## 나중에 메인 추가

루트 index.html을 새 메인으로 교체하고 performances/로 연결하는 버튼을 추가하면 됩니다. 공연 이력 화면과 CSV·포스터 위치는 유지할 수 있습니다. 필요하면 공연 이력에 ../로 돌아가는 링크를 추가합니다.

## 로컬 확인

CSV를 fetch로 불러오므로 HTML을 더블클릭하는 대신 웹 서버로 실행해야 합니다. 폴더에서 python3 -m http.server 8000 실행 후 http://localhost:8000/performances/로 접속하세요. GitHub Pages에서는 별도 서버 실행 없이 동작합니다.
