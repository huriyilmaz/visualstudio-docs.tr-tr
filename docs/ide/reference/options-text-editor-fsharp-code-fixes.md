---
title: Seçenekler, Metin Düzenleyicisi, F#, Kod Düzeltmeleri
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666277"
---
# <a name="options-text-editor--f--code-fixes"></a>Seçenekler: Metin Düzenleyicisi > F# > Kod Düzeltmeleri

Kod hatalarını belirlemeye ve çözümler sunmaya yardımcı olabilecek ayarları belirtmek için Kod Düzeltmeleri seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Metin Düzenleyicisi** > **F#** > **Kod Düzeltmeleri'ni**seçin.

## <a name="code-fixes"></a>Kod Düzeltmeleri

- **Adları basitleştirin (gereksiz niteleyicileri kaldırın)**

  Bu onay kutusu seçilirse, nitelikler gerekli olmadığında (örneğin, sık kullanılan ad alanının bir üyesi için) tam nitelikli adlar basitleştirilir.

- **Açık ifadeleri her zaman en üst düzeye yerleştirin**

  Bu onay kutusu seçilirse `open` ve koda bir ifade yazarsanız, en üst düzeye konur.

- **Kullanılmayan açık ifadeleri kaldırma**

  Bu onay kutusu seçilirse, belgeler kullanılmayan `open` ifadeler için çözümlenir ve kullanılmayan `open` tüm ifadeleri kaldırmak için bir eylemle birlikte [hızlı eylem](../quick-actions.md) ampulü görüntülenir.

- **Kullanılmayan değerler için düzeltmeleri analiz edin ve önerin**

  Bu onay kutusu seçilirse, araç kodda kullanılmayan bir değeri tanır. Daha sonra, kullanılmayan değerin üzerinde gezinirseniz, değeri kullanabileceğiniz yollar önerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../../ide/find-code-changes-and-other-history-with-codelens.md)
