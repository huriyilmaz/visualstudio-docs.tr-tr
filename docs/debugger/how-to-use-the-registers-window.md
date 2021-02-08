---
title: Hata ayıklayıcıda kayıt değerlerini görüntüle | Microsoft Docs
description: Kayıt değerlerini Visual Studio 'daki Yazmaçları penceresinde görüntüleyin. Hata ayıklama sırasında, uygulamanızda kod yürütme olarak değişiklik kaydeder.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: ea0275a5186b58c9b9a07934b95351b597a816f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845015"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Kayıt değerlerini Yazmaçları penceresinde görüntüleme (C#, C++, Visual Basic, F #)

**Yazmaçları** penceresi, Visual Studio hata ayıklama sırasında kayıt içeriğini görüntüler. Yazmaçların ve **yazmaçların** arkasındaki kavramlara yönelik yüksek düzey bir giriş için bkz. [hata ayıklama temelleri: kayıt penceresi](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Kayıt bilgileri, betik veya SQL uygulamaları için kullanılamaz.

Hata ayıklama sırasında, uygulamanızda kod yürütme olarak değişiklik kaydeder. Son zamanlarda değiştirilen değerler, **Yazmaçları** penceresinde kırmızı renkte görünür.

Dağınıklığı azaltmak için, **yazmaçların** penceresi, platform ve işlemci türüne göre değişiklik gösteren gruplara kayıtları düzenler. Kayıt gruplarını gösterebilir veya gizleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kayıt gruplarını görüntüleme ve gizleme](../debugger/how-to-display-and-hide-register-groups.md).

**Yazmaçları** penceresinde gördüğünüz bayraklarla ilgili bilgi için, bkz [. Yazmaçları penceresi hakkında](../debugger/debugging-basics-registers-window.md)

Kayıt değerlerini düzenleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kayıt değerini düzenleme](../debugger/how-to-edit-a-register-value.md).

**Yazmaçları penceresini açmak için**

1. **Araçlar** (veya **hata ayıklama**) > **seçeneklerde** hata ayıklama için **Adres düzeyinde hata ayıklamayı etkinleştir** ' i seçerek Adres düzeyinde hata ayıklamayı etkinleştirin  >  .

1. Hata ayıklama çalışırken veya bir kesme noktasında, **Hata Ayıkla**  >  **Windows**  >  **Yazmaçları**' nı seçin veya **alt** + **5**' e basın.

>[!NOTE]
>İletişim kutuları ve menü komutları, Visual Studio sürümünüz veya ayarlarınıza bağlı olarak farklılık gösterebilir. Ayarlarınızı değiştirmek için Visual Studio **araçları** menüsünde **ayarları Içeri ve dışarı aktar** ' ı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama temelleri: kayıt penceresi](../debugger/debugging-basics-registers-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
