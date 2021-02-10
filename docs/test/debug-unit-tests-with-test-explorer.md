---
title: Test Gezgini ile birim testlerinde hata ayıklama
description: Visual Studio 'da test Gezgini ile birim testlerinde hata ayıklamayı nasıl ayıklayacağınızı öğrenin.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09889839c9e2873810c78a5f0c3425820170b68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964387"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testlerini hata ayıklama ve çözümleme

Testleriniz için bir hata ayıklama oturumu başlatmak üzere test Gezgini ' ni kullanabilirsiniz. Visual Studio hata ayıklayıcı ile kodunuzda adım adım geçiş, birim testleri ve test edilen proje arasında sorunsuz bir şekilde geri ve ileri doğru bir şekilde gerçekleşir. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırada çalıştırılabildiğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

::: moniker range="vs-2017"
2. Test Gezgini 'nde test yöntemleri ' ni seçin ve sağ tıklama menüsünde **Seçili testlerin hatalarını ayıkla** ' yı seçin.
::: moniker-end
::: moniker range=">=vs-2019"
2. Test Gezgini 'nde test yöntemleri ' ni seçin ve sağ tıklama menüsünde **Hata Ayıkla** ' yı seçin.

   ![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Hata ayıklayıcı hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Test yöntemi performans sorunlarını tanılama

::: moniker range="vs-2017"
Bir test yönteminin neden çok fazla zaman aldığını tanılamak için test Gezgini 'nde yöntemi seçin ve sağ tıklama menüsünde **profil seçili test** ' i seçin. Bkz. [izleme profili oluşturma raporu](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

::: moniker range=">=vs-2019"
Test yönteminin neden çok fazla zaman aldığını tanılamak için test Gezgini 'nde yöntemi seçin ve sağ tıklama menüsünde **profil** ' i seçin. Bkz. [izleme profili oluşturma raporu](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

> [!NOTE]
> Bu özellik şu anda .NET Core için desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
