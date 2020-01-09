---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 67a614ed164b12070fe40f24cdba09a3051e36a5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566260"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

Bir 64 bit makineniz varsa, birim testleri çalıştırma ve 64-bit işlem olarak kod kapsamı bilgileri yakalayın.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Bir 64 bit işlem olarak birim testi çalıştırmak için

1. Kod veya testleri 32-bit/x86 derlendi ancak artık bunları 64 bit işlem olarak çalıştırmak istediğiniz, olarak yeniden derleyin **herhangi bir CPU**, ya da isteğe bağlı olarak **64-bit**.

    > [!TIP]
    > Maksimum esneklik için test projelerinizi derleyin **herhangi bir CPU** yapılandırma. Daha sonra hem 32-bit hem de 64 bit aracıların çalıştırabilirsiniz. İle test projelerini derlemek için herhangi bir avantaj sağlamaz **64-bit** yapılandırma.

2. Visual Studio menüsünden **Test**, ardından **ayarları**ve ardından **İşlemci mimarisi**. Seçin **x64** testleri 64 bit işlem olarak çalıştırılacak.

   - veya -

   Belirtin `<TargetPlatform>x64</TargetPlatform>` içinde bir *.runsettings* dosya. Bu yöntemin avantajı, farklı dosyalarında ayar gruplarını belirtin ve farklı ayarlar arasında hızlıca geçiş olmasıdır. Ayrıca, ayarları çözümleri arasında kopyalayabilirsiniz. Daha fazla bilgi için [bir .runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Birim testi kod](../test/unit-test-your-code.md)
