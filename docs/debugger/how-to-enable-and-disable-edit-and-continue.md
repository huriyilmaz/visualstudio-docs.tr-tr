---
title: Düzenle ve Devam'ı etkinleştirme ve devre dışı bırakma | Microsoft Docs
description: Tasarım zamanında Visual Studio Seçenekleri'nde Düzenle ve Devam'ı devre dışı bırakmayı ve etkinleştirmeyi öğrenin. Düzenle ve Devam Etmek yalnızca hata ayıklama derlemeleri için çalışır.
ms.date: 01/12/2022
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
ms.custom: devdivchpfy22
ms.openlocfilehash: e281b53871536592c73fa3445a17ecb82cc30aa2
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137095041"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Nasıl yap: Düzenle ve Devam'ı etkinleştirme ve devre dışı bırakma (C#, VB, C++)

Tasarım zamanında Visual Studio **Seçenekler iletişim kutusunda** Düzenle ve **Devam'ı devre** dışı bırakabilirsiniz veya etkinleştirebilirsiniz. **Düzenle ve Devam** Etmek yalnızca hata ayıklama derlemeleri için çalışır. Daha fazla bilgi için bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

Yerel C++ için **Düzenle ve Devam Etmek** için seçeneğinin kullanımı `/INCREMENTAL` gerekir. C++ içinde özellik gereksinimleri hakkında daha fazla bilgi için bu [blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) gönderisi ve Düzenle ve Devam Edin [(C++) blog gönderilerine bakın.](../debugger/edit-and-continue-visual-cpp.md)

**Düzenle ve Devam'ı etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız hata ayıklamayı durdurun ( Hata **Ayıklamayı** Durdur veya  >    + **Shift F5**).

1. Araçlar **Seçenekler menüsünde**  >  **>** (veya Hata Ayıklama Seçenekleri) >, sağ bölmede Düzenle ve   >     >   **Devam'ı** seçin.

    > [!NOTE]
    > IntelliTrace etkinse ve hem IntelliTrace olaylarını hem de çağrı bilgilerini toplarsanız Düzenle ve Devam Edin devre dışı bırakılır. Daha fazla bilgi için bkz. [IntelliTrace](../debugger/intellitrace.md).

1. C++ kodu için Yerel **Düzenlemeyi ve Devamını Etkinleştir'in seçili** olduğundan emin olun ve diğer seçenekleri ayarlayın:
    - **Devam eden değişiklikleri uygula (yalnızca yerel)**

      Seçiliyse, Visual Studio hata ayıklamaya devam ederken kod değişikliklerini otomatik olarak derler ve uygular. Aksi takdirde, Kod Değişikliklerini Uygula hata **ayıklaması kullanarak**  >  **değişiklikleri uygulayabilirsiniz.**

    - **Eski kod hakkında uyar (yalnızca yerel)**

      Seçiliyse, eski kod hakkında uyarılar verir.

1. **Tamam**’ı seçin.
