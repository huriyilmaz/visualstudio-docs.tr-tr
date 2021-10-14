---
title: API işlevleri Windows hata ayıklama | Microsoft Docs
description: NT sembolleri yüklü olan bir Windows API işlevinin hata ayıklamasını öğrenin. 32 bit kodda kesme noktası ayarlamak için işlev adının dekore edilmiş formunu kullanırız.
ms.date: 06/03/2020
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a862ff5144c92d9d89644d4debdc41f3e7c0db2d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969209"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API İşlevlerinde Nasıl Hata Ayıklayabilirim?
NT sembolleri yüklü olan bir Windows API işlevinin hatasını ayıklamak için aşağıdaki adımları gerçekleştirin.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT sembolleri yüklü bir api Windows kesme noktası ayarlamak için

- İşlev [kesme noktası içinde](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)işlevin bulunduğu DLL'nin adıyla birlikte işlev adını girin (bkz. [bağlam işleci).](../debugger/context-operator-cpp.md) 32 bit kodda işlev adının dekore edilmiş formunu kullanın. **MessageBeep** üzerinde bir kesme noktası ayarlamak için, örneğin, aşağıdakini girmeniz gerekir.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Dekore edilmiş adı almak için bkz. [Dekore Edilmiş Adları Görüntüleme.](/previous-versions/5x49w699(v=vs.140))

     Dekore edilmiş adı test etmek ve farklı kodlarda görüntülemek için bu adı sınayabilirsiniz. Visual Studio hata ayıklayıcısındaki işlevde duraklatılmışken, kod düzenleyicisinde veya çağrı yığını penceresinde işlevine sağ tıklayın ve Ayıkla'ya **Git'i seçin.**

- 64 bit kodda, düzeltlanmamış adı kullanabilirsiniz.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
