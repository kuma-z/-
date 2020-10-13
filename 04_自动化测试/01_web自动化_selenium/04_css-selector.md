# CSS-Selector

| 选择器              | 例子                                    | 描述                                                         |
| ------------------- | --------------------------------------- | ------------------------------------------------------------ |
| .class              | .intro<br />.aaa.bbb<br />.fff .aaa.bbb | 选择 class="intro" 的所有元素<br />选择 class="aaa bbb"的所有元素<br />选择父节点为fff，class="aaa bbb"的所有元素 |
| #id                 | #firstname                              | 选择 id="firstname" 的所有元素                               |
| *                   | *                                       | 选择所有元素                                                 |
| [attribute]         | [target]                                | 选择带有target属性的所有元素                                 |
| [attribute=value]   | [target=test]                           | 选择target=test的所有元素                                    |
| [attribute~=value]  | [title~=test]                           | 选择title包含test的所有元素                                  |
| [attribute\|=value] | [lang\|=en]                             | 选择lang属性以en开头的所有元素                               |
|                     |                                         |                                                              |

