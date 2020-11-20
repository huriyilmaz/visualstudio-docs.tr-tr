---
title: Yazılan ve yazılmayan veri kümelerinin karşılaştırması
description: Yazılı ve türsüz veri kümeleri arasındaki farkı anlayın. Türü belirtilmiş ve türsüz veri kümelerinde veri erişimini kontrast.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b2dc8d78f42d210741c904e3e475be33f2443e74
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998063"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
Türü belirtilmiş veri kümesi, ilk olarak temel sınıftan türetilmiş bir veri kümesidir <xref:System.Data.DataSet> ve sonra yeni ve türü kesin belirlenmiş bir veri kümesi sınıfı oluşturmak için bir. xsd dosyasında depolanan **veri kümesi Tasarımcısı** bilgileri kullanır. Şemadan alınan bilgiler (tablolar, sütunlar, vb.) oluşturulup ilk sınıf nesne ve özellik kümesi olarak bu yeni veri kümesi sınıfına derlenir. Türü belirtilmiş bir veri kümesi temel sınıftan devraldığı için <xref:System.Data.DataSet> , yazılan sınıf sınıfın tüm işlevselliğini varsayar <xref:System.Data.DataSet> ve bir sınıfın örneğini bir parametre olarak alan yöntemlerle birlikte kullanılabilir <xref:System.Data.DataSet> .

Bunun aksine, türsüz bir veri kümesinin karşılık gelen yerleşik bir şeması yoktur. Türü belirtilmiş bir veri kümesinde olduğu gibi, türsüz bir veri kümesi tablo, sütun vb. içerir, ancak bunlar yalnızca koleksiyonlar olarak sunulur. (Ancak, tablo ve diğer veri öğelerini türsüz bir veri kümesinde el ile oluşturduktan sonra, veri kümesinin yapısını bir şema olarak DataSet 'in metodunu kullanarak dışarı aktarabilirsiniz <xref:System.Data.DataSet.WriteXmlSchema%2A> .)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Türü belirtilmiş ve türsüz veri kümelerinde kontrast verileri erişimi
Türü belirtilmiş bir veri kümesinin sınıfının, özelliklerinin tablo ve sütunların gerçek adlarını aldığı bir nesne modeli vardır. Örneğin, türü belirtilmiş bir veri kümesiyle çalışıyorsanız, aşağıdaki gibi bir kod kullanarak bir sütuna başvurabilirsiniz:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Buna karşılık, türsüz bir veri kümesiyle çalışıyorsanız, eşdeğer kod şu şekilde olur:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

Yazılan erişim yalnızca Visual Studio **Kod Düzenleyicisi**'nde IntelliSense tarafından tam olarak desteklenmekte, ancak aynı zamanda daha kolay okunabilir. İle çalışmanın yanı sıra, yazılan veri kümesinin sözdizimi, derleme zamanında tür denetlemesi sağlar ve veri kümesi üyelerine değer atarken hata olasılığını büyük ölçüde azaltır. Sınıfınıza bir sütunun adını değiştirip <xref:System.Data.DataSet> uygulamanızı derlerseniz, derleme hatası alırsınız. **Görev listesi** yapı hatasına çift tıklayarak, eski sütun adına başvuruda bulunan satır veya kod satırlarına doğrudan gidebilirsiniz. Belirlenmiş bir veri kümesindeki tablo ve sütunlara erişim, çalışma zamanında, çalışma zamanında koleksiyonlar aracılığıyla değil, derleme zamanında belirlendiği için, çalışma zamanında biraz daha hızlıdır.

Yazılan veri kümelerinde birçok avantaj olsa da, türsüz bir veri kümesi çeşitli koşullarda yararlı olur. En belirgin senaryo, veri kümesi için kullanılabilir şema olmadığında olur. Bu durum, örneğin, uygulamanız veri kümesi döndüren bir bileşenle etkileşiyorsa, ancak yapısının ne olduğu konusunda bilgi sahibi değilseniz bu durum oluşabilir. Benzer şekilde, statik, öngörülebilir bir yapıya sahip olmayan verilerle çalışırken zamanlar da vardır. Bu durumda, yazılan veri kümesi sınıfını veri yapısındaki her değişiklik ile yeniden oluşturmanız gerektiğinden, türü belirtilmiş bir veri kümesi kullanılması pratik değildir.

Daha genel olarak, bir şemayı kullanılabilir olmadan dinamik olarak veri kümesi oluşturabileceğiniz Birçok zaman vardır. Bu durumda, veri kümesi, verilerin ilişkisel bir şekilde gösterilebileceği sürece, bilgileri saklayabilmeniz için yalnızca uygun bir yapıdır. Aynı zamanda, diğer bir işleme geçirilecek veya bir XML dosyası yazmak gibi bilgileri seri hale getirme yeteneği gibi veri kümesinin özelliğinden yararlanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
