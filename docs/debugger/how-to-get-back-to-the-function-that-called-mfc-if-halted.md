---
title: Durdurulmuşsa MFC 'yi çağıran işleve geri dön | Microsoft Docs
description: Visual Studio hata ayıklayıcısında yürütme durdurulmuşsa MFC 'yi çağıran işleve nasıl geri alınacağını anlayın.
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b069ef584724c0c4dbd592fb47268048c2ac6916
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803849"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. ayarlarınızı değiştirmek için **araçlar** menüsünden **içeri aktar ve dışarı aktar Ayarlar** seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Programı durdurmak ve MFC 'de sonlandırmak için **hata ayıklama** menüsündeki **kesme** komutunu kullandıysanız ve sorunun kodunuzda olduğundan eminseniz, Işlevinizde geri dönmek için çağrı yığını penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

Bazen kodunuzun ileti göndericisinin kesintiye uğramayabilir. Bu durumda, çağrı yığınında Kullanıcı kodu yoktur. Bu sorundan kaçınmak için **kesme komutu yerine kesme noktaları** (büyük olasılıkla koşullar ve isabet sayısı ile birlikte) kullanabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC 'nin çağrıldığı işleve gitme

- **Çağrı yığını** penceresini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)