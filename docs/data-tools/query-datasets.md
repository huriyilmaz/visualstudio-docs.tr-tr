---
title: Veri kümelerini sorgulama
description: Sorgu veri kümelerini anlayın. Veri kümesi büyük küçük harf duyarlılığı hakkında bilgi edinin. Veri tablosunda belirli bir satırı bulun, sütun değerlerine göre satırları bulun ve ilgili kayıtlara erişin.
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
ms.openlocfilehash: 2f047f38327f0773f7b370ba721b7e88afed2b90
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154868"
---
# <a name="query-datasets"></a>Veri kümelerini sorgulama
bir veri kümesindeki belirli kayıtları aramak için `FindBy` DataTable 'daki yöntemi kullanın, tablonun satır koleksiyonu üzerinde döngü yapmak için kendi foreach deyiminizi yazın veya [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)kullanın.

## <a name="dataset-case-sensitivity"></a>Veri kümesi büyük küçük harf duyarlılığı
Bir veri kümesi içinde tablo ve sütun adları, varsayılan olarak büyük/küçük harfe duyarlıdır; Yani, "Customers" adlı bir veri kümesindeki tablo, "müşteriler" olarak da adlandırılabilir. Bu, SQL Server dahil olmak üzere birçok veritabanında adlandırma kurallarıyla eşleşir. SQL Server, varsayılan davranış, veri öğelerinin adlarının yalnızca büyük/küçük harfe göre ayırt edilemez olması olabilir.

> [!NOTE]
> Veri kümelerinin aksine, XML belgeleri büyük/küçük harfe duyarlıdır; bu nedenle, şemalarda tanımlanan veri öğelerinin adları büyük/küçük harfe duyarlıdır. Örneğin, şema Protokolü şemanın "Customers" adlı bir tabloyu ve "Customers" adlı farklı bir tabloyu tanımlamasını sağlar. Bu, bir veri kümesi sınıfı oluşturmak için yalnızca büyük/küçük harfe göre farklı öğeler içeren bir şema kullanıldığında ad çakışmalarına neden olabilir.

Ancak, büyük/küçük harf duyarlılığı, verilerin veri kümesi içinde nasıl yorumlanacağına ilişkin bir etken olabilir. Örneğin, bir veri kümesi tablosundaki verileri filtrelemeniz durumunda arama ölçütleri, karşılaştırmanın büyük/küçük harfe duyarlı olmasına bağlı olarak farklı sonuçlar döndürebilir. Veri kümesinin özelliğini ayarlayarak filtreleme, arama ve sıralama için büyük/küçük harfe duyarlılık düzeyini kontrol edebilirsiniz <xref:System.Data.DataSet.CaseSensitive%2A> . Veri kümesindeki tüm tablolar varsayılan olarak bu özelliğin değerini alır. (Tablonun özelliğini ayarlayarak, her tablo için bu özelliği geçersiz kılabilirsiniz <xref:System.Data.DataTable.CaseSensitive%2A> .)

## <a name="locate-a-specific-row-in-a-data-table"></a>Veri tablosunda belirli bir satırı bulma

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Türü belirtilmiş bir veri kümesinde birincil anahtar değeri olan bir satır bulmak için

- Bir satırı bulmak için, `FindBy` tablonun birincil anahtarını kullanan türü kesin belirlenmiş yöntemi çağırın.

     Aşağıdaki örnekte, `CustomerID` sütunu tablonun birincil anahtarıdır `Customers` . Bu, oluşturulan `FindBy` yöntemin olduğu anlamına gelir `FindByCustomerID` . Örnek, oluşturulan yöntemi kullanarak belirli bir değişkene nasıl atanacağını gösterir <xref:System.Data.DataRow> `FindBy` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet18":::

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Türsüz bir veri kümesinde birincil anahtar değeri olan bir satır bulmak için

- <xref:System.Data.DataRowCollection.Find%2A> <xref:System.Data.DataRowCollection> Birincil anahtarı parametre olarak geçirerek bir koleksiyonun yöntemini çağırın.

     Aşağıdaki örnek, adlı yeni bir satırın nasıl bildirilemeyeceğini `foundRow` ve yöntemin dönüş değerini nasıl atayacağınızı gösterir <xref:System.Data.DataRowCollection.Find%2A> . Birincil anahtar bulunursa, sütun dizini 1 ' in içeriği bir ileti kutusunda görüntülenir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet19":::

## <a name="find-rows-by-column-values"></a>Sütun değerlerine göre satırları bulma

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Herhangi bir sütundaki değerlere göre satırları bulmak için

- Veri tabloları, <xref:System.Data.DataTable.Select%2A> <xref:System.Data.DataRow> yöntemine geçirilen ifadeye bağlı olarak bir dizisi döndüren yöntemiyle oluşturulur <xref:System.Data.DataTable.Select%2A> . Geçerli ifadeler oluşturma hakkında daha fazla bilgi için, özelliği hakkındaki sayfanın "Ifade sözdizimi" bölümüne bakın <xref:System.Data.DataColumn.Expression%2A> .

     Aşağıdaki örnek <xref:System.Data.DataTable.Select%2A> , <xref:System.Data.DataTable> belirli satırları bulmak için yönteminin nasıl kullanılacağını gösterir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet20":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet20":::

## <a name="access-related-records"></a>İlgili kayıtlara erişme
Bir veri kümesindeki tablolar ilişkili olduğunda, bir <xref:System.Data.DataRelation> nesnesi ilgili kayıtları başka bir tabloda kullanılabilir hale getirir. Örneğin, içeren bir veri kümesi `Customers` ve `Orders` tabloları kullanılabilir hale getirilebilir.

<xref:System.Data.DataRelation> <xref:System.Data.DataRow.GetChildRows%2A> Üst tablodaki bir öğesinin yöntemini çağırarak ilgili kayıtları bulmak için bir nesnesi kullanabilirsiniz <xref:System.Data.DataRow> . Bu yöntem, ilişkili alt kayıtların dizisini döndürür. Ya da <xref:System.Data.DataRow.GetParentRow%2A> alt tablosunda a yöntemini çağırabilirsiniz <xref:System.Data.DataRow> . Bu yöntem <xref:System.Data.DataRow> , üst tablodan bir Single döndürür.

Bu sayfa, türü belirtilmiş veri kümelerini kullanarak örnekler sağlar. Türsüz veri kümelerinde ilişkileri gezinme hakkında daha fazla bilgi için bkz. [Datareto gezinme](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Windows Forms bir uygulamada çalışıyorsanız ve verileri göstermek için veri bağlama özelliklerini kullanıyorsanız, tasarımcı tarafından oluşturulan form uygulamanız için yeterli işlevsellik sağlayabilir. Daha fazla bilgi için bkz. [Visual Studio denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Özellikle, bkz. [veri kümelerinde ilişkiler](relationships-in-datasets.md).

Aşağıdaki kod örnekleri, türü belirtilmiş veri kümelerinde yukarı ve aşağı ilişkileri nasıl gidebileceğinizi göstermektedir. Kod örnekleri, <xref:System.Data.DataRow> `NorthwindDataSet.OrdersRow`  `FindByCustomerID` istenen bir satırı bulmak ve ilgili kayıtları döndürmek için yazılan s () ve üretilen FindBy PrimaryKey () yöntemlerini kullanır. Örnekler yalnızca şunları yaptıysanız derleme ve doğru şekilde çalışır:

- Tablo ile adlı bir veri kümesinin örneği `NorthwindDataSet` `Customers` .

- Bir `Orders` tablo.

- `FK_Orders_Customers`İki tabloyla ilişkili adlı ilişki.

Ayrıca, her iki tablonun da döndürülecek kayıtlar için verilerle doldurulması gerekir.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Seçili bir üst kaydın alt kayıtlarını döndürmek için

- <xref:System.Data.DataRow.GetChildRows%2A>Belirli bir veri satırının yöntemini çağırın `Customers` ve tablodaki satırların dizisini döndürün `Orders` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet6":::

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Seçili alt kaydın üst kaydını döndürmek için

- <xref:System.Data.DataRow.GetParentRow%2A>Belirli bir veri satırının yöntemini çağırın `Orders` ve tablosundan tek bir satır döndürün `Customers` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
