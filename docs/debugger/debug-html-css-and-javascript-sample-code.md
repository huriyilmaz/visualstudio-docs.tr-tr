---
title: Hata ayıklama HTML ve CSS örnek kodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 460419d976211747c44f156a5821b88b75aa2e6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745542"
---
# <a name="debug-html-and-css-sample-code"></a>HTML ve CSS örnek kod hatalarını ayıklama

Bu konudaki kod [hızlı başlangıç: hata AYıKLA HTML ve CSS](../debugger/quickstart-debug-html-and-css.md)için örnek dosyadır. Hızlı başlangıçta tasarımda bulunan hatalar kodun bu sürümünde düzeltilmiştir.

## <a name="sample-code"></a>Örnek Kod
Aşağıdaki HTML kodu \<body> hızlı başlangıçtaki etiketinde kullanılır.

```html
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"
         style="display:none">
    <div class="fixedItem" >
        <img src="#" data-win-bind="src: flipImg" />
    </div>
</div>
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
</div>
```

Aşağıdaki CSS, default. css ' ye yapılan eklemeleri gösterir.

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

Aşağıdaki kod örneği default.js içindeki tüm JavaScript kodunu gösterir. Bu kod için WinJS ad alanlarına yapılan başvurular, şablonun default.html dosyasıdır.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
        myData[x] = { flipImg: "/images/logo.png" }
    };

    var pages = new WinJS.Binding.List(myData, { proxy: true });

    app.onactivated = function (args) {
        if (args.detail.kind === activation.ActivationKind.launch) {
            if (args.detail.previousExecutionState !==
            activation.ApplicationExecutionState.terminated) {
                // TODO: . . .
            } else {
                // TODO: . . .
            }
            args.setPromise(WinJS.UI.processAll());

            updateImages();
        }
    };

    function updateImages() {

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    };

    app.oncheckpoint = function (args) {
    };

    app.start();

    var publicMembers = {
        items: pages
    };

    WinJS.Namespace.define("Data", publicMembers);

})();
```

## <a name="see-also"></a>Ayrıca bkz.
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
