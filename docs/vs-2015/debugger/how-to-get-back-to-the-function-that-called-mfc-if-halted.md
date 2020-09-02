---
title: "Nasıl yapılır: durdurulmuşsa MFC 'yi çağıran Işleve geri dönme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685877"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Programı durdurmak ve MFC 'de sonlandırmak için **hata ayıklama** menüsündeki **kesme** komutunu kullandıysanız ve sorunun kodunuzda olduğundan eminseniz, Işlevinizde geri dönmek için çağrı yığını penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).  
  
 Bazen kodunuzun ileti göndericisinin kesintiye uğramayabilir. Bu durumda, çağrı yığınında Kullanıcı kodu yoktur. Bu sorundan kaçınmak için **kesme komutu yerine kesme noktaları** (büyük olasılıkla koşullar ve isabet sayısı ile birlikte) kullanabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>MFC 'nin çağrıldığı işleve gitmek için  
  
- **Çağrı yığını** penceresini kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
