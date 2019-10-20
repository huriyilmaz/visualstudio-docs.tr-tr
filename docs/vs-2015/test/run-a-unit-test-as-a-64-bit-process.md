---
title: 64 bitlik bir işlem olarak birim testi çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc379f522d119e76ef8be8ba60a4cc1482e57fd1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660459"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

64 bitlik bir makineniz varsa, birim testlerini çalıştırabilir ve kod kapsamı bilgilerini bir 64 bit işlem olarak yakalayabilirsiniz.

## <a name="running-a-unit-test-as-a-64-bit-process"></a>64 bitlik bir işlem olarak birim testi çalıştırma

#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Bir birim testini 64 bitlik bir işlem olarak çalıştırmak için

1. Kodunuz veya testleriniz, 32 bit/x86 olarak derlenmişse, ancak artık bunları 64 bitlik bir işlem olarak çalıştırmak istiyorsanız, bunları **herhangi BIR CPU**veya isteğe bağlı olarak **64 bit**olarak yeniden derleyin.

    > [!TIP]
    > En yüksek esneklik için, test projelerinizi **herhangi BIR CPU** yapılandırmasıyla derlemeniz gerekir. Ardından, hem 32 hem de 64 bit aracılarında çalıştırabilirsiniz. **64 bitlik** yapılandırma ile test projelerini derlemek avantajsız değildir.

2. Visual Studio menüsünden **Test**' i ve ardından **Ayarlar**' ı seçin ve ardından **işlemci mimarisi**' ni seçin. Testleri 64 bitlik bir işlem olarak çalıştırmak için **x64** seçeneğini belirleyin.

     \- veya-

     Bir. runsettings dosyasında `<TargetPlatform>x64</TargetPlatform>` belirtin. Bu yöntemin avantajı, farklı dosyalardaki ayar gruplarını belirtebileceğiniz ve farklı ayarlar arasında hızlı bir şekilde geçiş yapmak için kullanabileceğiniz bir avantajdır. Ayrıca, ayarları çözümler arasında kopyalayabilirsiniz. Daha fazla bilgi için bkz [. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Test Gezgini birim testi ile birim testlerini çalıştırma](../test/run-unit-tests-with-test-explorer.md) [Visual Studio Testleri için test ayarlarını belirtme](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901) [kodunuzu test](../test/unit-test-your-code.md) etme
