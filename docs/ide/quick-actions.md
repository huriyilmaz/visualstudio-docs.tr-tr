---
title: Hızlı Eylemler, hafif bulbs ve screwdrivers
ms.date: 03/28/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 18df1378218d2188ee78d1b1b2a991e35f5ed689
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666751"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, tek bir eylem ile kodu kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirmenize olanak sağlar. Hızlı Eylemler, [C++](/cpp/ide/writing-and-refactoring-code-cpp)ve Visual Basic C#kod dosyaları için kullanılabilir. Bazı eylemler bir dile özeldir ve diğerleri tüm diller için geçerlidir.

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

Hızlı Eylemler, ampulü ![light ampul simgesi ](media/light-bulb-icon.png) veya screwsürücü ![screwdriver simgesi ](media/screwdriver-icon.png) simgeleri kullanılarak veya **Ctrl** + tuşlarına basarak uygulanabilir **.** imlecinizin bir eylemin kullanılabildiği bir kod satırundayken. Bir hata olduğunu gösteren kırmızı renkli bir çizgi varsa ve Visual Studio 'Nun bu hata için kullanılabilir bir düzeltilmesi varsa ![error ampul simgesi ](media/error-light-bulb-icon.png) bir hata görürsünüz.

Herhangi bir dilde üçüncü taraflar, bir SDK 'nın parçası olarak özel tanılama ve öneriler sağlayabilir ve bu kurallara göre Visual Studio Light bulbs görüntülenir.

## <a name="icons"></a>Simgeler

Hızlı bir eylem kullanılabilir olduğunda görüntülenen simge, düzeltilmesi veya kullanılabilir yeniden düzenleme türü hakkında bir gösterge sağlar. *Screwdriver* ![screwdriver simgesi ](media/screwdriver-icon.png) simge, yalnızca kodu değiştirmek için kullanılabilen eylemlerin olduğunu gösterir, ancak bunları kullanmamanız gerekmez. *Sarı* ampul ![light ampul simgesi ](media/light-bulb-icon.png) simge, kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. Ampul *![error ampul* simgesi ](media/error-light-bulb-icon.png) simge, kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya screwsürücüyü görmek için

Bir çözüm varsa, hafif bulbs görünür:

- Fareyi bir hata konumuna getirdiğinizde

   ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015_lightbulb_hover.png)

- Giriş işaretini (imleç) geçerli kod satırına taşıdığınızda düzenleyicinin sol kenar boşluğunda

Ayrıca, **Ctrl** + de basabilirsiniz **.** kullanılabilir hızlı eylemlerin ve yeniden düzenlemeler listesini görmek için satırda herhangi bir yerde.

Olası düzeltmeleri görmek için, ampul ' ın yanındaki aşağı oku veya **olası düzeltmeleri göster** bağlantısını seçin. Kullanılabilir hızlı eylemlerin bir listesi görüntülenir.

![Hafif ampul genişletildi](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod oluşturma](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve hızlı eylemler](../ide/code-styles-and-code-cleanup.md)
- [Kodu yazma ve yeniden düzenlemeC++()](/cpp/ide/writing-and-refactoring-code-cpp)
- [Yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring)