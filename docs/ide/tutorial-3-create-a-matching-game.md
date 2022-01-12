---
title: 'Öğretici 3: Eşleştirme oyunu oluşturma'
description: Oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu derlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8d22d8600f3783ee14c260304135803aad4f149f
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135516549"
---
# <a name="tutorial-3-create-a-matching-game"></a>Öğretici 3: Eşleştirme oyunu oluşturma

Bu öğreticide, oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu oluşturuyorsunuz.

> [!NOTE]
> Bu öğreticide hem C# hem de Visual Basic, bu nedenle kullanmakta olan programlama diline özgü bilgilere odaklanın.

Bu öğretici, aşağıdaki görevlerde size yol gösterir:

- Simgeler gibi nesneleri bir nesnede <xref:System.Collections.Generic.List%601> depolar.

- C# içinde bir döngü veya bir Visual Basic öğeleri `foreach` arasında döngü yapmak için bir döngü `For Each` kullanın.

- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.

- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.

- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

Bitirişte, uygulamanız aşağıdaki görüntüye benzer şekilde görüntü gerekir:

![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Projeyi oluşturarak ve denetimlerin düzgün `TableLayoutPanel` hizalı olması için bir denetim ekleyerek başlayabilirsiniz.|
|[2. Adım: Rastgele nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Simge `Random` listesi oluşturmak `List` için bir nesnesi ve nesnesi ekleyin.|
|[3. Adım: Her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md)|Simgeleri denetimlere rastgele `Label` ataarak her bir oyunun farklı olduğunu görebilirsiniz.|
|[4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Tıklandı `Click` olan etiketin rengini değiştirmek için bir olay işleyicisi ekleyin.|
|[5. Adım: Etiket başvuruları ekleme](../ide/step-5-add-label-references.md)|Hangi etiketlere tıklandığını takip etmek için başvuru değişkenleri ekleyin.|
|[6. Adım: Süreölçer ekleme](../ide/step-6-add-a-timer.md)|Oyunda geçen süreyi takip etmek için forma bir zamanlayıcı ekleyin.|
|[7. Adım: Çiftleri görünür durumda tutma](../ide/step-7-keep-pairs-visible.md)|Eşleşen bir çift seçilirse, simge çiftlerini görünür durumda tutun.|
|[8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Oyuncunun `CheckForWinner()` kazanıp kazana olmadığını doğrulamak için bir yöntem ekleyin.|
|[9. Adım: Diğer özellikleri deneme](../ide/step-9-try-other-features.md)|Simgeleri ve renkleri değiştirme, kılavuz ekleme ve ses ekleme gibi diğer özellikleri deneyin. Tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.|

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için **[1. Adım: Proje oluşturma ve form sayfanıza bir tablo ekleyin.](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)