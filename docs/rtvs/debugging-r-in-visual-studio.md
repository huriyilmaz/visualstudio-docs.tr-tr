---
title: R kodunda hata ayıklama
description: Visual Studio, kesme noktaları, iliştirme, çağrı yığını ve değişkenleri inceleme dahil olmak üzere R için tam hata ayıklama deneyimi sağlar.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 5efa0a32f51e1f5060474a0d277bfca7f1e7d548
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189261"
---
# <a name="debug-r-in-visual-studio"></a>Visual Studio 'da R 'de hata ayıkla

Visual Studio için R Araçları (RTVS), Visual Studio 'nun tam hata ayıklama deneyimiyle tümleştirilir (bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugger-feature-tour.md)). Bu destek kesme noktaları, çalışan işlemlere ekleme, değişkenleri İnceleme ve izleme ve çağrı yığınını İnceleme içerir. Daha sonra bu makale, R ve RTVS 'e özgü olan hata ayıklama yönlerini araştırır.

Bir R projesinde başlangıç R dosyası için hata ayıklayıcı 'nın başlatılması, diğer proje türleri için de aynıdır: hata ayıklamayı başlatmak ** > ** hata **ayıklamayı**, **F5** tuşunu veya hata ayıklama araç çubuğundaki **kaynak başlangıç dosyasını** kullanın:

![R için hata ayıklayıcı Başlangıç düğmesi](media/debugger-start-button.png)

Başlangıç dosyasını değiştirmek için Çözüm Gezgini bir dosyaya sağ tıklayın ve **Başlangıç R betiği olarak ayarla**' yı seçin.

Her durumda, "kaynaklar" hata ayıklayıcısını etkileşimli pencerede başlatmak, bu da yükleme ve etkileşimli pencerenin çıktısında gösterildiği gibi bu dosyayı çalıştırmak anlamına gelir:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Komut dosyasını kaynak için `rtvs::debug_source` işlevi kullanıldığına dikkat edin. RTVS 'nin hata ayıklama hazırlığı için kodunuzu değiştirmesi gerektiğinden, bu işlev gereklidir. Herhangi bir RTVS kaynak kullanımı komutunu kullanırken ve bir hata ayıklayıcı eklendiğinde, Visual Studio otomatik olarak `rtvs::debug_source`kullanır.

Ayrıca, **R araçları** > **oturum** > **Ekle hata ayıklayıcı** komutunu, **hata ayıklama** > **R etkileşim komuta Ekle** veya Etkileşimli pencerenin araç çubuğunda **hata ayıklayıcı komutunu ekleyin** . Bunu yaptıktan sonra, hata ayıklamak istediğiniz dosyaları kaynak olarak kullanabilirsiniz. Dosyaları el ile kaynak olarak almak istiyorsanız, R 'de normal `source` komutu değil `rtvs::debug_source` kullandığınızdan emin olun.

Hata ayıklayıcı ve etkileşimli pencere arasındaki bu bağlantı, farklı parametre değerleriyle bir işlevi çağırma (ve hata ayıklama) gibi şeyleri daha kolay hale getirir. Örneğin, kaynak dosyada aşağıdaki işleve sahip olduğunuzu varsayalım (Bu, oturuma yüklenmiş olduğunu belirtir):

```R
add <- function(x, y) {
    return(x + y)
}
```

Sonra `return` bildiriminde bir kesme noktası ayarlarsınız. Artık etkileşimli pencerede, `add(4,5)` girmek kesme noktasında hata ayıklayıcıyı sonlandırır.

## <a name="environment-browser-in-the-interactive-window"></a>Etkileşimli pencerede ortam tarayıcısı

Hata ayıklayıcıda durdurulduğunda, [etkileşimli penceredeki](interactive-repl-for-r-in-visual-studio.md)ortam tarayıcısı isteminde de durulacağız. İstem, n 'nin bir sayı olduğu `Browse[n]>` görüntülenir.

Ortam tarayıcısı bazı özel komutları destekler:

| Komut | Açıklama |
| --- | --- |
| n | Sonraki: kod dosyasında sonraki ifadeyi çalıştırır (adımla aynı). |
| s | içine adımla: sonraki ifade bir işlev çağrısý ise, kod dosyasında bir sonraki ifadeyi çalıştırır, bir işlev kapsamına adımlayın. |
| Vadeli | Son: geçerli işlev kapsamının geri kalanını çalıştırır ve arayana döndürür (adımla aynı). |
| c, devamı | devam: programı bir sonraki kesme noktasına çalıştırır. |
| Q | çıkar: hata ayıklama oturumunu sonlandırır. |
| Burada | yığını göster: çağrı yığınını etkileşimli pencerede görüntüler. |
| Yardım | yardımı göster: etkileşimli pencerede kullanılabilir komutları görüntüler. |
| &lt;Expr&gt; | ifadeyi *Expr*'de değerlendirin. |

![Etkileşimli pencerede ortam tarayıcısı](media/debugger-environment-browser.png)
