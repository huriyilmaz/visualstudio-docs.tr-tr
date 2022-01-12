---
title: Veri kaynağında birleştirme çakışmalarını Visual Studio
titleSuffix: ''
description: Veri kaynağında birleştirme çakışmalarını anlama, önleme ve Visual Studio.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: dea007f1f02927271f17ce8a4d257e8312ffbe09
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534082"
---
# <a name="resolve-merge-conflicts-in-visual-studio"></a>Veri kaynağında birleştirme çakışmalarını Visual Studio

Bir dalı başka bir dalla birleştirin, bir dalda yapılan dosya değişiklikleri, diğer dalda yapılan değişikliklerle çakışır. Git, birleştirilen dosyaların nasıl olması gerektiğini belirlemek için depoda yer alan geçmişi kullanarak bu değişiklikleri çözmeye çalışır. Değişikliklerin nasıl birleştirilecek açık değilse Git birleştirmeyi durdurarak hangi dosyaların çakışması olduğunu söyler.

## <a name="understand-merge-conflicts"></a>Birleştirme çakışmalarını anlama

Aşağıdaki görüntüde, Git'te değişikliklerin çakışması ile ilgili temel bir örnek ve açıklama yer aecektir. Bu örnekte ana dal ve hata düzeltmesi dalı, aynı kaynak kodu satırlarında güncelleştirmeler yapacaktır.

:::image type="content" source="media/vs-2022/git-conflicts-understand-1.png" alt-text="Birleştirme çakışması gösteren diyagram.":::

Hata düzeltme dallarını main ile birleştirmeye çalışsanız Git, birleştirilmiş sürümde hangi değişikliklerin kullanılamayacaklarını belirleyemez. Değişiklikleri ana dalda, hata düzeltme dalda veya iki birleşiminde tutmak istiyor olabilir. Bu çakışmayı, ana dalda iki dal arasındaki çakışan değişiklikleri uzlaştıran birleştirme işlemesi ile çözebilirsiniz.

:::image type="content" source="media/vs-2022/git-conflicts-understand-2.png" alt-text="Birleştirme işlemenin birleştirme çakışmalarını nasıl çözümleyeni diyagram.":::

En yaygın birleştirme çakışması senaryosu, güncelleştirmeleri uzak bir daldan yerel dalınıza (örneğin, origin/bugfix'den yerel hata düzeltme dalnıza) çekebilirsiniz. Bu çakışmaları aynı şekilde çözümleyebilirsiniz: Değişiklikleri muadi olarak kabul etmek için yerel dalda bir işleme oluşturun ve ardından birleştirmeyi tamamlar.

## <a name="prevent-merge-conflicts"></a>Birleştirme çakışmalarını önleme

Git, çoğu durumda dosya içeriğinin işlemeler arasında önemli ölçüde değişmeme durumuyla dosya değişikliklerini otomatik olarak birleştirmede iyidir. Dalınız ana dalın çok gerisinde ise, çekme isteği açmadan önce dallarınızı yeniden temel asanız iyi bir değerlendirmeyi göz önünde bulundurarak. Yeniden temel dallar çakışma olmadan ana dalınıza birleşecektir.

## <a name="resolve-merge-conflicts"></a>Birleştirme çakışmalarını çözümleme

- Aynı dalda başkalarla işbirliği yapmak için değişikliklerinizi iletirken birleştirme çakışmalarıyla karşınıza çıkabilirsiniz.

    :::image type="content" source="media/vs-2022/git-conflicts-push-link.png" alt-text="Bir anından sonra birleştirme çakışması ekran görüntüsü.":::

- Visual Studio üzerinde çalıştığın yerel dalı uzaktan izleme dalını algılar ve ardından size seçenekler sunar.

    :::image type="content" source="media/vs-2022/git-conflicts-pull-push-ui.png" alt-text="Yerel dal uzak dal arkasında olduğunda kullanılabilen seçeneklerin ekran görüntüsü.":::

    > [!NOTE]
    > Uzak deponız Zorla **Itme'yi destekliyorsa** Git'i kullanarak bunu   >  Ayarlar.

    Bu örnekte, uzak **depoda tanıtilen değişiklikleri** eklemek için Çekme ve Itme'yi seçin. Değişiklikleri çekme veya iki dalı birleştirmeye çalışırken birleştirme çakışmaları varsa, Visual Studio **Git** Değişiklikleri penceresinde, **Git** Deposu penceresinde ve çakışmaları olan tüm dosyalarda bunu size gösterir.

    :::image type="content" source="media/vs-2022/git-conflicts-notification-ui.png" alt-text="Birleştirme çakışması bildiriminin ekran görüntüsü.":::

- **Git Değişiklikleri penceresi,** **Unmerged Changes** altında çakışmaları olan dosyaların listesini gösterir. Çakışmaları çözümlemeye başlamak için bir dosyaya çift tıklayın. Veya düzenleyicide açılan çakışmaları olan bir dosyanız varsa Birleştirme Düzenleyicisini **Aç'ı da seçin.**

    :::image type="content" source="media/vs-2022/git-conflicts-status-ui.png" alt-text="Git Değişiklikleri penceresinde birleştirme çakışması durumunun ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-status-ui.png":::

- Birleştirme Düzenleyicisi'nde aşağıdaki yöntemlerden birini kullanarak (numaralı ekran görüntüsünde gösterilen şekilde) çakışmanızı çözümlemeye başlayabilirsiniz:

    1. Çakışmalarınızı satır satır kontrol edin ve onay kutularını seçerek sağ tarafı veya sol tarafı tutma arasında seçim seçin.
    1. Çakışan tüm değişikliklerinizi olduğu gibi yapın veya yoksayın.
    1. Sonuç penceresinde kodunuzu **el** ile düzenleyin.

    :::image type="content" source="media/vs-2022/git-conflicts-resolve-conflict.png" alt-text="2022'de birleştirme çakışması Visual Studio ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-resolve-conflict.png":::

    > [!TIP]
    > Birleştirme Düzenleyicisi'nde varsayılan düzenden farklı bir düzen kullanmak için dişli açılan menüsünü kullanabilirsiniz.
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-layout-options.png" alt-text="Düzenleyici düzenini birleştir seçeneklerinin ekran görüntüsü.":::
    >
    >Örneğin, aşağıdaki ekran görüntüsü dikey görünümün nasıl göründüğünü gösterir:
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-vertical-view.png" alt-text="Birleştirme Düzenleyicisi kullanıcı arabiriminde dikey görünümün ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-vertical-view.png":::

- Birleştirme çakışmalarını çözmeyi bitirerek Birleştirmeyi Kabul **Et'i seçin.** Çakışan tüm dosyalar için bu işlemi tekrarlayın.

    :::image type="content" source="media/vs-2022/git-conflicts-accept-merge.png" alt-text="Visual Studio 2022'de Birleştirmeyi Kabul Et eyleminin ekran görüntüsü.":::

- Bir birleştirme **işlemesi** oluşturmak ve çakışmayı çözmek için Git Değişiklikleri penceresini kullanın.

    :::image type="content" source="media/vs-2022/git-conflicts-merge-commit.png" alt-text="Git Değişiklikleri penceresini kullanarak birleştirme işlemesi oluşturma ekran görüntüsü.":::

    > [!NOTE]
    > Bir dosyada yaptığınız tüm değişiklikleri tutmanız gerekirse, Birleştirme Düzenleyicisi'ni açmak zorunda kalmadan, Birleştirilen Değişiklikler bölümünde dosyaya sağ tıklar ve Geçerli **Tut (Yerel)** öğesini seçin. 
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-keep-changes.png" alt-text="Güncel Tut ve Geleni Al menü seçeneklerinin ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek ve çakışmaları çözme hakkında daha fazla bilgi edinmek için birleştirme [komutunun Git web sayfasına bakın.](https://git-scm.com/docs/git-merge)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](git-with-visual-studio.md)
- [Visual Studio ve GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
