# Uncommon HTML Bug: Premature innerHTML Modification

This repository demonstrates a subtle bug that can occur in HTML when JavaScript attempts to manipulate the `innerHTML` property of an element before that element has been fully parsed and added to the Document Object Model (DOM). This often happens when the script is placed within the `<head>` section or before the element it intends to modify.

The `bug.html` file shows the buggy code, and the `bugSolution.html` file provides a corrected version.

## Bug Description

The primary issue lies in trying to access and modify an element's `innerHTML` before the browser has fully rendered it.  This leads to either a runtime error (if strict error handling is in place) or silently failing to update the element's content.

## Solution

The solution is to ensure that the JavaScript code executes *after* the element is ready in the DOM. This can be achieved through different methods including:

1. **Placing the script at the end of the `<body>`:** This is the simplest method; it guarantees the element will be available.
2. **Using `DOMContentLoaded` event listener:** This method offers more control and is generally preferred for larger applications. This event fires when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.
3. **Using `window.onload` event listener:** This will wait for all resources (images, stylesheets) to be loaded.

The `bugSolution.html` showcases how to fix the issue using the `DOMContentLoaded` event.