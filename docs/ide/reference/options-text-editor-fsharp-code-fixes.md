---
title: Seçenekler, metin düzenleyici, F#kod düzeltmeleri
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666277"
---
# <a name="options-text-editor--f--code-fixes"></a>Seçenekler: metin Düzenleyicisi > F# > kod düzeltmeleri

Kod hatalarını ve teklif çözümlerini belirlemenize yardımcı olabilecek ayarları belirtmek için kod düzeltmeleri seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **araçlar**  > **Seçenekler**' i seçin ve ardından**kod düzeltmeleri** >  **metin Düzenleyicisi**  > **F#** seçin.

## <a name="code-fixes"></a>Kod Düzeltmeleri

- **Adları basitleştirme (gereksiz niteleyicileri Kaldır)**

  Bu onay kutusu işaretliyse, nitelikler gerekli olmadığında (sık kullanılan ad alanının bir üyesi gibi) tam nitelikli adlar basitleştirilir.

- **Açık deyimleri her zaman en üst düzeyde yerleştir**

  Bu onay kutusu işaretliyse ve koda bir `open` ifadesini yazarsanız, en üst düzeye konur.

- **Kullanılmayan açık deyimleri kaldır**

  Bu onay kutusu işaretliyse, belgeler kullanılmamış `open` deyimlerine göre çözümlenir ve kullanılmayan tüm `open` deyimlerini kaldırma eylemi içeren [hızlı bir eylem](../quick-actions.md) ampul görünür.

- **Kullanılmayan değerler için düzeltmeleri çözümle ve önerme**

  Bu onay kutusu işaretliyse araç, kodda kullanılmayan bir değeri tanır. Daha sonra, kullanılmayan değerin üzerine geldiğinizde, bu değeri kullanabilmeniz için gereken yolları önerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../../ide/find-code-changes-and-other-history-with-codelens.md)
