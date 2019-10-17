---
title: 'Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3cef755721a9c5b917b080fa10f1819055a18ed7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430562"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
Visual Studio C++ projesinde, yerel [runtime_checks](/cpp/preprocessor/runtime-checks) kullanarak şu yaygın çalışma zamanı hatalarını yakalayabilirsiniz:

- Yığın işaretçisi bozulması.

- Yerel dizilerin taşmaları.

- Yığın bozulması.

- Başlatılmamış yerel değişkenlerde bağımlılıklar.

- Bir atamadaki daha kısa bir değişkene veri kaybı.

  En iyileştirilmiş ( **/o**) derleme ile **/RTC** kullanırsanız, bir derleyici hatası oluşur. İyileştirilmiş bir derlemede `runtime_checks` pragma kullanırsanız, pragma 'ın hiçbir etkisi yoktur.

  Çalışma zamanı denetimleri etkin olan bir programda hata ayıklarken, bir çalışma zamanı hatası oluştuğunda programın durdurulması ve hata ayıklayıcıya kesmesine yönelik varsayılan eylem. Herhangi bir çalışma zamanı denetimi için bu varsayılan davranışı değiştirebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı Ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).

  Aşağıdaki yordamlarda, bir hata ayıklama derlemesinde yerel çalışma zamanı denetimlerinin nasıl etkinleştirileceği ve yerel çalışma zamanı denetimi davranışının nasıl değiştirileceği açıklanır.

  Bu bölümdeki diğer konular hakkında bilgi sağlar:

- [C çalışma zamanı kitaplığıyla çalışma zamanı denetimlerini özelleştirme](../debugger/native-run-time-checks-customization.md)

- [C çalışma zamanı kitaplığı olmadan çalışma zamanı denetimlerini kullanma](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Bir hata ayıklama derlemesinde yerel çalışma zamanı denetimlerini etkinleştirmek için

- **/RTC** seçeneğini kullanın ve bir C çalışma zamanı kitaplığının hata ayıklama sürümüyle bağlantı (örneğin,/MDD).

### <a name="to-modify-native-run-time-check-behavior"></a>Yerel çalışma zamanı denetimi davranışını değiştirmek için

- @No__t-0 pragma kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Çalışma Zamanı Hata Denetimi](/cpp/c-runtime-library/run-time-error-checking)