---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
description: Birim testleri çalıştırmayı ve 64 bit işlem olarak kod kapsamı bilgilerini yakalamayı öğrenin. 64 bit bilgisayarınız olmalıdır.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 64c125736abd67b37cf84e2b67b6b54a863032b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100393"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

64 bit makine varsa birim testleri çalıştırabilir ve kod kapsamı bilgilerini 64 bit işlem olarak yakalayabilirsiniz.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Birim testini 64 bit işlem olarak çalıştırmak için

1. Kodunuz veya testlerinizi 32 bit/x86 olarak derledik ancak şimdi bunları 64 bit işlem olarak çalıştırmak istiyorsanız, bunları Herhangi bir CPU olarak **yeniden derle.**

   ::: moniker range="vs-2017"
   Alternatif olarak, Visual Studio 2017'de projenizi **64 bit olarak da derleyesiniz.**
   ::: moniker-end

    > [!TIP]
    > Maksimum esneklik için test projelerinizi Herhangi bir **CPU yapılandırmasıyla derle.** Ardından hem 32 bit hem de 64 bit aracılar üzerinde çalıştırarak. Yalnızca 64 bit üzerinde desteklenen kodu çağırmadıkça test projelerini **64 bit** yapılandırmayla derlemenin bir avantajı yoktur.

2. Birim testlerini 64 bit işlem olarak çalıştıracak şekilde ayarlayın.

   ::: moniker range=">=vs-2019"
   Yeni Visual Studio Test'i ve **ardından** **AnyCPU projeleri için İşlemci Mimarisi'ne tıklayın.** Testleri **64** bit işlem olarak çalıştırmak için x64'ü seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Yeni Visual Studio, **Test'i** ve ardından **Test** Ayarlar ve ardından İşlemci **Mimarisi'ne tıklayın.** Testleri **64** bit işlem olarak çalıştırmak için x64'ü seçin.
   ::: moniker-end

   \- veya -

   `<TargetPlatform>x64</TargetPlatform>` *.runsettings dosyasında belirtin.* Bu yöntemin bir avantajı, farklı dosyalarda ayar grupları belirterek farklı ayarlar arasında hızla geçiş yapabilirsiniz. Ayrıca, ayarları çözümler arasında kopya edebilirsiniz. Daha fazla bilgi için [bkz. Bir .runsettings dosyası kullanarak birim testlerini yapılandırma.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
