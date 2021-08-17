---
title: Düzenle ve devam et 'i etkinleştir ve devre dışı bırak | Microsoft Docs
description: tasarım zamanında Visual Studio seçeneklerinde düzenle ve devam et seçeneklerini devre dışı bırakmayı ve etkinleştirmeyi öğrenin. Düzenle ve devam et yalnızca hata ayıklama yapılarında geçerlidir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 8e01926f5ec245fe611e72f9f15b8da780d9423e38e568e2992869ebd9a55db1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379288"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Nasıl yapılır: Düzenle ve devam et 'i etkinleştirme ve devre dışı bırakma (C#, VB, C++)

tasarım zamanında Visual Studio **seçenekleri** iletişim kutusunda **düzenle ve devam et ' i** etkinleştirebilir veya devre dışı bırakabilirsiniz. **Düzenle ve devam et** yalnızca hata ayıklama yapılarında geçerlidir. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

Yerel C++ için **Düzenle ve devam et** seçeneğinin kullanılmasını gerektirir `/INCREMENTAL` . C++ ' ta özellik gereksinimleri hakkında daha fazla bilgi için bu [blog gönderisi](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) ve [düzenleme ve devam etme (C++)](../debugger/edit-and-continue-visual-cpp.md)bölümüne bakın.

**Düzenle ve devam et 'i etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız, hata ayıklamayı **durdurun (hata ayıklama**  >  **durdurma** veya **SHIFT** + **F5**).

1. **Araç**  >  **seçeneklerinde** > (veya **hata ayıklama**  >  **seçenekleri**) genel **hata ayıklama**>  >  , sağ bölmedeki **Düzenle ve devam et** ' i seçin.

    > [!NOTE]
    > IntelliTrace etkinleştirilmişse ve hem IntelliTrace olaylarını hem de çağrı bilgilerini toplayıp, Düzenle ve devam et devre dışı bırakıldı. Daha fazla bilgi için bkz. [IntelliTrace](../debugger/intellitrace.md).

1. C++ kodu için **Yerel Düzenle ve devam et 'ı etkinleştir** ' in seçili olduğundan emin olun ve ek seçenekleri ayarlayın:
    - **Değişiklikleri devam ederken Uygula (yalnızca yerel)**

      seçilirse, kesme durumundan hata ayıklamaya devam ettiğinizde Visual Studio otomatik olarak derlenir ve kod değişikliklerini uygular. Aksi takdirde, **Hata Ayıkla**  >  **kod değişikliklerini Uygula**' yı kullanarak değişiklikleri uygulamayı seçebilirsiniz.

    - **Eski kod hakkında uyar (yalnızca yerel)**

      Seçilirse, eski kod hakkında uyarı verir.

1. **Tamam**'a tıklayın.
