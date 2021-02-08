---
title: Hata ayıklayıcıda ayrıştırılmış kodu görüntüle | Microsoft Docs
description: Derleyici tarafından oluşturulan yönergelere karşılık gelen derleme kodunu göstermek için Visual Studio 'daki ayrıştırma penceresini kullanın.
ms.custom: SEO-VS-2020, seodec18
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
ms.workload:
- multiple
ms.openlocfilehash: b7d772ed757b231ce68fe27b74123f7f5878d0ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845054"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında ayrıştırılmış kodu görüntüleme (C#, C++, Visual Basic, F #)

**Ayrıştırılmış** pencere, derleyici tarafından oluşturulan yönergelere karşılık gelen derleme kodunu gösterir. Yönetilen kodda hata ayıklaması yapıyorsanız, bu derleme yönergeleri, Visual Studio derleyicisi tarafından oluşturulan Microsoft ara dili (MSIL) değil, tam zamanında (JıT) derleyicisi tarafından oluşturulan yerel koda karşılık gelir.

> [!NOTE]
> **Ayrıştırma** penceresinin tam avantajlarından yararlanabilmek için, [Derleme dili programlama](https://wikipedia.org/wiki/Assembly_language)hakkında temel bilgileri anlayın veya öğrenin.

Bu özellik yalnızca adres düzeyinde hata ayıklama etkinse kullanılabilir. Betik veya SQL hata ayıklama için kullanılamaz.

Bütünleştirilmiş kod yönergelerine ek olarak, **ayrıştırılmış** bir pencere aşağıdaki isteğe bağlı bilgileri gösterebilir:

- Her yönergenin bulunduğu bellek adresi. Yerel uygulamalar için gerçek bellek adresidir. Visual Basic veya C# ' de, işlevin başından itibaren bir uzaklığa sahip olur.

- Derleme kodunun türetildiği kaynak kodu.

- Kod baytları, diğer bir deyişle, gerçek makinenin veya MSIL yönergelerinin bayt temsilleri.

- Bellek adreslerinin sembol adları.

- Kaynak koda karşılık gelen satır numaraları.

Derleme dili yönergeleri, yönerge adları için kısaltmalar ve değişkenler, Yazmaçları ve sabitler için *semboller* olan *anımsatıcıları* içerir. Her makine dili yönergesi, isteğe bağlı olarak bir veya daha fazla sembol tarafından bir derleme dili anımsatıcı tarafından temsil edilir.

Derleme kodu, işlemci kayıtlarına veya yönetilen kod, ortak dil çalışma zamanı saklayıcıları için yoğun bir şekilde bağımlıdır. **Ayrıştırma** penceresini, kayıt içeriğini incelemenize olanak sağlayan **Yazmaçları** penceresiyle birlikte kullanabilirsiniz.

Makine kodu yönergelerini, derleme dili yerine ham sayısal biçiminde görüntülemek için, **bellek** penceresini kullanın veya **ayrıştırma** penceresindeki kısayol menüsünden **kod baytları** ' ni seçin.

## <a name="use-the-disassembly-window"></a>Ayrıştırma penceresini kullanma

**Ayrıştırma** penceresini etkinleştirmek için, **Araçlar**  >  **Seçenekler**  >  **hata ayıklama** altında **Adres düzeyinde hata ayıklamayı etkinleştir**' i seçin.

Hata ayıklama sırasında **ayrıştırma** penceresini açmak için **Windows**  >  **ayrıştırılmış derleme** ' yi seçin veya **alt** + **8**' e basın.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

İsteğe bağlı bilgileri açmak veya kapatmak için, **ayrıştırma** penceresinde sağ tıklayın ve kısayol menüsünde istenen seçenekleri ayarlayın veya temizleyin.

Sol kenar boşluğunda sarı bir ok, geçerli yürütme noktasını işaret ediyor. Yerel kod için, yürütme noktası CPU 'nun program sayacına karşılık gelir. Bu konum, programınızda yürütülecek sonraki yönergeyi gösterir.

## <a name="see-also"></a>Ayrıca bkz.

* [Belleği belleği artırma veya azaltma](../debugger/how-to-page-up-or-down-in-memory.md)
* [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
* [Nasıl yapılır: Yazmaçları penceresini kullanma](../debugger/how-to-use-the-registers-window.md)