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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621063"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verilerin doğrulanması, veri nesnelerine girilen değerlerin bir veri kümesinin şeması içindeki kısıtlamalara uygun olduğunu onaylama işlemidir. Doğrulama işlemi, bu değerlerin uygulamanız için oluşturulan kurallara göre olduğunu da onaylar. Temel alınan veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak iyi bir uygulamadır. Bu, hataların yanı sıra bir uygulama ve veritabanı arasındaki gidiş dönüş sayısını azaltır.

 Veri kümesine yazılan verilerin veri kümesine doğrulama denetimleri oluşturarak geçerli olduğunu doğrulayabilirsiniz. Veri kümesi, bir formda, bir bileşen içinde veya başka bir şekilde bir biçimde, doğrudan denetimler tarafından değil, güncelleştirmenin nasıl gerçekleştirildiğine bakılmaksızın verileri denetleyebilir. Veri kümesi uygulamanızın bir parçası olduğundan (veritabanı arka ucunun aksine) uygulamaya özgü doğrulama oluşturmak için mantıksal bir yerdir.

 Uygulamanıza doğrulama eklemek için en iyi yer, DataSet 'in kısmi sınıf dosyasında bulunur. Ya da ' de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] **veri kümesi Tasarımcısı** açın ve doğrulama oluşturmak istediğiniz sütun veya tabloya çift tıklayın. Bu eylem otomatik olarak bir <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay işleyicisi oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) veya [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Tüm bir örnek için bkz. [Izlenecek yol: bir veri kümesine doğrulama ekleme](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).

## <a name="validate-data"></a>Verileri doğrulama
 Bir veri kümesi içindeki doğrulama, aşağıdaki yollarla gerçekleştirilebilir:

- Değişiklik sırasında tek bir veri sütunundaki değerleri kontrol eden, uygulamaya özgü bir doğrulama oluşturarak.  Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Tüm veri satırları değiştirilirken, verileri değerlere denetleyerek uygulamaya özgü doğrulama bilgilerinizi oluşturarak. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

- Veri kümesinin gerçek şema tanımının bir parçası olarak anahtarlar, benzersiz kısıtlamalar ve benzeri bir oluşturma. Şema tanımına doğrulama ekleme hakkında daha fazla bilgi için, bkz. [bir DataColumn 'ı benzersiz değerler içerecek şekilde kısıtlama](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

- , Ve gibi nesnenin özelliklerini ayarlayarak <xref:System.Data.DataColumn> <xref:System.Data.DataColumn.MaxLength%2A> <xref:System.Data.DataColumn.AllowDBNull%2A> <xref:System.Data.DataColumn.Unique%2A> .

  Bir kayıtta değişiklik yapıldığında nesne tarafından birkaç olay tetiklenir <xref:System.Data.DataTable> :

- <xref:System.Data.DataTable.ColumnChanging>Ve <xref:System.Data.DataTable.ColumnChanged> olayları, tek bir sütundaki her değişiklikten sonra ve sonrasında oluşturulur. Bu <xref:System.Data.DataTable.ColumnChanging> olay, belirli sütunlardaki değişiklikleri doğrulamak istediğinizde yararlı olur. Önerilen değişiklik hakkındaki bilgiler, olaya bir bağımsız değişken olarak geçirilir. Daha fazla bilgi için bkz. [nasıl yapılır: sütun değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- <xref:System.Data.DataTable.RowChanging>Ve <xref:System.Data.DataTable.RowChanged> olayları, bir satırdaki herhangi bir değişiklik sırasında ve sonrasında oluşturulur. <xref:System.Data.DataTable.RowChanging>Olay daha genel. Bu, satırda bir yerde değişiklik gerçekleştiğini gösterir, ancak hangi sütunun değiştiğini bilemezsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

  Varsayılan olarak, bir sütunda yapılan her değişiklik dört olay oluşturur. Birincisi, değiştirilmekte <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> olan belirli bir sütunun ve olaylardır. Sonraki <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> Olaylar ve olaylardır. Satırda birden fazla değişiklik yapılırsa, olaylar her değişiklik için oluşturulur.

> [!NOTE]
> Veri satırının <xref:System.Data.DataRow.BeginEdit%2A> metodu, <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> her sütun değişikliğinden sonra ve olaylarını kapatır. Bu durumda, <xref:System.Data.DataRow.EndEdit%2A> <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowChanged> olayları yalnızca bir kez oluşturulduğunda, olay çağrılana kadar olay oluşturulmaz. Daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

 Seçtiğiniz olay, doğrulamanın ne kadar ayrıntılı olmasını istediğinize bağlıdır. Bir sütun değiştiğinde bir hatayı hemen yakalayabilmeniz önemliyse olayını kullanarak doğrulama oluşturun <xref:System.Data.DataTable.ColumnChanging> . Aksi takdirde, <xref:System.Data.DataTable.RowChanging> bir kerede birkaç hata oluşmasına neden olabilecek olayını kullanın. Ayrıca, verileriniz bir sütunun değerinin başka bir sütunun içeriğine göre doğrulanması için yapılandırılmış ise, olay sırasında doğrulama işlemini gerçekleştirin <xref:System.Data.DataTable.RowChanging> .

 Kayıtlar güncelleştirilirken, <xref:System.Data.DataTable> nesne, değişiklikler yapıldığında ve değişiklikler yapıldıktan sonra yanıt verebildiği olaylar oluşturur.

 Uygulamanız türü belirtilmiş bir veri kümesi kullanıyorsa, türü kesin belirlenmiş olay işleyicileri oluşturabilirsiniz. Bu, için işleyiciler oluşturabileceğiniz dört tür ek olay ekler: `dataTableNameRowChanging` ,, `dataTableNameRowChanged` `dataTableNameRowDeleting` , ve `dataTableNameRowDeleted` . Bu tür olay işleyicileri, kodunuzun daha kolay yazılması ve okunması için tablonuzun sütun adlarını içeren bir bağımsız değişken iletir.

## <a name="data-update-events"></a>Veri güncelleştirme olayları

|Olay|Description|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Bir sütundaki değer değiştiriliyor. Bu olay, önerilen yeni değerle birlikte satır ve sütunu size geçirir.|
|<xref:System.Data.DataTable.ColumnChanged>|Bir sütundaki değer değiştirildi. Olay satırı ve sütunu, önerilen değerle birlikte size geçirir.|
|<xref:System.Data.DataTable.RowChanging>|Bir nesne üzerinde yapılan değişiklikler <xref:System.Data.DataRow> veri kümesine geri aktarılmalıdır. Yöntemini çağırdıysanız olay, <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataTable.RowChanging> olay oluşturulduktan hemen sonra bir sütundaki her değişiklik için oluşturulur <xref:System.Data.DataTable.ColumnChanging> . <xref:System.Data.DataRow.BeginEdit%2A>Değişiklik yapmadan önce çağrılırsa, <xref:System.Data.DataTable.RowChanging> olay yalnızca yöntemini çağırdığınızda tetiklenir <xref:System.Data.DataRow.EndEdit%2A> .<br /><br /> Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowChanged>|Bir satır değiştirildi. Olay, ne tür bir eylem (değişiklik, ekleme, vb.) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleting>|Bir satır siliniyor. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|
|<xref:System.Data.DataTable.RowDeleted>|Bir satır silindi. Olay, ne tür bir eylem (silme) gerçekleştirildiğinin belirten bir değer ile birlikte size satırı geçirir.|

 <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> Ve <xref:System.Data.DataTable.RowDeleting> olayları güncelleştirme işlemi sırasında oluşturulur. Bu olayları, verileri doğrulamak veya diğer işleme türlerini gerçekleştirmek için kullanabilirsiniz. Güncelleştirme bu olaylar sırasında işlemde olduğundan, bir özel durum oluşturarak iptal edebilirsiniz ve bu da güncelleştirmenin tamamlanmasını önler.

 <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> Ve <xref:System.Data.DataTable.RowDeleted> olayları güncelleştirme başarıyla tamamlandığında oluşturulan bildirim olaylardır. Bu olaylar, başarılı bir güncelleştirmeye göre daha fazla işlem yapmak istediğinizde faydalıdır.

## <a name="validate-data-during-column-changes"></a>Sütun değişiklikleri sırasında verileri doğrulama

> [!NOTE]
> **Veri kümesi Tasarımcısı** , bir veri kümesine doğrulama mantığının eklenebileceği kısmi bir sınıf oluşturur. Tasarımcı tarafından oluşturulan veri kümesi, kısmi sınıftaki hiçbir kodu silmez veya değiştirmez.

 Bir veri sütunundaki değer, olaya yanıt vererek değiştiğinde verileri doğrulayabilirsiniz <xref:System.Data.DataTable.ColumnChanging> . Bu olay, oluşturulduğunda, <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> Geçerli sütun için önerilen değeri içeren bir olay bağımsız değişkeni () geçirir. İçeriğine göre şunları `e.ProposedValue` yapabilirsiniz:

- Hiçbir şey yapmadan önerilen değeri kabul edin.

- Sütun değiştirme olay işleyicisi içinden sütun hatası () ayarlayarak önerilen değeri reddedin <xref:System.Data.DataRow.SetColumnError%2A> .

- İsteğe bağlı olarak <xref:System.Windows.Forms.ErrorProvider> , kullanıcıya bir hata iletisi göstermek için bir denetim kullanın. Daha fazla bilgi için bkz. [ErrorProvider Component](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).

  Doğrulama olay sırasında da gerçekleştirilebilir <xref:System.Data.DataTable.RowChanging> . Daha fazla bilgi için bkz. [nasıl yapılır: satır değişiklikleri sırasında verileri doğrulama](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında verileri doğrulama
 Doğrulamak istediğiniz her sütunun, uygulamanızın gereksinimlerini karşılayan veriler içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen bir değer kabul edilemez ise, sütunu hata içerdiğini belirtecek şekilde ayarlayarak bunu yapın. Aşağıdaki örneklerde `Quantity` sütun 0 veya daha az olduğunda bir sütun hatası ayarlanır. Satır değişen olay işleyicileri aşağıdaki örneklere benzer olmalıdır.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Bir satır değiştiğinde verileri doğrulamak için (Visual Basic)

1. Veri kümenizi **veri kümesi Tasarımcısı**açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem <xref:System.Data.DataTable.RowChanging> , <xref:System.Data.DataTable> veri kümesinin kısmi sınıf dosyasında öğesinin olay işleyicisini otomatik olarak oluşturur.

    > [!TIP]
    > Satır değiştiren olay işleyicisini oluşturmak için tablo adının sol tarafında çift tıklayın. Tablo adını çift tıklarsanız düzenleyebilirsiniz.

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satır değiştiğinde verileri doğrulamak için (C#)

1. Veri kümenizi **veri kümesi Tasarımcısı**açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem, için bir kısmi sınıf dosyası oluşturur <xref:System.Data.DataTable> .

    > [!NOTE]
    > **Veri kümesi Tasarımcısı** , olay için otomatik olarak bir olay işleyici oluşturmaz <xref:System.Data.DataTable.RowChanging> . Olayı işlemek için bir yöntem oluşturmanız <xref:System.Data.DataTable.RowChanging> ve olayı tablonun başlatma yönteminde bağlamak için kodu çalıştırmanız gerekir.

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
 Bir veri tablosundaki her satır, <xref:System.Data.DataRow.RowState%2A> Numaralandırmadaki değerleri kullanarak o satırın geçerli durumunu izlemeyi tutan bir özelliğe sahiptir <xref:System.Data.DataRowState> . Bir veya yöntemini çağırarak bir veri kümesinden veya veri tablosundan değiştirilen satırları döndürebilirsiniz `GetChanges` <xref:System.Data.DataSet> <xref:System.Data.DataTable> . `GetChanges`Bir veri kümesinin yöntemini çağırarak, çağrılmadan önce değişikliklerin mevcut olduğunu doğrulayabilirsiniz <xref:System.Data.DataSet.HasChanges%2A> . Hakkında daha fazla bilgi için <xref:System.Data.DataSet.HasChanges%2A> bkz. [nasıl yapılır: değiştirilen satırları denetleme](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).

> [!NOTE]
> Bir veri kümesine veya veri tablosuna değişiklikler yaptıktan sonra ( <xref:System.Data.DataSet.AcceptChanges%2A> yöntemini çağırarak), `GetChanges` Yöntem hiçbir veri döndürmez. Uygulamanızın değiştirilen satırları işlemesi gerekiyorsa, metodu çağırmadan önce değişiklikleri işlemelidir `AcceptChanges` .

 Bir veri kümesi <xref:System.Data.DataSet.GetChanges%2A> veya veri tablosu yöntemini çağırmak, yalnızca değiştirilmiş kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — Örneğin, yalnızca yeni kayıtlar veya yalnızca değiştirilen kayıtlar —, Numaralandırmadaki bir değeri, <xref:System.Data.DataRowState> yönteme parametre olarak geçirebilirsiniz `GetChanges` .

 <xref:System.Data.DataRowVersion>Bir satırın farklı sürümlerine erişmek için numaralandırmayı kullanın (örneğin, işlemeden önce bir satırdaki özgün değerler).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden tüm değiştirilen kayıtları almak için

- <xref:System.Data.DataSet.GetChanges%2A>Bir veri kümesinin yöntemini çağırın.

     Aşağıdaki örnek adlı yeni bir veri kümesi oluşturur `changedRecords` ve bunu adlı başka bir veri kümesinden değiştirilen tüm kayıtlarla doldurur `dataSet1` .

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değiştirilen tüm kayıtları almak için

- <xref:System.Data.DataTable.GetChanges%2A>DataTable metodunu çağırın.

     Aşağıdaki örnek adlı yeni bir veri tablosu oluşturur `changedRecordsTable` ve adlı başka bir veri tablosundan değiştirilen tüm kayıtlarla doldurur `dataTable1` .

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumuna sahip tüm kayıtları almak için

- Bir veri `GetChanges` kümesinin veya veri tablosunun yöntemini çağırın ve bir <xref:System.Data.DataRowState> sabit listesi değerini bağımsız değişken olarak geçirin.

     Aşağıdaki örnekte, adlı yeni bir veri kümesinin nasıl oluşturulacağı `addedRecords` ve yalnızca veri kümesine eklenen kayıtlarla doldurulması gösterilmektedir `dataSet1` .

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- Aşağıdaki örnek, son olarak tabloya eklenen tüm kayıtların nasıl geri alınacağını gösterir `Customers` :

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>DataRow 'ın orijinal sürümüne erişin
 Veri satırlarında değişiklik yapıldığında veri kümesi, satırın hem özgün ( <xref:System.Data.DataRowVersion> ) hem de yeni ( <xref:System.Data.DataRowVersion> ) sürümlerini korur. Örneğin, yöntemini çağırmadan önce `AcceptChanges` , uygulamanız bir kaydın farklı sürümlerine erişebilir ( <xref:System.Data.DataRowVersion> numaralandırmada tanımlandığı gibi) ve değişiklikleri buna göre işleyebilir.

> [!NOTE]
> Bir satırın farklı sürümleri, yalnızca düzenlendikten sonra ve `AcceptChanges` yöntemi çağrılmadan önce bulunur. `AcceptChanges`Yöntem çağrıldıktan sonra, geçerli ve orijinal sürümler aynıdır.

 <xref:System.Data.DataRowVersion>Değeri sütun dizini (veya bir dize olarak sütun adı) ile birlikte geçirmek, bu sütunun belirli satır sürümünden değeri döndürür. Değiştirilen sütun, ve olayları sırasında tanımlanır <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> . Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya aldıysanız, bu olaylar oluşturulmaz ve hangi sütunların değiştiğini programlı bir şekilde belirlemeniz gerekir. Bunu, <xref:System.Data.DataTable.Columns%2A> koleksiyonu kullanarak ve farklı değerleri karşılaştırarak yapabilirsiniz <xref:System.Data.DataRowVersion> .

#### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için

- Döndürmek istediğiniz satırın değerini geçirerek bir sütunun değerine erişin <xref:System.Data.DataRowVersion> .

     Aşağıdaki örnek, <xref:System.Data.DataRowVersion> içindeki bir alanın orijinal değerini almak için bir değerinin nasıl kullanılacağını gösterir `CompanyName` <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>Bir DataRow 'ın geçerli sürümüne erişin

#### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için

- Bir sütunun değerine erişin ve sonra dizine döndürmek istediğiniz bir satır sürümünü gösteren bir parametre ekleyin.

     Aşağıdaki örnek, <xref:System.Data.DataRowVersion> içindeki bir alanın geçerli değerini almak için bir değerinin nasıl kullanılacağını gösterir `CompanyName` <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki Verileri Doğrulama](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)