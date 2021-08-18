---
title: Bellek kullanımını analiz etme
description: Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için kullanabileceğiniz araçlar, bellek kullanımı aracı ve .NET nesne ayırma aracı gibi araçlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ec323cea6d2a5e5ed41b226a3994b5084a70968c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131995"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için .NET nesne ayırma aracı ve mortem sonrası bellek kullanımı aracı gibi performans Profiler 'daki hata ayıklayıcı ile tümleşik bellek kullanımı Tanılama aracı veya araçları gibi araçları kullanabilirsiniz.

Bellek kullanımı aracı, yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .net, ASP.NET, C++ veya karma mod (.net ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz. **bellek kullanımı** aracı, açık bir Visual Studio projesi üzerinde, yüklü bir Microsoft Store uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalışabilir. **Bellek kullanımı** aracını hata ayıklama olmadan veya olmadan çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Hata ayıklayıcıda, bellek profilini açma ve kapatma ' yı açıp bellek kullanımının nesne başına dökümünü görebilirsiniz. Yürütme duraklatıldığında, örneğin bir kesme noktasında bellek kullanım sonuçlarını görüntüleyebilirsiniz.

.NET geliştiricileri, .NET nesne ayırma aracı ya da [bellek kullanımı](../profiling/memory-usage.md) aracı arasında seçim gösterebilir.

- [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md) , .net kodunuzda ayırma düzenlerini ve anormallikleri belirlemenize yardımcı olur ve çöp toplama ile ilgili yaygın sorunları belirlemenize yardımcı olur. Bu araç yalnızca bir post-mordıtem aracı olarak çalışır. Bu aracı, yerel veya uzak makinelerde çalıştırabilirsiniz.
- [Bellek kullanımı aracı](../profiling/memory-usage-without-debugging2.md) , genellikle .NET uygulamalarında yaygın olmayan bellek sızıntılarını tanımlamaya yardımcı olur. Bellek denetlenirken hata ayıklayıcı özelliklerini kod üzerinden atlama gibi kullanmanız gerekiyorsa, [hata ayıklayıcı ile tümleşik bellek kullanım](../profiling/memory-usage.md) aracı önerilir.

C++ geliştiricileri, hata ayıklayıcı ile tümleşik veya hata ayıklayıcı olmayan bellek kullanımı aracını kullanabilir.

- [Hata ayıklayıcı ile bellek kullanımını analiz etme](../profiling/memory-usage.md)
- [Hata ayıklayıcı olmadan bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)

profil oluşturma araçlarını Windows 7 ve üzeri bir hata ayıklayıcı olmadan kullanabilirsiniz. hata ayıklayıcı (**Tanılama Araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

## <a name="blogs-and-videos"></a>Blogların ve videoların

[Hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Visual C++ 2015 ' de bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
