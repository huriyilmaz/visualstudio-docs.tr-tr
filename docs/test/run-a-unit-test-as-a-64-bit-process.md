---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093914"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

64 bit makineniz varsa, birim testleri çalıştırabilir ve kod kapsamı bilgilerini 64 bit işlem olarak yakalayabilirsiniz.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Birim testini 64 bit işlem olarak çalıştırmak için

1. Kodunuz veya testler32-bit/x86 olarak derlenmiş, ancak şimdi bunları 64 bit işlem olarak çalıştırmak istiyorsanız, bunları Herhangi bir **CPU**olarak yeniden derleyin.

   ::: moniker range="vs-2017"
   Alternatif olarak Visual Studio 2017'de projenizi **64 bit**olarak da derleyebilirsiniz.
   ::: moniker-end

    > [!TIP]
    > Maksimum esneklik için test projelerinizi **Herhangi Cpu** yapılandırması ile derle. Daha sonra hem 32 bit hem de 64 bit aracılar üzerinde çalıştırabilirsiniz. Test projelerini **64 bit** yapılandırmayla derlemenin bir avantajı yoktur.

2. Birim testlerini 64 bit işlem olarak çalışacak şekilde ayarlayın.

   ::: moniker range=">=vs-2019"
   Visual Studio menüsünden **Test'i**seçin, ardından **AnyCPU projeleri için İşlemci Mimarisi'ni**seçin. Testleri 64 bit işlem olarak çalıştırmak için **x64'i** seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio menüsünden **Test'i**seçin, ardından **Test Ayarları'nı**seçin ve ardından **İşlemci Mimarisi'ni**seçin. Testleri 64 bit işlem olarak çalıştırmak için **x64'i** seçin.
   ::: moniker-end

   \-veya -

   `<TargetPlatform>x64</TargetPlatform>` *.runsettings* dosyasında belirtin. Bu yöntemin bir avantajı, farklı dosyalardaki ayar gruplarını belirtebilir ve farklı ayarlar arasında hızlı bir şekilde geçiş yapabilirsiniz. Ayrıca çözümler arasındaki ayarları da kopyalayabilirsiniz. Daha fazla bilgi için [bkz.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
