# Document.querySelector()

Document.querySelector()는 제공한 선택자 또는 선택자 뭉치와 일치하는 문서 내 첫 번째 Element를 반환한다.  
일치하는 요소가 없으면 null을 반환한다.

```js
document.querySelector(selectors);
```

selectors: 하나 이상의 선택자를 포함한 DOMString. 유효한 CSS 선택자여야만 하며 아닐 경우 SYNTAX_ERR 예외가 발생

```html
<body>
  <div data-key="65" class="key">A</div>
  <div data-key="83" class="key">S</div>
  <audio
    data-key="65"
    src="http://tizours.free.fr/dicoanimaux/cris/chien.wav"
  ></audio>
  <audio
    data-key="83"
    src="http://www.brunover.com/wave_files/pigs.wav"
  ></audio>

  <script>
    window.addEventListener("keydown", function (e) {
      const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      console.log(audio);
    });
  </script>

  <!-- key 65 번인 "a" 를 눌렀을 때 
  <audio data-key="65" src="http://tizours.free.fr/dicoanimaux/cris/chien.wav"></audio> -->
</body>
```

`data-key`값이 `e.keyCode`인 `<audio/>` 중 첫번째 요소
