---
title: Durdurulmuşsa MFC 'yi çağıran işleve geri dön | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b05e703958fe7a1c630b542522f1f33b0fe5981
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600284"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Programı durdurmak ve MFC 'de sonlandırmak için **hata ayıklama** menüsündeki **kesme** komutunu kullandıysanız ve sorunun kodunuzda olduğundan eminseniz, Işlevinizde geri dönmek için çağrı yığını penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

Bazen kodunuzun ileti göndericisinin kesintiye uğramayabilir. Bu durumda, çağrı yığınında Kullanıcı kodu yoktur. Bu sorundan kaçınmak için **kesme komutu yerine kesme noktaları** (büyük olasılıkla koşullar ve isabet sayısı ile birlikte) kullanabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC 'nin çağrıldığı işleve gitme

- **Çağrı yığını** penceresini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)