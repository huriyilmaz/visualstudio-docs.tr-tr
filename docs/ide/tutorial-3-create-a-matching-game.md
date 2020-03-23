---
title: 'öğretici 3: eşleşen bir oyun oluşturma'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619c21f4878f2e421ee5ac5ea76a68cd6e6bc337
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579710"
---
# <a name="tutorial-3-create-a-matching-game"></a>öğretici 3: eşleşen bir oyun oluşturma

Bu öğreticide, oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu oluşturuyorsunuz.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic'i kapsar, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.

Bu öğretici aşağıdaki görevleri size yol sağlar:

- Simgeler gibi nesneleri bir <xref:System.Collections.Generic.List%601> nesnede depolayın.

- Listedeki `foreach` öğeleri tekrarlamak `For Each` için C# veya Visual Basic'teki bir döngü yü kullanın.

- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.

- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.

- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

İşlemi tamamladığınızda, uygulamanız aşağıdaki resme benzer olmalıdır:

![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Öğretici bağlantılar

|Başlık|Açıklama|
|-----------|-----------------|
|[Adım 1: Proje oluşturma ve forma tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Projeyi oluşturarak ve `TableLayoutPanel` denetimleri düzgün hizalamak için bir denetim ekleyerek başlayın.|
|[Adım 2: Rastgele bir nesne ve simgelerin listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Simgelerin `Random` listesini `List` oluşturmak için bir nesne ve nesne ekleyin.|
|[Adım 3: Her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md)|Her oyun farklı olacak şekilde `Label` simgeleri denetimlere rasgele atayın.|
|[Adım 4: Her etikete bir tıklama olay işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Tıklanan `Click` etiketin rengini değiştiren bir olay işleyicisi ekleyin.|
|[Adım 5: Etiket referansları ekleme](../ide/step-5-add-label-references.md)|Hangi etiketlere tıklandığını takip etmek için başvuru değişkenleri ekleyin.|
|[Adım 6: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md)|Oyunda geçen süreyi takip etmek için forma bir zamanlayıcı ekleyin.|
|[Adım 7: Çiftleri görünür tutun](../ide/step-7-keep-pairs-visible.md)|Eşleşen bir çift seçilirse, simge çiftlerini görünür durumda tutun.|
|[Adım 8: Oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Oyuncunun `CheckForWinner()` kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin.|
|[Adım 9: Diğer özellikleri deneyin](../ide/step-9-try-other-features.md)|Simgeleri ve renkleri değiştirme, kılavuz ekleme ve ses ekleme gibi diğer özellikleri deneyin. Tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.|

Ayrıca büyük, ücretsiz video öğrenme kaynakları sizin için kullanılabilir. C#'da programlama hakkında daha fazla bilgi edinmek [için C# temellerine bakın: Yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Visual Basic'te programlama hakkında daha fazla bilgi edinmek [için Visual Basic temellerine bakın: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için Adım 1 ile **[başlayın: Bir proje oluşturun ve formunuza bir tablo ekleyin.](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# eğitimleri](/visualstudio/get-started/csharp/)
* [Visual Basic eğitimleri](/visualstudio/get-started/visual-basic/)
* [C++ eğitimleri](/cpp/get-started/tutorial-console-cpp)
