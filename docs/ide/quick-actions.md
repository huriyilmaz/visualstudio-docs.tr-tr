---
title: Hızlı Eylemler, ampuller ve tornavidalar
description: Kodunuzu yeniden düzenleme, oluşturma veya başka bir şekilde değiştirme için tek bir Hızlı Eylem kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/15/2021
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
ms.openlocfilehash: a5c11391c0874d1a57aa3d9a05b6d8e7e55463ae
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920087"
---
# <a name="quick-actions"></a>Hızlı Eylemler

Hızlı Eylemler, tek bir eylemle kodu kolayca yeniden düzenlemenizi, oluşturmanizi veya başka bir şekilde değiştirmenizi sağlar. Hızlı Eylemler C#, [C++ ve Visual Basic](/cpp/ide/writing-and-refactoring-code-cpp)kullanılabilir. Bazı eylemler bir dile özgü, diğerleri ise tüm diller için geçerlidir.

Hızlı Eylemler şunları yapmak için kullanılabilir:

- Kod çözümleyicisi kural ihlali [için kod](../code-quality/roslyn-analyzers-overview.md) düzeltmesi uygulama

::: moniker range=">=vs-2019"

- [Kod](../code-quality/use-roslyn-analyzers.md#suppress-violations) çözümleyicisi kural ihlalini gizleme [veya](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) önem derecesini yapılandırma

::: moniker-end

::: moniker range="vs-2017"

- [Kod](../code-quality/use-roslyn-analyzers.md#suppress-violations) çözümleyicisi kural ihlallerini gizleme

::: moniker-end

- Yeniden düzenleme uygulama (örneğin, [satır içi geçici değişken)](../ide/reference/inline-temporary-variable.md)

- Kod oluşturma (örneğin, [bir yerel değişken tanıt)](../ide/reference/introduce-local-variable.md)

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring).

Hızlı Eylemler ampul ampul simgesi veya tornavida tornavida simgesi simgeleri kullanılarak ![ ](media/light-bulb-icon.png) veya ![ ](media/screwdriver-icon.png) Ctrl tuşlarına basılarak  + **uygulanabilir.** İmleciniz bir eylemin kullanılabilir olduğu bir kod satırı üzerinde olduğunda. Hata olduğunu belirten kırmızı bir geçiş varsa ve hatanın düzeltmesi varsa hata ampulü Visual Studio ampul ![ ](media/error-light-bulb-icon.png) simgesiyle gösterilir.

Herhangi bir dil için üçüncü taraflar, örneğin sdk'nın bir parçası olarak özel tanılama ve öneriler Visual Studio ampuller bu kurallara göre görünür.

## <a name="icons"></a>Simgeler

Hızlı Eylem kullanılabilir olduğunda görüntülenen simge, kullanılabilir düzeltmenin veya yeniden düzenlemenin türünü gösterir. *Tornavida* tornavida simgesi simgesi, kodu değiştirmek için kullanabileceğiniz eylemler olduğunu gösterir, ancak bunları ![ ](media/screwdriver-icon.png) mutlaka kullanmamak gerekir. Sarı *ampul ampul* simgesi ![ ](media/light-bulb-icon.png) simgesi, kodunuzu geliştirmek için gerçekleştirebilirsiniz *eylemler* olduğunu gösterir. Hata *ampulü* ![ hata ampul simgesi ](media/error-light-bulb-icon.png) simgesi, kodundaki bir hatayı düzelten bir eylem olduğunu gösterir.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Bir ampulü veya tornavidayı görmek için

Bir düzeltme varsa ampuller görüntülenir:

- Fareyle hatanın bulunduğu konuma gelindiğinde

   ![Fareyle üzerine gelinen ampul](../ide/media/vs2015_lightbulb_hover.png)

- Baş çizgisini (imleç) ilgili kod satırına taşıyarak düzenleyicinin sol kenar boşluğunda

Ctrl tuşlarına **da basarak da tuşlarına basın.** +  kullanılabilir Hızlı Eylemler ve yeniden düzenleme listesini görmek için bir satırda herhangi bir yere.

Olası düzeltmeleri görmek için ampulün yanındaki aşağı oku veya Olası düzeltmeleri **göster bağlantısını** seçin. Kullanılabilir Hızlı Eylemler listesi görüntülenir.

![Genişletilmiş ampul](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio)
- [Kod oluşturma Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Yaygın Hızlı Eylemler](../ide/common-quick-actions.md)
- [Kod stilleri ve Hızlı Eylemler](../ide/code-styles-and-code-cleanup.md)
- [Kod yazma ve yeniden düzenleme (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Yeniden düzenleme (Mac için Visual Studio)](/visualstudio/mac/refactoring)
