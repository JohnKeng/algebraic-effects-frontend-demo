# Algebraic Effects in Frontend Demo / 前端代數效應演示

This repository is a demonstration of how algebraic effects and effect handlers can be utilized for UI rendering in vanilla JavaScript.

示例演示了如何在JavaScript中模擬代數效應和效果處理器（Algebraic Effects and Handlers）的概念，特別是在構建用戶界面（UI）時。


## Overview

Algebraic effects are a programming construct used to represent side effects in a program. This demo provides a simple implementation to manage UI side effects using this concept.

代數效應是一種用於表示程序中副作用的編程結構。這個演示提供了一個簡單的實現，使用這一概念來管理UI副作用。

## Features

- 集中式副作用管理 / Centralized Side Effect Management: 所有的副作用都在一個中心位置定義，便於管理和維護。All side effects are managed in a centralized location for ease of management and maintenance.

- 副作用抽象化 / Abstracted Side Effect Execution: 副作用執行通過一個簡單的介面，抽象化了實現細節。Side effects are executed through a simple interface that abstracts away the implementation details.

- 統一錯誤處理 / Unified Error Handling: 為錯誤處理專門設計的效應，允許在應用程序中一致地管理錯誤。A dedicated effect for handling errors allows for consistent error management throughout the application.

- 數據驅動的組件構建 / Data-Driven Component Construction: UI組件基於數據構建，促進了可重用性和關注點分離。UI components are built based on data, which promotes reusability and separation of concerns.

- 模擬異步數據獲取 / Simulated Asynchronous Data Fetching: 異步行為被模擬出來，以便於與真實的數據獲取機制整合。Asynchronous behavior is simulated to facilitate integration with real data fetching mechanisms.

- 容錯性設計 / Resilient Design: 應用程序能夠在遇到缺失數據時通過錯誤效應提供清晰的反饋，從而優雅地處理。The application gracefully handles missing data by providing clear feedback through error effects.


## Structure

- `effectHandlers`: An object that holds all the side effects and their associated handling functions.
- `defineEffect`: A function to register an effect and its handler.
- `performEffect`: A function that performs an effect given its name and arguments.
- `componentBuilders`: A collection of functions that return HTML strings for different UI components, throwing errors if required data is missing.
- `mockData`: Simulated data to demonstrate the UI rendering based on data.

## Getting Started

To view the demo:
1. Clone the repository.
2. Open the `index.html` in a browser.

### Example Usage

Below is an example of how a UI component is created using the system:

以下是使用該系統創建UI組件的示例：

```javascript
// Register an effect for fetching data
defineEffect('fetchData', (callback) => {
    // Simulate fetching data asynchronously
    setTimeout(() => callback(mockData), 1000);
});

// Register an effect for rendering content to the DOM
defineEffect('render', (elementId, content) => {
    const element = document.getElementById(elementId);
    if (element) {
        element.innerHTML = content;
    } else {
        performEffect('error', `Element with ID "${elementId}" not found.`);
    }
});

// Perform the 'fetchData' effect and then render the UI with the data
performEffect('fetchData', (data) => {
    const postsHtml = data.posts.map(componentBuilders.createPostItem).join('');
    performEffect('render', 'app', `<ul>${postsHtml}</ul>`);
});

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



