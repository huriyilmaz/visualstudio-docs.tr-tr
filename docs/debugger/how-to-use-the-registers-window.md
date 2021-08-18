---
title: Hata ayıklayıcıda kayıt değerlerini görüntüle | Microsoft Docs
description: Kayıt değerlerini Visual Studio kayıtları penceresinde görüntüleyin. Hata ayıklama sırasında, uygulamanızda kod yürütme olarak değişiklik kaydeder.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 94048bef497f21a77e3e94d583f26d65ceef53553725195ea1100ab5313b9887
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453246"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>kayıt değerlerini yazmaçları penceresinde görüntüleme (C#, C++, Visual Basic, F #)

**yazmaçları** penceresi Visual Studio hata ayıklama sırasında kayıt içeriğini görüntüler. Yazmaçların ve **yazmaçların** arkasındaki kavramlara yönelik yüksek düzey bir giriş için bkz. [hata ayıklama temelleri: kayıt penceresi](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> kayıt bilgileri, betik veya SQL uygulamaları için kullanılamaz.

Hata ayıklama sırasında, uygulamanızda kod yürütme olarak değişiklik kaydeder. Son zamanlarda değiştirilen değerler, **Yazmaçları** penceresinde kırmızı renkte görünür.

Dağınıklığı azaltmak için, **yazmaçların** penceresi, platform ve işlemci türüne göre değişiklik gösteren gruplara kayıtları düzenler. Kayıt gruplarını gösterebilir veya gizleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kayıt gruplarını görüntüleme ve gizleme](../debugger/how-to-display-and-hide-register-groups.md).

**Yazmaçları** penceresinde gördüğünüz bayraklarla ilgili bilgi için, bkz [. Yazmaçları penceresi hakkında](../debugger/debugging-basics-registers-window.md)

Kayıt değerlerini düzenleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kayıt değerini düzenleme](../debugger/how-to-edit-a-register-value.md).

**Yazmaçları penceresini açmak için**

1. **Araçlar** (veya **hata ayıklama**) > **seçeneklerde** hata ayıklama için **Adres düzeyinde hata ayıklamayı etkinleştir** ' i seçerek Adres düzeyinde hata ayıklamayı etkinleştirin  >  .

1. hata ayıklama çalışırken veya bir kesme noktasında **hata ayıkla**  >  **Windows**  >  **yazmaçları** seçin veya **Alt** + **5**' e basın.

>[!NOTE]
>iletişim kutuları ve menü komutları, Visual Studio sürümüne veya ayarlarınıza göre farklılık gösterebilir. ayarlarınızı değiştirmek için Visual Studio **araçlar** menüsünden **içeri aktar ve dışarı aktar Ayarlar** seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama temelleri: kayıt penceresi](../debugger/debugging-basics-registers-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
