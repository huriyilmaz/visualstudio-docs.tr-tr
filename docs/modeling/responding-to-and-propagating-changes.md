---
title: Değişikliklere Yanıt Verme ve Değişiklikleri Yayma
description: Bir öğe oluşturulduğunda, silindiğinde veya güncelleştirildiğinde, değişikliği modelin diğer bölümlerine veya dış kaynaklara yayın kod yazabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8027b1fa5a2b050a0bb40160d44063857cc76927
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637510"
---
# <a name="respond-to-and-propagate-changes"></a>Değişiklikleri yanıtlama ve yayma

Bir öğe oluşturulduğunda, silindiğinde veya güncelleştirildiğinde, değişikliği modelin diğer bölümlerine ya da dosyalar, veritabanları veya diğer bileşenler gibi dış kaynaklara yayın kod yazabilirsiniz.

## <a name="reference"></a>Başvuru

Bir kılavuz olarak, bu teknikleri aşağıdaki sırayla düşünün:

|Teknik|Senaryolar|Daha fazla bilgi edinmek için|
|-|-|-|
|Hesaplanan etki alanı özelliği tanımlayın.|Değeri modelde diğer özelliklerden hesaplanan bir etki alanı özelliği. Örneğin, ilgili öğelerin fiyatlarının toplamı olan bir fiyat.|[Hesaplanan ve Özel Depolama Özellikleri](../modeling/calculated-and-custom-storage-properties.md)|
|Özel etki alanı Depolama tanımlayın.|Modelin diğer kısımlarında veya harici olarak depolanan bir etki alanı özelliği. Örneğin, bir ifade dizesini modelde bir ağaçta ayrıştırarak.|[Hesaplanan ve Özel Depolama Özellikleri](../modeling/calculated-and-custom-storage-properties.md)|
|OnValueChanging ve OnDeleting gibi değişiklik işleyicilerini geçersiz kılma|Farklı öğeleri eşitle ve dış değerleri modelle eşitle tut.<br /><br /> Değerleri tanımlı aralıklar ile kısıtlar.<br /><br /> Özellik değeri ve diğer değişikliklerden hemen önce ve sonra çağrılır. Bir özel durum atarak değişikliği sonlandırarak sonlandırılır.|[Etki Alanı Özellik Değeri Değişiklik İşleyicileri](../modeling/domain-property-value-change-handlers.md)|
|Kurallar|Bir değişikliğin olduğu bir işlem sona ermeden hemen önce yürütme için kuyruğa alınan kurallar tanımlayabilirsiniz. Bunlar Geri Al veya Yeniden Çalıştır'da yürütülmez. Bunları kullanarak mağazanın bir bölümünü başka bir bölümle eşitlerken tutabilirsiniz.|[Değişiklikleri Modelin İçinde Yayan Kurallar](../modeling/rules-propagate-changes-within-the-model.md)|
|Olayları Depolama|Modelleme deposu, öğe veya bağlantı ekleme veya silme ya da bir özelliğin değerini değiştirme gibi olayların bildirimlerini sağlar. Olay, Geri Al ve Yinele'de de yürütülür. Depoda yer alan değerleri güncelleştirmek için mağaza olaylarını kullanın.|[Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET Olayları|Şekiller, fare tıklamalarına ve diğer hareketlere yanıt veren olay işleyicilerine sahiptir. Her nesne için bu olaylara kaydolmanız gerekir. Kayıt genellikle InitializeInstanceResources geçersiz kılınarak yapılır ve her öğe için yapılması gerekir.<br /><br /> Bu olaylar genellikle bir işlem dışında gerçekleşir.|[Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Sınır Kuralları|Bir sınır kuralı, bir şeklin sınırlarını sınırlamak için özel olarak kullanılır.|[BoundsRules Şekil Konumunu ve Boyutunu Kısıtlamama](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Seçim kuralları|Seçim kuralları özellikle kullanıcının seçeceklerini kısıtlar.|[Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Gölge, ok ucu, renk ve çizgi genişlikleri ve stil gibi şekillerin ve bağlayıcıların özelliklerini kullanarak model öğelerinin eyaletlerini gösterir.|[Modeli Yansıtacak Şekilleri ve Bağlayıcıları Güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Kuralları karşılaştırma ve olayları depolama

Modelde değişiklikler oluştuğunda değişiklik doğrulayıcıları, kuralları ve olayları çalıştırın.

Kurallar genellikle değişikliğin meydana geldiği son işlemde uygulanır ve bir işlemde yapılan değişiklikler işlendikten sonra olaylar uygulanır.

Modeli Store dışındaki nesnelerle eşitlemek için mağaza olaylarını ve Mağaza içindeki tutarlılığı korumak için kuralları kullanın.

- **Özel Kurallar Oluşturma** Soyut bir kuraldan türetilmiş bir sınıf olarak özel bir kural oluşturabilirsiniz. Çerçeveyi özel kural hakkında da bilgilendirmelisiniz. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

- **Olaylara Abone Olmak** Bir etkinliğe abone olmadan önce bir olay işleyicisi ve temsilci oluşturun. Ardından özelliği <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> kullanarak olayına abone olun. Daha fazla bilgi için [bkz. Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

- **Değişiklikleri Geri Alma** Bir işlemi geri almak için olaylar ortaya çıkar ancak kurallar uygulanmaz. Bir kural bir değeri değiştirirse ve bu değişikliği geri asanız, geri alma eylemi sırasında değer özgün değere sıfırlanır. Bir olay ekleyebilirsiniz, el ile değeri özgün değerine geri değiştirmelisiniz. İşlemler ve geri alma hakkında daha fazla bilgi edinmek için, [bkz. How to: Use Transactions to Update the Model](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Olay Bağımsız Değişkenlerini Kurallara ve Olaylara Geçirme** Hem olaylara hem de kurallara, `EventArgs` modelin nasıl değiştikleri hakkında bilgi olan bir parametre geçirildi.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Domain-Specific Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)