---
title: Veri kümelerindeki verileri düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b51b5b4be12f76e2237ff93659617e1c1843722a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586659"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
Veri tablolarında verileri, herhangi bir veritabanındaki tablodaki verileri düzenlemenize benzer şekilde düzenlersiniz. İşlem, tablodaki kayıtları ekleme, güncelleştirme ve silme işlemlerini içerebilir. Veri bağlantılı bir formda, hangi alanların Kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu durumlarda, verilerin veritabanına daha sonra geri gönderilebilmesi için veri bağlama altyapısı tüm değişiklik izlemeyi işler. Programlı olarak verilerde düzenlemeler yaparsanız ve bu değişiklikleri veritabanına geri göndermek istiyorsanız, değişiklik izlemeyi sizin için yapan nesneleri ve yöntemleri kullanmanız gerekir.

Gerçek verileri değiştirmenin yanı sıra, belirli veri satırlarını döndürmek için de bir <xref:System.Data.DataTable> sorgulama yapabilirsiniz. Örneğin, tek tek satırları, satır belirli sürümlerini (orijinal ve önerilen), değişen satırları veya hata içeren satırları sorgulayabilirsiniz.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesindeki satırları düzenlemek için
<xref:System.Data.DataTable>varolan bir satırı düzenlemek için, düzenlemek istediğiniz <xref:System.Data.DataRow> bulmanız ve ardından güncelleştirilmiş değerleri istenen sütunlara atamanız gerekir.

Düzenlemek istediğiniz satırın dizinini bilmiyorsanız, birincil anahtara göre aramak için `FindBy` yöntemini kullanın:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Satır dizinini biliyorsanız, satırlara aşağıdaki gibi erişebilir ve bunları düzenleyebilirsiniz:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satırlar eklemek için
Veriye bağlı denetimler kullanan uygulamalar, genellikle bir [BindingNavigator denetimindeki](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) **yeni kayıtları ekle** düğmesi aracılığıyla ekler.

Yeni kayıtları bir veri kümesine el ile eklemek için, DataTable üzerinde yöntemini çağırarak yeni bir veri satırı oluşturun. Ardından, satırı <xref:System.Data.DataTable><xref:System.Data.DataRow> koleksiyonuna (<xref:System.Data.DataTable.Rows%2A>) ekleyin:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Veri kümesine güncelleştirmeleri göndermek için gereken bilgileri almak için, bir veri tablosundaki satırları kaldırmak için <xref:System.Data.DataRow.Delete%2A> yöntemini kullanın. Örneğin, uygulamanız bir TableAdapter (veya <xref:System.Data.Common.DataAdapter>) kullanıyorsa, TableAdapter 'ın `Update` yöntemi veritabanında <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>satırları siler.

Uygulamanızın güncelleştirmeleri bir veri kaynağına geri gönderebilmesi gerekmiyorsa, veri satırı koleksiyonuna (<xref:System.Data.DataRowCollection.Remove%2A>) doğrudan erişerek kayıtları kaldırmak mümkündür.

#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için

- Bir <xref:System.Data.DataRow><xref:System.Data.DataRow.Delete%2A> yöntemini çağırın.

     Bu yöntem, kaydı fiziksel olarak kaldırmaz. Bunun yerine, kaydı silinmek üzere işaretler.

    > [!NOTE]
    > Bir <xref:System.Data.DataRowCollection>Count özelliğini alırsanız, sonuçta elde edilen sayım silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaretlenmeyen kayıtların doğru sayısını almak için, her kaydın <xref:System.Data.DataRow.RowState%2A> özelliğine bakarak koleksiyonda döngü yapabilirsiniz. (Silinmek üzere işaretlenen kayıtlar <xref:System.Data.DataRowState.Deleted><xref:System.Data.DataRow.RowState%2A> sahiptir.) Alternatif olarak, satır durumuna göre filtreleyen bir veri kümesinin veri görünümünü oluşturabilir ve buradan Count özelliğini alabilirsiniz.

Aşağıdaki örnek, `Customers` tablosundaki ilk satırı silindiği şekilde işaretlemek için <xref:System.Data.DataRow.Delete%2A> yönteminin nasıl çağrılacağını gösterir:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırların olup olmadığını belirleme
Bir veri kümesindeki kayıtlar üzerinde değişiklik yapıldığında, bu değişiklikler hakkındaki bilgiler, siz bunları yapana kadar saklanır. Bir veri kümesinin veya veri tablosunun `AcceptChanges` yöntemini çağırdığınızda veya bir TableAdapter ya da veri bağdaştırıcısının `Update` yöntemini çağırdığınızda değişiklikleri işleyin.

Değişiklikler her bir veri satırında iki şekilde izlenir:

- Her veri satırı, <xref:System.Data.DataRow.RowState%2A> ilgili bilgiler içerir (örneğin, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>veya <xref:System.Data.DataRowState.Unchanged>).

- Değiştirilen her veri satırı, bu satırın birden çok sürümünü (<xref:System.Data.DataRowVersion>), özgün sürümü (değişikliklerden önce) ve geçerli sürümü (değişikliklerden sonra) içerir. Bir değişiklik beklendiğinde (<xref:System.Data.DataTable.RowChanging> olayına yanıt verebildiği zaman), üçüncü bir sürüm — önerilen sürüm — da kullanılabilir.

Veri kümesinde değişiklik yapılırsa, bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemi `true` döndürür. Değiştirilen satırların bulunduğunu belirledikten sonra, bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> `GetChanges` yöntemini çağırabilirsiniz ve bir dizi değiştirilen satırı döndürebilirsiniz.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satırda değişiklik yapıldığını belirleme

- Değiştirilen satırları denetlemek için bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemini çağırın.

Aşağıdaki örnek, `NorthwindDataset1`adlı bir veri kümesindeki değiştirilen satırların olup olmadığını algılamak için <xref:System.Data.DataSet.HasChanges%2A> yönteminden dönüş değerinin nasıl kontrol edilip edilmeyeceğini gösterir:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Değişiklik türünü belirleme
Ayrıca, <xref:System.Data.DataRowState> numaralandırmasından <xref:System.Data.DataSet.HasChanges%2A> yöntemine bir değer geçirerek bir veri kümesinde ne tür değişiklikler yapıldığını da denetleyebilirsiniz.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Bir satırda ne tür değişiklikler yapıldığını belirlemek için

- <xref:System.Data.DataSet.HasChanges%2A> yöntemine bir <xref:System.Data.DataRowState> değeri geçirin.

Aşağıdaki örnek, öğesine yeni bir satır eklenip eklenmediğine yönelik `NorthwindDataset1` adlı bir veri kümesinin nasıl kontrol alınacağını gösterir:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Hatalı satırları bulmak için
Bireysel sütunlarla ve veri satırlarıyla çalışırken hatalarla karşılaşabilirsiniz. <xref:System.Data.DataSet>, <xref:System.Data.DataTable>veya <xref:System.Data.DataRow>bir hata olup olmadığını öğrenmek için `HasErrors` özelliğini denetleyebilirsiniz.

1. Veri kümesinde herhangi bir hata olup olmadığını görmek için `HasErrors` özelliğini denetleyin.

2. `HasErrors` Özellik `true`, tablo koleksiyonları ' nı ve ardından satır yoluyla, hata ile satırı bulun.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
