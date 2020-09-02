---
title: Kimin Yanlış Parametre Değeri Geçirdiğini Nasıl Bulabilirim? | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b0787a0d700859e7728762fd7846911fcd41e369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704548"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Kimin Yanlış Parametre Değeri Geçirdiğini Nasıl Bulabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun Açıklaması  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Kesme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
