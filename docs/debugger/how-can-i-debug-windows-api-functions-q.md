---
title: Windows API işlevlerinde hata ayıkla | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7b5f3842160f4ffc6cecd41e65dd05ab7566dd0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734356"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim?
Yüklü NT sembolleri olan bir Windows API işlevinde hata ayıklamak istiyorsanız, aşağıdakileri yapmanız gerekir.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT sembolleri yüklenmiş bir Windows API işlevi üzerinde bir kesme noktası ayarlamak için

- İşlev adını, işlevin bulunduğu DLL adı ile birlikte girin. 32 bitlik kodda, işlev adının düzenlenmiş formunu kullanın. Örneğin, **Messagebip**üzerinde bir kesme noktası ayarlamak için, şunu girmeniz gerekir.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Düzenlenmiş adı almak için bkz. [düzenlenmiş adları görüntüleme](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
