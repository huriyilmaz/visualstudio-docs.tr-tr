---
title: Sorgu veri kümeleri | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607444"
---
# <a name="query-datasets"></a>Veri kümelerini sorgulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veri kümesindeki belirli kayıtları aramak için DataTable üzerinde FindBy metodunu kullanın, tablonun satır koleksiyonu üzerine kendi foreach döngüsünü yazın veya [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)kullanın. LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Veri kümesi büyük küçük harf duyarlılığı
 Bir veri kümesi içinde tablo ve sütun adları, varsayılan olarak büyük/küçük harfe duyarlıdır; Yani, "Customers" adlı bir veri kümesindeki tablo, "müşteriler" olarak da adlandırılabilir. Bu, SQL Server.In SQL Server dahil olmak üzere birçok veritabanında adlandırma kurallarıyla eşleşir, varsayılan davranış, veri öğelerinin adlarının yalnızca büyük/küçük harfe göre ayırt edilemez olması olabilir.

> [!NOTE]
> Veri kümelerinin aksine, XML belgeleri büyük/küçük harfe duyarlıdır; bu nedenle, şemalarda tanımlanan veri öğelerinin adları büyük/küçük harfe duyarlıdır. Örneğin, şema Protokolü şemanın "Customers" adlı bir tabloyu ve "Customers" adlı farklı bir tabloyu tanımlamasını sağlar. Bu, bir veri kümesi sınıfı oluşturmak için yalnızca büyük/küçük harfe göre farklı öğeler içeren bir şema kullanıldığında ad çakışmalarına neden olabilir.

 Ancak, büyük/küçük harf duyarlılığı, verilerin veri kümesi içinde nasıl yorumlanacağına ilişkin bir etken olabilir. Örneğin, bir veri kümesi tablosundaki verileri filtrelemeniz durumunda arama ölçütleri, karşılaştırmanın büyük/küçük harfe duyarlı olmasına bağlı olarak farklı sonuçlar döndürebilir. Veri kümesinin özelliğini ayarlayarak filtreleme, arama ve sıralama için büyük/küçük harfe duyarlılık düzeyini kontrol edebilirsiniz <xref:System.Data.DataSet.CaseSensitive%2A> . Veri kümesindeki tüm tablolar varsayılan olarak bu özelliğin değerini alır. (Tablonun özelliğini ayarlayarak, her tablo için bu özelliği geçersiz kılabilirsiniz <xref:System.Data.DataTable.CaseSensitive%2A> .)

## <a name="locate-a-specific-row-in-a-data-table"></a>Veri tablosunda belirli bir satırı bulma

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Türü belirtilmiş bir veri kümesinde birincil anahtar değeri olan bir satır bulmak için

- Bir satırı bulmak için, `FindBy` tablonun birincil anahtarını kullanan türü kesin belirlenmiş yöntemi çağırın.

     Aşağıdaki örnekte, `CustomerID` sütunu tablonun birincil anahtarıdır `Customers` . Bu, oluşturulan `FindBy` yöntemin olduğu anlamına gelir `FindByCustomerID` . Örnek, oluşturulan yöntemi kullanarak belirli bir değişkene nasıl atanacağını gösterir <xref:System.Data.DataRow> `FindBy` .

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Türsüz bir veri kümesinde birincil anahtar değeri olan bir satır bulmak için

- <xref:System.Data.DataRowCollection.Find%2A> <xref:System.Data.DataRowCollection> Birincil anahtarı parametre olarak geçirerek bir koleksiyonun yöntemini çağırın.

     Aşağıdaki örnek, adlı yeni bir satırın nasıl bildirilemeyeceğini `foundRow` ve yöntemin dönüş değerini nasıl atayacağınızı gösterir <xref:System.Data.DataRowCollection.Find%2A> . Birincil anahtar bulunursa, sütun dizini 1 ' in içeriği bir ileti kutusunda görüntülenir.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>Sütun değerlerine göre FindRows

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Herhangi bir sütundaki değerlere göre satırları bulmak için

- Veri tabloları, <xref:System.Data.DataTable.Select%2A> <xref:System.Data.DataRow> yöntemine geçirilen ifadeye bağlı olarak bir dizisi döndüren yöntemiyle oluşturulur <xref:System.Data.DataTable.Select%2A> . Geçerli ifadeler oluşturma hakkında daha fazla bilgi için, özelliği hakkındaki sayfanın "Ifade sözdizimi" bölümüne bakın <xref:System.Data.DataColumn.Expression%2A> .

     Aşağıdaki örnek <xref:System.Data.DataTable.Select%2A> , <xref:System.Data.DataTable> belirli satırları bulmak için yönteminin nasıl kullanılacağını gösterir.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>İlgili kayıtlara erişme
 Bir veri kümesindeki tablolar ilişkili olduğunda, bir <xref:System.Data.DataRelation> nesnesi ilgili kayıtları başka bir tabloda kullanılabilir hale getirir. Örneğin, içeren bir veri kümesi `Customers` ve `Orders` tabloları kullanılabilir hale getirilebilir.

 <xref:System.Data.DataRelation> <xref:System.Data.DataRow.GetChildRows%2A> Üst tablodaki bir öğesinin yöntemini çağırarak ilgili kayıtları bulmak için bir nesnesi kullanabilirsiniz <xref:System.Data.DataRow> . Bu yöntem, ilişkili alt kayıtların dizisini döndürür. Ya da <xref:System.Data.DataRow.GetParentRow%2A> alt tablosunda a yöntemini çağırabilirsiniz <xref:System.Data.DataRow> . Bu yöntem <xref:System.Data.DataRow> , üst tablodan bir Single döndürür.

 Bu sayfa, türü belirtilmiş veri kümelerini kullanarak örnekler sağlar. Türsüz veri kümelerinde ilişkileri gezinme hakkında daha fazla bilgi için bkz. [Datareto gezinme](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Windows Forms bir uygulamada çalışıyorsanız ve verileri göstermek için veri bağlama özelliklerini kullanıyorsanız, tasarımcı tarafından oluşturulan form uygulamanız için yeterli işlevsellik sağlayabilir. Daha fazla bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

 Aşağıdaki kod örnekleri, türü belirtilmiş veri kümelerinde yukarı ve aşağı ilişkileri nasıl gidebileceğinizi göstermektedir. Kod örnekleri, <xref:System.Data.DataRow> `NorthwindDataSet.OrdersRow` `FindBy` *PrimaryKey* `FindByCustomerID` istenen bir satırı bulmak ve ilgili kayıtları döndürmek için yazılan s () ve üretilen PrimaryKey () yöntemlerini kullanır. Örnekler yalnızca şunları yaptıysanız derleme ve doğru şekilde çalışır:

- Tablo ile adlı bir veri kümesinin örneği `NorthwindDataSet` `Customers` .

- Bir `Orders` tablo.

- `FK_Orders_Customers`Kodunuzun kapsamına uygun iki tabloyla ilişkili adlı ilişki

Ayrıca, her iki tablonun da döndürülecek kayıtlar için verilerle doldurulması gerekir.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Seçili bir üst kaydın alt kayıtlarını döndürmek için

- <xref:System.Data.DataRow.GetChildRows%2A>Belirli bir veri satırının yöntemini çağırın `Customers` ve tablodaki satırların dizisini döndürün `Orders` :

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Seçili alt kaydın üst kaydını döndürmek için

- <xref:System.Data.DataRow.GetParentRow%2A>Belirli bir veri satırının yöntemini çağırın `Orders` ve tablosundan tek bir satır döndürün `Customers` :

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
