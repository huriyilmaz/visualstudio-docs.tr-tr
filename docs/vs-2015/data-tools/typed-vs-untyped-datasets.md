---
title: Türü belirtilmiş veya türsüz veri kümeleri | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39a16a200bbc057288ae2741e7d504566b0368e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667148"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Türü belirtilmiş veri kümesi, ilk olarak temel sınıftan türetilmiş bir veri kümesidir <xref:System.Data.DataSet> ve sonra yeni ve türü kesin belirlenmiş bir veri kümesi sınıfı oluşturmak için bir. xsd dosyasında depolanan **veri kümesi Tasarımcısı**bilgileri kullanır. Şemadan alınan bilgiler (tablolar, sütunlar, vb.) oluşturulup ilk sınıf nesne ve özellik kümesi olarak bu yeni veri kümesi sınıfına derlenir. Türü belirtilmiş bir veri kümesi temel sınıftan devraldığı için <xref:System.Data.DataSet> , yazılan sınıf sınıfın tüm işlevselliğini varsayar <xref:System.Data.DataSet> ve bir sınıfın örneğini bir parametre olarak alan yöntemlerle birlikte kullanılabilir <xref:System.Data.DataSet> .

 Bunun aksine, türsüz bir veri kümesinin karşılık gelen yerleşik bir şeması yoktur. Türü belirtilmiş bir veri kümesinde olduğu gibi, türsüz bir veri kümesi tablo, sütun vb. içerir, ancak bunlar yalnızca koleksiyonlar olarak sunulur. (Ancak, tablo ve diğer veri öğelerini türsüz bir veri kümesinde el ile oluşturduktan sonra, veri kümesinin yapısını bir şema olarak DataSet 'in metodunu kullanarak dışarı aktarabilirsiniz <xref:System.Data.DataSet.WriteXmlSchema%2A> .)

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Türü belirtilmiş ve türsüz veri kümelerinde veri erişimini karşıt olarak
 Türü belirtilmiş bir veri kümesinin sınıfının, özelliklerinin tablo ve sütunların gerçek adlarını aldığı bir nesne modeli vardır. Örneğin, türü belirtilmiş bir veri kümesiyle çalışıyorsanız, aşağıdaki gibi bir kod kullanarak bir sütuna başvurabilirsiniz:

 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]

 Buna karşılık, türsüz bir veri kümesiyle çalışıyorsanız, eşdeğer kod şu şekilde olur:

 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]

 Yazılan erişim yalnızca daha kolay okunabilir, ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **kod düzenleyicisinde**IntelliSense tarafından tam olarak desteklenir. İle çalışmanın yanı sıra, yazılan veri kümesinin sözdizimi, derleme zamanında tür denetlemesi sağlar ve veri kümesi üyelerine değer atarken hata olasılığını büyük ölçüde azaltır. Sınıfınıza bir sütunun adını değiştirip <xref:System.Data.DataSet> uygulamanızı derlerseniz, derleme hatası alırsınız. **Görev listesi**yapı hatasına çift tıklayarak, eski sütun adına başvuruda bulunan satır veya kod satırlarına doğrudan gidebilirsiniz. Yazılan bir veri kümesindeki tablo ve sütunlara erişim çalışma zamanında daha hızlı bir şekilde erişim, çalışma zamanında koleksiyonlar aracılığıyla değil, derleme zamanında belirlendiği için de biraz daha hızlıdır.

 Yazılan veri kümelerinde birçok avantaj olsa da, türsüz bir veri kümesi çeşitli koşullarda yararlı olur. En belirgin senaryo, veri kümesi için kullanılabilir şema olmadığında olur. Bu durum, örneğin, uygulamanız veri kümesi döndüren bir bileşenle etkileşiyorsa, ancak yapısının ne olduğu konusunda bilgi sahibi değilseniz bu durum oluşabilir. Benzer şekilde, statik, öngörülebilir bir yapıya sahip olmayan verilerle çalışırken zamanlar da vardır. Bu durumda, yazılan veri kümesi sınıfını veri yapısındaki her değişiklik ile yeniden oluşturmanız gerektiğinden, türü belirtilmiş bir veri kümesi kullanılması pratik değildir.

 Daha genel olarak, bir şemayı kullanılabilir olmadan dinamik olarak veri kümesi oluşturabileceğiniz Birçok zaman vardır. Bu durumda, veri kümesi, verilerin ilişkisel bir şekilde gösterilebileceği sürece, bilgileri saklayabilmeniz için yalnızca uygun bir yapıdır. Aynı zamanda, diğer bir işleme geçirilecek veya bir XML dosyası yazmak gibi bilgileri seri hale getirme yeteneği gibi veri kümesinin özelliğinden yararlanabilirsiniz.
