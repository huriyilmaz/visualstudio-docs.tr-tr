---
title: Bellek kullanımını analiz etme
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21522ba32990a850a388bfcf69ab239232a2c23d
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638420"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için, hata ayıklama tümleşik Bellek Kullanımı tanılama aracı veya Performans Profilleyicisi'ndeki .NET Nesne Ayırma aracı ve post-mortem Memory Usage aracı gibi araçlar gibi araçları kullanabilirsiniz.

Bellek Kullanımı aracı, yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .NET, ASP.NET, yerel veya karma mod (.NET ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz. **Bellek Kullanımı** aracı açık bir Visual Studio projesinde, yüklü bir Microsoft Mağazası uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalıştırılabilir. Hata ayıklama ile veya olmadan **Bellek Kullanımı** aracını çalıştırabilirsiniz. Daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Hata ayıklamada, bellek profil oluşturmayı açıp kapatabilir ve bellek kullanımının nesne başına dökümünü görebilirsiniz. Yürütme duraklatıldığında bellek kullanım sonuçlarını (örneğin bir kesme noktasında) görüntüleyebilirsiniz.

**.NET Nesne Ayırma** aracı, .NET kodunuzdaki ayırma desenlerini ve anormallikleri belirlemenize yardımcı olur. Bu alet sadece bir post-mortem aracı olarak çalışır. Bu aracı yerel veya uzaktan kumandalı makinelerde çalıştırabilirsiniz.

Bellek çözümleme araçlarının nasıl kullanılacağını açıklayan ayrıntılı talimatlar için, [bellek kullanım](../profiling/memory-usage.md) kılavuzunu ve [.NET Nesne Ayırma aracına](../profiling/dotnet-alloc-tool.md)bakın.

Profil oluşturma araçlarını Windows 7 ve sonraki hata ayıklama olmadan kullanabilirsiniz. Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir.

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata ayıklama sırasında CPU ve bellek analiz](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blogu: Visual C++ 2015'te bellek profilleme](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [Hata ayıklama olmadan bellek kullanımını analiz edin](../profiling/memory-usage-without-debugging2.md)
