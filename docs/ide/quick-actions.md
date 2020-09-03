---
title: Hızlı Eylemler, hafif bulbs ve screwdrivers
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2ce8ce85e027a7ed7f78d0da1f68f328c1ca103d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596963"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)ve Visual Basic kod dosyaları Için hızlı eylemler kullanılabilir. Bazı eylemler bir dile özeldir ve diğerleri tüm diller için geçerlidir.

Hızlı eylemler şu Işlemler için kullanılabilir:

- [Kod Çözümleyicisi](../code-quality/roslyn-analyzers-overview.md) kural ihlali için kod düzeltmesini uygulayın

::: moniker range=">=vs-2019"

- Bir kod Çözümleyicisi kural ihlalini [gösterme](../code-quality/use-roslyn-analyzers.md#suppress-violations) veya önem derecesini [yapılandırma](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity)

::: moniker-end

::: moniker range="vs-2017"

- Kod Çözümleyicisi kural ihlalini [gösterme](../code-quality/use-roslyn-analyzers.md#suppress-violations)

::: moniker-end

- Yeniden düzenleme uygulama (örneğin, [satır içi geçici değişken](../ide/reference/inline-temporary-variable.md))

- Kod oluştur (örneğin, [yerel bir değişken tanıtma](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. yeniden [düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring).

Hızlı Eylemler, ampullü ampul ![ simgesi ](media/light-bulb-icon.png) veya screwsürücü ![ , Screwdriver simgesi ](media/screwdriver-icon.png) simgeleri kullanılarak veya **CTRL**'e basılarak uygulanabilir + **.** imlecinizin bir eylemin kullanılabildiği bir kod satırundayken. ![ ](media/error-light-bulb-icon.png) Bir hatayı gösteren kırmızı renkli bir çizgi varsa ve Visual Studio 'nun bu hata için kullanılabilir bir düzeltilmesi varsa, bir hata ışığı hatası ampul simgesi görürsünüz.

Herhangi bir dilde üçüncü taraflar, bir SDK 'nın parçası olarak özel tanılama ve öneriler sağlayabilir ve bu kurallara göre Visual Studio Light bulbs görüntülenir.

## <a name="icons"></a>Simgeler

Hızlı bir eylem kullanılabilir olduğunda görüntülenen simge, düzeltilmesi veya kullanılabilir yeniden düzenleme türü hakkında bir gösterge sağlar. *Screwdriver* ![ screwdriver simge ](media/screwdriver-icon.png) simgesi, yalnızca kodu değiştirecek eylemlerin olduğunu gösterir, ancak bunları kullanmamanız gerekmez. *Sarı* ampul ![ ışığı ampul simgesi simgesi, ](media/light-bulb-icon.png) kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. *Hata ampulü* ![ hatası ampul simgesi ](media/error-light-bulb-icon.png) simgesi kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya screwsürücüyü görmek için

Bir çözüm varsa, hafif bulbs görünür:

- Fareyi bir hata konumuna getirdiğinizde

   ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015_lightbulb_hover.png)

- Giriş işaretini (imleç) geçerli kod satırına taşıdığınızda düzenleyicinin sol kenar boşluğunda

Ayrıca, **CTRL**tuşuna da basabilirsiniz + **.** kullanılabilir hızlı eylemlerin ve yeniden düzenlemeler listesini görmek için satırda herhangi bir yerde.

Olası düzeltmeleri görmek için, ampul ' ın yanındaki aşağı oku veya **olası düzeltmeleri göster** bağlantısını seçin. Kullanılabilir hızlı eylemlerin bir listesi görüntülenir.

![Hafif ampul genişletildi](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod oluşturma](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve hızlı eylemler](../ide/code-styles-and-code-cleanup.md)
- [Kodu yazma ve yeniden düzenleme (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring)
