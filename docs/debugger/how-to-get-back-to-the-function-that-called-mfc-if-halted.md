---
title: Durdurulan MFC işlevini çağıran işleve | Microsoft Docs
description: Hata ayıklayıcısında yürütme durdurulsa MFC'yi çağıran işleve Visual Studio anlıyoruz.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5cdb2ffd30b8fcf1a0dd8a9b1df8e2be21057db1
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972550"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri **ve Dışarı Ayarlar'yi** seçin.  Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

Hata Ayıklama **menüsündeki** Break  komutunu kullanarak programı durdurduysanız ve MFC'de sonlandı ve sorunun kodunda olduğundan emin olduysanız Çağrı Yığını penceresini kullanarak işlevinize geri dönebilirsiniz. Daha fazla bilgi için, [bkz. How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md).

Bazen kodunuz ileti pompasını bozabilir. Bu durumda, çağrı yığınında kullanıcı kodu yoktur. Bu sorunu önlemek için Kesme komutu yerine kesme noktaları (büyük olasılıkla koşullar ve isabet sayıları ile) **kullanabilirsiniz.** Daha fazla bilgi için [bkz. Kesme Noktaları ve İzleme Noktaları.](/previous-versions/ktf38f66(v=vs.100))

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC'nin çağrıldı olduğu işleve gidin

- Çağrı Yığını **penceresini** kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)