---
title: 'Öğretici 3: eşleşen oyun oluşturma'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5161f81aaf3edf654a5979f6226449bc52604167
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516585"
---
# <a name="tutorial-3-create-a-matching-game"></a>Öğretici 3: eşleşen oyun oluşturma

Bu öğreticide, oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu oluşturuyorsunuz.

> [!NOTE]
> Bu öğretici hem hem C# de Visual Basic, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanırsınız.

Bu öğretici aşağıdaki görevlerde size kılavuzluk eder:

- Simgeleri gibi nesneleri bir <xref:System.Collections.Generic.List%601> nesnesinde depolayın.

- Bir listedeki öğeler arasında yinelemek C# için, içinde bir `foreach` döngüsü veya `For Each` Visual Basic döngüsü kullanın.

- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.

- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.

- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

Bitirdiğinizde, uygulamanız aşağıdaki görüntüye benzer görünmelidir:

![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Projeyi oluşturarak ve denetimleri düzgün şekilde hizalı tutmak için bir `TableLayoutPanel` denetimi ekleyerek başlayın.|
|[2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Simgelerin bir listesini oluşturmak için bir `Random` nesnesi ve `List` nesnesi ekleyin.|
|[3. Adım: her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md)|Her oyunun farklı olması için simgeleri `Label` denetimlerine rastgele atayın.|
|[4. Adım: Her Etikete Click olay işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Tıklanan etiketin rengini değiştiren `Click` bir olay işleyicisi ekleyin.|
|[5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md)|Hangi etiketlere tıklandığını takip etmek için başvuru değişkenleri ekleyin.|
|[6. Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md)|Oyunda geçen süreyi takip etmek için forma bir zamanlayıcı ekleyin.|
|[7. Adım: çiftleri görünür tutma](../ide/step-7-keep-pairs-visible.md)|Eşleşen bir çift seçilirse, simge çiftlerini görünür durumda tutun.|
|[8. Adım: oyuncunun kazandığını doğrulamak için bir yöntem ekleyin](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Oyuncunun kazanıp kazanılmadığını doğrulamak için bir `CheckForWinner()` yöntemi ekleyin.|
|[9. Adım: diğer özellikleri deneme](../ide/step-9-try-other-features.md)|Simgeleri ve renkleri değiştirme, kılavuz ekleme ve ses ekleme gibi diğer özellikleri deneyin. Tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.|

Ayrıca harika, ücretsiz video öğrenimi kaynakları da mevcuttur. İçinde C#programlama hakkında daha fazla bilgi edinmek için bkz [ C# . temel bilgiler: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için, 1. **[Adım: proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** ile başlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticiler](/visualstudio/get-started/csharp/)
* [Visual Basic öğreticileri](/visualstudio/get-started/visual-basic/)
* [C++izleyin](/cpp/get-started/tutorial-console-cpp)
