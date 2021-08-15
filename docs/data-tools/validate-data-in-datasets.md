---
title: Veri kümelerindeki verileri doğrulama
description: Veri kümelerini doğrulamayı öğrenin. Verileri doğrulama, veri nesnelerine girilen değerlerin bir veri kümesi şeması içindeki kısıtlamalara uygun olduğunu onaylamayı içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 94c167ab1709597a8e25b9dea52bc68ac8649bfa364eab574533c6acaa94b437
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346642"
---
# <a name="validate-data-in-datasets"></a>Veri kümelerindeki verileri doğrulama
Verileri doğrulama, veri nesnelerine girilen değerlerin bir veri kümesi şeması içindeki kısıtlamalara uygun olduğunu doğrulama işlemidir. Doğrulama işlemi ayrıca bu değerlerin, uygulamanız için kurulmuş kurallara uygun olduğunu onaylar. Temel alınan veritabanına güncelleştirme göndermeden önce verileri doğrulamak iyi bir uygulamadır. Bu, hem hataları hem de bir uygulama ile veritabanı arasındaki gidiş dönüş sayısını azaltır.

Veri kümesine yazılan verilerin geçerli olduğunu onaylamak için veri kümesine doğrulama denetimleri ebilirsiniz. Veri kümesi, güncelleştirmenin nasıl gerçekleştirilip gerçekleştiril bir formda, bileşen içinde veya başka bir yolla doğrudan denetimler tarafından veri denetimi gerçekleştirebilirsiniz. Veri kümesi uygulamanıza bağlı olduğundan (veritabanı arka ucu yerine), uygulamaya özgü doğrulama oluşturmanın mantıksal bir yeridir.

Uygulamanıza doğrulama eklemek için en iyi yer veri kümesi kısmi sınıf dosyasındadır. veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] içinde, **Veri Kümesi Tasarımcısı** açın ve doğrulama oluşturmak istediğiniz sütuna veya tabloya çift tıklayın. Bu eylem otomatik olarak bir <xref:System.Data.DataTable.ColumnChanging> veya olay <xref:System.Data.DataTable.RowChanging> işleyicisi oluşturur.

## <a name="validate-data"></a>Verileri doğrulama
Bir veri kümesinde doğrulama aşağıdaki yollarla işler:

- Değişiklikler sırasında tek bir veri sütunundaki değerleri kontrol etmek için uygulamaya özgü kendi doğrulamanızı oluşturarak. Daha fazla bilgi için [bkz. Nasıl kullanılır: Sütun değişiklikleri sırasında verileri doğrulama.](validate-data-in-datasets.md)

- Veri satırın tamamı değişirken değerleri kontrol etmek için uygulamaya özgü kendi doğrulamanızı oluşturarak. Daha fazla bilgi için [bkz. Nasıl kullanılır: Satır değişiklikleri sırasında verileri doğrulama.](validate-data-in-datasets.md)

- Anahtarlar, benzersiz kısıtlamalar ve benzeri, veri kümesi gerçek şema tanımının bir parçası olarak oluşturarak.

- Nesnesinin özelliklerini <xref:System.Data.DataColumn> ayar olarak , ve gibi <xref:System.Data.DataColumn.MaxLength%2A> <xref:System.Data.DataColumn.AllowDBNull%2A> <xref:System.Data.DataColumn.Unique%2A> .

Kayıtta bir değişiklik <xref:System.Data.DataTable> oluştuğunda nesnesi tarafından birkaç olay ortaya çıkar:

- ve <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> olayları, her bir sütunda yapılan her değişiklik sırasında ve sonrasında ortaya çıkar. Olay, <xref:System.Data.DataTable.ColumnChanging> belirli sütunlarda yapılan değişiklikleri doğrulamak istediğiniz zaman kullanışlıdır. Önerilen değişiklikle ilgili bilgiler, olayıyla birlikte bağımsız değişken olarak geçirildi.
- ve <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> olayları, satırdaki herhangi bir değişiklik sırasında ve sonrasında ortaya çıkar. Olay <xref:System.Data.DataTable.RowChanging> daha genel bir olaydır. Bu, satırın herhangi bir yerde değişiklik olduğunu gösterir, ancak hangi sütunun değiştiğini bilmiyor olur.

Varsayılan olarak, her sütunda yapılan her değişiklik dört olaya neden olur. Birincisi, değiştirilen <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> belirli bir sütuna yönelik ve olaylarıdır. Sonrakiler ve <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> olaylarıdır. Satırda birden çok değişiklik yapılıyorsa, her değişiklik için olaylar ortaya çıkar.

> [!NOTE]
> Veri satırı yöntemi, <xref:System.Data.DataRow.BeginEdit%2A> her sütun değiştikten <xref:System.Data.DataTable.RowChanging> sonra ve <xref:System.Data.DataTable.RowChanged> olaylarını kapatıyor. Bu durumda, yöntemi çağrılana kadar ve <xref:System.Data.DataRow.EndEdit%2A> olayları yalnızca bir kez <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> yükseltene kadar olay yükseltlanmaz. Daha fazla bilgi için [bkz. Veri kümesi doldururken kısıtlamaları kapatma.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

Seçtiğiniz olay, doğrulamanın ne kadar ayrıntılı olması istediğinize bağlıdır. Bir sütunda değişiklik olduğunda bir hatayı hemen yakalamanız önemli ise, olayı kullanarak derleme doğrulaması <xref:System.Data.DataTable.ColumnChanging> yapın. Aksi takdirde, <xref:System.Data.DataTable.RowChanging> aynı anda birkaç hatanın yakalanmasıyla sonuçlanabilecek olayı kullanın. Ayrıca, verileriniz bir sütunun değerinin başka bir sütunun içeriğine göre doğrulanması için yapılandırılmışsa etkinlik sırasında doğrulamanızı <xref:System.Data.DataTable.RowChanging> gerçekleştirin.

Kayıtlar güncelleştirildiğinde, nesne değişiklikler meydana geldiğinde ve değişiklikler yapıldıktan sonra yanıt <xref:System.Data.DataTable> verilebilecek olayları oluşturur.

Uygulamanız türü türü türü kesin olarak doğru olan bir veri kümesi kullanıyorsa, kesin olarak türü kesin olarak yazıldı olay işleyicileri oluşturabilirsiniz. Bu, işleyiciler oluşturarak dört ek türe neden olan olay ekler: `dataTableNameRowChanging` , `dataTableNameRowChanged` , ve `dataTableNameRowDeleting` `dataTableNameRowDeleted` . Bu tür olay işleyicileri, kodun yaz ve okunmalarını kolaylaştıran tablo sütun adlarını içeren bir bağımsız değişken iletir.

## <a name="data-update-events"></a>Veri güncelleştirme olayları

|Olay|Açıklama|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Sütundaki değer değiştir ediliyor. Olay, önerilen yeni değerle birlikte satırı ve sütunu size iletir.|
|<xref:System.Data.DataTable.ColumnChanged>|Sütundaki değer değiştirilmiştir. Olay, önerilen değerle birlikte satırı ve sütunu size iletir.|
|<xref:System.Data.DataTable.RowChanging>|Bir nesnede yapılan <xref:System.Data.DataRow> değişiklikler, veri kümesine geri işlendi. yöntemini çağırmadıysanız, olay başlatıldıktan hemen sonra her bir <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataTable.RowChanging> sütunda yapılan <xref:System.Data.DataTable.ColumnChanging> her değişiklik için olay yükseltildi. Değişiklik <xref:System.Data.DataRow.BeginEdit%2A> yapmadan önce çağrısı yaptıysanız, <xref:System.Data.DataTable.RowChanging> olay yalnızca yöntemini çağırarak ortaya <xref:System.Data.DataRow.EndEdit%2A> çıkar.<br /><br /> Olay, gerçekleştirilen eylem türünü (değiştirme, ekleme ve diğer) belirten bir değerle birlikte satırı size iletir.|
|<xref:System.Data.DataTable.RowChanged>|Bir satır değiştirildi. Olay, gerçekleştirilen eylem türünü (değiştirme, ekleme ve diğer) belirten bir değerle birlikte satırı size iletir.|
|<xref:System.Data.DataTable.RowDeleting>|Bir satır siliniyor. Olay, satırla birlikte gerçekleştirilecek eylem türünü (silme) belirten bir değer ile birlikte size iletir.|
|<xref:System.Data.DataTable.RowDeleted>|Bir satır silindi. Olay, satırla birlikte gerçekleştirilecek eylem türünü (silme) belirten bir değer ile birlikte size iletir.|

<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> ve <xref:System.Data.DataTable.RowDeleting> olayları güncelleştirme işlemi sırasında ortaya çıkar. Bu olayları verileri doğrulamak veya diğer işlem türlerini gerçekleştirmek için kullanabilirsiniz. Güncelleştirme bu olaylar sırasında devam ediyor olduğundan, güncelleştirmenin bitmelerini önleyen bir özel durum atarak bunu iptal edebilirsiniz.

<xref:System.Data.DataTable.ColumnChanged>ve <xref:System.Data.DataTable.RowChanged> <xref:System.Data.DataTable.RowDeleted> olayları, güncelleştirme başarıyla tamamlandığında ortaya çıkar. Bu olaylar, başarılı bir güncelleştirmeye göre daha fazla işlem yapmak istediğiniz zaman kullanışlıdır.

## <a name="validate-data-during-column-changes"></a>Sütun değişiklikleri sırasında verileri doğrulama

> [!NOTE]
> Bu **Veri Kümesi Tasarımcısı,** doğrulama mantığının bir veri kümesine eklenemedik bir kısmi sınıf oluşturur. Tasarımcı tarafından oluşturulan veri kümesi kısmi sınıftaki herhangi bir kodu silemez veya değiştirmez.

Bir veri sütunundaki değer değişirken olaya yanıt olarak verileri <xref:System.Data.DataTable.ColumnChanging> doğruabilirsiniz. Bu olay, 2004'e yükseltildi ve bu olay geçerli sütun için önerilen değeri içeren bir olay bağımsız değişkeni ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ) iletir. içeriğini temel alarak `e.ProposedValue` şunları sabilirsiniz:

- Hiçbir şey yaparak önerilen değeri kabul etme.

- Sütun değiştiren olay işleyicisinde sütun hatasını ( <xref:System.Data.DataRow.SetColumnError%2A> ) ayarerek önerilen değeri reddedin.

- İsteğe bağlı olarak <xref:System.Windows.Forms.ErrorProvider> kullanıcıya bir hata iletisi görüntülemek için bir denetim kullanın. Daha fazla bilgi için bkz. [ErrorProvider bileşeni.](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)

Doğrulama olay sırasında da <xref:System.Data.DataTable.RowChanging> yapılabilir.

## <a name="validate-data-during-row-changes"></a>Satır değişiklikleri sırasında verileri doğrulama
Doğrulamak istediğiniz her sütunun, uygulama gereksinimlerinizi karşılayacak veriler içerdiğini doğrulamak için kod yazabilirsiniz. Önerilen bir değer kabul edilemezse, sütunu hata içerdiğini belirtecek şekilde ayarerek bunu yapma. Aşağıdaki örneklerde sütun 0 veya daha `Quantity` küçük olduğunda bir sütun hatası ayarlanır. Satır değiştiren olay işleyicileri aşağıdaki örneklere benzemektedir.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Bir satır değişirken verileri doğrulamak için (Visual Basic)

1. veri kümenizi **Veri Kümesi Tasarımcısı.** Daha fazla bilgi için [bkz. Adım Adım: Veri Kümesi Oluşturma Veri Kümesi Tasarımcısı.](walkthrough-creating-a-dataset-with-the-dataset-designer.md)

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem, veri <xref:System.Data.DataTable.RowChanging> kümesinde kısmi <xref:System.Data.DataTable> sınıf dosyasında otomatik olarak olay işleyicisini oluşturur.

    > [!TIP]
    > Satır değiştiren olay işleyicisini oluşturmak için tablo adının sol tarafından çift tıklayın. Tablo adına çift tıklarsanız düzenleyebilirsiniz.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb" id="Snippet3":::

### <a name="to-validate-data-when-a-row-changes-c"></a>Bir satırda değişiklik olduğunda verileri doğrulamak için (C#)

1. veri kümenizi **Veri Kümesi Tasarımcısı.** Daha fazla bilgi için [bkz. Adım adım kılavuz:](walkthrough-creating-a-dataset-with-the-dataset-designer.md)veri kümesi oluşturma Veri Kümesi Tasarımcısı.

2. Doğrulamak istediğiniz tablonun başlık çubuğuna çift tıklayın. Bu eylem için bir kısmi sınıf dosyası <xref:System.Data.DataTable> oluşturur.

    > [!NOTE]
    > Bu **Veri Kümesi Tasarımcısı,** olay için otomatik olarak bir olay işleyicisi <xref:System.Data.DataTable.RowChanging> oluşturmaz. Olayı işlemek için bir yöntem oluşturmanız ve tablonun başlatma yönteminde <xref:System.Data.DataTable.RowChanging> olayı bağacak kodu çalıştırmanızı gerekir.

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
Bir veri tablosundaki her satırın, numaralamadaki değerleri kullanarak bu satırın geçerli durumunu takip <xref:System.Data.DataRow.RowState%2A> etmek için bir özelliği <xref:System.Data.DataRowState> vardır. veya yöntemini çağırarak veri kümesinden veya veri tablosundan `GetChanges` değiştirilen satırları <xref:System.Data.DataSet> <xref:System.Data.DataTable> getirebilirsiniz. `GetChanges`Bir veri kümesinin yöntemini çağırarak, çağrılmadan önce değişikliklerin mevcut olduğunu doğrulayabilirsiniz <xref:System.Data.DataSet.HasChanges%2A> .

> [!NOTE]
> Bir veri kümesine veya veri tablosuna değişiklikler yaptıktan sonra ( <xref:System.Data.DataSet.AcceptChanges%2A> yöntemini çağırarak), `GetChanges` Yöntem hiçbir veri döndürmez. Uygulamanızın değiştirilen satırları işlemesi gerekiyorsa, metodu çağırmadan önce değişiklikleri işlemelidir `AcceptChanges` .

Bir veri kümesi <xref:System.Data.DataSet.GetChanges%2A> veya veri tablosu yöntemini çağırmak, yalnızca değiştirilmiş kayıtları içeren yeni bir veri kümesi veya veri tablosu döndürür. Belirli kayıtları almak istiyorsanız — Örneğin, yalnızca yeni kayıtlar veya yalnızca değiştirilen kayıtlar —, Numaralandırmadaki bir değeri, <xref:System.Data.DataRowState> yönteme parametre olarak geçirebilirsiniz `GetChanges` .

<xref:System.Data.DataRowVersion>Bir satırın farklı sürümlerine erişmek için numaralandırmayı kullanın (örneğin, işlemeden önce bir satırdaki özgün değerler).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Bir veri kümesinden tüm değiştirilen kayıtları almak için

- <xref:System.Data.DataSet.GetChanges%2A>Bir veri kümesinin yöntemini çağırın.

     Aşağıdaki örnek adlı yeni bir veri kümesi oluşturur `changedRecords` ve bunu adlı başka bir veri kümesinden değiştirilen tüm kayıtlarla doldurur `dataSet1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet14":::

### <a name="to-get-all-changed-records-from-a-data-table"></a>Bir veri tablosundan değiştirilen tüm kayıtları almak için

- <xref:System.Data.DataTable.GetChanges%2A>DataTable metodunu çağırın.

     Aşağıdaki örnek adlı yeni bir veri tablosu oluşturur `changedRecordsTable` ve adlı başka bir veri tablosundan değiştirilen tüm kayıtlarla doldurur `dataTable1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet15":::

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Belirli bir satır durumuna sahip tüm kayıtları almak için

- Bir veri `GetChanges` kümesinin veya veri tablosunun yöntemini çağırın ve bir <xref:System.Data.DataRowState> sabit listesi değerini bağımsız değişken olarak geçirin.

     Aşağıdaki örnekte, adlı yeni bir veri kümesinin nasıl oluşturulacağı `addedRecords` ve yalnızca veri kümesine eklenen kayıtlarla doldurulması gösterilmektedir `dataSet1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet16":::

     Aşağıdaki örnek, son olarak tabloya eklenen tüm kayıtların nasıl geri alınacağını gösterir `Customers` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet17":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet17":::

## <a name="access-the-original-version-of-a-datarow"></a>DataRow 'ın orijinal sürümüne erişin
Veri satırlarında değişiklik yapıldığında veri kümesi, satırın hem özgün ( <xref:System.Data.DataRowVersion.Original> ) hem de yeni ( <xref:System.Data.DataRowVersion.Current> ) sürümlerini korur. Örneğin, yöntemini çağırmadan önce `AcceptChanges` , uygulamanız bir kaydın farklı sürümlerine erişebilir ( <xref:System.Data.DataRowVersion> numaralandırmada tanımlandığı gibi) ve değişiklikleri buna göre işleyebilir.

> [!NOTE]
> Bir satırın farklı sürümleri, yalnızca düzenlendikten sonra ve `AcceptChanges` yöntemi çağrılmadan önce bulunur. `AcceptChanges`Yöntem çağrıldıktan sonra, geçerli ve orijinal sürümler aynıdır.

<xref:System.Data.DataRowVersion>Değeri sütun dizini (veya bir dize olarak sütun adı) ile birlikte geçirmek, bu sütunun belirli satır sürümünden değeri döndürür. Değiştirilen sütun, ve olayları sırasında tanımlanır <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> . Bu, doğrulama amacıyla farklı satır sürümlerini incelemek için iyi bir zamandır. Ancak, kısıtlamaları geçici olarak askıya aldıysanız, bu olaylar oluşturulmaz ve hangi sütunların değiştiğini programlı bir şekilde belirlemeniz gerekir. Bunu, <xref:System.Data.DataTable.Columns%2A> koleksiyonu kullanarak ve farklı değerleri karşılaştırarak yapabilirsiniz <xref:System.Data.DataRowVersion> .

### <a name="to-get-the-original-version-of-a-record"></a>Bir kaydın orijinal sürümünü almak için

- Döndürmek istediğiniz satırın değerini geçirerek bir sütunun değerine erişin <xref:System.Data.DataRowVersion> .

     Aşağıdaki örnek, <xref:System.Data.DataRowVersion> içindeki bir alanın orijinal değerini almak için bir değerinin nasıl kullanılacağını gösterir `CompanyName` <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet21":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet21":::

## <a name="access-the-current-version-of-a-datarow"></a>Bir DataRow 'ın geçerli sürümüne erişin

### <a name="to-get-the-current-version-of-a-record"></a>Bir kaydın geçerli sürümünü almak için

- Bir sütunun değerine erişin ve sonra dizine döndürmek istediğiniz bir satır sürümünü gösteren bir parametre ekleyin.

     Aşağıdaki örnek, <xref:System.Data.DataRowVersion> içindeki bir alanın geçerli değerini almak için bir değerinin nasıl kullanılacağını gösterir `CompanyName` <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet22":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [nasıl yapılır: Windows Forms DataGridView denetimindeki verileri doğrulama](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [nasıl yapılır: Windows Forms ErrorProvider bileşeni ile form doğrulama için hata simgeleri görüntüleme](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
