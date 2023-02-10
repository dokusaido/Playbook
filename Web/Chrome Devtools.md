# Chrome Devtools

## Functions

- The `debug()` function

Create a breakpoint for a specified function under  certain conditions

```js
debug(postMessage, 'arguments[1] == "*"');
```

---

- The `monitorEvents()` function

Creates a logger for DOM events for monitoring purposes

```js
monitorEvents(window, 'message');
```

## Source tab
- Modify the response for certain request. Enable override under the source tab and modify any resource. All requests related to this response will be overriden.

## Proxy tab
- You can search globally though all resources by pressing *Ctrl + Shift + F*
- Select multiple filters by holding the *Ctrl* key
- View dependencies of javascript files and documents by holding the *Shift* key

## Network Conditions
- Set user agent inside the Network Conditions tab to test for XSS

## Memory
- The memory tab takes a snapshot of the memory heap. It contains all the strings in the memory. This is really useful for finding sensitive information.

## Lighthouse
- Use the Lighthouse tab to find vulnerabilities and outdates javascript libraries. Leave only the "best practices" category selected when generating a report.