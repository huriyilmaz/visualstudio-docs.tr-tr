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
ms.openlocfilehash: 98382cdcde1e8413d7b6592b52aaee09e6c4274c
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76923330"
---
# <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme
Hata ayıklayıcıyla tümleştirilmiş kullanın **bellek kullanımı** Tanılama aracını bellek sızıntılarını ve verimsiz bellek kullanımını bulun. Bir veya daha fazla atmanız bellek kullanımı aracı sağlar *anlık görüntüleri* yönetilen ve yerel bellek yığın. .NET, ASP.NET, yerel veya karma mod (.NET ve yerel) uygulamaları, anlık toplayabilirsiniz.

- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.

- Ayrıca bir uygulamanın iki anlık görüntüsünü (fark) karşılaştırarak kodunuzda, zamanla bellek kullanımının artmasına yol açan bölümleri bulabilirsiniz.

Ayrıntılı yönergeler için bkz. [bellek kullanımını analiz etme](../profiling/memory-usage.md) öğretici.  Şu anda .NET Core uygulaması için bellek kullanımını ölçmek için hata ayıklayıcısı ekli aracını kullanmanız gerekir. Diğer yönetilen ve yerel uygulamalar için veya bilginiz olmaksızın hata ayıklayıcısı ekli aracını kullanabilirsiniz.

Windows 7 ve daha sonra hata ayıklayıcı olmadan profil oluşturma araçları kullanabilirsiniz. Windows 8 ve üzeri, hata ayıklayıcısı ile profil oluşturma araçları çalıştırmak için gereklidir (**tanılama araçları** pencere).

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata ayıklama sırasında CPU ve bellek çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blogu: Visual C++ 2015'te bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
- [Hata ayıklayıcı olmadan bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)
