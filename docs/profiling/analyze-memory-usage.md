---
title: Bellek kullanımını analiz etme
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578167"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için .NET nesne ayırma aracı ve mortem sonrası bellek kullanımı aracı gibi performans Profiler 'daki hata ayıklayıcı ile tümleşik bellek kullanımı Tanılama aracı veya araçları gibi araçları kullanabilirsiniz. Bellek kullanımı aracı, yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .NET, ASP.NET, yerel veya karma mod (.NET ve yerel) uygulamaları, anlık toplayabilirsiniz. 

**Bellek kullanımı** aracı açık bir Visual Studio projesi üzerinde, yüklü bir Microsoft Store uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalışabilir. Yerel veya uzak makinelerde veya öykünücü veya simülatör aracı çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

**Bellek kullanımı** aracını hata ayıklama olmadan veya olmadan çalıştırabilirsiniz. Hata ayıklayıcıda, bellek profilini açma ve kapatma ' yı açıp bellek kullanımının nesne başına dökümünü görebilirsiniz. Yürütme duraklatıldığında, örneğin bir kesme noktasında bellek kullanım sonuçlarını görüntüleyebilirsiniz.

**.NET nesne ayırma** aracı yalnızca bir post-mordıtem aracı olarak çalışır.

Bellek analizi araçlarının nasıl kullanılacağını açıklayan ayrıntılı yönergeler için bkz. [bellek kullanımı](../profiling/memory-usage.md) öğreticisini ve [.NET nesne ayırma aracını](../profiling/dotnet-alloc-tool.md)çözümleme.

Windows 7 ve daha sonra hata ayıklayıcı olmadan profil oluşturma araçları kullanabilirsiniz. Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Visual C++ 2015 'da bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [Hata ayıklayıcı olmadan bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)
