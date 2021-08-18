---
title: Test Gezgini ile birim testlerinde hata ayıklama
description: Test Gezgini ile birim testlerinde hata ayıklamayı Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 52817c2a3f0ad48c44b9eb1033a9e5b78d833e9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083875"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testlerinde hata ayıklama ve analiz etme

Test Gezgini'ni kullanarak testlerinizi hata ayıklama oturumu başlatabilirsiniz. Visual Studio hata ayıklayıcısıyla kodunuzu adımlamanız, sizi birim testleri ile test altındaki proje arasında sorunsuz bir şekilde ileri ve geri alır. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yönteminde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırayla çalıştırılana kadar, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

::: moniker range="vs-2017"
2. Test Gezgini'nde test yöntemlerini seçin ve ardından sağ tıklama menüsünde Seçili **Testlerde** Hata Ayıkla'yı seçin.
::: moniker-end
::: moniker range=">=vs-2019"
2. Test Gezgini'nde test yöntemlerini seçin ve ardından sağ **tıklama** menüsünden Hata Ayıkla'yı seçin.

   ![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Hata ayıklayıcısı hakkında daha fazla bilgi için [bkz.](../debugger/debugger-feature-tour.md)Visual Studio.

## <a name="diagnose-test-method-performance-issues"></a>Test yöntemi performans sorunlarını tanılama

::: moniker range="vs-2017"
Bir test yönteminin neden çok uzun zaman alalı olduğunu  tanılamak için Test Gezgini'nde yöntemini seçin ve ardından sağ tıklama menüsünde Profil Seçili Test'i seçin. Bkz. [Ölçümler profil oluşturma raporu.](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true)
::: moniker-end

::: moniker range=">=vs-2019"
Bir test yönteminin neden çok uzun zaman alalı olduğunu  tanılamak için Test Gezgini'nde yöntemini seçin ve ardından sağ tıklama menüsünde Profil'i seçin. Bkz. [Ölçümler profil oluşturma raporu.](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true)
::: moniker-end

> [!NOTE]
> Bu özellik şu anda .NET Core için desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
