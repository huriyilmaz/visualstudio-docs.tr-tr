---
title: 64 bitlik bir işlem olarak birim testi çalıştırma
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3c5cb51232457a43200c8a71ace51cc4b8a63e02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88507992"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

64 bitlik bir makineniz varsa, birim testlerini çalıştırabilir ve kod kapsamı bilgilerini bir 64 bit işlem olarak yakalayabilirsiniz.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Bir birim testini 64 bitlik bir işlem olarak çalıştırmak için

1. Kodunuz veya testleriniz, 32 bit/x86 olarak derlenmişse, ancak artık bunları 64 bitlik bir işlem olarak çalıştırmak istiyorsanız, bunları **herhangi BIR CPU**olarak yeniden derleyin.

   ::: moniker range="vs-2017"
   Alternatif olarak, Visual Studio 2017 ' de projenizi **64 bit**olarak derleyebilirsiniz.
   ::: moniker-end

    > [!TIP]
    > En yüksek esneklik için, test projelerinizi **herhangi BIR CPU** yapılandırmasıyla derleyin. Ardından, 32-bit ve 64 bit aracılarında çalıştırabilirsiniz. Yalnızca 64 bit üzerinde desteklenen kodu çağırırken **64 bitlik** yapılandırma ile test projelerini derlemek avantajına sahip değildir.

2. Birim testlerini 64 bitlik bir işlem olarak çalışacak şekilde ayarlayın.

   ::: moniker range=">=vs-2019"
   Visual Studio menüsünden **Test**' i ve sonra **anycpu projeleri için işlemci mimarisi**' ni seçin. Testleri 64 bitlik bir işlem olarak çalıştırmak için **x64** seçeneğini belirleyin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio menüsünden **Test**' i seçin, ardından **Test ayarları**' nı seçin ve ardından **işlemci mimarisi**' ni seçin. Testleri 64 bitlik bir işlem olarak çalıştırmak için **x64** seçeneğini belirleyin.
   ::: moniker-end

   \- veya

   `<TargetPlatform>x64</TargetPlatform>`Bir *. runsettings* dosyasında belirtin. Bu yöntemin avantajı, farklı dosyalardaki ayar gruplarını belirtebileceğiniz ve farklı ayarlar arasında hızlı bir şekilde geçiş yapmak için kullanabileceğiniz bir avantajdır. Ayrıca, ayarları çözümler arasında kopyalayabilirsiniz. Daha fazla bilgi için bkz [.. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
