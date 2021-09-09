---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

# Flexbox

Новопашин Алексей P4109

---

# `align-content`

Выравнивание элементов контейнера по cross axis.

<FlexboxSandbox flexboxPropName="align-content" wrap />

---

# `align-self`

Выравнивание конкретного элемента по cross axis. Перезаписывает значение свойства `align-items`.

<FlexboxSandbox flexboxPropName="align-self" />

<!-- <FlexboxSandbox flexboxPropName="align-content" /> -->

---

# `flex-basis`

Устанавливает размер элемента в flexbox. Имеет приоритет над `height` и `width`.

<FlexboxSandbox flexboxPropName="flex-basis" />

---


# `flex-shrink`

Устанавливает фактор сжатия, относительно соседей. Все элементы списка имеют значение `flex-grow: 0`.

<FlexboxSandbox flexboxPropName="flex-shrink" />
