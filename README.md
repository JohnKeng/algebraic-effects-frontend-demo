# Algebraic Effects in Frontend Demo / 前端代數效應演示

This repository demonstrates the usage of algebraic effects and handlers for UI rendering in vanilla JavaScript without the use of frameworks like React or Vue.

這個倉庫演示了如何在不使用如React或Vue等框架的情況下，用原生JavaScript通過代數效應和處理器進行UI渲染。

## Overview

Algebraic effects are a programming construct used to represent side effects in a program. This demo provides a simple implementation to manage UI side effects using this concept.

代數效應是一種用於表示程序中副作用的編程結構。這個演示提供了一個簡單的實現，使用這一概念來管理UI副作用。

## Features

- Simple implementation of algebraic effects and handlers without frameworks. 函數式組件創建和副作用管理。

- Dedicated error handling using effects. 專門使用效應進行錯誤處理。


## Structure

- `effectHandlers`: Contains effect handlers for rendering and error handling. 包含用於渲染和錯誤處理的效果處理器。
- `componentBuilders`: Functions returning HTML strings for UI components. 用於UI組件的函數返回HTML字符串。
- `mockData`: Mock data for dynamic content rendering. 模擬數據，用於動態內容渲染。

## Getting Started

To view the demo:
1. Clone the repository.
2. Open the `index.html` in a browser.

### Example Usage

Below is an example of how a UI component is created using the system:

以下是使用該系統創建UI組件的示例：

```javascript
// Define a component
const MyComponent = props => componentBuilders.createDiv(props);

// Render the component with props
performEffect(createEffect(EFFECT_TYPES.RENDER, { 
  component: MyComponent,
  props: { id: 'my-div', className: 'my-style', content: 'Hello World!' }
}));
```

### Contributions

Contributions to improve or extend this demo are welcome. Please feel free to fork this repository and submit a pull request with your changes.

歡迎貢獻以改進或擴展此演示。請隨時fork這個倉庫並提交您的更改。

### License 

This project is open sourced under the MIT License.

該項目在MIT許可下開源。

### Acknowledgments 
This demo is for educational purposes, illustrating functional programming concepts in UI development.

這個演示是出於教育目的，說明瞭在UI開發中的函數式編程概念。



