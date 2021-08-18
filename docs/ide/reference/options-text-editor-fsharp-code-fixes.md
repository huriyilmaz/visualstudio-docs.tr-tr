---
title: Seçenekler, Metin Düzenleyici, F#, Kod Düzeltmeleri
description: Kod hatalarını tanımlamanıza ve çözüm sunmanıza yardımcı olacak ayarları belirtmek için F# bölümündeki Kod Düzeltmeleri sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 2f63076cdccf2324ab85602054babecb27628ec5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041132"
---
# <a name="options-text-editor--f--code-fixes"></a>Seçenekler: F# > Metin Düzenleyici > Kod Düzeltmeleri

Kod hatalarını tanımlamanıza ve çözüm sunmanıza yardımcı olacak ayarları belirtmek için Kod Düzeltmeleri seçenekleri sayfasını kullanın. Bu seçenekler sayfasına erişmek için Araçlar **Seçenekleri'ni**  >  **ve** ardından Metin Düzenleyici   >  **F# Kod**  >  **Düzeltmeleri'ni seçin.**

## <a name="code-fixes"></a>Kod Düzeltmeleri

- **Adları basitleştirme (gereksiz niteleyicileri kaldırma)**

  Bu onay kutusu seçilirse, nitelikler gerekli olmadığı durumlarda (örneğin, sık kullanılan ad alanının bir üyesi için) tam adlar basitleştirilir.

- **Açık deyimleri her zaman en üst düzeye yer açın**

  Bu onay kutusu seçiliyse ve koda bir deyim yazarak `open` en üst düzeye konabilir.

- **Kullanılmayan açık deyimlerini kaldırma**

  Bu onay kutusu seçiliyse, belgeler kullanılmayan deyimler için analiz edilir ve kullanılmayan tüm deyimleri kaldırma eylemiyle birlikte Hızlı Eylem `open` [](../quick-actions.md) `open` ampulü görüntülenir.

- **Kullanılmayan değerler için düzeltmeler analiz etme ve önerme**

  Bu onay kutusu seçiliyse, araç kodda kullanılmayacak bir değeri tanır. Ardından, kullanılmayan değerin üzerine gelmeniz, değeri kullanabileceğiniz yolların önerilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../../ide/find-code-changes-and-other-history-with-codelens.md)
