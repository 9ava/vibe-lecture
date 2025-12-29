# Project Guidelines for Claude

## 코드 예시 작성 규칙

- 코드 예시에는 항상 복사하기 버튼을 적용할 것
- 복사 버튼은 코드 블록 오른쪽 상단에 위치
- 복사 성공 시 체크 아이콘으로 변경 후 2초 후 원래대로 복원

### 복사 버튼 구현 예시

```html
<div class="code-wrapper">
  <button class="copy-btn" onclick="copyCode(this)">
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z" />
    </svg>
  </button>
  <div class="code-block">코드 내용</div>
</div>
```

### 필요한 CSS

```css
.code-wrapper {
  position: relative;
  margin: 1rem 0;
}

.copy-btn {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  color: #999;
  padding: 0.5rem;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
}

.copy-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  color: #fff;
}

.copy-btn.copied {
  color: #4caf50;
}

.copy-btn svg {
  width: 18px;
  height: 18px;
}
```

### 필요한 JavaScript

```javascript
function copyCode(button) {
  const codeBlock = button.nextElementSibling;
  const code = codeBlock.textContent;

  navigator.clipboard.writeText(code).then(() => {
    button.classList.add("copied");
    button.innerHTML = `
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
      </svg>
    `;

    setTimeout(() => {
      button.classList.remove("copied");
      button.innerHTML = `
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z" />
        </svg>
      `;
    }, 2000);
  });
}
```
