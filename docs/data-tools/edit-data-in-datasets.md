---
title: Veri kümelerindeki verileri düzenleme
description: Veri kümelerini düzenlemeyi öğrenin. Veri kümesi satırlarını düzenlemeyi, veri kümesine yeni satırlar eklemeyi, değişen satırlar olup olmadığını belirlemeyi ve hata içeren satırları bulmayı bilirsiniz.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5cec6bccd2f1b2e6dd2e8250039a82cb4607b65d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631406"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
Veri tablolarında verileri, herhangi bir veritabanındaki bir tablodaki verileri düzenlemeye çok benzer şekilde düzenlersiniz. İşlem, tablodaki kayıtları ekleme, güncelleştirme ve silme işlemlerini içerebilir. Veriye bağlı bir formda, hangi alanların kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu gibi durumlarda veri bağlama altyapısı tüm değişiklik izleme işlemlerini üstlemektedir, böylece değişiklikler daha sonra veritabanına geri gönderebilirsiniz. Program aracılığıyla verilerde düzenlemeler yapar ve bu değişiklikleri veritabanına geri göndermek için değişiklik izlemesini sizin için yapan nesneleri ve yöntemleri kullanabilirsiniz.

Gerçek verileri değiştirmenin yanı sıra, belirli veri satırlarını geri dönmek <xref:System.Data.DataTable> için de sorgu gönderebilirsiniz. Örneğin, tek tek satırları, satırların belirli sürümlerini (özgün ve önerilen), değiştirilmiş satırları veya hata içeren satırları sorguabilirsiniz.

## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesinde satırları düzenlemek için
içinde mevcut bir satırı düzenlemek için düzenlemek istediğiniz satırı bulmanız ve ardından <xref:System.Data.DataTable> <xref:System.Data.DataRow> güncelleştirilmiş değerleri istenen sütunlara atamanız gerekir.

Düzenlemek istediğiniz satırın dizinini bilmiyorsanız, birincil `FindBy` anahtara göre arama yapmak için yöntemini kullanın:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet3":::

Satır dizinini biliyorsanız satırlara aşağıdaki gibi erişebilirsiniz ve satırları düzenleyebilirsiniz:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet5":::

## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine yeni satırlar eklemek için
Veriye bağlı denetimler kullanan uygulamalar genellikle [BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)denetimi üzerinde **Yeni** Ekle düğmesi aracılığıyla yeni kayıtlar ekler.

Bir veri kümesine el ile yeni kayıtlar eklemek için DataTable'da yöntemini çağırarak yeni bir veri satırı oluşturun. Ardından, satırı koleksiyonunun <xref:System.Data.DataRow> ( <xref:System.Data.DataTable.Rows%2A> ) koleksiyonuna <xref:System.Data.DataTable> ekleyin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet1":::

Veri kümesinde veri kaynağına güncelleştirme göndermek için gereken bilgileri korumak için yöntemini kullanarak bir veri tablosunda <xref:System.Data.DataRow.Delete%2A> satırları kaldırın. Örneğin, uygulamanız bir TableAdapter <xref:System.Data.Common.DataAdapter> (veya) kullanıyorsa, TableAdapter'ın yöntemi veritabanında bir içeren `Update` satırları <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> siler.

Uygulamanın güncelleştirmeleri bir veri kaynağına geri göndermesi gerek yoksa, veri satırı koleksiyonuna () doğrudan erişerek kayıtları kaldırmak <xref:System.Data.DataRowCollection.Remove%2A> mümkündür.

#### <a name="to-delete-records-from-a-data-table"></a>Veri tablosundan kayıtları silmek için

- yöntemini <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> çağırma.

     Bu yöntem kaydı fiziksel olarak kaldırmaz. Bunun yerine, kaydı silinmek üzere işaretler.

    > [!NOTE]
    > bir sayma özelliğini elde <xref:System.Data.DataRowCollection> ediyorsanız, sonuçta elde edilen sayı, silinmek üzere işaretlenmiş kayıtları içerir. Silinmek üzere işaret almayan kayıtların doğru sayısını almak için her kaydın özelliğine bakarak koleksiyonda <xref:System.Data.DataRow.RowState%2A> döngüye geçabilirsiniz. (Silme için işaretlenmiş kayıtlarda bir <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> olur.) Alternatif olarak, satır durumuna göre filtre alan bir veri kümesi veri görünümü oluşturabilir ve count özelliğini buradan edinebilirsiniz.

Aşağıdaki örnekte, tablodaki ilk satırı <xref:System.Data.DataRow.Delete%2A> silinmiş olarak işaretlemek için yönteminin `Customers` nasıl çağrıl olduğu gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet8":::

## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırlar olup olmadığını belirleme
Bir veri kümesinde kayıtlarda değişiklik yapıldı mı, siz bunları işleyene kadar bu değişikliklerle ilgili bilgiler depolanır. Değişiklikleri bir veri kümesi veya veri tablosu yöntemini çağırarak veya TableAdapter ya da veri bağdaştırıcısının yöntemini `AcceptChanges` `Update` çağırarak işlersiniz.

Değişiklikler her veri satırı için iki şekilde iz olur:

- Her veri satırı ile ilgili bilgiler <xref:System.Data.DataRow.RowState%2A> içerir (örneğin, <xref:System.Data.DataRowState.Added> , , veya <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> <xref:System.Data.DataRowState.Unchanged> ).

- Değiştirilen her veri satırı, bu satırın ( ), özgün sürümün (değişikliklerden önce) ve geçerli <xref:System.Data.DataRowVersion> sürümün (değişikliklerden sonra) birden çok sürümünü içerir. Bir değişikliğin beklemede olduğu süre boyunca (olayı yanıtlamak için gereken süre), üçüncü bir sürüm olan önerilen <xref:System.Data.DataTable.RowChanging> sürüm de kullanılabilir.

Veri <xref:System.Data.DataSet.HasChanges%2A> kümesinde değişiklik `true` yapılmışsa veri kümesi yöntemi döndürür. Değiştirilen satırların mevcut olduğunu belirleydikten sonra bir veya yöntemini çağırarak `GetChanges` <xref:System.Data.DataSet> değiştirilmiş <xref:System.Data.DataTable> satırlar kümesi getirebilirsiniz.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Herhangi bir satırda değişiklik olup olmadığını belirlemek için

- Değiştirilen <xref:System.Data.DataSet.HasChanges%2A> satırları kontrol etmek için veri kümesi yöntemini çağırma.

Aşağıdaki örnekte, adlı bir veri kümesinde değiştirilen satır olup olmadığını algılamak için yönteminden <xref:System.Data.DataSet.HasChanges%2A> dönüş değerinin nasıl kontrol etmek için olduğu `NorthwindDataset1` gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet12":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet12":::

## <a name="determine-the-type-of-changes"></a>Değişiklik türünü belirleme
Ayrıca, bir veri kümesinde yapılan değişikliklerin türünü görmek için numaralamadan yöntemine <xref:System.Data.DataRowState> bir değer geçirmeyi de kontrol <xref:System.Data.DataSet.HasChanges%2A> edin.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Bir satırda ne tür değişiklikler yapılmış olduğunu belirlemek için

- yöntemine <xref:System.Data.DataRowState> bir değer <xref:System.Data.DataSet.HasChanges%2A> iletir.

Aşağıdaki örnekte, adlı bir veri kümesine yeni satır ekli olup olmadığını `NorthwindDataset1` belirlemek için nasıl denetim gerçekleştirin?

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet13":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet13":::

## <a name="to-locate-rows-that-have-errors"></a>Hata içeren satırları bulmak için
Tek tek sütunlarla ve veri satırlarıyla çalışırken hatalarla karşılaşabilirsiniz. Hataların , `HasErrors` veya içinde olup olmadığını belirlemek için özelliğini kontrol <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> edin.

1. Veri `HasErrors` kümesinde herhangi bir hata olup denetleyin.

2. özelliği ise, hata içeren satırı bulmak için tablo koleksiyonları ve ardından satırlar arasında `HasErrors` `true` yineler.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet23":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
