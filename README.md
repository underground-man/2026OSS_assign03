# 도서 관리 시스템 (Book Management CRUD Frontend)
학번/이름
22300330/ 박찬

Vercel Deploy URL:https://2026-oss-assign03-green.vercel.app/
git hub url:https://github.com/2026-2-OSS/assign03-c02-22300330
개인 git hub url:https://github.com/underground-man/2026OSS_assign03


## Service Topic
도서 정보를 등록·조회·수정·삭제하는 **도서 관리 CRUD Frontend Service**입니다.
서버 없이 HTML/CSS/JavaScript와 Bootstrap만으로 4개 페이지(목록/추가/상세/수정)를 구성했습니다.

## Data Fields
| 필드 | 설명 | 입력 형태 |
|---|---|---|
| 도서명 (title) | 책 제목 (필수) | text |
| 저자 (writer) | 책을 쓴 사람 | text |
| 출판사 (publisher) | 책을 발행한 출판사 | text |
| 출판년도 (date) | 책이 출판된 연도 | number |
| ISBN (ISBN) | 도서 고유 식별 번호, 13자리 (필수) | text |
| 카테고리 (category) | 도서 분류 (IT / 문학 / 비문학 / sf) | select |

## Pages
| 파일 | 설명 |
|---|---|
| `index.html` | 도서 목록 페이지 |
| `add.html` | 도서 추가 폼 |
| `view.html` | 도서 상세 페이지 (수정/삭제/목록 버튼) |
| `edit.html` | 도서 수정 폼 (기존 값 미리 표시) |
| `my.css` | 모든 페이지 공통 스타일 |
| `example.html` | Bootstrap 예제 실습 |

페이지 이동 흐름: `index → add`, `index → view → edit`, `view → Delete(confirm)`, 각 페이지에서 목록으로 복귀 링크 제공

## List Page
`index.html` 목록에 표시한 필드 (4개 이상):
- 번호
- 도서명
- 저자
- 출판사
- 상세보기 링크 (`view.html`로 이동)

## Validation
`add.html`과 `edit.html`에 동일하게 적용 (JavaScript, 각 5개):

1. **필수값 입력 여부**: 도서명이 비어 있으면 안 됨
2. **문자열 길이**: 저자는 2자 이상
3. **형식 검사(정규식)**: ISBN은 숫자 13자리
4. **숫자 범위**: 출판년도는 1900~2026
5. **Select 선택 여부**: 카테고리를 반드시 선택

- 검사에 실패하면 `alert()`로 원인을 안내하고 제출을 중단합니다.
- 추가: 통과 시 `alert("도서가 추가됩니다.")`
- 수정: 통과 시 `confirm("도서를 수정할까요?")`
- 삭제 (`view.html`): `confirm("정말 삭제하시겠습니까?")`

## RWD
- 모든 페이지 `<head>`에 `viewport` meta 태그를 적용해 모바일 화면 배율을 맞췄습니다.
- Bootstrap의 `container`로 콘텐츠 폭을 제한하고 화면 크기에 따라 좌우 여백이 조절되게 했습니다. (`my.css`에서 `max-width: 900px` 지정)
- 입력창은 `form-control`, `form-select`로 부모 폭에 맞게 100% 너비로 표시됩니다.
- navbar는 `navbar-expand-lg`로 작은 화면에서 접히도록 구성했습니다.

## Bootstrap
사용한 Bootstrap 컴포넌트 및 class:
- **레이아웃**: `container`, `container-fluid`
- **Navbar**: `navbar`, `navbar-brand`, `navbar-expand-lg`, `bg-body-tertiary`
- **Table**: `table`, `table-bordered`
- **Form**: `form-label`, `form-control`, `form-select`
- **Button**: `btn`, `btn-primary`, `btn-secondary`, `btn-danger`, `btn-sm`
- **Card**: `card`, `card-body`
- **유틸리티**: `mt-4`, `mb-3`

## Problem & Solution
| 문제 | 해결 |
|---|---|
| `mb=4`처럼 class에 하이픈 대신 등호를 써서 여백이 적용되지 않음 | Bootstrap class는 `mb-4`처럼 하이픈(`-`)으로 연결해야 함을 확인하고 수정 |
| 입력창 여러 개에 `id="title"`을 중복으로 써서 라벨/JS가 첫 번째 입력창만 인식 | 필드마다 고유한 `id`(title, writer, publisher, date, ISBN, category)로 변경 |
| `<button>` 안에 `<a>` 링크를 넣어 추가 버튼이 없어지고 취소 버튼 클릭 시 폼이 제출됨 | `<button>` 감싸개를 제거하고 `<a class="btn btn-secondary">`만 사용 |
| `view.html`에 add.html의 스크립트를 복사해 `addForm`을 못 찾고 오류 발생 | 삭제 버튼(`deleteBtn`)용 confirm 스크립트로 교체 |
| `my.css`에 `border-bottom: 5ms`, `box-shadow: 10%` 같은 잘못된 값 | 길이/색을 포함한 올바른 값(`2px solid #dee2e6`, `0 2px 6px rgba(...)`)으로 수정 |

## Reflection
- Bootstrap은 클래스를 모두 외우기보다 공식 문서의 예제를 찾아 구조(부모-자식 class)를 그대로 따라 쓰는 것이 핵심이라는 점을 알게 되었습니다.
- 갑자기 javascript를 쓰게 되어서 어려웠습니다.
- `<div>`와 `<nav>`처럼 의미 있는 태그와 스타일을 담당하는 class를 구분해서 이해하게 되었습니다.
- 궁금한 점: 서버 없이 만든 이번 화면에 실제 데이터 저장(localStorage나 DB)을 연결하면 목록/상세/수정 페이지가 어떻게 연동되는지 알고 싶습니다.
