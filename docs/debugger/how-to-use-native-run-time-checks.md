---
title: Yerel Denetimler Run-Time Denetimlerini | Microsoft Docs
description: Yığın işaretçisinin bozulması, yerel Visual Studio ve yığın bozulması gibi yaygın çalışma zamanı hatalarını yakalamak için yerel çalışma zamanı denetimlerini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 0c74cdc63e7c72950050872135f2181002c3d4e57ca718db206f0fdf8979e88b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378742"
---
# <a name="how-to-use-native-run-time-checks"></a>Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma
Bir Visual Studio C++ projesinde, yerel [](/cpp/preprocessor/runtime-checks) runtime_checks gibi yaygın çalışma zamanı hatalarını yakalamak için kullanabilirsiniz:

- Yığın işaretçisi bozulması.

- Yerel dizilerin fazla çalıştırmaları.

- Yığın bozulması.

- Uninitialized yerel değişkenlere bağımlılıklar.

- Daha kısa bir değişkene atamada veri kaybı.

  İyileştirilmiş (**/O**) derlemesi ile **/RTC** kullanırsanız, derleyici hatasıyla sonuç verir. İyileştirilmiş bir `runtime_checks` derlemede pragma kullanırsanız pragmanın hiçbir etkisi olmaz.

  Çalışma zamanı denetimleri etkinleştirilmiş bir programda hata ayıklarken, varsayılan eylem bir çalışma zamanı hatası oluştuğunda programın durdurması ve hata ayıklayıcısına kesmesi için kullanılır. Herhangi bir çalışma zamanı denetimi için bu varsayılan davranışı değiştirebilirsiniz. Daha fazla bilgi için, [bkz. Managing Exceptions with the Debugger](../debugger/managing-exceptions-with-the-debugger.md).

  Aşağıdaki yordamlar, bir hata ayıklama derlemesinde yerel çalışma zamanı denetimlerini etkinleştirmeyi ve yerel çalışma zamanı denetim davranışını değiştirmeyi açıklar.

  Bu bölümdeki diğer konular şu konularda bilgi sağlar:

- [C Run-Time Kitaplığı ile Run-Time Denetimlerini Özelleştirme](../debugger/native-run-time-checks-customization.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Hata ayıklama derlemesinde yerel çalışma zamanı denetimlerini etkinleştirmek için

- **/RTC seçeneğini** kullanın ve C çalışma zamanı kitaplığının (/MDd gibi) hata ayıklama sürümüyle bağlantı kullanın.

### <a name="to-modify-native-run-time-check-behavior"></a>Yerel çalışma zamanı denetim davranışını değiştirmek için

- `runtime_checks`Pragma kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Çalışma Zamanı Hata Denetimi](/cpp/c-runtime-library/run-time-error-checking)