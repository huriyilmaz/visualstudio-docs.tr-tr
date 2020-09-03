---
title: Veri kümelerinde verileri düzenleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672399"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri tablolarında verileri, herhangi bir veritabanındaki tablodaki verileri düzenlemenize benzer şekilde düzenlersiniz. İşlem, tablodaki kayıtları ekleme, güncelleştirme ve silme işlemlerini içerebilir. Veri bağlantılı bir formda, hangi alanların Kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu durumlarda, verilerin veritabanına daha sonra geri gönderilebilmesi için veri bağlama altyapısı tüm değişiklik izlemeyi işler. Programlı olarak verilerde düzenlemeler yaparsanız ve bu değişiklikleri veritabanına geri göndermek istiyorsanız, değişiklik izlemeyi sizin için yapan nesneleri ve yöntemleri kullanmanız gerekir.

 Gerçek verileri değiştirmenin yanı sıra, <xref:System.Data.DataTable> belirli veri satırlarını döndürmek için de bir sorgulama yapabilirsiniz. Örneğin, tek tek satırları, satır belirli sürümlerini (orijinal ve önerilen), değişen satırları veya hata içeren satırları sorgulayabilirsiniz.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesindeki satırları düzenlemek için
 İçinde varolan bir satırı düzenlemek için, düzenlemek istediğiniz ' i <xref:System.Data.DataTable> bulmanız <xref:System.Data.DataRow> ve ardından güncelleştirilmiş değerleri istenen sütunlara atamanız gerekir.

 Düzenlemek istediğiniz satırın dizinini bilmiyorsanız, `FindBy` birincil anahtara göre arama yapmak için yöntemini kullanın:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Satır dizinini biliyorsanız, satırlara aşağıdaki gibi erişebilir ve bunları düzenleyebilirsiniz:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satırlar eklemek için
 Veriye bağlı denetimler kullanan uygulamalar, genellikle bir [BindingNavigator denetimindeki](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e) **yeni kayıtları ekle** düğmesi aracılığıyla ekler.

 Yeni kayıtları bir veri kümesine el ile eklemek için, DataTable üzerinde yöntemini çağırarak yeni bir veri satırı oluşturun. Daha sonra satırı <xref:System.Data.DataRow> koleksiyonuna ( <xref:System.Data.DataTable.Rows%2A> ) ekleyin <xref:System.Data.DataTable> :

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Veri kümesinin güncelleştirmeleri veri kaynağına göndermek için gereken bilgileri bekletmek için, <xref:System.Data.DataRow.Delete%2A> bir veri tablosundaki satırları kaldırmak için yöntemini kullanın. Örneğin, uygulamanız bir TableAdapter (veya <xref:System.Data.Common.DataAdapter> ) kullanıyorsa, TableAdapter `Update` yöntemi ' a sahip olan veritabanındaki satırları siler <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> .

 Uygulamanızın güncelleştirmeleri bir veri kaynağına geri gönderebilmesi gerekmiyorsa, veri satırı koleksiyonuna () doğrudan erişerek kayıtları kaldırmak mümkündür <xref:System.Data.DataRowCollection.Remove%2A> .

#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için

- Yöntemini çağırın <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> .

     Bu yöntem, kaydı fiziksel olarak kaldırmaz. Bunun yerine, kaydı silinmek üzere işaretler.

    > [!NOTE]
    > Bir öğesinin Count özelliğini alırsanız <xref:System.Data.DataRowCollection> , sonuçta elde edilen sayım silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaretlenmemiş kayıtların doğru sayısını almak için, her kaydın özelliğine bakarak koleksiyonda dolaşmanız gerekir <xref:System.Data.DataRow.RowState%2A> . (Silinmek üzere işaretlenen kayıtlar öğesinin öğesine <xref:System.Data.DataRow.RowState%2A> sahip <xref:System.Data.DataRowState> .) Alternatif olarak, satır durumuna göre filtreleyen bir veri kümesinin veri görünümünü oluşturabilir ve buradan Count özelliğini alabilirsiniz.

     Aşağıdaki örnek, <xref:System.Data.DataRow.Delete%2A> tablodaki ilk satırı silindiği şekilde işaretlemek için yönteminin nasıl çağrılacağını göstermektedir `Customers` :

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırların olup olmadığını belirleme
 Bir veri kümesindeki kayıtlar üzerinde değişiklik yapıldığında, bu değişiklikler hakkındaki bilgiler, siz bunları yapana kadar saklanır. Bir veri kümesinin veya veri tablosunun yöntemini çağırdığınızda `AcceptChanges` veya `Update` bir TableAdapter ya da veri bağdaştırıcısının yöntemini çağırdığınızda değişiklikleri işleyin.

 Değişiklikler her bir veri satırında iki şekilde izlenir:

- Her veri satırı, onunla ilgili bilgiler içerir <xref:System.Data.DataRow.RowState%2A> (örneğin,,, <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> veya <xref:System.Data.DataRowState> ).

- Değiştirilen her veri satırı, bu satırın birden çok sürümünü ( <xref:System.Data.DataRowVersion> ), özgün sürümü (değişikliklerden önce) ve geçerli sürümü (değişikliklerden sonra) içerir. Bir değişiklik beklendiğinde (olaya yanıt verebildiği zaman <xref:System.Data.DataTable.RowChanging> ), üçüncü bir sürüm — önerilen sürüm — da kullanılabilir.

  Veri kümesinde <xref:System.Data.DataSet.HasChanges%2A> değişiklik yapılırsa, veri kümesinin yöntemi döndürür `true` . Değiştirilen satırların bulunduğunu belirledikten sonra, `GetChanges` bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> değiştirilmiş satır kümesi döndürmek için veya metodunu çağırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: değiştirilen satırları alma](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satırda değişiklik yapıldığını belirleme

- <xref:System.Data.DataSet.HasChanges%2A>Değiştirilen satırları denetlemek için bir veri kümesinin yöntemini çağırın.

     Aşağıdaki örnek, <xref:System.Data.DataSet.HasChanges%2A> adlı bir veri kümesindeki değiştirilen satırların olup olmadığını algılamak için yönteminin dönüş değerinin nasıl kontrol edilip edilmeyeceğini gösterir `NorthwindDataset1` :

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Değişiklik türünü belirleme
 Ayrıca, sabit listesinden bir değer geçirerek bir veri kümesinde ne tür değişiklikler yapıldığını da denetleyebilirsiniz <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> .

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Bir satırda ne tür değişiklikler yapıldığını belirlemek için

- Yöntemine bir <xref:System.Data.DataRowState> değer geçirin <xref:System.Data.DataSet.HasChanges%2A> .

     Aşağıdaki örnek, `NorthwindDataset1` öğesine yeni bir satır eklenip eklenmediğine yönelik olarak adlandırılan bir veri kümesini nasıl denetleyeceğini göstermektedir:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Hatalı satırları bulmak için
 Bireysel sütunlarla ve veri satırlarıyla çalışırken hatalarla karşılaşabilirsiniz. `HasErrors`, Veya ' de hata olup olmadığını anlamak için özelliğini denetleyebilirsiniz <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> .

1. `HasErrors`Veri kümesinde herhangi bir hata olup olmadığını görmek için özelliği denetleyin.

2. `HasErrors`Özelliği ise, `true` tablo koleksiyonları arasında yineleme yapın ve sonra satırı hata ile bulmak için satırları.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
