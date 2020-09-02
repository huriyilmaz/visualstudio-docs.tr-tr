---
title: Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim? | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c5fd73eb64c79ac9476c0036b9f2d709294d178
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704590"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yüklü NT sembolleri olan bir Windows API işlevinde hata ayıklamak istiyorsanız, aşağıdakileri yapmanız gerekir.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT sembolleri yüklenmiş bir Windows API işlevi üzerinde bir kesme noktası ayarlamak için  
  
- İşlev adını, işlevin bulunduğu DLL adı ile birlikte girin. 32 bitlik kodda, işlev adının düzenlenmiş formunu kullanın. Örneğin, **Messagebip**üzerinde bir kesme noktası ayarlamak için, şunu girmeniz gerekir.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Düzenlenmiş adı almak için bkz. [düzenlenmiş adları görüntüleme](https://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
