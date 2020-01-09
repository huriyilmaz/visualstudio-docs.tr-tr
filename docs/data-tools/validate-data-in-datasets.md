---
title: Veri kümelerindeki verileri doğrulama
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed115e851e9c2291dfc9d00f4bb36f670a7f3e00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586074"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
Verilerin doğrulanması, veri nesnelerine girilen değerlerin bir veri kümesinin şeması içindeki kısıtlamalara uygun olduğunu onaylama işlemidir. Doğrulama işlemi, bu değerlerin uygulamanız için oluşturulan kurallara göre olduğunu da onaylar. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak iyi bir uygulamadır. Bu, hataların yanı sıra bir uygulama ve veritabanı arasındaki gidiş dönüş sayısını azaltır.

Veri kümesine yazılan verilerin veri kümesine doğrulama denetimleri oluşturarak geçerli olduğunu doğrulayabilirsiniz. Veri kümesi, bir formda, bir bileşen içinde veya başka bir şekilde bir biçimde, doğrudan denetimler tarafından değil, güncelleştirmenin nasıl gerçekleştirildiğine bakılmaksızın verileri denetleyebilir. Veri kümesi uygulamanızın bir parçası olduğundan (veritabanı arka ucunun aksine) uygulamaya özgü doğrulama oluşturmak için mantıksal bir yerdir.

Uygulamanıza doğrulama eklemek için en iyi yer, DataSet 'in kısmi sınıf dosyasında bulunur. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]içinde, **veri kümesi Tasarımcısı** açın ve doğrulama oluşturmak istediğiniz sütun veya tabloya çift tıklayın. Bu eylem otomatik olarak bir <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay işleyicisi oluşturur.

## <a name="validate-data"></a>Verileri doğrulama
Bir veri kümesi içinde doğrulama işlemi aşağıdaki yollarla gerçekleştirilir:

- Değişiklik sırasında tek bir veri sütunundaki değerleri kontrol eden, uygulamaya özgü bir doğrulama oluşturarak. Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](validate-data-in-datasets.md).

- Tüm veri satırları değiştirilirken, verileri değerlere denetleyerek uygulamaya özgü doğrulama bilgilerinizi oluşturarak. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](validate-data-in-datasets.md).

- Veri kümesinin gerçek şema tanımının bir parçası olarak anahtarlar, benzersiz kısıtlamalar ve benzeri bir oluşturma.

- <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>ve <xref:System.Data.DataColumn.Unique%2A>gibi <xref:System.Data.DataColumn> nesnenin özelliklerini ayarlayarak.

Bir kayıtta değişiklik yapıldığında <xref:System.Data.DataTable> nesnesi tarafından çeşitli olaylar tetiklenir:

- <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olayları, tek bir sütundaki her değişiklikten sonra ve sonra oluşturulur. <xref:System.Data.DataTable.ColumnChanging> olay, belirli sütunlardaki değişiklikleri doğrulamak istediğinizde faydalıdır. Önerilen değişiklik hakkındaki bilgiler, olaya bir bağımsız değişken olarak geçirilir.
- <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları, bir satırdaki herhangi bir değişiklik sırasında ve sonrasında oluşturulur. <xref:System.Data.DataTable.RowChanging> olayı daha genel. Bu, satırda bir yerde değişiklik gerçekleştiğini gösterir, ancak hangi sütunun değiştiğini bilemezsiniz.

Varsayılan olarak, bir sütunda yapılan her değişiklik dört olay oluşturur. Birincisi, değiştirilen belirli bir sütunun <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olaylardır. Daha sonra <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları vardır. Satırda birden fazla değişiklik yapılırsa, olaylar her değişiklik için oluşturulur.

> [!NOTE]
> Veri satırının <xref:System.Data.DataRow.BeginEdit%2A> yöntemi, her sütun değişikliğinden sonra <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olaylarını kapatır. Bu durumda, <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları tek bir kez oluşturulduğunda <xref:System.Data.DataRow.EndEdit%2A> yöntemi çağrılana kadar olay oluşturulmaz. Daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

Seçtiğiniz olay, doğrulamanın ne kadar ayrıntılı olmasını istediğinize bağlıdır. Bir sütun değiştiğinde bir hatayı hemen yakalayabilmeniz önemliyse, <xref:System.Data.DataTable.ColumnChanging> olayını kullanarak doğrulama oluşturun. Aksi takdirde, birden çok hata oluşmasına neden olabilecek <xref:System.Data.DataTable.RowChanging> olayını kullanın. Ayrıca, verileriniz bir sütunun değerinin başka bir sütunun içeriğine göre doğrulanması için yapılandırılmış ise, <xref:System.Data.DataTable.RowChanging> olayı sırasında doğrulama işlemini gerçekleştirin.

Kayıtlar güncelleştirilirken <xref:System.Data.DataTable> nesnesi, değişiklikler yapıldığından ve değişiklikler yapıldıktan sonra yanıt verebilmeniz gereken olayları oluşturur.

Uygulamanız türü belirtilmiş bir veri kümesi kullanıyorsa, türü kesin belirlenmiş olay işleyicileri oluşturabilirsiniz. Bu, işleyiciler oluşturabileceğiniz dört tür içeren olayları ekler: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`ve `dataTableNameRowDeleted`. Bu tür olay işleyicileri, kodunuzun daha kolay yazılması ve okunması için tablonuzun sütun adlarını içeren bir bağımsız değişken iletir.

## <a name="data-update-events"></a>Veri güncelleştirme olayları

|Olay|Açıklama|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Bir sütundaki değer değiştiriliyor. Bu olay, önerilen yeni değerle birlikte satır ve sütunu size geçirir.|
|<xref:System.Data.DataTable.ColumnChanged>|Bir sütundaki değer değiştirildi. Olay satırı ve sütunu, önerilen değerle birlikte size geçirir.|
|<xref:System.Data.DataTable.RowChanging>|Bir <xref:System.Data.DataRow> nesnesinde yapılan değişiklikler veri kümesine geri dönmek için kullanılır. <xref:System.Data.DataRow.BeginEdit%2A> yöntemi çağırdıysanız, <xref:System.Data.DataTable.ColumnChanging> olayı oluşturulduktan hemen sonra sütundaki her değişiklik için <xref:System.Data.DataTable.RowChanging> olayı tetiklenir. Değişiklik yapmadan önce <xref:System.Data.DataRow.BeginEdit%2A> çağrılırsa, <xref:System.Data.DataTable.RowChanging> olay yalnızca <xref:System.Data.DataRow.EndEdit%2A> yöntemini çağırdığınızda tetiklenir.<br /><br /> Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowChanged>|Bir satır değiştirildi. Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleting>|Bir satır siliniyor. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleted>|Bir satır silindi. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|

<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>ve <xref:System.Data.DataTable.RowDeleting> olayları güncelleştirme işlemi sırasında oluşturulur. Bu olayları, verileri doğrulamak veya diğer işleme türlerini gerçekleştirmek için kullanabilirsiniz. Güncelleştirme bu olaylar sırasında işlemde olduğundan, bir özel durum oluşturarak iptal edebilirsiniz ve bu da güncelleştirmenin tamamlanmasını önler.

<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> ve <xref:System.Data.DataTable.RowDeleted> olayları, güncelleştirme başarıyla tamamlandığında oluşan bildirim olaylardır. Bu olaylar, başarılı bir güncelleştirmeye göre daha fazla işlem yapmak istediğinizde faydalıdır.

## <a name="validate-data-during-column-changes"></a>Sütun değişiklikleri sırasında verileri doğrulama

> [!NOTE]
> **Veri kümesi Tasarımcısı** , bir veri kümesine doğrulama mantığının eklenebileceği kısmi bir sınıf oluşturur. Tasarımcı tarafından oluşturulan veri kümesi, kısmi sınıftaki hiçbir kodu silmez veya değiştirmez.

Veri sütunundaki değer <xref:System.Data.DataTable.ColumnChanging> olayına yanıt vererek değiştiğinde verileri doğrulayabilirsiniz. Bu olay, oluşturulduğunda, geçerli sütun için önerilen değeri içeren bir olay bağımsız değişkeni (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) geçirir. `e.ProposedValue`içeriğine göre şunları yapabilirsiniz:

- Hiçbir şey yapmadan önerilen değeri kabul edin.

- Sütun değiştirme olay işleyicisi içinden sütun hatası (<xref:System.Data.DataRow.SetColumnError%2A>) ayarlayarak önerilen değeri reddedin.

- İsteğe bağlı olarak, kullanıcıya bir hata iletisi göstermek için bir <xref:System.Windows.Forms.ErrorProvider> denetimi kullanın. Daha fazla bilgi için bkz. [ErrorProvider Component](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Doğrulama <xref:System.Data.DataTable.RowChanging> olay sırasında da gerçekleştirilebilir.

## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında verileri doğrulama
Doğrulamak istediğiniz her sütunun, uygulamanızın gereksinimlerini karşılayan veriler içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen bir değer kabul edilemez ise, sütunu hata içerdiğini belirtecek şekilde ayarlayarak bunu yapın. Aşağıdaki örneklerde `Quantity` sütunu 0 veya daha az olduğunda bir sütun hatası ayarlanır. Satır değişen olay işleyicileri aşağıdaki örneklere benzer olmalıdır.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Bir satır değiştiğinde verileri doğrulamak için (Visual Basic)

1. Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem, veri kümesinin kısmi sınıf dosyasında <xref:System.Data.DataTable> <xref:System.Data.DataTable.RowChanging> olay işleyicisini otomatik olarak oluşturur.

    > [!TIP]
    > Satır değiştiren olay işleyicisini oluşturmak için tablo adının sol tarafında çift tıklayın. Tablo adını çift tıklarsanız düzenleyebilirsiniz.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satır değiştiğinde verileri doğrulamak için (C#)

1. Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem <xref:System.Data.DataTable>için kısmi sınıf bir dosya oluşturur.

    > [!NOTE]
    > **Veri kümesi Tasarımcısı** , <xref:System.Data.DataTable.RowChanging> olayı için otomatik olarak bir olay işleyici oluşturmaz. <xref:System.Data.DataTable.RowChanging> olayını işlemek için bir yöntem oluşturmanız ve olayı tablonun başlatma yönteminde bağlamak için kodu çalıştırmanız gerekir.

3. Aşağıdaki kodu kısmi sınıfa kopyalayın:

    ```csharp
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
Bir veri tablosundaki her satır, <xref:System.Data.DataRowState> Numaralandırmadaki değerleri kullanarak o satırın geçerli durumunu takip eden bir <xref:System.Data.DataRow.RowState%2A> özelliğine sahiptir. Bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>`GetChanges` yöntemini çağırarak bir veri kümesinden veya veri tablosundan değiştirilen satırları döndürebilirsiniz. Bir veri kümesinin <xref:System.Data.DataSet.HasChanges%2A> yöntemini çağırarak `GetChanges` çağrılmadan önce değişikliklerin mevcut olduğunu doğrulayabilirsiniz.

> [!NOTE]
> Bir veri kümesine veya veri tablosuna değişiklikler yaptıktan sonra (<xref:System.Data.DataSet.AcceptChanges%2A> yöntemini çağırarak), `GetChanges` yöntemi veri döndürmez. Uygulamanızın değiştirilen satırları işlemesi gerekiyorsa, `AcceptChanges` yöntemini çağırmadan önce değişiklikleri işlemelidir.

Bir veri kümesinin veya veri tablosunun <xref:System.Data.DataSet.GetChanges%2A> yöntemini çağırmak, yalnızca değiştirilmiş kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — Örneğin, yalnızca yeni kayıtlar veya yalnızca değiştirilen kayıtlar — <xref:System.Data.DataRowState> Numaralandırmadaki bir değeri `GetChanges` yöntemine bir parametre olarak geçirebilirsiniz.

Bir satırın farklı sürümlerine erişmek için <xref:System.Data.DataRowVersion> numaralandırmayı kullanın (örneğin, işlemeden önce bir satırdaki özgün değerler).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden tüm değiştirilen kayıtları almak için

- Bir veri kümesinin <xref:System.Data.DataSet.GetChanges%2A> yöntemini çağırın.

     Aşağıdaki örnek, `changedRecords` adlı yeni bir veri kümesi oluşturur ve `dataSet1`adlı başka bir veri kümesinden değişen tüm kayıtlarla doldurur.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değiştirilen tüm kayıtları almak için

- DataTable 'ın <xref:System.Data.DataTable.GetChanges%2A> yöntemini çağırın.

     Aşağıdaki örnek, `changedRecordsTable` adlı yeni bir veri tablosu oluşturur ve `dataTable1`adlı başka bir veri tablosundan değiştirilen tüm kayıtlarla doldurur.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumuna sahip tüm kayıtları almak için

- Bir veri kümesinin veya veri tablosunun `GetChanges` yöntemini çağırın ve bir <xref:System.Data.DataRowState> numaralandırma değerini bağımsız değişken olarak geçirin.

     Aşağıdaki örnekte, `addedRecords` adlı yeni bir veri kümesinin nasıl oluşturulacağı ve yalnızca `dataSet1` veri kümesine eklenen kayıtlarla doldurulması gösterilmektedir.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Aşağıdaki örnek, `Customers` tablosuna yakın zamanda eklenen tüm kayıtların nasıl geri alınacağını gösterir:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>DataRow 'ın orijinal sürümüne erişin
Veri satırlarında değişiklik yapıldığında veri kümesi, satırın hem özgün (<xref:System.Data.DataRowVersion.Original>) hem de yeni (<xref:System.Data.DataRowVersion.Current>) sürümlerini korur. Örneğin, `AcceptChanges` yöntemi çağrılmadan önce, uygulamanız bir kaydın farklı sürümlerine erişebilir (<xref:System.Data.DataRowVersion> numaralandırmada tanımlandığı gibi) ve değişiklikleri buna göre işleyebilir.

> [!NOTE]
> Bir satırın farklı sürümleri, yalnızca düzenlendikten sonra ve `AcceptChanges` yöntemi çağrıldıktan sonra bulunur. `AcceptChanges` yöntemi çağrıldıktan sonra, geçerli ve orijinal sürümler aynıdır.

<xref:System.Data.DataRowVersion> değeri sütun diziniyle (veya bir dize olarak sütun adı) geçirmek, bu sütunun belirli bir satır sürümünden değeri döndürür. Değiştirilen sütun <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.ColumnChanged> olayları sırasında belirlenir. Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya aldıysanız, bu olaylar oluşturulmaz ve hangi sütunların değiştiğini programlı bir şekilde belirlemeniz gerekir. Bunu, <xref:System.Data.DataTable.Columns%2A> koleksiyonunu kullanarak ve farklı <xref:System.Data.DataRowVersion> değerlerini karşılaştırarak yapabilirsiniz.

### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için

- Döndürmek istediğiniz satırın <xref:System.Data.DataRowVersion> geçirerek bir sütunun değerine erişin.

     Aşağıdaki örnek, bir <xref:System.Data.DataRow>`CompanyName` alanın orijinal değerini almak için bir <xref:System.Data.DataRowVersion> değerinin nasıl kullanılacağını gösterir:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Bir DataRow 'ın geçerli sürümüne erişin

### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için

- Bir sütunun değerine erişin ve sonra dizine döndürmek istediğiniz bir satır sürümünü gösteren bir parametre ekleyin.

     Aşağıdaki örnek, bir <xref:System.Data.DataRow>`CompanyName` alanının geçerli değerini almak için bir <xref:System.Data.DataRowVersion> değerinin nasıl kullanılacağını gösterir:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri doğrulama](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile form doğrulama için hata simgeleri görüntüleme](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
