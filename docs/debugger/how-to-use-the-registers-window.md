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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9ab893453cb0f0603ded5220c45268dc5f0ad058
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097109"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Yazmaçlar penceresinde yazmaç değerlerini görüntüleme (C#, C++, Visual Basic, F#)

**Yazmazlar penceresi,** hata ayıklama sırasında Visual Studio görüntüler. Yazmalıkların ve Yazmanlar penceresinin  arkasındaki kavramlara üst düzey bir giriş için bkz. Temel hata [ayıklama: Yazmanlar penceresi.](../debugger/debugging-basics-registers-window.md)

> [!NOTE]
> Kayıt bilgileri betik veya uygulama SQL kullanılamaz.

Hata ayıklama sırasında, uygulamanıza kod yürütülürken değerleri kaydetme değişir. Kısa süre önce değiştirilen değerler Yazmanlar penceresinde **kırmızı renkle** gösterilir.

Dağınıklığı azaltmak için **Yazmalar penceresi,** kayıtları platform ve işlemci türüne göre değişen gruplar halinde düzenleyebilir. Kayıt gruplarını görüntü veya gizleysiniz. Daha fazla bilgi için, [bkz. How to: Display and hide register groups](../debugger/how-to-display-and-hide-register-groups.md).

Yazmanlar penceresinde gördüğünüz bayraklar hakkında **bilgi için** [bkz. Yazmanlar penceresi hakkında](../debugger/debugging-basics-registers-window.md)

Kayıt değerlerini düzenleyebilirsiniz. Daha fazla bilgi için [bkz. Nasıl 2.](../debugger/how-to-edit-a-register-value.md)

**Yazmazlar penceresini açmak için**

1. Araçlar (veya Hata **Ayıkla)** menüsünden Adres **düzeyinde** hata ayıklamayı etkinleştir'i  seçerek adres düzeyinde hata >   >  **ayıklamayı etkinleştirin.**

1. Hata ayıklama çalışırken veya bir kesme noktası üzerinde Hata Ayıkla'Windows Registers 'ı seçin veya  >    >  Alt  + **5 tuşuna basın.**

>[!NOTE]
>İletişim kutuları ve menü komutları, uygulama sürümünüze veya ayarlarınıza Visual Studio farklılık gösterebilir. Ayarlarınızı değiştirmek için, Visual Studio Tools **menüsünde İçeri ve Dışarı** Aktar'Ayarlar'ı seçin.  Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

### <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklamanın temelleri: Yazmalar penceresi](../debugger/debugging-basics-registers-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
