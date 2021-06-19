---
title: Bellek kullanımını analiz etme
description: Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için kullanabileceğiniz araçlar, Bellek Kullanımı aracı ve .NET Nesne Ayırma aracı gibi araçlar hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6af0cd98e69a3c43ba70f5609567243e6285201
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387976"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

Bellek sızıntılarını ve verimsiz bellek kullanımını bulmak için hata ayıklayıcı ile tümleşik Bellek Kullanımı tanılama aracı gibi araçları veya .NET Nesne Ayırma aracı ve son sınanmış Bellek Kullanımı aracı gibi Performans Profili Oluşturucu'daki araçları kullanabilirsiniz.

Bellek Kullanımı aracı, yönetilen ve yerel bellek yığınının *bir veya* daha fazla anlık görüntüsünü alasiniz. .NET, ASP.NET, C++ veya karma mod (.NET ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz. Bellek **Kullanımı** aracı açık bir Visual Studio projesinde, yüklü bir Microsoft Store uygulamada veya çalışan bir uygulamaya ya da işleme bağlı olarak çalışıyor olabilir. Bellek Kullanımı aracını **hata ayıklama ile** veya hata ayıklama olmadan çalıştırabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Hata ayıklayıcısında bellek profili oluşturmayı aç/kapatabilirsiniz ve bellek kullanımının nesne başına dökümünü görüntüebilirsiniz. Yürütme duraklatılırken bellek kullanım sonuçlarını görüntüabilirsiniz, örneğin bir kesme noktası.

.NET geliştiricileri .NET Nesne Ayırma aracı veya Bellek kullanım [aracı arasında seçim](../profiling/memory-usage.md) olabilir.

- [.NET Nesne Ayırma aracı,](../profiling/dotnet-alloc-tool.md) .NET kodundaki ayırma desenlerini ve anomalilerini tanımlamanıza yardımcı olur ve atık toplama ile ilgili yaygın sorunların belirlenmesine yardımcı olur. Bu araç yalnızca son bir son durum aracı olarak çalışır. Bu aracı yerel veya uzak makinelerde çalıştırabilirsiniz.
- Bellek [Kullanımı aracı,](../profiling/memory-usage-without-debugging2.md) genellikle .NET uygulamalarıyla sık karşılaşılan bellek sızıntılarını tanımlamaya yardımcı olur. Kodda adımlama gibi belleği kontrol ederken hata ayıklayıcı özelliklerini kullanmak için hata [ayıklayıcı ile tümleşik Bellek](../profiling/memory-usage.md) kullanım aracı önerilir.

C++ geliştiricileri hata ayıklayıcısıyla tümleşik veya hata ayıklayıcı olmayan Bellek Kullanımı aracını kullanabilir.

- [Hata ayıklayıcı ile bellek kullanımını analiz etme](../profiling/memory-usage.md)
- [Hata ayıklayıcı olmadan bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)

Windows 7 ve sonraki bir sürümüyle hata ayıklayıcı olmadan profil oluşturma araçlarını kullanabilirsiniz. Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir.

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata ayıklama sırasında CPU ve belleği analiz etme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blogu: Visual C++ 2015'te bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
