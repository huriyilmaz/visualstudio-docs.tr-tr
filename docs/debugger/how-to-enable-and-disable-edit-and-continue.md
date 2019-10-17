---
title: "Nasıl yapılır: Düzenle ve devam et 'i etkinleştirme ve devre dışı bırakma | Microsoft Docs"
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430527"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Nasıl yapılır: Düzenle ve devam et 'i etkinleştirme veC#devre dışı bırakma C++(, vb,)

Tasarım zamanında Visual Studio **seçenekleri** Iletişim kutusunda **Düzenle ve devam et ' i** etkinleştirebilir veya devre dışı bırakabilirsiniz. **Düzenle ve devam et** yalnızca hata ayıklama yapılarında geçerlidir. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

Yerel C++, **Düzenle ve devam et** için `/INCREMENTAL` seçeneğini kullanmanız gerekir. İçindeki C++özellik gereksinimleri hakkında daha fazla bilgi için bu [blog gönderisi](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) ve [Düzenle ve devam et (C++)](../debugger/edit-and-continue-visual-cpp.md)bölümüne bakın.

**Düzenle ve devam et 'i etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız, hata ayıklamayı durdurun (**hata ayıkla** > **hata ayıklamayı durdur** veya **SHIFT**+**F5**).

1. **Araçlar** > **seçenekleri** > (veya **hata ayıklama** > **seçenekleri**) > **hata**ayıklama  > **genel**, sağ bölmedeki **Düzenle ve devam et** ' i seçin.

    > [!NOTE]
    > IntelliTrace etkinleştirilmişse ve hem IntelliTrace olaylarını hem de çağrı bilgilerini toplayıp, Düzenle ve devam et devre dışı bırakıldı. Daha fazla bilgi için bkz. [IntelliTrace](../debugger/intellitrace.md).

1. Kod C++ Için **Yerel Düzenle ve devam et 'i etkinleştir** ' in seçili olduğundan emin olun ve ek seçenekleri ayarlayın:
    - **Değişiklikleri devam ederken Uygula (yalnızca yerel)**

      Seçilirse, bir kesme durumundan hata ayıklamaya devam ettiğinizde, Visual Studio otomatik olarak kod değişikliklerini derler ve uygular. Aksi takdirde, **hata ayıkla** > **kod değişikliklerini Uygula**' yı kullanarak değişiklikleri uygulamayı seçebilirsiniz.

    - **Eski kod hakkında uyar (yalnızca yerel)**

      Seçilirse, eski kod hakkında uyarı verir.

1. **Tamam**'a tıklayın.
