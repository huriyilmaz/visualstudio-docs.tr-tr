---
title: Yerel çalışma zamanı denetimlerini kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 586f43f14a8638ab9c3c67f8ffef52ef52a70c53
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852673"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
Visual Studio C++ projesinde, şu gibi yaygın çalışma zamanı hatalarını yakalamak için yerel [runtime_checks](/cpp/preprocessor/runtime-checks) kullanabilirsiniz:

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

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Çalışma zamanı hata denetimi](/cpp/c-runtime-library/run-time-error-checking)