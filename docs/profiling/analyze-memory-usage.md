---
title: Bellek kullanımını analiz etme
ms.custom: seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0262081489ec6e037a006649c3041baf02b32d58
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007210"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için .NET nesne ayırma aracı ve mortem sonrası bellek kullanımı aracı gibi performans Profiler 'daki hata ayıklayıcı ile tümleşik bellek kullanımı Tanılama aracı veya araçları gibi araçları kullanabilirsiniz.

Bellek kullanımı aracı, yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .NET, ASP.NET, C++ veya karma mod (.NET ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz. **Bellek kullanımı** aracı açık bir Visual Studio projesi üzerinde, yüklü bir Microsoft Store uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalışabilir. **Bellek kullanımı** aracını hata ayıklama olmadan veya olmadan çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Hata ayıklayıcıda, bellek profilini açma ve kapatma ' yı açıp bellek kullanımının nesne başına dökümünü görebilirsiniz. Yürütme duraklatıldığında, örneğin bir kesme noktasında bellek kullanım sonuçlarını görüntüleyebilirsiniz.

.NET geliştiricileri, [bellek kullanımı](../profiling/memory-usage.md) aracı ve [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md)arasında seçim gösterebilir.
- **.NET nesne ayırma** Aracı, .net kodunuzda ayırma düzenlerini ve anormallikleri belirlemenize yardımcı olur ve çöp toplama ile ilgili yaygın sorunları belirlemenize yardımcı olur. Bu araç yalnızca bir post-mordıtem aracı olarak çalışır. Bu aracı, yerel veya uzak makinelerde çalıştırabilirsiniz.
- **Bellek kullanımı** Aracı, genellikle .NET uygulamalarında yaygın olmayan bellek sızıntılarını tanımlamaya yardımcı olur. Bellek denetlenirken hata ayıklayıcı özelliklerini kod üzerinden atlama gibi kullanmanız gerekiyorsa, [hata ayıklayıcı ile tümleşik bellek kullanım](../profiling/beginners-guide-to-performance-profiling.md) aracı önerilir.

Profil oluşturma araçlarını Windows 7 ve üzeri bir hata ayıklayıcı olmadan kullanabilirsiniz. Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

## <a name="blogs-and-videos"></a>Blogların ve videoların

[Hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Visual C++ 2015 ' de bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı olmadan bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)
- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
