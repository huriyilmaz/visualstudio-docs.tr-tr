---
title: 'Seçenekler, metin düzenleyici, F #, kod düzeltmeleri'
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770927"
---
# <a name="options-text-editor--f--code-fixes"></a>Seçenekler: metin Düzenleyicisi > F # > kod düzeltmeleri

Kod hatalarını ve teklif çözümlerini belirlemenize yardımcı olabilecek ayarları belirtmek için kod düzeltmeleri seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için **Araçlar**  >  **Seçenekler**' i ve ardından **metin düzenleyici**  >  **F #**  >  **kod düzeltmeleri**' ni seçin.

## <a name="code-fixes"></a>Kod Düzeltmeleri

- **Adları basitleştirme (gereksiz niteleyicileri Kaldır)**

  Bu onay kutusu işaretliyse, nitelikler gerekli olmadığında (sık kullanılan ad alanının bir üyesi gibi) tam nitelikli adlar basitleştirilir.

- **Açık deyimleri her zaman en üst düzeyde yerleştir**

  Bu onay kutusu işaretliyse ve `open` koda bir ifade yazarsanız, en üst düzeye konur.

- **Kullanılmayan açık deyimleri kaldır**

  Bu onay kutusu işaretliyse, belgeler kullanılmamış deyimler için analiz edilir `open` ve tüm kullanılmayan deyimleri kaldırma eylemi Içeren [hızlı bir eylem](../quick-actions.md) ampul görüntülenir `open` .

- **Kullanılmayan değerler için düzeltmeleri çözümle ve önerme**

  Bu onay kutusu işaretliyse araç, kodda kullanılmayan bir değeri tanır. Daha sonra, kullanılmayan değerin üzerine geldiğinizde, bu değeri kullanabilmeniz için gereken yolları önerir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../../ide/find-code-changes-and-other-history-with-codelens.md)
