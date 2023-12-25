---
title: react富文本编辑器react-draft-wysiwyg
excerpt: 记录react富文本编辑器react-draft-wysiwyg的使用
categories: 
  - 前端
tags: 
  - react
  - 工具组件
index_img: https://ooo.0x0.ooo/2023/12/24/OKRApU.png
banner_img: https://ooo.0x0.ooo/2023/12/24/OKRApU.png
date: 2023-12-24 20:20:00
---
# react富文本编辑器react-draft-wysiwyg的使用

## 一、前言以及效果图

本文主要记录react中富文本编辑器react-draft-wysiwyg的使用
(npm中react-draft-wysiwyg的官方地址为https://www.npmjs.com/package/react-draft-wysiwyg)

![富文本编辑器](https://ooo.0x0.ooo/2023/12/24/OKR1nt.png)

## 二、使用步骤

### 1.下载依赖

```jsx
npm install react-draft-wysiwyg
npm install draft-js
npm install draftjs-to-html
npm install html-to-draftjs
```

### 2.引入相关依赖和样式

```jsx
import { Editor } from 'react-draft-wysiwyg';
import 'react-draft-wysiwyg/dist/react-draft-wysiwyg.css';
import { EditorState, convertToRaw, ContentState } from 'draft-js';
import draftToHtml from 'draftjs-to-html';
import htmlToDraft from 'html-to-draftjs';
```

### 3.初始化

react-draft-wysiwyg一般是被当做一个子组件进行使用的。

“子组件”核心代码：

```jsx
// src\components\News\Editor.jsx
import React,{useEffect,useState} from 'react'
//引入的依赖和样式
import { Editor } from 'react-draft-wysiwyg';
import 'react-draft-wysiwyg/dist/react-draft-wysiwyg.css';
import { EditorState, convertToRaw, ContentState } from 'draft-js';
import draftToHtml from 'draftjs-to-html';
import htmlToDraft from 'html-to-draftjs';
export default function NewsEditor(props) {
  const [editorState,setEditorState]=useState("");
    
  useEffect(() => {
    // 初始化富文本
    const html = props.content;
    if (html === undefined) return
    const contentBlock = htmlToDraft(html);
    if (contentBlock) {
      const contentState = ContentState.createFromBlockArray(contentBlock.contentBlocks);
      const editorState = EditorState.createWithContent(contentState);
      setEditorState(editorState)
    }
  }, [props.content])
    
  return (
    <div>
      <Editor
        editorState={editorState}
        toolbarClassName="toolbarClassName"
        wrapperClassName="wrapperClassName"
        editorClassName="editorClassName"
        onEditorStateChange={(editorContent) => setEditorState(editorContent)}
        onBlur={() => {
          // console.log()
          // 失去焦点时，把内容传给父组件
          props.getContent(draftToHtml(convertToRaw(editorState.getCurrentContent())));
        }}
      />
    </div>
  )
}

```

### 4.在父组件中使用

```jsx
import React, { useState, useRef, useEffect } from 'react'
// 引入自定义的富文本子组件
import NewsEditor from "@/components/News/NewsEditor"
export default function NewsAdd(props) {
//在父组件中定义的富文本框中的内容
  const [content, setContent] = useState("")
  return (
    <div>
         <NewsEditor
            content={content}
            getContent={(value) => { setContent(value); console.log("content", content); }}
          />
    </div >
  )
}

```

## 三、验证

![验证成功](https://ooo.0x0.ooo/2023/12/24/OKRN6j.png)