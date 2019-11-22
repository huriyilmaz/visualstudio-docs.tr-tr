---
title: Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce5b21f92eecf2e8929c142bc1ee32e20d386335
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299253"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun açıklaması  
 Kendi programımı Visual Studio ortamında düzgün çalışıyor, ancak bu tek başına Windows işletim sistemiyle birlikte çalıştırabilir, erişim ihlali üretir. Bu sorunu nasıl hata ayıklaması yapabilirsiniz?  
  
## <a name="solution"></a>Çözüm  
 Ayarlama [Just-ın-time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçenek ve erişim ihlali gerçekleşene kadar tek başına programınızı çalıştırın. Ardından **erişim ihlali** iletişim kutusu, tıklayabilirsiniz **iptal** hata ayıklayıcıyı başlatmak için.  
  
 Ayrıca, "genel koruma (GP) hatasının nerede oluştuğunu bulma" başlıklı Bilgi Bankası makalesine bakın. Bilgi Bankası makalelerini MSDN Kitaplığı CD 'sinde veya [http://support.microsoft.com/](https://support.microsoft.com/)arayarak bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod hata ayıklaması SSS](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
