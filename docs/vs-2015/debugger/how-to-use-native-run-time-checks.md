---
title: 'Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
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
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b50dda3e31e27fa5d177c3b0ba2790babd2a660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685853"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++, yerel [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) kullanarak şu yaygın çalışma zamanı hatalarını yakalayabilirsiniz:  
  
- Yığın işaretçisi bozulması.  
  
- Yerel dizilerin taşmaları.  
  
- Yığın bozulması.  
  
- Başlatılmamış yerel değişkenlerde bağımlılıklar.  
  
- Bir atamadaki daha kısa bir değişkene veri kaybı.  
  
  En iyileştirilmiş (**/o**) derleme ile **/RTC** kullanırsanız, bir derleyici hatası oluşur. `runtime_checks`İyileştirilmiş bir derlemede pragma kullanırsanız, pragma üzerinde hiçbir etkisi olmaz.  
  
  Çalışma zamanı denetimleri etkin olan bir programda hata ayıklarken, bir çalışma zamanı hatası oluştuğunda programın durdurulması ve hata ayıklayıcıya kesmesine yönelik varsayılan eylem. Herhangi bir çalışma zamanı denetimi için bu varsayılan davranışı değiştirebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı Ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).  
  
  Aşağıdaki yordamlarda, bir hata ayıklama derlemesinde yerel çalışma zamanı denetimlerinin nasıl etkinleştirileceği ve yerel çalışma zamanı denetimi davranışının nasıl değiştirileceği açıklanır.  
  
  Bu bölümdeki diğer konular hakkında bilgi sağlar:  
  
- [C çalışma zamanı kitaplığıyla çalışma zamanı denetimlerini özelleştirme](../debugger/native-run-time-checks-customization.md)  
  
- [C çalışma zamanı kitaplığı olmadan çalışma zamanı denetimlerini kullanma](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Bir hata ayıklama derlemesinde yerel çalışma zamanı denetimlerini etkinleştirmek için  
  
- **/RTC** seçeneğini kullanın ve bir C çalışma zamanı kitaplığının hata ayıklama sürümüyle bağlantı (örneğin,/MDD).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Yerel çalışma zamanı denetimi davranışını değiştirmek için  
  
- Pragma kullanın `runtime_checks` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio 'da hata ayıklama](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Çalışma zamanı hata denetimi](https://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)
