---
title: Hata ayıklama R kodu
description: Visual Studio, kırılma noktaları, ekleme, arama yığını ve değişkenleri denetleme dahil olmak üzere R için tam bir hata ayıklama deneyimi sağlar.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 5efa0a32f51e1f5060474a0d277bfca7f1e7d548
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189261"
---
# <a name="debug-r-in-visual-studio"></a>Görsel Stüdyo'da Hata Ayıklama R

R Tools for Visual Studio (RTVS) Visual Studio'nun tam hata ayıklama deneyimiyle bütünleşir [(Bkz. Görsel Stüdyo'da Hata Ayıklama.](../debugger/debugger-feature-tour.md) Bu destek kesme noktalarını, çalıştırma işlemlerine bağlanmayı, değişkenleri incelemeyi ve izlemeyi ve çağrı yığınını incelemeyi içerir. Bu makale, daha sonra, R ve RTVS benzersiz hata ayıklama bu yönlerini araştırıyor.

R projesinde başlangıç R dosyası için hata ayıklayıcısını başlatmak diğer proje türleri ile aynıdır: **Hata Ayıklama** > **Başlat Hata Ayıklama'yı,** **F5** anahtarını veya hata ayıklama araç çubuğundaki **Kaynak başlangıç dosyasını** kullanın:

![R için hata ayıklama başlangıç düğmesi](media/debugger-start-button.png)

Başlangıç dosyasını değiştirmek için Solution Explorer'da bir dosyayı sağ tıklatın ve **Başlangıç R Komut Dosyası Olarak Ayarla'yı**seçin.

Her durumda, hata ayıklama "kaynakları" etkileşimli pencerede dosya yı başlayarak, hangi yükleme ve etkileşimli pencerenin çıktıgösterildiği gibi orada çalışan anlamına gelir:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

İşlevin `rtvs::debug_source` komut dosyası için kullanıldığına dikkat edin. RTVS hata ayıklama için hazırlık kodunuzu değiştirmek için gereken den bu işlevi gereklidir. Herhangi bir RTVS kaynak komutu kullanırken ve bir hata ayıklayıcı takılıyken, Visual Studio otomatik olarak kullanır. `rtvs::debug_source`

Ayrıca, **doğrudan R Tools** > **Session** > **Attach Hataayıklama** komutunu, Hata**Ayıklama'yı** **Debug** > R Interactive komutuna eklemeyi veya etkileşimli pencerenin araç çubuğundaki Hata Ayıklayıcı yı **kak** komutunu kullanarak aracıyı doğrudan etkileşimli pencereden el ile ekleyebilirsiniz. Bunu yaptıktan sonra, hata ayıklamak istediğiniz dosyaları kaynak yapmak sizin sorumluluğunuzdadır. Dosyaları el ile kaynak olarak kullanmak istiyorsanız, `rtvs::debug_source` R'deki `source` normal komutu değil, kullandığınızdan emin olun.

Hata ayıklama ve etkileşimli pencere arasındaki bu bağlantı, farklı parametre değerlerine sahip bir işlevi arama (ve hata ayıklama) gibi şeyleri yapmayı kolaylaştırır. Örneğin, kaynaklı bir dosyada aşağıdaki işlevi gördüğünüzü varsayalım (oturuma yüklendiği anlamına gelir):

```R
add <- function(x, y) {
    return(x + y)
}
```

Sonra `return` ekstreüzerinde bir kesme noktası ayarlayın. Şimdi, etkileşimli pencerede, `add(4,5)` giriş kesme noktanızdaki hata ayıklamayı durdurur.

## <a name="environment-browser-in-the-interactive-window"></a>Etkileşimli pencerede Çevre Tarayıcısı

Hata ayıklamada durdurulduğunuzzaman, [etkileşimli penceredeki](interactive-repl-for-r-in-visual-studio.md)Çevre Tarayıcısı komut isteminde de durdurulursunuz. İstem, n'nin bir sayı olduğu yerde `Browse[n]>` görünür.

Çevre Tarayıcısı bir dizi özel komutu destekler:

| Komut | Açıklama |
| --- | --- |
| n | sonraki: kod dosyasındaki bir sonraki deyimi çalıştırın (adım adım ile aynıdır). |
| s | adım: kod dosyasındaki bir sonraki deyimi çalıştırArak, bir sonraki deyim bir işlev çağrısıysa işlev kapsamına girer. |
| f | bitiş: geçerli işlev kapsamının geri kalanını çalıştırın ve arayanın (adım dışarı aynı) döner. |
| c, cont | devam: programı bir sonraki kesme noktasına çalıştırın. |
| Q | bırakır: hata ayıklama oturumu sona erer. |
| where | yığın göster: etkileşimli pencerede arama yığınını görüntüler. |
| Yardım | yardım göster: etkileşimli pencerede kullanılabilir komutları görüntüler. |
| &lt;expr&gt; | *expr*ifadesini değerlendirmek. |

![Etkileşimli pencerede Çevre Tarayıcısı](media/debugger-environment-browser.png)
