---
title: Değişikliklere Yanıt Verme ve Değişiklikleri Yayma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe09c242fce137d90b90ff2d6c547cee1ed2dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595403"
---
# <a name="respond-to-and-propagate-changes"></a>Değişiklikleri yanıtlama ve yayma

Bir öğe oluşturulduğunda, silindiğinde veya güncelleştirilirken, değişikliği modelin diğer bölümlerine veya dosyalar, veritabanları veya diğer bileşenler gibi dış kaynaklara yayan bir kod yazabilirsiniz.

## <a name="reference"></a>Başvuru

Bir kılavuz olarak aşağıdaki şekilde bu teknikleri göz önünde bulundurun:

|Teknik|Senaryolar|Daha fazla bilgi edinmek için|
|-|-|-|
|Hesaplanan bir etki alanı özelliği tanımlayın.|Değeri modeldeki diğer özelliklerden hesaplanan bir alan özelliği. Örneğin, ilgili öğelerin fiyatlarının toplamı olan bir fiyat.|[Hesaplanan ve Özel Depolama Özellikleri](../modeling/calculated-and-custom-storage-properties.md)|
|Özel bir depolama alanı özelliği tanımlayın.|Modelin diğer bölümlerinde veya dışarıdan depolanan bir etki alanı özelliği. Örneğin, bir ifade dizesini modeldeki bir ağaca ayrıştırabilirsiniz.|[Hesaplanan ve Özel Depolama Özellikleri](../modeling/calculated-and-custom-storage-properties.md)|
|OnValueChanging ve Onsilinmeye gibi değişiklik işleyicilerini geçersiz kılın|Farklı öğeleri eşitlenmiş halde tutun ve dış değerleri modeliyle eşitlenmiş halde tutun.<br /><br /> Değerleri tanımlı aralıklar ile sınırlayın.<br /><br /> Özellik değeri ve diğer değişikliklerden hemen önce ve sonra çağrılır. Bir özel durum oluşturarak değişikliği sonlandırabilirsiniz.|[Etki Alanı Özellik Değeri Değişiklik İşleyicileri](../modeling/domain-property-value-change-handlers.md)|
|Kurallar|Yalnızca bir değişikliğin gerçekleştiği işlemin sonundan önce yürütülmek üzere kuyruğa alınan kuralları tanımlayabilirsiniz. Bunlar geri alma veya yineleme sırasında yürütülmez. Depolama alanının bir bölümünü başka bir ile eşitlenmiş halde tutmak için bunları kullanın.|[Değişiklikleri Modelin İçinde Yayan Kurallar](../modeling/rules-propagate-changes-within-the-model.md)|
|Olayları depola|Modelleme deposu bir öğe veya bağlantı ekleme veya silme ya da bir özelliğin değerini değiştirme gibi olayların bildirimlerini sağlar. Olay Ayrıca geri al ve Yinele ' de yürütülür. Depoda olmayan değerleri güncelleştirmek için mağaza olaylarını kullanın.|[Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET etkinlikleri|Şekillerin fare tıklamalarına ve diğer hareketlere yanıt veren olay işleyicileri vardır. Her nesne için bu olaylara kaydolmanız gerekir. Kayıt genellikle ınitializeınstanceresogenellerinin geçersiz kılması sırasında yapılır ve her öğe için yapılmalıdır.<br /><br /> Bu olaylar genellikle bir işlemin dışında oluşur.|[Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Sınır kuralları|Sınır kuralı özellikle bir şeklin sınırlarını kısıtlamak için kullanılır.|[BoundsRules Şekil Konumunu ve Boyutunu Kısıtlamama](/visualstudio/modeling/boundsrules-constrain-shape-location-and-size?view=vs-2015)|
|Seçim kuralları|Seçim kuralları, kullanıcının neleri seçbileceklerini özellikle kısıtlar.|[Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Model öğelerinin durumlarını gölge, ok uçları, renk ve çizgi genişlikleri ve stil gibi şekillerin ve bağlayıcıların özelliklerini kullanarak belirtin.|[Modeli Yansıtacak Şekilleri ve Bağlayıcıları Güncelleştirme](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Kuralları karşılaştırın ve olayları depolayın

Bir modelde değişiklik olduğunda değişiklik noers, kurallar ve olaylar çalıştırılır.

Kurallar genellikle değişikliğin gerçekleştiği bitiş işleminde uygulanır ve bir işlemdeki değişiklikler gerçekleştirildikten sonra olaylar uygulanır.

Modeli mağaza dışındaki nesnelerle eşleştirmek için mağaza olaylarını ve mağaza içinde tutarlılığı sürdürmek için kuralları kullanın.

- **Özel kurallar oluşturma** Bir soyut kuraldan türetilmiş sınıf olarak özel bir kural oluşturursunuz. Ayrıca, özel kural hakkında çatıya bildirimde bulunmalıdır. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

- **Olaylara abone olma** Bir olaya abone olabilmek için önce bir olay işleyicisi ve temsilci oluşturun. Ardından, <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> olaya abone olmak için özelliğini kullanın. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Değişiklikler geri alınıyor** Bir işlemi geri aldığınızda, olaylar tetiklenir, ancak kurallar uygulanmaz. Bir kural bir değeri değiştirirse ve bu değişikliği geri alırsanız, geri alma eylemi sırasında değer özgün değere sıfırlanır. Bir olay ortaya çıktığında, değeri el ile özgün değerine geri değiştirmeniz gerekir. İşlemler ve geri alma hakkında daha fazla bilgi edinmek için bkz. [nasıl yapılır: modeli güncelleştirmek Için Işlemleri kullanma](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Olay bağımsız değişkenlerini kurallara ve olaylara geçirme** Her iki olay ve kurala de `EventArgs` modelin nasıl değiştiği hakkında bilgi içeren bir parametre iletilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
