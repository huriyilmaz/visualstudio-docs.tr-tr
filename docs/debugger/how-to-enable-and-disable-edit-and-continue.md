---
title: Düzenleme ve devam etmeyi etkinleştirme ve devre dışı bırakma | Microsoft Docs
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: how-to
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
ms.openlocfilehash: 1907a67412a787148da7a6679e173383e2bb7423
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349672"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Nasıl yapılır: Düzenle ve devam et 'i etkinleştirme ve devre dışı bırakma (C#, VB, C++)

Tasarım zamanında Visual Studio **seçenekleri** Iletişim kutusunda **Düzenle ve devam et ' i** etkinleştirebilir veya devre dışı bırakabilirsiniz. **Düzenle ve devam et** yalnızca hata ayıklama yapılarında geçerlidir. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

Yerel C++ için **Düzenle ve devam et** seçeneğinin kullanılmasını gerektirir `/INCREMENTAL` . C++ ' ta özellik gereksinimleri hakkında daha fazla bilgi için bu [blog gönderisi](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) ve [düzenleme ve devam etme (C++)](../debugger/edit-and-continue-visual-cpp.md)bölümüne bakın.

**Düzenle ve devam et 'i etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız, hata ayıklamayı**durdurun (hata ayıklama**  >  **durdurma** veya **SHIFT** + **F5**).

1. **Araç**  >  **seçeneklerinde** > (veya **hata ayıklama**  >  **seçenekleri**) genel **hata ayıklama**>  >  **General**, sağ bölmedeki **Düzenle ve devam et** ' i seçin.

    > [!NOTE]
    > IntelliTrace etkinleştirilmişse ve hem IntelliTrace olaylarını hem de çağrı bilgilerini toplayıp, Düzenle ve devam et devre dışı bırakıldı. Daha fazla bilgi için bkz. [IntelliTrace](../debugger/intellitrace.md).

1. C++ kodu için **Yerel Düzenle ve devam et 'ı etkinleştir** ' in seçili olduğundan emin olun ve ek seçenekleri ayarlayın:
    - **Değişiklikleri devam ederken Uygula (yalnızca yerel)**

      Seçilirse, bir kesme durumundan hata ayıklamaya devam ettiğinizde, Visual Studio otomatik olarak kod değişikliklerini derler ve uygular. Aksi takdirde, **Hata Ayıkla**  >  **kod değişikliklerini Uygula**' yı kullanarak değişiklikleri uygulamayı seçebilirsiniz.

    - **Eski kod hakkında uyar (yalnızca yerel)**

      Seçilirse, eski kod hakkında uyarı verir.

1. **Tamam**’a tıklayın.
