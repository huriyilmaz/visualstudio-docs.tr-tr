---
title: 'İzlenecek yol: tasarım zamanında hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149425"
---
# <a name="walkthrough-debugging-at-design-time"></a>İzlenecek Yol: Tasarım Zamanında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanız çalışmadığı sırada bir işlevi veya alt yordamı yürütmek için Visual Studio **anında** penceresini kullanabilirsiniz. İşlev veya alt yordam bir kesme noktası içeriyorsa, Visual Studio uygun noktada yürütmeyi keser. Daha sonra program durumlarınızı incelemek için hata ayıklayıcı pencerelerini kullanabilirsiniz. Bu özellik tasarım zamanında hata ayıklama olarak adlandırılır.  
  
 Aşağıdaki yordamda bu özelliği nasıl kullanabileceğiniz gösterilmektedir.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Komut penceresinden isabet kesme noktaları için  
  
1. Aşağıdaki kodu bir Visual Basic konsol uygulamasına yapıştırın:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. ' I okuyan satırda bir kesme noktası ayarlayın `s="Add BreakPoint Here"` .  
  
3. **Hemen** penceresine şunu yazın:`?MyFunction<enter>`  
  
4. Kesme noktasının isabet ettiğini ve çağrı yığınının doğru olduğunu doğrulayın.  
  
5. **Hata Ayıkla** menüsünde, **devam**' a tıklayın ve hala tasarım modunda olduğunuzdan emin olun.  
  
6. **Hemen** penceresine şunu yazın:`?MyFunction<enter>`  
  
7. **Hemen** penceresine şunu yazın:`?MySub<enter>`  
  
8. Kesme noktasına isabet ettiğini doğrulayın ve Locals penceresinde static değişkenin değerini inceleyin `i` . **Locals** 3 değeri olmalıdır.  
  
9. Çağrı yığınının doğru olduğunu doğrulayın.  
  
10. **Hata Ayıkla** menüsünde, **devam**' a tıklayın ve hala tasarım modunda olduğunuzdan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Hata Ayıklayıcı Temel Bilgileri](../debugger/debugger-basics.md)
