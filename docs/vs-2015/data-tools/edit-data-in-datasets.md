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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672399"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri tablolarında verileri, herhangi bir veritabanındaki tablodaki verileri düzenlemenize benzer şekilde düzenlersiniz. İşlem, tablodaki kayıtları ekleme, güncelleştirme ve silme işlemlerini içerebilir. Veri bağlantılı bir formda, hangi alanların Kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu durumlarda, verilerin veritabanına daha sonra geri gönderilebilmesi için veri bağlama altyapısı tüm değişiklik izlemeyi işler. Programlı olarak verilerde düzenlemeler yaparsanız ve bu değişiklikleri veritabanına geri göndermek istiyorsanız, değişiklik izlemeyi sizin için yapan nesneleri ve yöntemleri kullanmanız gerekir.

 Gerçek verileri değiştirmenin yanı sıra, belirli veri satırlarını döndürmek için de bir <xref:System.Data.DataTable> sorgulama yapabilirsiniz. Örneğin, tek tek satırları, satır belirli sürümlerini (orijinal ve önerilen), değişen satırları veya hata içeren satırları sorgulayabilirsiniz.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesindeki satırları düzenlemek için
 @No__t_0 varolan bir satırı düzenlemek için, düzenlemek istediğiniz <xref:System.Data.DataRow> bulmanız ve ardından güncelleştirilmiş değerleri istenen sütunlara atamanız gerekir.

 Düzenlemek istediğiniz satırın dizinini bilmiyorsanız, birincil anahtara göre aramak için `FindBy` yöntemini kullanın:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Satır dizinini biliyorsanız, satırlara aşağıdaki gibi erişebilir ve bunları düzenleyebilirsiniz:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satırlar eklemek için
 Veriye bağlı denetimler kullanan uygulamalar, genellikle bir [BindingNavigator denetimindeki](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e) **yeni kayıtları ekle** düğmesi aracılığıyla ekler.

 Yeni kayıtları bir veri kümesine el ile eklemek için, DataTable üzerinde yöntemini çağırarak yeni bir veri satırı oluşturun. Sonra satırı <xref:System.Data.DataTable> <xref:System.Data.DataRow> koleksiyonuna (<xref:System.Data.DataTable.Rows%2A>) ekleyin:

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Veri kümesine güncelleştirmeleri göndermek için gereken bilgileri almak için, bir veri tablosundaki satırları kaldırmak için <xref:System.Data.DataRow.Delete%2A> yöntemini kullanın. Örneğin, uygulamanız bir TableAdapter (veya <xref:System.Data.Common.DataAdapter>) kullanıyorsa, TableAdapter 'ın `Update` yöntemi veritabanında <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> satırları siler.

 Uygulamanızın güncelleştirmeleri bir veri kaynağına geri gönderebilmesi gerekmiyorsa, veri satırı koleksiyonuna (<xref:System.Data.DataRowCollection.Remove%2A>) doğrudan erişerek kayıtları kaldırmak mümkündür.

#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için

- Bir <xref:System.Data.DataRow> <xref:System.Data.DataRow.Delete%2A> yöntemini çağırın.

     Bu yöntem, kaydı fiziksel olarak kaldırmaz. Bunun yerine, kaydı silinmek üzere işaretler.

    > [!NOTE]
    > Bir <xref:System.Data.DataRowCollection> Count özelliğini alırsanız, sonuçta elde edilen sayım silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaretlenmeyen kayıtların doğru sayısını almak için, her kaydın <xref:System.Data.DataRow.RowState%2A> özelliğine bakarak koleksiyonda döngü yapabilirsiniz. (Silinmek üzere işaretlenen kayıtlar <xref:System.Data.DataRowState> <xref:System.Data.DataRow.RowState%2A> sahiptir.) Alternatif olarak, satır durumuna göre filtreleyen bir veri kümesinin veri görünümünü oluşturabilir ve buradan Count özelliğini alabilirsiniz.

     Aşağıdaki örnek, `Customers` tablosundaki ilk satırı silindiği şekilde işaretlemek için <xref:System.Data.DataRow.Delete%2A> yönteminin nasıl çağrılacağını gösterir:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırların olup olmadığını belirleme
 Bir veri kümesindeki kayıtlar üzerinde değişiklik yapıldığında, bu değişiklikler hakkındaki bilgiler, siz bunları yapana kadar saklanır. Bir veri kümesinin veya veri tablosunun `AcceptChanges` yöntemini çağırdığınızda veya bir TableAdapter ya da veri bağdaştırıcısının `Update` yöntemini çağırdığınızda değişiklikleri işleyin.

 Değişiklikler her bir veri satırında iki şekilde izlenir:

- Her veri satırı, <xref:System.Data.DataRow.RowState%2A> ilgili bilgiler içerir (örneğin, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> veya <xref:System.Data.DataRowState>).

- Değiştirilen her veri satırı, bu satırın birden çok sürümünü (<xref:System.Data.DataRowVersion>), özgün sürümü (değişikliklerden önce) ve geçerli sürümü (değişikliklerden sonra) içerir. Bir değişiklik beklendiğinde (<xref:System.Data.DataTable.RowChanging> olayına yanıt verebildiği zaman), üçüncü bir sürüm — önerilen sürüm — da kullanılabilir.

  Veri kümesinde değişiklik yapılırsa, bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemi `true` döndürür. Değiştirilen satırların bulunduğunu belirledikten sonra, bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> `GetChanges` yöntemini çağırabilirsiniz ve bir dizi değiştirilen satırı döndürebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: değiştirilen satırları alma](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satırda değişiklik yapıldığını belirleme

- Değiştirilen satırları denetlemek için bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemini çağırın.

     Aşağıdaki örnek, `NorthwindDataset1` adlı bir veri kümesindeki değiştirilen satırların olup olmadığını algılamak için <xref:System.Data.DataSet.HasChanges%2A> yönteminden dönüş değerinin nasıl kontrol edilip edilmeyeceğini gösterir:

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Değişiklik türünü belirleme
 Ayrıca, <xref:System.Data.DataRowState> numaralandırmasından <xref:System.Data.DataSet.HasChanges%2A> yöntemine bir değer geçirerek bir veri kümesinde ne tür değişiklikler yapıldığını da denetleyebilirsiniz.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Bir satırda ne tür değişiklikler yapıldığını belirlemek için

- @No__t_1 yöntemine bir <xref:System.Data.DataRowState> değeri geçirin.

     Aşağıdaki örnek, öğesine yeni bir satır eklenip eklenmediğine yönelik `NorthwindDataset1` adlı bir veri kümesinin nasıl kontrol alınacağını gösterir:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Hatalı satırları bulmak için
 Bireysel sütunlarla ve veri satırlarıyla çalışırken hatalarla karşılaşabilirsiniz. @No__t_1, <xref:System.Data.DataTable> veya <xref:System.Data.DataRow> bir hata olup olmadığını öğrenmek için `HasErrors` özelliğini denetleyebilirsiniz.

1. Veri kümesinde herhangi bir hata olup olmadığını görmek için `HasErrors` özelliğini denetleyin.

2. @No__t_0 Özellik `true`, tablo koleksiyonları ' nı ve ardından satır yoluyla, hata ile satırı bulun.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
