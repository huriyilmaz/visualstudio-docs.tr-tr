---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 3971fe0513c98cb957d8013cdad932aa0c04bed1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646632"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

64 bitlik bir makineniz varsa, birim testlerini çalıştırabilir ve kod kapsamı bilgilerini bir 64 bit işlem olarak yakalayabilirsiniz.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Bir birim testini 64 bitlik bir işlem olarak çalıştırmak için

1. Kodunuz veya testleriniz, 32 bit/x86 olarak derlenmişse, ancak artık bunları 64 bitlik bir işlem olarak çalıştırmak istiyorsanız, bunları **herhangi BIR CPU**veya isteğe bağlı olarak **64 bit**olarak yeniden derleyin.

    > [!TIP]
    > En yüksek esneklik için, test projelerinizi **herhangi BIR CPU** yapılandırmasıyla derleyin. Ardından, 32-bit ve 64 bit aracılarında çalıştırabilirsiniz. **64 bitlik** yapılandırma ile test projelerini derleme avantajına sahip değildir.

2. Visual Studio menüsünden **Test**' i ve ardından **Ayarlar**' ı seçin ve ardından **işlemci mimarisi**' ni seçin. Testleri 64 bitlik bir işlem olarak çalıştırmak için **x64** seçeneğini belirleyin.

   - veya

   Bir *. runsettings* dosyasında `<TargetPlatform>x64</TargetPlatform>` belirtin. Bu yöntemin avantajı, farklı dosyalardaki ayar gruplarını belirtebileceğiniz ve farklı ayarlar arasında hızlı bir şekilde geçiş yapmak için kullanabileceğiniz bir avantajdır. Ayrıca, ayarları çözümler arasında kopyalayabilirsiniz. Daha fazla bilgi için bkz [. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
