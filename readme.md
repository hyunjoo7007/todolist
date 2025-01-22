# Todo List 코드 설명

## 개요
이 Todo List 코드는 브라우저에서 실행되는 간단한 할 일 관리 애플리케이션입니다. 사용자가 할 일을 추가, 수정, 완료 표시 및 삭제할 수 있는 기능을 제공합니다. 본 문서에서는 HTML, CSS, 그리고 JavaScript로 구현된 코드를 설명합니다.

---

## 코드 구조

### 1. HTML 구조
- **`<head>` 태그**: 문서의 메타정보와 스타일(CSS)을 정의합니다.
- **`<body>` 태그**: 화면에 표시되는 주요 콘텐츠를 담고 있습니다.
  - `.todo-container`: Todo List의 전체 컨테이너로, 디자인을 담당하는 요소입니다.
  - `h1`: Todo List의 제목.
  - `.icon-container`: 수정(✏) 및 삭제(🗑) 아이콘을 표시합니다.
  - `#current-date`: 현재 날짜를 표시하는 영역.
  - `#todo-input`: 할 일 입력창.
  - `#add-btn`: 할 일을 추가하는 버튼.
  - `#todo-list`: 할 일 항목을 나열하는 리스트.

### 2. CSS 스타일
- **전체 레이아웃**: 중앙 정렬을 통해 사용자가 편리하게 사용할 수 있도록 설계되었습니다.
- **할 일 항목 스타일**:
  - `li` 요소는 가로로 긴 디자인을 적용하여 글자가 잘리지 않도록 설정.
  - `completed` 클래스는 완료된 항목에 취소선과 흐릿한 색상을 적용.
- **버튼 및 아이콘**:
  - 수정 버튼(✏)과 삭제 버튼(🗑)은 각각 귀여운 아이콘으로 표시.
  - 버튼은 마우스오버 시 색상이 변경됩니다.

### 3. JavaScript 기능

#### (1) 현재 날짜 표시
```javascript
const today = new Date();
const formattedDate = today.toLocaleDateString('ko-KR', {
  year: 'numeric',
  month: 'long',
  day: 'numeric'
});
currentDate.textContent = formattedDate;
```
- 현재 날짜를 `#current-date` 영역에 표시합니다.

#### (2) 할 일 추가
```javascript
function addTodo() {
  const todoText = todoInput.value.trim();
  if (todoText === '') return;

  const todoItem = document.createElement('li');
  const checkbox = document.createElement('input');
  checkbox.type = 'checkbox';
  const textNode = document.createElement('span');
  textNode.textContent = todoText;

  const deleteButton = document.createElement('button');
  deleteButton.innerHTML = '🗑';
  const editButton = document.createElement('button');
  editButton.innerHTML = '✏';

  todoItem.appendChild(checkbox);
  todoItem.appendChild(textNode);
  todoItem.appendChild(editButton);
  todoItem.appendChild(deleteButton);
  todoList.appendChild(todoItem);

  todoInput.value = '';
}
```
- 사용자가 입력창에 내용을 작성하고 버튼을 클릭하면 새로운 항목이 생성됩니다.

#### (3) 수정 버튼
```javascript
editButton.addEventListener('click', function() {
  const newText = prompt('수정할 내용을 입력하세요:', textNode.textContent);
  if (newText !== null && newText.trim() !== '') {
    textNode.textContent = newText.trim();
  }
});
```
- 클릭 시 `prompt` 창을 통해 사용자가 새로운 내용을 입력할 수 있습니다.

#### (4) 삭제 버튼
```javascript
deleteButton.addEventListener('click', function() {
  todoList.removeChild(todoItem);
});
```
- 클릭 시 해당 항목을 리스트에서 삭제합니다.

#### (5) 완료 표시
```javascript
checkbox.addEventListener('change', function() {
  todoItem.classList.toggle('completed');
});
```
- 체크박스를 클릭하면 완료 표시(취소선)가 적용됩니다.

---

## 주요 기능 요약
1. **할 일 추가**: 사용자가 텍스트를 입력하고 추가 버튼을 누르면 리스트에 항목이 추가됩니다.
2. **수정 기능**: 수정 버튼(✏)을 클릭하여 할 일의 내용을 변경할 수 있습니다.
3. **삭제 기능**: 삭제 버튼(🗑)을 클릭하여 항목을 제거할 수 있습니다.
4. **완료 표시**: 체크박스를 클릭하면 완료된 항목으로 표시됩니다.
5. **현재 날짜 표시**: 페이지 상단에 현재 날짜가 표시됩니다.

---

## 활용 방법
1. 코드를 HTML 파일로 저장하고 브라우저에서 열어 실행합니다.
2. 입력창에 내용을 작성하고 "추가" 버튼을 눌러 할 일을 생성합니다.
3. 각 항목에 있는 수정(✏) 및 삭제(🗑) 버튼을 활용하여 할 일을 관리합니다.

---

## 추가 제안
- **로컬 저장소 연동**: 브라우저의 로컬 저장소를 사용하여 새로고침 후에도 데이터가 유지되도록 개선할 수 있습니다.
- **반응형 디자인**: 모바일 환경에서도 보기 편하도록 스타일을 조정할 수 있습니다.

---

이 코드는 사용자가 간단한 할 일 관리를 시작하기에 적합하며, 추가적인 기능 구현과 디자인 변경으로 더 발전시킬 수 있습니다.
