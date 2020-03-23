---
title: Hızlı İşlemler, ampuller ve tornavidalar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596963"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, kodu tek bir eylemle kolayca yeniden düzenlemenize, oluşturmanıza veya başka bir şekilde değiştirmenize izin sağlar. C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)ve Visual Basic kod dosyaları için Hızlı Eylemler kullanılabilir. Bazı eylemler bir dile özgüdür ve diğerleri tüm diller için geçerlidir.

Hızlı Eylemler için kullanılabilir:

- [Kod çözümleyici](../code-quality/roslyn-analyzers-overview.md) kural ihlali için kod düzeltmesi uygulama

::: moniker range=">=vs-2019"

- Kod çözümleyicikural ihlalini [bastırma](../code-quality/use-roslyn-analyzers.md#suppress-violations) veya önem derecesini [yapılandırma](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity)

::: moniker-end

::: moniker range="vs-2017"

- Kod çözümleyicikural ihlalini [bastırma](../code-quality/use-roslyn-analyzers.md#suppress-violations)

::: moniker-end

- Yeniden düzenleme uygulayın (örneğin, [geçici bir değişken inline)](../ide/reference/inline-temporary-variable.md)

- Kod oluşturma (örneğin, [yerel bir değişken tanıtın)](../ide/reference/introduce-local-variable.md)

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Refactoring (Mac için Visual Studio) adresine](/visualstudio/mac/refactoring)bakın.

Hızlı İşlemler ![ampul ampul simgesi](media/light-bulb-icon.png) veya tornavida ![simgeleri](media/screwdriver-icon.png) kullanılarak veya **Ctrl**+tuşuna basarak**uygulanabilir.** imleciniz, bir eylemin kullanılabildiği bir kod satırında olduğunda. Bir hata gösteren kırmızı ![bir dalgalı](media/error-light-bulb-icon.png) ve Visual Studio bu hata için kullanılabilir bir düzeltme varsa bir hata ampul hata ampul simgesi görürsünüz.

Herhangi bir dil için, üçüncü taraflar özel tanılama ve öneriler sağlayabilir, örneğin bir SDK'nın bir parçası olarak ve Visual Studio ampuller bu kurallara göre görünür.

## <a name="icons"></a>Simgeler

Hızlı Eylem kullanılabilir olduğunda görünen simge, kullanılabilen düzeltme veya yeniden düzenleme türünü gösterir. *Tornavida* ![simgesi](media/screwdriver-icon.png) simgesi, kodu değiştirmek için kullanılabilir eylemler olduğunu gösterir, ancak bunları mutlaka kullanmamalısınız. *Sarı ampul* ![ampul simgesi,](media/light-bulb-icon.png) kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. Hata ![ *ampulü* hata ampul](media/error-light-bulb-icon.png) simge simgesi, kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya tornavida görmek için

Düzeltme varsa, ampuller görünür:

- Fareyi bir hatanın bulunduğu yerde gezinirken

   ![Fare havada gezinen ampul](../ide/media/vs2015_lightbulb_hover.png)

- İlgili kod satırına caret (imleci) taşıdığınızda editörün sol kenar boşluğunda

**Ctrl**+tuşuna da**basabilirsiniz.** kullanılabilir Hızlı Eylemler ve yeniden düzenleme listesini görmek için bir satır üzerinde herhangi bir yerde.

Olası düzeltmeleri görmek için, ampulün yanındaki aşağı oku veya **Olası düzeltmeleri göster** bağlantısını seçin. Kullanılabilir Hızlı Eylemlerin listesi görüntülenir.

![Ampul genişletilmiş](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod oluşturma](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve Hızlı Eylemler](../ide/code-styles-and-code-cleanup.md)
- [Yazma ve yeniden düzenleme kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactoring (Mac için Visual Studio)](/visualstudio/mac/refactoring)
