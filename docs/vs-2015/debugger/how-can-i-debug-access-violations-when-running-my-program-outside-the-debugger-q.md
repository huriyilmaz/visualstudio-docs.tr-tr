---
title: Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim? | Microsoft Belgeleri
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299253"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun Açıklaması  
 Programımı Visual Studio ortamında sorunsuz çalışıyor, ancak Windows işletim sistemiyle tek başına çalıştırıldığında bir erişim ihlali oluşturur. Bu sorunu nasıl ayıklayabilirim?  
  
## <a name="solution"></a>Çözüm  
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçeneğini ayarlayın ve erişim ihlali gerçekleşene kadar programınızı tek başına çalıştırın. Ardından, **erişim ihlali** iletişim kutusunda, hata ayıklayıcıyı başlatmak için **iptal** ' e tıklayabilirsiniz.  
  
 Ayrıca, "genel koruma (GP) hatasının nerede oluştuğunu bulma" başlıklı Bilgi Bankası makalesine bakın. Bilgi Bankası makalelerini MSDN Kitaplığı CD 'sinde veya arayarak bulabilirsiniz [http://support.microsoft.com/](https://support.microsoft.com/) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
