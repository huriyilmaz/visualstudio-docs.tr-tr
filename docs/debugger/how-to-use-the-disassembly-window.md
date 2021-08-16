---
title: Hata ayıklayıcısında Farklı Kod | Microsoft Docs
description: Derleyici tarafından oluşturulan yönergelere karşılık gelen derleme Visual Studio göstermek için Visual Studio'da Disassembly penceresini kullanın.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 296917e01b6279c971181f79c475ab1fc590af7da3ae1bbf121a901fe91b062e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378729"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Hata ayıklayıcısında (C#, C++, Visual Basic, F#) Visual Studio kodu görüntüleme

**Disassembly penceresinde,** derleyici tarafından oluşturulan yönergelere karşılık gelen derleme kodu gösterilir. Yönetilen kodda hata ayıklarsanız, bu derleme yönergeleri microsoft derleyicisi tarafından oluşturulan Microsoft ara diline (MSIL) değil Tam Zamanında (JIT) derleyicisi tarafından oluşturulan yerel koda karşılık Visual Studio sağlar.

> [!NOTE]
> **Disassembly penceresinden tam olarak yararlanmak** için, derleme dili programlamanın [temellerini anlamayı veya öğrenin.](https://wikipedia.org/wiki/Assembly_language)

Bu özellik yalnızca adres düzeyinde hata ayıklama etkinleştirildiğinde kullanılabilir. Betik veya hata ayıklama için SQL kullanılamaz.

Derleme yönergelerine ek olarak, **Disassembly** penceresi aşağıdaki isteğe bağlı bilgileri gösterebilir:

- Her yönergenin bulunduğu bellek adresi. Yerel uygulamalar için gerçek bellek adresidir. Visual Basic veya C# için, işlevin başından bir uzaklıktır.

- Derleme kodunun türet olduğu kaynak kod.

- Kod baytları, yani gerçek makinenin bayt gösterimleri veya MSIL yönergeleri.

- Bellek adreslerinin sembol adları.

- Kaynak koduna karşılık gelen satır numaraları.

Derleme dili yönergeleri, yönerge adlarının kısaltmaları olan *mnemonics*  ve değişkenler, yazmacı ve sabitler için sembollerden oluşur. Her makine dili yönergesi, isteğe bağlı olarak bir derleme dili mnemonik ile ve ardından bir veya daha fazla simgeyle temsil ediliyor.

Derleme kodu yoğun olarak işlemci yazmalarına veya yönetilen kod için ortak dil çalışma zamanı kayıtlarına dayandır. Yazmazların **içeriğini incelemeye olanak** sağlayan Yazmacalar **penceresiyle** birlikte Deassembly penceresini kullanabilirsiniz.

Makine kodu yönergelerini derleme dili yerine ham sayısal biçimlerinde görüntülemek için  Bellek penceresini kullanın veya **Disassembly** penceresindeki kısayol menüsünden Kod Baytları'ı seçin. 

## <a name="use-the-disassembly-window"></a>Disassembly penceresini kullanma

**Disassembly penceresini etkinleştirmek için** Araçlar Seçenekler Hata Ayıklama altında Adres düzeyinde hata   >    >   **ayıklamayı etkinleştir'i seçin.**

Hata ayıklama sırasında **Deassembly penceresini** açmak için,  >  **Windows'yi** seçin veya Alt  + **8 tuşuna basın.**

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

İsteğe bağlı bilgileri açmak veya kapatmak  için, Ayır penceresine sağ tıklayın ve kısayol menüsünde istenen seçenekleri ayarlayın veya silin.

Sol kenar boşluğundaki sarı ok, geçerli yürütme noktasını işaretler. Yerel kod için yürütme noktası CPU'nun program sayacına karşılık gelen bir koddur. Bu konum, programda yürütülecek sonraki yönergeyi gösterir.

## <a name="see-also"></a>Ayrıca bkz.

* [Bellekte disk belleğini yukarı veya aşağı](../debugger/how-to-page-up-or-down-in-memory.md)
* [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
* [Nasıl: Yazmazlar penceresini kullanma](../debugger/how-to-use-the-registers-window.md)