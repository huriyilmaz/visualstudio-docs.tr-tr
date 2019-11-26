---
title: 'Öğretici 3: eşleşen oyun oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299857"
---
# <a name="tutorial-3-create-a-matching-game"></a>Öğretici 3: eşleşen oyun oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, oyuncunun gizli simge çiftlerini eşleştirmesi gereken bir eşleştirme oyunu oluşturuyorsunuz. Aşağıdakileri nasıl yapacağınızı öğrenirsiniz:

- Simgeleri gibi nesneleri bir `List` nesnesinde depolayın.

- Bir listedeki öğeler arasında yinelemek için C# , Visual Basic içinde görsel veya bir `For Each` döngüsünde `foreach` döngüsünü kullanın.

- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.

- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.

- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

  Bu öğreticiyi bitirdiğinizde, programınız aşağıdaki resim gibi görünecektir.

  ![Bu öğreticide oluşturduğunuz oyun](../ide/media/express-finishedgame.png "Express_FinishedGame") Bu öğreticide oluşturduğunuz oyun

> [!NOTE]
> Bu öğreticide, hem Visual C# hem de Visual Basic ele alınmaktadır; bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.

 Bir yerde tıkanıp kalırsanız veya programlamayla ilgili sorularınız olursa, MSDN forumlarından birinde sorunuzu göndermeyi deneyin. Bkz. forum ve [görsel C# forumuna](https://social.msdn.microsoft.com/Forums/en-US/home) [Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) . Ayrıca, yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Görselde C#programlama hakkında daha fazla bilgi edinmek için bkz [ C# . temel bilgiler: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje Oluşturma ve Formunuza Tablo Ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Projeyi oluşturarak ve denetimleri düzgün şekilde hizalı tutmak için bir `TableLayoutPanel` denetimi ekleyerek başlayın.|
|[2. Adım: Rasgele Nesne ve Simge Listesi Ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Simgelerin bir listesini oluşturmak için bir `Random` nesnesi ve `List` nesnesi ekleyin.|
|[3. Adım: Her Etikete Rasgele Simge Atama](../ide/step-3-assign-a-random-icon-to-each-label.md)|Her oyunun farklı olması için simgeleri `Label` denetimlerine rastgele atayın.|
|[4. Adım: Her Etikete Click Olay İşleyicisi Ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Tıklanan etiketin rengini değiştiren bir Click olayı işleyicisi ekleyin.|
|[5. Adım: Etiket Başvuruları Ekleme](../ide/step-5-add-label-references.md)|Hangi etiketlere tıklandığını takip etmek için başvuru değişkenleri ekleyin.|
|[6. Adım: Zamanlayıcı Ekleme](../ide/step-6-add-a-timer.md)|Oyunda geçen süreyi takip etmek için forma bir zamanlayıcı ekleyin.|
|[7. Adım: Çiftleri Görünür Kılma](../ide/step-7-keep-pairs-visible.md)|Eşleşen bir çift seçilirse, simge çiftlerini görünür durumda tutun.|
|[8. Adım: Oyuncunun Kazandığını Doğrulamak için Yöntem Ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Oyuncunun kazanıp kazanılmadığını doğrulamak için bir `CheckForWinner()` yöntemi ekleyin.|
|[9. Adım: Diğer Özellikleri Deneme](../ide/step-9-try-other-features.md)|Simgeleri ve renkleri değiştirme, kılavuz ekleme ve ses ekleme gibi diğer özellikleri deneyin. Tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.|
