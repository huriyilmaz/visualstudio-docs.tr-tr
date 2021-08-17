---
title: Yanlış parametre değerini kimlerin geçirmesi olduğunu | Microsoft Docs
description: İşlevini çağıran kodu ve hatalı parametre değerini geçirmeyi bulabilirsiniz. Bunu yapmak için koşullu kesme noktası kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ea7f361905fa87630c2db2a8371975c056d8211548262fb551f6d1129d278f0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453951"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Kimin Yanlış Parametre Değeri Geçirdiğini Nasıl Bulabilirim?
## <a name="problem-description"></a>Sorun Açıklaması
 İşlevlerimin biri için yanlış parametre değeri geçirildi. Bu işlev her yerde çağrılır. Neyin yanlış değere aktarılmış olduğunu nasıl bulamıyorum?

## <a name="solution"></a>Çözüm

#### <a name="to-resolve-this-problem"></a>Bu sorunu çözmek için

1. İşlevin başında bir konum kesme noktası ayarlayın.

2. Kesme noktası'ne sağ tıklayın ve Koşul'u **seçin.**

3. Kesme **Noktası Koşulu iletişim** kutusunda Koşul onay **kutusuna** tıklayın. Bkz. [Gelişmiş Kesme Noktaları.](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)

4. Metin kutusuna gibi bir ifade girin; burada, hatalı değeri içeren parametrenin adıdır ve bu değere `Var==3` `Var` geçirilen hatalı `3` değerdir.

5. True **radyo düğmesini** seçin ve Tamam **düğmesine** tıklayın.

6. Şimdi programı yeniden çalıştırın. Kesme noktası, parametre değerine sahip olduğunda programın işlevin başında `Var` durmasına neden `3` olur.

7. Çağrı Yığını penceresini kullanarak çağıran işlevi bulun ve kaynak koduna gidin. Daha fazla bilgi için, [bkz. How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Kesme noktaları](/previous-versions/ktf38f66(v=vs.100))
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
