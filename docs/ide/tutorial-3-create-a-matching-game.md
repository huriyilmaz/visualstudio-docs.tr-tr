---
title: 'Öğretici 3: eşleşen oyun oluşturma'
description: Player 'ın gizli simge çiftlerini eşleşmesi gereken, eşleşen bir oyun oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfb5a8af72d7c41cdee913ee94c382c57e8cf5dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971420"
---
# <a name="tutorial-3-create-a-matching-game"></a>Öğretici 3: eşleşen oyun oluşturma

Bu öğreticide, oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu oluşturuyorsunuz.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanırsınız.

Bu öğretici aşağıdaki görevlerde size kılavuzluk eder:

- Simgeler gibi nesneleri bir <xref:System.Collections.Generic.List%601> nesnede depolayın.

- `foreach` `For Each` Bir listedeki öğeler arasında yinelemek Için C# veya Visual Basic döngüsünde bir döngü kullanın.

- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.

- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.

- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

Bitirdiğinizde, uygulamanız aşağıdaki görüntüye benzer görünmelidir:

![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Projeyi oluşturarak ve `TableLayoutPanel` denetimleri doğru hizalı tutmak için bir denetim ekleyerek başlayın.|
|[2. Adım: Rastgele nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Bir `Random` `List` Simge listesi oluşturmak için bir nesne ve nesne ekleyin.|
|[3. Adım: Her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md)|`Label`Her oyunun farklı olması için simgeleri denetimlere rastgele atayın.|
|[4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)|`Click`Tıklanan etiketin rengini değiştiren bir olay işleyicisi ekleyin.|
|[5. Adım: Etiket başvuruları ekleme](../ide/step-5-add-label-references.md)|Hangi etiketlere tıklandığını takip etmek için başvuru değişkenleri ekleyin.|
|[6. Adım: Süreölçer ekleme](../ide/step-6-add-a-timer.md)|Oyunda geçen süreyi takip etmek için forma bir zamanlayıcı ekleyin.|
|[7. Adım: Çiftleri görünür durumda tutma](../ide/step-7-keep-pairs-visible.md)|Eşleşen bir çift seçilirse, simge çiftlerini görünür durumda tutun.|
|[8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|`CheckForWinner()`Oyuncunun kazanıp kazanılmadığını doğrulamak için bir yöntem ekleyin.|
|[9. Adım: Diğer özellikleri deneme](../ide/step-9-try-other-features.md)|Simgeleri ve renkleri değiştirme, kılavuz ekleme ve ses ekleme gibi diğer özellikleri deneyin. Tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.|

Ayrıca harika, ücretsiz video öğrenimi kaynakları da mevcuttur. C# dilinde programlama hakkında daha fazla bilgi edinmek için bkz. [C# temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için, 1. **[Adım: proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** ile başlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)