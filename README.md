# Tag Layout Input Field
HTML, CSS JavaScript Tag input field

Style CSS

```CSS

    .tag-container {
      display: flex;
      flex-wrap: wrap;
      border: 1px solid #ccc;
      padding: 5px;
      min-height: 40px;
      cursor: text;
    }

    .tag {
      background-color: #f0f0f0;
      border: 1px solid #ccc;
      border-radius: 4px;
      padding: 5px 10px;
      margin: 3px;
      font-size: 14px;
    }

    .tag-input {
      border: none;
      outline: none;
      flex-grow: 1;
      min-width: 100px;
      font-size: 14px;
      padding: 5px;
    }

```

```HTML

...
<body>

  <div class="tag-container" id="tagContainer">
    <input type="text" id="tagInput" class="tag-input" placeholder="Type something..." />
  </div>

</body>
...


```

JavaScript 

```JS

  const tagInput = document.getElementById('tagInput');
    const tagContainer = document.getElementById('tagContainer');

    function createTag(text) {
      const trimmed = text.trim().replace(/,$/, ''); // remove trailing comma
      if (trimmed === '') return;

      const tag = document.createElement('span');
      tag.className = 'tag';
      tag.textContent = trimmed;
      tagContainer.insertBefore(tag, tagInput);
      tagInput.value = '';
    }

    tagInput.addEventListener('keydown', function (e) {
      if (e.key === ',' || e.key === ' ' || e.key === 'Enter') {
        e.preventDefault();
        createTag(tagInput.value);
      }
    });

    // Optional: Paste comma-separated values
    tagInput.addEventListener('paste', function (e) {
      e.preventDefault();
      const text = e.clipboardData.getData('text');
      text.split(/[, ]+/).forEach(createTag);
    });

```
