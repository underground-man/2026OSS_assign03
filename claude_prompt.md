다음 조건으로 CRUD 웹페이지를 하나의 HTML 파일로 만들어줘.

[제약 조건]
- 결과물은 index.html 파일 하나뿐이어야 함 (별도 CSS/JS 파일 분리 금지)
- Bootstrap은 CDN 링크로 <head>에 불러와서 사용 (별도 다운로드 금지)
- 커스텀 CSS는 <style> 태그로 <head> 안에 작성
- JavaScript는 <script> 태그로 </body> 바로 위에 작성
- 데이터 저장은 브라우저 localStorage 사용 (새로고침해도 데이터 유지)
- 외부 백엔드/서버 없이 순수 프론트엔드로만 동작

[데이터 항목: 예시 - "할일(Task)" 항목 관리]
- 필드: id(자동생성), 제목(title, 텍스트), 설명(description, 텍스트), 완료여부(done, 체크박스)

[기능]
1. Create: 상단에 입력 폼(제목, 설명, 완료여부)과 "추가" 버튼
2. Read: 등록된 항목들을 Bootstrap 카드 또는 테이블로 목록 표시
3. Update: 각 항목에 "수정" 버튼 → 클릭 시 해당 항목을 폼에 불러와 수정 가능
4. Delete: 각 항목에 "삭제" 버튼 → confirm 창으로 확인 후 삭제

[UI 요구사항]
- Bootstrap의 navbar, card, table, button, modal 컴포넌트를 활용해서 깔끔하게 구성
- 반응형(모바일에서도 레이아웃 안 깨지게)
- 입력값이 비어있을 때 등록 방지 및 경고 메시지 표시

[출력 형식]
- 완성된 index.html 코드 전체를 한 번에 출력
- 코드 중간에 주요 부분마다 짧은 한글 주석 추가