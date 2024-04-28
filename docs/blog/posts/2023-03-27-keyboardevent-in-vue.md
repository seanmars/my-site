---
title: KeyboardEvent in Vue
tags: vue, input, event, keyboard, ime, js, javascript, vue.js, composing
---

# KeyboardEvent in Vue

最近在寫 [Vue](https://vuejs.org/) 的時候遇到輸入法選字以及輸入的時候觸發了 @keyup , @keydown 的事件，造成一些不正常的結果；為了避免還在輸入法選字或者輸入後就會觸發輸入框的 KeyboardEvent 需要多增加一些判斷，後來找到 [MDN](https://developer.mozilla.org) 的說明：

---

The **`KeyboardEvent.isComposing`** read-only property returns a boolean value indicating if the event is fired within a composition session, i.e. after [`compositionstart`](https://developer.mozilla.org/en-US/docs/Web/API/Element/compositionstart_event) and before [`compositionend`](https://developer.mozilla.org/en-US/docs/Web/API/Element/compositionend_event).

---

The **`compositionstart`** event is fired when a text composition system such as an [input method editor](https://developer.mozilla.org/en-US/docs/Glossary/Input_method_editor) starts a new composition session.

For example, this event could be fired after a user starts entering a Chinese character using a [Pinyin](https://en.wikipedia.org/wiki/Pinyin) IME.

---

因此只要在觸發後增加判斷 event.isComposing 即可避免此問題。

    const onClick = (event) => {
    	if(event.isComposing) {
            return;
        }
        
        // do something...
    }
    

參考:

- [KeyboardEvent.isComposing](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/isComposing)
- [Element: compositionstart event](https://developer.mozilla.org/en-US/docs/Web/API/Element/compositionstart_event)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
