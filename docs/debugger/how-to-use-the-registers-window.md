---
title: Hata ayıklayıcısının kayıt değerlerini | Microsoft Docs
description: Yazmazlar penceresindeki kayıt değerlerini Visual Studio. Hata ayıklama sırasında, uygulamanıza kod yürütülürken değerleri kaydetme değişir.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2648f74453f51cd8d655ccb0c2344eb1030c1ed
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385402"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Yazmaçlar penceresinde yazmaç değerlerini görüntüleme (C#, C++, Visual Basic, F#)

**Yazmazlar penceresi,** hata ayıklama sırasında Visual Studio görüntüler. Yazmalıkların ve Yazmanlar penceresinin  arkasındaki kavramlara üst düzey bir giriş için bkz. Temel hata [ayıklama: Yazmanlar penceresi.](../debugger/debugging-basics-registers-window.md)

> [!NOTE]
> Kayıt bilgileri betik veya SQL uygulamaları için kullanılamaz.

Hata ayıklama sırasında, uygulamanıza kod yürütülürken değerleri kaydetme değişir. Kısa süre önce değiştirilen değerler Yazmanlar penceresinde **kırmızı renkle** gösterilir.

Dağınıklığı azaltmak için **Yazmalar penceresi,** kayıtları platforma ve işlemci türüne göre değişen gruplar halinde düzenleyebilir. Kayıt gruplarını görüntü veya gizleysiniz. Daha fazla bilgi için, [bkz. How to: Display and hide register groups](../debugger/how-to-display-and-hide-register-groups.md).

Yazmanlar penceresinde gördüğünüz bayraklar hakkında **bilgi için** [bkz. Yazmanlar penceresi hakkında](../debugger/debugging-basics-registers-window.md)

Kayıt değerlerini düzenleyebilirsiniz. Daha fazla bilgi için [bkz. Nasıl: Yazmadır değerini düzenleme.](../debugger/how-to-edit-a-register-value.md)

**Yazmazlar penceresini açmak için**

1. Araçlar (veya Hata **Ayıkla)** menüsünden Adres **düzeyinde** hata ayıklamayı etkinleştir'i  seçerek adres düzeyinde hata ayıklamayı etkinleştirin > **Ayıklama**  >  **seçeneklerinden birini belirleyin.**

1. Hata ayıklama çalışırken veya bir kesme noktası üzerinde Hata Ayıkla'ya tıklayın veya  >    >   **Alt** + **5'e basın.**

>[!NOTE]
>İletişim kutuları ve menü komutları, uygulama sürümünüz veya Visual Studio farklılık gösterebilir. Ayarlarınızı değiştirmek için, Visual Studio Tools **menüsünde** Ayarları İçeri ve Dışarı **Aktar'ı** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

### <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklamanın temelleri: Yazmalar penceresi](../debugger/debugging-basics-registers-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
