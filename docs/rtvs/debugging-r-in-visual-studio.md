---
title: R kodunda hata ayıklama
description: Visual Studio kesme noktaları, ekleme, çağrı yığını ve değişkenleri inceleme dahil olmak üzere R için tam hata ayıklama deneyimi sağlar.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 35762badb0c3c3bd86e84d2414d99a70d53b896e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625317"
---
# <a name="debug-r-in-visual-studio"></a>Visual Studio'da R'de hata ayıklama

Visual Studio için R Araçları (RTVS), uygulamanın tam hata ayıklama deneyimiyle tüm Visual Studio [(bkz.](../debugger/debugger-feature-tour.md)Visual Studio. . Bu destek kesme noktaları, çalışan işlemlere ekleme, değişkenleri inceleme ve izleme ve çağrı yığınını incelemeyi içerir. Bu makale daha sonra R ve RTVS'ye özgü hata ayıklama yönlerini inceler.

R projesinde başlangıç R dosyası için hata ayıklayıcıyı başlatmak diğer proje türleriyle aynıdır: hata ayıklama araç çubuğunda Hata AyıklamaYı  >  Başlat, **F5** anahtarı veya Kaynak **başlangıç** dosyasını kullanın:

![R için hata ayıklayıcı başlat düğmesi](media/debugger-start-button.png)

Başlangıç dosyasını değiştirmek için, dosyanın içinde bir dosyaya sağ tıklayın Çözüm Gezgini Başlangıç **R Betiği Olarak Ayarla'yı seçin.**

Her durumda, hata ayıklayıcısını etkileşimli pencerede "kaynaklar&quot; olarak başlatma, etkileşimli pencerenin çıkışında gösterildiği gibi dosyayı yükleme ve orada çalıştırma anlamına gelir:

```output
> rtvs::debug_source(&quot;c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Betiğin `rtvs::debug_source` kaynağının işlevine dikkat etmek. RTVS'nin hata ayıklamaya hazır olarak kodunuzu değiştirmesi gerektiğinden bu işlev gereklidir. Herhangi bir RTVS kaynak komutu kullanırken ve bir hata ayıklayıcı ekliyken, Visual Studio otomatik olarak `rtvs::debug_source` kullanır.

Hata ayıklayıcıyı etkileşimli pencereden **doğrudan R Araçları** Oturum Iliştirme Hata Ayıklayıcısı komutunu, Hata Ayıklama R Etkileşim'ye Ekle komutunu veya etkileşimli pencerenin araç çubuğundaki Hata Ayıklayıcıyı Ekle komutunu kullanarak da el ile  >    >     >   ekleyebilirsiniz.  Bunu yaptıktan sonra, hata ayıklamak istediğiniz dosyaları kaynak olarak almak sizin sorumluluğuzdur. Dosyaları el ile kaynak olarak kullanmak için R'de normal komutu `rtvs::debug_source` değil, kullanmayı `source` deneyin.

Hata ayıklayıcı ile etkileşimli pencere arasındaki bu bağlantı, farklı parametre değerlerine sahip bir işlevi çağırma (ve hata ayıklama) gibi şeyleri daha kolay hale getirir. Örneğin, kaynak dosyada (oturuma yükleniyor anlamına gelir) aşağıdaki işlevin olduğunu varsayalım:

```R
add <- function(x, y) {
    return(x + y)
}
```

Ardından deyimi üzerinde bir kesme noktası `return` ayarlayın. Şimdi etkileşimli pencereye girerek kesme `add(4,5)` noktanız üzerinde hata ayıklayıcıyı durdurur.

## <a name="environment-browser-in-the-interactive-window"></a>Etkileşimli pencerede Ortam Tarayıcısı

Hata ayıklayıcısında durdurulursanız, etkileşimli penceresindeki Ortam Tarayıcısı isteminde de [durdurulursınız.](interactive-repl-for-r-in-visual-studio.md) İstem, `Browse[n]>` n'nin sayı olduğu yerde görünür.

Ortam Tarayıcısı bir dizi özel komutu destekler:

| Komut | Açıklama |
| --- | --- |
| n | next: Kod dosyasında bir sonraki deyimi çalıştırır (adım atarak aynı şekilde). |
| s | step into: Kod dosyasında sonraki deyimi çalıştırır ve sonraki deyim bir işlev çağrısı ise işlev kapsamına adımlar. |
| f | finish: geçerli işlev kapsamının geri kalanını çalıştırır ve çağırana geri döner (adım adım dışarı adımla aynıdır). |
| c, cont | continue: programı sonraki kesme noktası için çalıştırır. |
| Q | quits: hata ayıklama oturumunu sonlar. |
| konum | show stack: çağrı yığınını etkileşimli pencerede görüntüler. |
| Yardım | yardımı göster: Kullanılabilir komutları etkileşimli pencerede görüntüler. |
| &lt;expr&gt; | ifadesini *expr içinde değerlendirin.* |

![Etkileşimli pencerede Ortam Tarayıcısı](media/debugger-environment-browser.png)
