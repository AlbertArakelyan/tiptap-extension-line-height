# tiptap-extensions-line-height

![tiptap-extension-line-height](https://github.com/AlbertArakelyan/tiptap-extension-line-height/blob/main/src/assets/screenshot.gif?raw=true)

[Tiptap](https://tiptap.dev/) is a suite of open source content editing and real-time collaboration tools for developers building apps like Notion or Google Docs.

This package provides the ability to adjust the line height of the tip tap text or paragraph.

<!-- It has been tested in 
[React](https://codesandbox.io/p/some_sandbox_link), and [NextJS](https://codesandbox.io/p/some_sandbox_link) -->

## Installation

You can install it using npm:

```bash
$ npm install tiptap-extensions-line-height
```

## Usage

```tsx
import StarterKit from '@tiptap/starter-kit';
import LineHeight from 'tiptap-extensions-resize-image';
import { EditorContent, useEditor } from '@tiptap/react';

export const Editor = () => {
  const editor = useEditor({
    extensions: [StarterKit, LineHeight],
  });

  const lineHeights = [
    { label: 'Normal', value: 'normal' },
    { label: 'Simple', value: '1' },
    { label: '1.15', value: '1.15' },
    { label: '1.5', value: '1.5' },
    { label: 'Double', value: '2' },
  ];

  const handleLineHeightChange = (e: React.ChangeEvent<HTMLSelectElement>) => {
    editor?.chain().focus().setLineHeight(e.target.value).run();
  }

  return (
    <div>
      <select onChange={handleLineHeightChange}>
        {lineHeights.map((lineHeight) => (
          <option key={lineHeight.value} value={lineHeight.value}>
            {lineHeight.label}
          </option>
        ))}
      </select>
      <EditorContent editor={editor} />
    </div>
  );
};

```