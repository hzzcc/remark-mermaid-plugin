# remark-mermaid-plugin

remark plugin to support mermaid for browser use, helpful for react-markdown

## Install

```sh
npm install remark-mermaid-plugin
```


## Usage

Our module `exampl.js` looks as follows:
```js
import ReactMarkdown from "react-markdown";
import rehypeRaw from "rehype-raw";
import rehypeStringify from "rehype-stringify";
import remarkMermaidPlugin from 'remark-mermaid-plugin';

const markdownContent = `
    ```mermaid
    graph LR
      excute1[i = 1]
      excute2[j = 0]
      excute3[i ++]
      excute4["a = arr[j], b = arr[j + 1]"]
      excute5[change a, b]
      excute6[j ++]
        judge1["i < n"]
        judge2["j < n - i"]
      judge3["a > b"]
      start --> excute1
      excute1 --> judge1
      judge1 --Y--> excute2
      excute2 --> judge2
      judge2 --Y--> excute4
      judge2 --N--> excute3
      excute3 --> judge1
      excute4 --> judge3
      judge3 --N--> judge2
      judge3 --Y--> excute5
      excute5 --> excute6
      excute6 --> judge2
      judge1 --N--> end
    ```
`

function Markdown() {

  return (
    <ReactMarkdown
      children={markdownContent}
      remarkPlugins={[
        [remarkMermaidPlugin, { theme: "dark" }],
      ]}
      rehypePlugins={[
        rehypeRaw,
        rehypeStringify,
      ]}
    />
  );
}
```