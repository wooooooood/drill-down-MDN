# [Position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
![https://hackernoon.com/_next/image?url=https%3A%2F%2Fcdn.hackernoon.com%2Fdrafts%2Ft2w3yae.png&w=1920&q=75](https://hackernoon.com/_next/image?url=https%3A%2F%2Fcdn.hackernoon.com%2Fdrafts%2Ft2w3yae.png&w=1920&q=75)
- element가 문서 내에서 어떻게 positioned(위치되어있는지) 되어있는지를 설정하며, 다섯 가지 종류가 있다.

### position : static
- default값 (static element를 제외하면 모두 positioned element이다)
- normal flow: 문서의 flow를 있는 그대로 따라간다
- `top`, `right`, `bottom`, `left`, `z-index` property를 설정해도 **영향이 없다**

### position : relative
- normal flow: 문서의 flow를 있는 그대로 따라가기에 차지하는 영역은 `position: static`과 같다
- 단! **자기 자신**을 기준으로 `top`, `right`, `bottom`, `left` 값에 따라 offset을 적용한다. 자신 바깥 요소에는 영향이 없다
- `z-index`의 값이 auto가 아니라면 [**stacking context**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)을 생성한다. (즉 `z-index`의 사용을 위해 사용되기도 한다)

### position : absolute
- normal flow를 따르지 않는다! 따라서 space를 할당받지 않는다.
- 사용하면 해당 element는 ancestor 또는 initial [containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block)에 상대적으로 위치된다
- 위치는 `top`, `right`, `bottom`, `left` 설정으로 offset 지정한다
- `z-index`의 값이 auto가 아니라면 [**stacking context**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)을 생성한다.
- absolute element는 다른 margin과 [collapse](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)되지 않는다  
  => 간단하게 말하면 마진이 겹치지 않는다

### position : fixed
- normal flow를 따르지 않는다! 따라서 space를 할당받지 않는다.
- ancestor 중 하나가 `none`이 아닌 `transform` | `perspective` | `filter` property를 가진 경우를 제외하고(=ancestor가 containing block으로 행동할 때를 제외하고), [viewport](https://developer.mozilla.org/en-US/docs/Glossary/Viewport)에 의해 생성된 initial containing block에 상대적으로 위치한다
- 위치는 `top`, `right`, `bottom`, `left` 설정으로 offset 지정한다
- **항상** [**stacking context**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)을 생성한다
- 문서를 인쇄할 때는 해당 요소가 **모든 페이지의 같은 위치**에 출력된다 = 페이지를 **스크롤해도 항상 그 위치**에 있다

### position : sticky
- normal flow: 문서의 flow를 있는 그대로 따라간다
- 가장 가까운 scrolling ancestor, containing block 에 상대적으로 위치된다
- 위치는 `top`, `right`, `bottom`, `left` 설정으로 offset 지정한다. (다른 element에는 영향이 없다)
- **항상** [**stacking context**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)을 생성한다
- scrolling mechanism(`overflow` = hidden | scroll | auto | overlay)을 가진 가장 가까운 ancestor에 붙는다  
  => scrolling mechanism을 가졌음에도 실제로 scroll이 되지 않는 ancestor에 붙는다는 뜻이므로 우리가 보기에 un-sticky 할 수 있다

### 우선순위
- top > bottom
- [direction](https://developer.mozilla.org/en-US/docs/Web/CSS/direction) == ltr ? left : right
- [direction](https://developer.mozilla.org/en-US/docs/Web/CSS/direction) === rtl ? right : left

![https://miro.medium.com/max/798/1*3nHXvVEEbQziTats5DlZOA.png](https://miro.medium.com/max/798/1*3nHXvVEEbQziTats5DlZOA.png)

### Additional ref
- https://codecrunch.org/css-position-23ad6d0cc5f9
- https://hackernoon.com/tutorial-how-to-use-css-position-property-p32d3un7
