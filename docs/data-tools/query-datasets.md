---
title: Veri kümelerini sorgulama
description: Sorgu veri kümelerini anlama. Veri kümesi büyük/küçük harf duyarlılığı hakkında bilgi öğrenin. Veri tablosunda belirli bir satırı bulma, sütun değerlerine göre satırları bulma ve ilgili kayıtlara erişme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3e9b05dc4687744a73958c05ff2aa4fd1c987e92964fcd11792141659dfe7e73
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121328182"
---
# <a name="query-datasets"></a>Veri kümelerini sorgulama
Bir veri kümesinde belirli kayıtları aramak için DataTable'da yöntemini kullanın, tablonun Satırlar koleksiyonunda döngü yapmak için kendi foreach deyiminizi yazın veya `FindBy` LINQ to DataSet. [](/dotnet/framework/data/adonet/linq-to-dataset)

## <a name="dataset-case-sensitivity"></a>Veri kümesi büyük/küçük harf duyarlılığı
Bir veri kümesinde tablo ve sütun adları varsayılan olarak büyük/küçük harfe duyarlı değildir. Diğer bir ifadeyle, "Müşteriler" adlı bir veri kümesinde yer alan tabloya "müşteriler" de denir. Bu, aşağıdakiler de dahil olmak üzere birçok veritabanındaki adlandırma SQL Server. Bu SQL Server varsayılan davranış, veri öğelerinin adlarının yalnızca büyük/büyük harfe göre ayırtı olamaz olmasıdır.

> [!NOTE]
> Veri kümelerinden farklı olarak, XML belgeleri büyük/büyük/büyük harfe duyarlıdır, bu nedenle şemalarda tanımlanan veri öğelerinin adları büyük/büyük/büyük harfe duyarlıdır. Örneğin şema protokolü, şemanın "Müşteriler" adlı bir tablo ve "customers" adlı farklı bir tablo tanımlamalarını sağlar. Bir veri kümesi sınıfı oluşturmak için yalnızca büyük/küçük harfe göre farklı öğeler içeren bir şema kullanılırken ad çakışmaları ile sonuçlanabilirsiniz.

Ancak büyük/küçük harf duyarlılığı, verilerin veri kümesi içinde yorumlanmasında bir faktör olabilir. Örneğin, bir veri kümesi tablosunda verileri filtrelerken, karşılaştırmanın büyük/küçük harfe duyarlı olup olmadığına bağlı olarak arama ölçütleri farklı sonuçlar getirebilirsiniz. Veri kümesi özelliğini ayarerek filtreleme, arama ve sıralamanın büyük/küçük harf duyarlılığını kontrol <xref:System.Data.DataSet.CaseSensitive%2A> altına aabilirsiniz. Veri kümesinde yer alan tüm tablolar varsayılan olarak bu özelliğin değerini devralmaktadır. (Tablonun özelliğini ayarerek her tablo için bu özelliği geçersiz <xref:System.Data.DataTable.CaseSensitive%2A> kılabilirsiniz.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Veri tablosunda belirli bir satırı bulma

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Birincil anahtar değerine sahip türüne sahip bir veri kümesinde satır bulmak için

- Bir satırı bulmak için tablonun birincil anahtarını `FindBy` kullanan kesin olarak türü kesin olarak yazıldı yöntemini çağırabilirsiniz.

     Aşağıdaki örnekte sütun, `CustomerID` tablonun birincil `Customers` anahtarıdır. Bu, oluşturulan yöntemin `FindBy` olduğu anlamına `FindByCustomerID` gelir. Örnekte, oluşturulan yöntemi kullanarak belirli <xref:System.Data.DataRow> bir değişkenin nasıl atan olduğu `FindBy` gösterir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet18":::

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Birincil anahtar değerine sahip türlanmamış bir veri kümesinde satır bulmak için

- Birincil <xref:System.Data.DataRowCollection.Find%2A> anahtarı parametre <xref:System.Data.DataRowCollection> olarak geçerek koleksiyonun yöntemini çağırma.

     Aşağıdaki örnek adlı yeni bir satırın nasıl bildir ve `foundRow` yöntemin dönüş değerini atamayı <xref:System.Data.DataRowCollection.Find%2A> gösterir. Birincil anahtar bulunursa, sütun dizini 1'in içeriği bir ileti kutusunda görüntülenir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet19":::

## <a name="find-rows-by-column-values"></a>Sütun değerlerine göre satırları bulma

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Herhangi bir sütundaki değerleri temel alan satırları bulmak için

- Veri tabloları, <xref:System.Data.DataTable.Select%2A> yöntemine geçirilen ifadeye göre <xref:System.Data.DataRow> bir dizi s döndüren yöntemiyle <xref:System.Data.DataTable.Select%2A> oluşturulur. Geçerli ifadeler oluşturma hakkında daha fazla bilgi için, özelliği hakkında sayfanın "İfade Söz Dizimi" bölümüne <xref:System.Data.DataColumn.Expression%2A> bakın.

     Aşağıdaki örnek, belirli satırları bulmak <xref:System.Data.DataTable.Select%2A> için <xref:System.Data.DataTable> yönteminin nasıl kullanılageldi.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet20":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet20":::

## <a name="access-related-records"></a>İlgili kayıtlara erişme
Bir veri kümesinde bulunan tablolar ilişkili olduğunda, <xref:System.Data.DataRelation> bir nesne ilgili kayıtları başka bir tabloda kullanılabilir hale detebilirsiniz. Örneğin, ve tablolarını içeren `Customers` `Orders` bir veri kümesi kullanılabilir.

Üst tablodaki <xref:System.Data.DataRelation> bir yöntemini çağırarak ilgili kayıtları bulmak için <xref:System.Data.DataRow.GetChildRows%2A> nesnesini <xref:System.Data.DataRow> kullanabilirsiniz. Bu yöntem, ilgili alt kayıtlardan bir dizi döndürür. Veya alt tablodaki <xref:System.Data.DataRow.GetParentRow%2A> bir yöntemini <xref:System.Data.DataRow> çağırabilirsiniz. Bu yöntem, üst <xref:System.Data.DataRow> tablodan tek bir döndürür.

Bu sayfada, türü türü belirli veri kümelerini kullanan örnekler verilmiştir. Türlanmamış veri kümelerinden ilişkilerde gezinme hakkında bilgi için bkz. [DataRelations'da Gezinme.](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)

> [!NOTE]
> Windows Forms uygulamasında çalışıyorsanız ve verileri görüntülemek için veri bağlama özelliklerini kullanıyorsanız, tasarımcı tarafından oluşturulan form, uygulamanıza yeterli işlevsellik sağlar. Daha fazla bilgi için [bkz. Denetimlerini Visual Studio.](../data-tools/bind-controls-to-data-in-visual-studio.md) Özellikle [bkz. Veri Kümelerde İlişkiler.](relationships-in-datasets.md)

Aşağıdaki kod örnekleri, türe bağlı veri kümelerinden yukarı ve aşağı ilişkilerin nasıl gezineceğini gösteriyor. Kod örnekleri, istenen satırı bulmak ve ilgili kayıtları geri dönmek için türü ( ) ve oluşturulan <xref:System.Data.DataRow> `NorthwindDataSet.OrdersRow` FindBy *PrimaryKey* ( `FindByCustomerID` ) yöntemlerini kullanır. Örnekler yalnızca aşağıdakilere sahipse doğru şekilde derlenmiş ve çalışmalı:

- adlı bir veri kümesi `NorthwindDataSet` örneği. `Customers`

- `Orders`Tablo.

- İki tabloyla `FK_Orders_Customers` ilgili adlı bir ilişki.

Ayrıca, döndürülen tüm kayıtlar için her iki t tablo da verilerle doldurulmalıdır.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Seçili bir üst kaydın alt kayıtlarını geri dönmek için

- Belirli <xref:System.Data.DataRow.GetChildRows%2A> bir veri satırı `Customers` yöntemini çağırarak tablodan bir satır dizisi `Orders` döndürür:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet6":::

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Seçili bir alt kaydın üst kaydını geri dönmek için

- Belirli <xref:System.Data.DataRow.GetParentRow%2A> bir veri satırı `Orders` yöntemini çağırma ve tablodan tek bir satır `Customers` dönme:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
