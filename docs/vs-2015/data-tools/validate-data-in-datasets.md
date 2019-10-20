---
title: Veri kümelerinde verileri doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d42553fbee6de6a89e16716a191db8a3d9fb883
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621063"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verilerin doğrulanması, veri nesnelerine girilen değerlerin bir veri kümesinin şeması içindeki kısıtlamalara uygun olduğunu onaylama işlemidir. Doğrulama işlemi, bu değerlerin uygulamanız için oluşturulan kurallara göre olduğunu da onaylar. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak iyi bir uygulamadır. Bu, hataların yanı sıra bir uygulama ve veritabanı arasındaki gidiş dönüş sayısını azaltır.

 Veri kümesine yazılan verilerin veri kümesine doğrulama denetimleri oluşturarak geçerli olduğunu doğrulayabilirsiniz. Veri kümesi, bir formda, bir bileşen içinde veya başka bir şekilde bir biçimde, doğrudan denetimler tarafından değil, güncelleştirmenin nasıl gerçekleştirildiğine bakılmaksızın verileri denetleyebilir. Veri kümesi uygulamanızın bir parçası olduğundan (veritabanı arka ucunun aksine) uygulamaya özgü doğrulama oluşturmak için mantıksal bir yerdir.

 Uygulamanıza doğrulama eklemek için en iyi yer, DataSet 'in kısmi sınıf dosyasında bulunur. @No__t_0 veya [!INCLUDE[csprcs](../includes/csprcs-md.md)] içinde, **veri kümesi Tasarımcısı** açın ve doğrulama oluşturmak istediğiniz sütun veya tabloya çift tıklayın. Bu eylem otomatik olarak bir <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay işleyicisi oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) veya [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Tüm bir örnek için bkz. [Izlenecek yol: bir veri kümesine doğrulama ekleme](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).

## <a name="validate-data"></a>Verileri doğrulama
 Bir veri kümesi içindeki doğrulama, aşağıdaki yollarla gerçekleştirilebilir:

- Değişiklik sırasında tek bir veri sütunundaki değerleri kontrol eden, uygulamaya özgü bir doğrulama oluşturarak.  Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Tüm veri satırları değiştirilirken, verileri değerlere denetleyerek uygulamaya özgü doğrulama bilgilerinizi oluşturarak. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

- Veri kümesinin gerçek şema tanımının bir parçası olarak anahtarlar, benzersiz kısıtlamalar ve benzeri bir oluşturma. Şema tanımına doğrulama ekleme hakkında daha fazla bilgi için, bkz. [bir DataColumn 'ı benzersiz değerler içerecek şekilde kısıtlama](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

- @No__t_1, <xref:System.Data.DataColumn.AllowDBNull%2A> ve <xref:System.Data.DataColumn.Unique%2A> gibi <xref:System.Data.DataColumn> nesnenin özelliklerini ayarlayarak.

  Bir kayıtta değişiklik yapıldığında <xref:System.Data.DataTable> nesnesi tarafından çeşitli olaylar tetiklenir:

- @No__t_0 ve <xref:System.Data.DataTable.ColumnChanged> olayları, tek bir sütundaki her değişiklikten sonra ve sonra oluşturulur. @No__t_0 olay, belirli sütunlardaki değişiklikleri doğrulamak istediğinizde faydalıdır. Önerilen değişiklik hakkındaki bilgiler, olaya bir bağımsız değişken olarak geçirilir. Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- @No__t_0 ve <xref:System.Data.DataTable.RowChanged> olayları, bir satırdaki herhangi bir değişiklik sırasında ve sonrasında oluşturulur. @No__t_0 olayı daha genel. Bu, satırda bir yerde değişiklik gerçekleştiğini gösterir, ancak hangi sütunun değiştiğini bilemezsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

  Varsayılan olarak, bir sütunda yapılan her değişiklik dört olay oluşturur. Birincisi, değiştirilen belirli bir sütunun <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olaylardır. Daha sonra <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları vardır. Satırda birden fazla değişiklik yapılırsa, olaylar her değişiklik için oluşturulur.

> [!NOTE]
> Veri satırının <xref:System.Data.DataRow.BeginEdit%2A> yöntemi, her sütun değişikliğinden sonra <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olaylarını kapatır. Bu durumda, <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları tek bir kez oluşturulduğunda <xref:System.Data.DataRow.EndEdit%2A> yöntemi çağrılana kadar olay oluşturulmaz. Daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

 Seçtiğiniz olay, doğrulamanın ne kadar ayrıntılı olmasını istediğinize bağlıdır. Bir sütun değiştiğinde bir hatayı hemen yakalayabilmeniz önemliyse, <xref:System.Data.DataTable.ColumnChanging> olayını kullanarak doğrulama oluşturun. Aksi takdirde, birden çok hata oluşmasına neden olabilecek <xref:System.Data.DataTable.RowChanging> olayını kullanın. Ayrıca, verileriniz bir sütunun değerinin başka bir sütunun içeriğine göre doğrulanması için yapılandırılmış ise, <xref:System.Data.DataTable.RowChanging> olayı sırasında doğrulama işlemini gerçekleştirin.

 Kayıtlar güncelleştirilirken <xref:System.Data.DataTable> nesnesi, değişiklikler yapıldığından ve değişiklikler yapıldıktan sonra yanıt verebilmeniz gereken olayları oluşturur.

 Uygulamanız türü belirtilmiş bir veri kümesi kullanıyorsa, türü kesin belirlenmiş olay işleyicileri oluşturabilirsiniz. Bu, için işleyiciler oluşturabileceğiniz dört tür ek olay ekler: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` ve `dataTableNameRowDeleted`. Bu tür olay işleyicileri, kodunuzun daha kolay yazılması ve okunması için tablonuzun sütun adlarını içeren bir bağımsız değişken iletir.

## <a name="data-update-events"></a>Veri güncelleştirme olayları

|Olay|Açıklama|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Bir sütundaki değer değiştiriliyor. Bu olay, önerilen yeni değerle birlikte satır ve sütunu size geçirir.|
|<xref:System.Data.DataTable.ColumnChanged>|Bir sütundaki değer değiştirildi. Olay satırı ve sütunu, önerilen değerle birlikte size geçirir.|
|<xref:System.Data.DataTable.RowChanging>|Bir <xref:System.Data.DataRow> nesnesinde yapılan değişiklikler veri kümesine geri dönmek için kullanılır. @No__t_0 yöntemi çağırdıysanız, <xref:System.Data.DataTable.ColumnChanging> olayı oluşturulduktan hemen sonra sütundaki her değişiklik için <xref:System.Data.DataTable.RowChanging> olayı tetiklenir. Değişiklik yapmadan önce <xref:System.Data.DataRow.BeginEdit%2A> çağrılırsa, <xref:System.Data.DataTable.RowChanging> olay yalnızca <xref:System.Data.DataRow.EndEdit%2A> yöntemini çağırdığınızda tetiklenir.<br /><br /> Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowChanged>|Bir satır değiştirildi. Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleting>|Bir satır siliniyor. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleted>|Bir satır silindi. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|

 @No__t_0, <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowDeleting> olayları güncelleştirme işlemi sırasında oluşturulur. Bu olayları, verileri doğrulamak veya diğer işleme türlerini gerçekleştirmek için kullanabilirsiniz. Güncelleştirme bu olaylar sırasında işlemde olduğundan, bir özel durum oluşturarak iptal edebilirsiniz ve bu da güncelleştirmenin tamamlanmasını önler.

 @No__t_0, <xref:System.Data.DataTable.RowChanged> ve <xref:System.Data.DataTable.RowDeleted> olayları, güncelleştirme başarıyla tamamlandığında oluşan bildirim olaylardır. Bu olaylar, başarılı bir güncelleştirmeye göre daha fazla işlem yapmak istediğinizde faydalıdır.

## <a name="validate-data-during-column-changes"></a>Sütun değişiklikleri sırasında verileri doğrulama

> [!NOTE]
> **Veri kümesi Tasarımcısı** , bir veri kümesine doğrulama mantığının eklenebileceği kısmi bir sınıf oluşturur. Tasarımcı tarafından oluşturulan veri kümesi, kısmi sınıftaki hiçbir kodu silmez veya değiştirmez.

 Veri sütunundaki değer <xref:System.Data.DataTable.ColumnChanging> olayına yanıt vererek değiştiğinde verileri doğrulayabilirsiniz. Bu olay, oluşturulduğunda, geçerli sütun için önerilen değeri içeren bir olay bağımsız değişkeni (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) geçirir. @No__t_0 içeriğine göre şunları yapabilirsiniz:

- Hiçbir şey yapmadan önerilen değeri kabul edin.

- Sütun değiştirme olay işleyicisi içinden sütun hatası (<xref:System.Data.DataRow.SetColumnError%2A>) ayarlayarak önerilen değeri reddedin.

- İsteğe bağlı olarak, kullanıcıya bir hata iletisi göstermek için bir <xref:System.Windows.Forms.ErrorProvider> denetimi kullanın. Daha fazla bilgi için bkz. [ErrorProvider Component](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).

  Doğrulama <xref:System.Data.DataTable.RowChanging> olay sırasında da gerçekleştirilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında verileri doğrulama
 Doğrulamak istediğiniz her sütunun, uygulamanızın gereksinimlerini karşılayan veriler içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen bir değer kabul edilemez ise, sütunu hata içerdiğini belirtecek şekilde ayarlayarak bunu yapın. Aşağıdaki örneklerde `Quantity` sütunu 0 veya daha az olduğunda bir sütun hatası ayarlanır. Satır değişen olay işleyicileri aşağıdaki örneklere benzer olmalıdır.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Bir satır değiştiğinde verileri doğrulamak için (Visual Basic)

1. Veri kümenizi **veri kümesi Tasarımcısı**açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem, veri kümesinin kısmi sınıf dosyasında <xref:System.Data.DataTable> <xref:System.Data.DataTable.RowChanging> olay işleyicisini otomatik olarak oluşturur.

    > [!TIP]
    > Satır değiştiren olay işleyicisini oluşturmak için tablo adının sol tarafında çift tıklayın. Tablo adını çift tıklarsanız düzenleyebilirsiniz.

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satır değiştiğinde verileri doğrulamak için (C#)

1. Veri kümenizi **veri kümesi Tasarımcısı**açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem <xref:System.Data.DataTable> için kısmi sınıf bir dosya oluşturur.

    > [!NOTE]
    > **Veri kümesi Tasarımcısı** , <xref:System.Data.DataTable.RowChanging> olayı için otomatik olarak bir olay işleyici oluşturmaz. @No__t_0 olayını işlemek için bir yöntem oluşturmanız ve olayı tablonun başlatma yönteminde bağlamak için kodu çalıştırmanız gerekir.

3. Aşağıdaki kodu kısmi sınıfa kopyalayın:

    ```
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Değiştirilen satırları almak için
 Bir veri tablosundaki her satır, <xref:System.Data.DataRowState> Numaralandırmadaki değerleri kullanarak o satırın geçerli durumunu takip eden bir <xref:System.Data.DataRow.RowState%2A> özelliğine sahiptir. Bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> `GetChanges` yöntemini çağırarak bir veri kümesinden veya veri tablosundan değiştirilen satırları döndürebilirsiniz. Bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemini çağırarak `GetChanges` çağrılmadan önce değişikliklerin mevcut olduğunu doğrulayabilirsiniz. @No__t_0 hakkında daha fazla bilgi için bkz. [nasıl yapılır: değiştirilen satırları denetleme](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).

> [!NOTE]
> Bir veri kümesine veya veri tablosuna değişiklikler yaptıktan sonra (<xref:System.Data.DataSet.AcceptChanges%2A> yöntemini çağırarak), `GetChanges` yöntemi veri döndürmez. Uygulamanızın değiştirilen satırları işlemesi gerekiyorsa, `AcceptChanges` yöntemini çağırmadan önce değişiklikleri işlemelidir.

 Bir veri kümesinin veya veri tablosunun <xref:System.Data.DataSet.GetChanges%2A> yöntemini çağırmak, yalnızca değiştirilmiş kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — Örneğin, yalnızca yeni kayıtlar veya yalnızca değiştirilen kayıtlar — <xref:System.Data.DataRowState> Numaralandırmadaki bir değeri `GetChanges` yöntemine bir parametre olarak geçirebilirsiniz.

 Bir satırın farklı sürümlerine erişmek için <xref:System.Data.DataRowVersion> numaralandırmayı kullanın (örneğin, işlemeden önce bir satırdaki özgün değerler).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden tüm değiştirilen kayıtları almak için

- Bir veri kümesinin <xref:System.Data.DataSet.GetChanges%2A> yöntemini çağırın.

     Aşağıdaki örnek, `changedRecords` adlı yeni bir veri kümesi oluşturur ve `dataSet1` adlı başka bir veri kümesinden değişen tüm kayıtlarla doldurur.

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değiştirilen tüm kayıtları almak için

- DataTable 'ın <xref:System.Data.DataTable.GetChanges%2A> yöntemini çağırın.

     Aşağıdaki örnek, `changedRecordsTable` adlı yeni bir veri tablosu oluşturur ve `dataTable1` adlı başka bir veri tablosundan değiştirilen tüm kayıtlarla doldurur.

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumuna sahip tüm kayıtları almak için

- Bir veri kümesinin veya veri tablosunun `GetChanges` yöntemini çağırın ve bir <xref:System.Data.DataRowState> numaralandırma değerini bağımsız değişken olarak geçirin.

     Aşağıdaki örnekte, `addedRecords` adlı yeni bir veri kümesinin nasıl oluşturulacağı ve yalnızca `dataSet1` veri kümesine eklenen kayıtlarla doldurulması gösterilmektedir.

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- Aşağıdaki örnek, `Customers` tablosuna yakın zamanda eklenen tüm kayıtların nasıl geri alınacağını gösterir:

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>DataRow 'ın orijinal sürümüne erişin
 Veri satırlarında değişiklik yapıldığında veri kümesi, satırın hem özgün (<xref:System.Data.DataRowVersion>) hem de yeni (<xref:System.Data.DataRowVersion>) sürümlerini korur. Örneğin, `AcceptChanges` yöntemi çağrılmadan önce, uygulamanız bir kaydın farklı sürümlerine erişebilir (<xref:System.Data.DataRowVersion> numaralandırmada tanımlandığı gibi) ve değişiklikleri buna göre işleyebilir.

> [!NOTE]
> Bir satırın farklı sürümleri, yalnızca düzenlendikten sonra ve `AcceptChanges` yöntemi çağrıldıktan sonra bulunur. @No__t_0 yöntemi çağrıldıktan sonra, geçerli ve orijinal sürümler aynıdır.

 @No__t_0 değeri sütun diziniyle (veya bir dize olarak sütun adı) geçirmek, bu sütunun belirli bir satır sürümünden değeri döndürür. Değiştirilen sütun <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olayları sırasında belirlenir. Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya aldıysanız, bu olaylar oluşturulmaz ve hangi sütunların değiştiğini programlı bir şekilde belirlemeniz gerekir. Bunu, <xref:System.Data.DataTable.Columns%2A> koleksiyonunu kullanarak ve farklı <xref:System.Data.DataRowVersion> değerlerini karşılaştırarak yapabilirsiniz.

#### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için

- Döndürmek istediğiniz satırın <xref:System.Data.DataRowVersion> geçirerek bir sütunun değerine erişin.

     Aşağıdaki örnek, bir <xref:System.Data.DataRow> `CompanyName` alanın orijinal değerini almak için bir <xref:System.Data.DataRowVersion> değerinin nasıl kullanılacağını gösterir:

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>Bir DataRow 'ın geçerli sürümüne erişin

#### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için

- Bir sütunun değerine erişin ve sonra dizine döndürmek istediğiniz bir satır sürümünü gösteren bir parametre ekleyin.

     Aşağıdaki örnek, bir <xref:System.Data.DataRow> `CompanyName` alanının geçerli değerini almak için bir <xref:System.Data.DataRowVersion> değerinin nasıl kullanılacağını gösterir:

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)