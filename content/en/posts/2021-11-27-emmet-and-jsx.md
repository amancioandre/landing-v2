---
title: "Emmet and JSX"
date: 2021-11-27T09:06:47-03:00
type: "post"
draft: false
featured-img: "https://images.unsplash.com/photo-1638005906847-672f9fe8061d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8"
topics: ["Setup", "Programming", "React"]
tags: ["VSCode", "autocomplete", "emmet", "JSX", "TSX"]
categories: ["VSCode", "React"]
description: ""
---

If you've ever written HTML tags in an JSX file, you would already have noticed that you lost that flavourish VSCode Emmet autocomplete. Sit back and relax, where there is a will there is a way.

<!-- !more -->

{{<figure src="https://images.unsplash.com/photo-1638005906847-672f9fe8061d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8" title="Photo by Ferhat Deniz Fors on Unsplash">}}

All you have to do is `cmd+shift+p` on your Mac, or `ctrl+ship+p` for Linux/Windows to open your Profile>Settings/Json and add the following lines:

```json
{
    "emmet.includedLanguages": {
        "javascript": "javascriptreact",
        "typescript": "typescriptreact"
    }
}
```

It will work as is, but if you, like me, got some trouble "tabbing" the autocomplete, you can try adding also this line:

```json
{
    "emmet.triggetExpansionOnTab": true,
    "files.associations": {
        "*.js": "javascriptreact",
        "*.ts": "typescriptreact"
    }
}
```

Another cool thing to point out is that, if you don't want **Emmet** on all your files, you can add these lines to your `.vscode/settings.json` for your project. It will live only there.

Hope this helps, I know it did for me!