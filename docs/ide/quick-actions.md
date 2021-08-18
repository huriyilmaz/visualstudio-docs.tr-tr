---
title: Hızlı Eylemler, hafif bulbs ve screwdrivers
description: Kodunuzu yeniden düzenlemek, oluşturmak veya başka bir şekilde değiştirmek için tek bir hızlı eylemi nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9128a9b488c5f7ab76ce398aa2a087e7ccf1481
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137281"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)ve Visual Basic kod dosyaları için hızlı eylemler kullanılabilir. Bazı eylemler bir dile özeldir ve diğerleri tüm diller için geçerlidir.

Hızlı eylemler şu Işlemler için kullanılabilir:

- [Kod Çözümleyicisi](../code-quality/roslyn-analyzers-overview.md) kural ihlali için kod düzeltmesini uygulayın

::: moniker range=">=vs-2019"

- Bir kod Çözümleyicisi kural ihlalini [gösterme](../code-quality/use-roslyn-analyzers.md#suppress-violations) veya önem derecesini [yapılandırma](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)

::: moniker-end

::: moniker range="vs-2017"

- Kod Çözümleyicisi kural ihlalini [gösterme](../code-quality/use-roslyn-analyzers.md#suppress-violations)

::: moniker-end

- Yeniden düzenleme uygulama (örneğin, [satır içi geçici değişken](../ide/reference/inline-temporary-variable.md))

- Kod oluştur (örneğin, [yerel bir değişken tanıtma](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. yeniden [düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring).

Hızlı Eylemler, ampullü ampul ![ simgesi ](media/light-bulb-icon.png) veya screwsürücü ![ , Screwdriver simgesi ](media/screwdriver-icon.png) simgeleri kullanılarak veya **CTRL**'e basılarak uygulanabilir + **.** imlecinizin bir eylemin kullanılabildiği bir kod satırundayken. ![ ](media/error-light-bulb-icon.png) bir hatayı gösteren kırmızı bir dalgalı çizgi ve Visual Studio bu hata için bir düzeltilmesi varsa, bir hata ışığı hatası ampul simgesi görürsünüz.

herhangi bir dil için üçüncü taraflar, örneğin bir SDK 'nın parçası olarak özel tanılama ve öneriler sağlayabilir ve bu kurallara göre Visual Studio hafif bulbs görünür.

## <a name="icons"></a>Simgeler

Hızlı bir eylem kullanılabilir olduğunda görüntülenen simge, düzeltilmesi veya kullanılabilir yeniden düzenleme türü hakkında bir gösterge sağlar. *Screwdriver* ![ screwdriver simge ](media/screwdriver-icon.png) simgesi, yalnızca kodu değiştirecek eylemlerin olduğunu gösterir, ancak bunları kullanmamanız gerekmez. *Sarı* ampul ![ ışığı ampul simgesi simgesi, ](media/light-bulb-icon.png) kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. *Hata ampulü* ![ hatası ampul simgesi ](media/error-light-bulb-icon.png) simgesi kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya screwsürücüyü görmek için

Bir çözüm varsa, hafif bulbs görünür:

- Fareyi bir hata konumuna getirdiğinizde

   ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015_lightbulb_hover.png)

- Giriş işaretini (imleç) geçerli kod satırına taşıdığınızda düzenleyicinin sol kenar boşluğunda

Ayrıca, **CTRL** tuşuna da basabilirsiniz + **.** kullanılabilir hızlı eylemlerin ve yeniden düzenlemeler listesini görmek için satırda herhangi bir yerde.

Olası düzeltmeleri görmek için, ampul ' ın yanındaki aşağı oku veya **olası düzeltmeleri göster** bağlantısını seçin. Kullanılabilir hızlı eylemlerin bir listesi görüntülenir.

![Hafif ampul genişletildi](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kod üretimi](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve hızlı eylemler](../ide/code-styles-and-code-cleanup.md)
- [Kodu yazma ve yeniden düzenleme (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring)
