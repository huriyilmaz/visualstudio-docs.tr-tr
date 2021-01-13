---
title: Durdurulmuşsa MFC 'yi çağıran işleve geri dön | Microsoft Docs
description: Visual Studio hata ayıklayıcısında yürütme durdurulmuşsa MFC 'yi çağıran işleve nasıl geri alınacağını anlayın.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 751688b72a7603e76733906775c594cd28e78c28
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148955"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Programı durdurmak ve MFC 'de sonlandırmak için **hata ayıklama** menüsündeki **kesme** komutunu kullandıysanız ve sorunun kodunuzda olduğundan eminseniz, Işlevinizde geri dönmek için çağrı yığını penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

Bazen kodunuzun ileti göndericisinin kesintiye uğramayabilir. Bu durumda, çağrı yığınında Kullanıcı kodu yoktur. Bu sorundan kaçınmak için **kesme komutu yerine kesme noktaları** (büyük olasılıkla koşullar ve isabet sayısı ile birlikte) kullanabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC 'nin çağrıldığı işleve gitme

- **Çağrı yığını** penceresini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)