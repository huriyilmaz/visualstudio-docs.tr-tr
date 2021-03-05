---
title: Yanlış parametre değerini geçen kişileri öğrenin | Microsoft Docs
description: İşlevinizi hangi kodun çağırmasının ve yanlış parametre değeri geçirdiklerinizin olduğunu fark edebilirsiniz. Bunu yapmak için koşullu kesme noktası kullanmayı öğrenin.
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cb4b3c41b46817d15a13626983ccf55ffa9acc5f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155186"
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
- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Kesme noktaları](/previous-versions/ktf38f66(v=vs.100))
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
