---
title: Yanlış parametre değerini geçen kişileri öğrenin | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d00327315b98c4b55797187c59db3a81ee351fb0
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350348"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Kimin Yanlış Parametre Değeri Geçirdiğini Nasıl Bulabilirim?
## <a name="problem-description"></a>Sorun Açıklaması
 Yanlış parametre değeri, işlevlerimin birine geçiriliyor. Bu işlev, tüm konumdan çağrılır. Yanlış değere ne geçirdiklerinizi nasıl öğrenebilirim?

## <a name="solution"></a>Çözüm

#### <a name="to-resolve-this-problem"></a>Bu sorunu çözmek için

1. İşlevin başlangıcında bir konum kesme noktası ayarlayın.

2. Kesme noktasına sağ tıklayın ve **koşul**' ı seçin.

3. **Kesme noktası koşulu** iletişim kutusunda, **koşul** onay kutusuna tıklayın. [Gelişmiş kesme noktaları](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)konusuna bakın.

4. Metin kutusuna, gibi bir ifade girin, `Var==3` burada `Var` Hatalı değeri içeren parametrenin adıdır ve `3` kendisine geçirilen hatalı değerdir.

5. **True ise** radyo düğmesini seçin ve **Tamam** düğmesine tıklayın.

6. Şimdi programı yeniden çalıştırın. Kesme noktası, parametrenin değeri olduğunda işlevin başlangıcında durmasına neden olur `Var` `3` .

7. Çağırma işlevini bulmak ve kaynak koduna gitmek için çağrı yığını penceresini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Kesme Noktaları](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)