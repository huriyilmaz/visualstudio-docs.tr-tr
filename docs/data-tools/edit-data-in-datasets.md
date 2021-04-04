---
title: Veri kümelerindeki verileri düzenleme
description: Veri kümelerinde verileri düzenlemeyi öğrenin. Veri kümesi satırlarını nasıl düzenleyeceğimizi, bir veri kümesine yeni satırlar eklemeyi, değiştirilen satırların olup olmadığını belirlemeyi ve hata içeren satırları bulmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 38ceec2cafd3476342d9319d9b5d034564759fad
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215909"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
Veri tablolarında verileri, herhangi bir veritabanındaki tablodaki verileri düzenlemenize benzer şekilde düzenlersiniz. İşlem, tablodaki kayıtları ekleme, güncelleştirme ve silme işlemlerini içerebilir. Veri bağlantılı bir formda, hangi alanların Kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu durumlarda, verilerin veritabanına daha sonra geri gönderilebilmesi için veri bağlama altyapısı tüm değişiklik izlemeyi işler. Programlı olarak verilerde düzenlemeler yaparsanız ve bu değişiklikleri veritabanına geri göndermek istiyorsanız, değişiklik izlemeyi sizin için yapan nesneleri ve yöntemleri kullanmanız gerekir.

Gerçek verileri değiştirmenin yanı sıra, <xref:System.Data.DataTable> belirli veri satırlarını döndürmek için de bir sorgulama yapabilirsiniz. Örneğin, tek tek satırları, satır belirli sürümlerini (orijinal ve önerilen), değişen satırları veya hata içeren satırları sorgulayabilirsiniz.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesindeki satırları düzenlemek için
İçinde varolan bir satırı düzenlemek için, düzenlemek istediğiniz ' i <xref:System.Data.DataTable> bulmanız <xref:System.Data.DataRow> ve ardından güncelleştirilmiş değerleri istenen sütunlara atamanız gerekir.

Düzenlemek istediğiniz satırın dizinini bilmiyorsanız, `FindBy` birincil anahtara göre arama yapmak için yöntemini kullanın:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet3":::

Satır dizinini biliyorsanız, satırlara aşağıdaki gibi erişebilir ve bunları düzenleyebilirsiniz:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet5":::

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satırlar eklemek için
Veriye bağlı denetimler kullanan uygulamalar, genellikle bir [BindingNavigator denetimindeki](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) **yeni kayıtları ekle** düğmesi aracılığıyla ekler.

Yeni kayıtları bir veri kümesine el ile eklemek için, DataTable üzerinde yöntemini çağırarak yeni bir veri satırı oluşturun. Ardından, satırı <xref:System.Data.DataRow> koleksiyonuna ( <xref:System.Data.DataTable.Rows%2A> ) ekleyin <xref:System.Data.DataTable> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet1":::

Veri kümesinin güncelleştirmeleri veri kaynağına göndermek için gereken bilgileri bekletmek için, <xref:System.Data.DataRow.Delete%2A> bir veri tablosundaki satırları kaldırmak için yöntemini kullanın. Örneğin, uygulamanız bir TableAdapter (veya <xref:System.Data.Common.DataAdapter> ) kullanıyorsa, TableAdapter `Update` yöntemi ' a sahip olan veritabanındaki satırları siler <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> .

Uygulamanızın güncelleştirmeleri bir veri kaynağına geri gönderebilmesi gerekmiyorsa, veri satırı koleksiyonuna () doğrudan erişerek kayıtları kaldırmak mümkündür <xref:System.Data.DataRowCollection.Remove%2A> .

#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için

- Yöntemini çağırın <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> .

     Bu yöntem, kaydı fiziksel olarak kaldırmaz. Bunun yerine, kaydı silinmek üzere işaretler.

    > [!NOTE]
    > Bir öğesinin Count özelliğini alırsanız <xref:System.Data.DataRowCollection> , sonuçta elde edilen sayım silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaretlenmemiş kayıtların doğru sayısını almak için, her kaydın özelliğine bakarak koleksiyonda dolaşmanız gerekir <xref:System.Data.DataRow.RowState%2A> . (Silinmek üzere işaretlenen kayıtlar öğesinin öğesine <xref:System.Data.DataRow.RowState%2A> sahip <xref:System.Data.DataRowState.Deleted> .) Alternatif olarak, satır durumuna göre filtreleyen bir veri kümesinin veri görünümünü oluşturabilir ve buradan Count özelliğini alabilirsiniz.

Aşağıdaki örnek, <xref:System.Data.DataRow.Delete%2A> tablodaki ilk satırı silindiği şekilde işaretlemek için yönteminin nasıl çağrılacağını göstermektedir `Customers` :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet8":::

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırların olup olmadığını belirleme
Bir veri kümesindeki kayıtlar üzerinde değişiklik yapıldığında, bu değişiklikler hakkındaki bilgiler, siz bunları yapana kadar saklanır. Bir veri kümesinin veya veri tablosunun yöntemini çağırdığınızda `AcceptChanges` veya `Update` bir TableAdapter ya da veri bağdaştırıcısının yöntemini çağırdığınızda değişiklikleri işleyin.

Değişiklikler her bir veri satırında iki şekilde izlenir:

- Her veri satırı, onunla ilgili bilgiler içerir <xref:System.Data.DataRow.RowState%2A> (örneğin,, <xref:System.Data.DataRowState.Added> , <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> veya <xref:System.Data.DataRowState.Unchanged> ).

- Değiştirilen her veri satırı, bu satırın birden çok sürümünü ( <xref:System.Data.DataRowVersion> ), özgün sürümü (değişikliklerden önce) ve geçerli sürümü (değişikliklerden sonra) içerir. Bir değişiklik beklendiğinde (olaya yanıt verebildiği zaman <xref:System.Data.DataTable.RowChanging> ), üçüncü bir sürüm — önerilen sürüm — da kullanılabilir.

Veri kümesinde <xref:System.Data.DataSet.HasChanges%2A> değişiklik yapılırsa, veri kümesinin yöntemi döndürür `true` . Değiştirilen satırların bulunduğunu belirledikten sonra, `GetChanges` bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> değiştirilmiş satır kümesi döndürmek için veya metodunu çağırabilirsiniz.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satırda değişiklik yapıldığını belirleme

- <xref:System.Data.DataSet.HasChanges%2A>Değiştirilen satırları denetlemek için bir veri kümesinin yöntemini çağırın.

Aşağıdaki örnek, <xref:System.Data.DataSet.HasChanges%2A> adlı bir veri kümesindeki değiştirilen satırların olup olmadığını algılamak için yönteminin dönüş değerinin nasıl kontrol edilip edilmeyeceğini gösterir `NorthwindDataset1` :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet12":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet12":::

## <a name="determine-the-type-of-changes"></a>Değişiklik türünü belirleme
Ayrıca, sabit listesinden bir değer geçirerek bir veri kümesinde ne tür değişiklikler yapıldığını da denetleyebilirsiniz <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> .

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Bir satırda ne tür değişiklikler yapıldığını belirlemek için

- Yöntemine bir <xref:System.Data.DataRowState> değer geçirin <xref:System.Data.DataSet.HasChanges%2A> .

Aşağıdaki örnek, `NorthwindDataset1` öğesine yeni bir satır eklenip eklenmediğine yönelik olarak adlandırılan bir veri kümesini nasıl denetleyeceğini göstermektedir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet13":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet13":::

## <a name="to-locate-rows-that-have-errors"></a>Hatalı satırları bulmak için
Bireysel sütunlarla ve veri satırlarıyla çalışırken hatalarla karşılaşabilirsiniz. `HasErrors`, Veya ' de hata olup olmadığını anlamak için özelliğini denetleyebilirsiniz <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> .

1. `HasErrors`Veri kümesinde herhangi bir hata olup olmadığını görmek için özelliği denetleyin.

2. `HasErrors`Özelliği ise, `true` tablo koleksiyonları arasında yineleme yapın ve sonra satırı hata ile bulmak için satırları.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet23":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
