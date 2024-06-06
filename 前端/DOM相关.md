# 知识点积累

# 1（MutationObserver
MutationObserver 是一种用于监视DOM中变更的接口。它允许你在DOM树中的任何变更发生时收到通知，从而可以在这些变更发生时执行相应的操作。与传统的DOM事件不同，MutationObserver可以更高效地监听DOM的修改，并且能够监听更广泛的变化类型。
基本用法
1、创建一个 MutationObserver 实例：

· 传入一个回调函数，当监视的DOM变更时，这个回调函数会被调用。
2、调用 observe 方法：

· 指定要监视的DOM节点和需要观察的变更类型。
3、可选地：停止观察：

· 调用 disconnect 方法来停止观察。
示例代码
`
// 创建一个 MutationObserver 实例，并定义回调函数
const observer = new MutationObserver((mutationsList, observer) => {
    for (const mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('A child node has been added or removed.');
        } else if (mutation.type === 'attributes') {
            console.log(`The ${mutation.attributeName} attribute was modified.`);
        }
    }
});

// 选择要观察的节点
const targetNode = document.getElementById('someElement');

// 配置观察选项
const config = { attributes: true, childList: true, subtree: true };

// 开始观察目标节点
observer.observe(targetNode, config);

// 停止观察（根据需要调用）
// observer.disconnect();
`

## 主要参数和选项
- 回调函数：

  - 当指定的DOM变更发生时，会调用此回调函数。该函数接收两个参数：变更记录列表 (mutationsList) 和观察者实例 (observer)。
- observe 方法：

  - observe(targetNode, options)：启动对 targetNode 的监视，options 是一个配置对象，可以包含以下属性：
    - attributes：布尔值，表示是否观察属性变更。
    - childList：布尔值，表示是否观察子节点的添加或删除。
    - subtree：布尔值，表示是否观察整个子树的变更。
    - attributeOldValue：布尔值，表示是否在记录中包含属性变更前的值。
    - characterData：布尔值，表示是否观察节点文本内容或CDATA节点的变化。
    - characterDataOldValue：布尔值，表示是否在记录中包含文本内容变更前值。
    - attributeFilter：数组，指定观察特定的属性。
## 变更记录对象
回调函数中的 mutationsList 包含若干 MutationRecord 对象，每个对象描述了一个DOM变更。常用属性有：

- type：变更的类型，如 "attributes"、"childList" 或 "characterData"。
- target：受变更影响的节点。
- addedNodes：被添加的节点列表。
- removedNodes：被移除的节点列表。
- previousSibling：被添加或移除节点的前一个兄弟节点。
- nextSibling：被添加或移除节点的下一个兄弟节点。
- attributeName：变更的属性名。
- attributeNamespace：变更属性的命名空间。
- oldValue：变更前的值（如果 attributeOldValue 或 
- characterDataOldValue 选项设置为 true）。
### 使用场景
- 动态更新页面内容时监控DOM变更：可以用来监视和处理动态内容的变化。
- 实现自定义的DOM变更处理逻辑：例如自动更新特定部分的内容或执行某些操作。
- 替代一些依赖频繁轮询的场景：从而提高性能。
MutationObserver 提供了一种高效的方式来检测和响应DOM变更，相比于传统的事件监听和轮询方法，它更加灵活和高效。

# 2）