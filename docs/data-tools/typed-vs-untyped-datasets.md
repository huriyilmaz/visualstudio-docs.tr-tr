---
title: Yazılan ve yazılmayan veri kümelerinin karşılaştırması
description: Türü yazıldı ve yazlanmamış veri kümeleri arasındaki farkı anlıyoruz. Türü yazlanmamış ve yazlanmamış veri kümelerinden veri erişimini karşıtlıklı olarak kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3ce12fd272297429ba62c4e947025ada7c350d26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036842"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
Türetilen veri kümesi, ilk olarak temel sınıftan türetilen ve daha sonra yeni, kesin türü kesin olarak yazlanmış bir veri kümesi sınıfı oluşturmak için bir .xsd dosyasında depolanan Veri Kümesi Tasarımcısı 'den bilgileri kullanan bir veri <xref:System.Data.DataSet> kümesidir.  Şemadan alınan bilgiler (tablolar, sütunlar ve diğer), bu yeni veri kümesi sınıfına bir dizi birinci sınıf nesne ve özellik olarak oluşturulur ve derlenmiş olur. Türü türüne sahip bir veri kümesi temel sınıftan devralına olduğundan, türü türüne sahip sınıf sınıfın tüm işlevlerini varsayer ve bir sınıfın örneğini parametre olarak alan <xref:System.Data.DataSet> <xref:System.Data.DataSet> <xref:System.Data.DataSet> yöntemlerle kullanılabilir.

Buna karşılık türlanmamış bir veri kümesine karşılık gelen yerleşik şema yoktur. Türü yaznmış bir veri kümesinde olduğu gibi, türe sahip olmayan bir veri kümesinde tablolar, sütunlar ve diğer veriler bulunur; ancak bunlar yalnızca koleksiyonlar olarak ortaya çıkar. (Ancak, türlanmamış bir veri kümesinde tabloları ve diğer veri öğelerini el ile oluşturduktan sonra, veri kümesi yöntemini kullanarak veri kümesi yapısını şema olarak dışarı <xref:System.Data.DataSet.WriteXmlSchema%2A> aktarabilirsiniz.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Türü yazıldı ve yazlanmamış veri kümelerine veri erişimini karşıtlığı
Türü türüne sahip bir veri kümesi sınıfı, özelliklerinin tabloların ve sütunların gerçek adlarını alan bir nesne modeline sahiptir. Örneğin, türü türüne sahip bir veri kümesiyle çalışıyorsanız, aşağıdaki gibi bir kodu kullanarak bir sütuna başvurabilirsiniz:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet4":::

Buna karşılık, türlanmamış bir veri kümesiyle çalışıyorsanız eşdeğer kod şöyledir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet5":::

Türü yazarak erişim okumak kolay değildir, aynı zamanda Kod Düzenleyicisi'nde IntelliSense tarafından Visual Studio **de destekler.** Türü daha kolay olan veri kümesi söz dizimi, derleme zamanında tür denetimi sağlar ve veri kümesi üyelerine değer atarken hata olma olasılığını büyük ölçüde azaltır. Sınıfınıza bir sütunun adını değiştirir ve <xref:System.Data.DataSet> sonra da uygulamayı derlersiniz, derleme hatası alırsınız. içinde derleme hatasına çift **Görev Listesi,** doğrudan eski sütun adına başvurulan satır veya kod satırlarına gidebilirsiniz. Türe sahip bir veri kümesinde tablolara ve sütunlara erişim de çalışma zamanında biraz daha hızlıdır çünkü erişim çalışma zamanında koleksiyonlar aracılığıyla değil derleme zamanında belirlenir.

Tür türe sahip veri kümelerinin birçok avantajı olsa da, türlanmamış bir veri kümesi çeşitli durumlarda yararlıdır. En belirgin senaryo, veri kümesi için kullanılabilir şema olmadığıdır. Örneğin, uygulamanız veri kümesi döndüren bir bileşenle etkileşimde bulunabiliyorsa ancak yapısının ne olduğunu önceden bilmiyorsanız bu durum oluşabilir. Benzer şekilde, statik, tahmin edilebilir bir yapıya sahip olmayan verilerle çalışırken de bazı zamanlar vardır. Bu durumda, türe sahip bir veri kümesi kullanmak pratik değildir, çünkü türe sahip veri kümesi sınıfını veri yapısında her değişiklikle yeniden oluşturabilirsiniz.

Daha genel olarak, kullanılabilir bir şemaya sahip olmadan dinamik olarak bir veri kümesi oluşturabilirsiniz. Bu durumda, veriler ilişkisel bir şekilde temsil edilen sürece, veri kümesi yalnızca bilgileri tutabilirsiniz kullanışlı bir yapıdır. Aynı zamanda, başka bir işleme aktaracak bilgileri seri hale getirme veya bir XML dosyası yazma gibi veri kümesi özelliklerine sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
