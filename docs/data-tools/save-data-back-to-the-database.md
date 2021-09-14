---
title: Verileri yeniden veritabanına kaydetme
description: Verileri veritabanına geri kaydetmek için DataSet araçlarını kullanın. Veri kümesi, değiştirildiğinde veritabanına geri kaydedilecek verilerin bellek içinde bir kopyasıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 36140f928450cbb8ef498ae1edb490b4c2a32eae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631227"
---
# <a name="save-data-back-to-the-database"></a>Verileri yeniden veritabanına kaydetme

Veri kümesi, verilerin bellek içinde bir kopyasıdır. Bu verileri değiştirirsiniz, bu değişiklikleri veritabanına geri kaydetmek iyi bir uygulamadır. Bunu üç farklı şekilde yapabilirsiniz:

- `Update`TableAdapter'ın yöntemlerinden birini çağırarak

- `DBDirect`TableAdapter'ın yöntemlerinden birini çağırarak

- TableAdapterManager üzerinde yöntemini çağırarak Visual Studio kümesi veri kümesinde diğer tablolarla ilgili tablolar içerdiğinde sizin `UpdateAll` için oluşturur

Veri kümesi tablolarını form veya XAML Windows veri bağlama sayfasındaki denetimlere bağlarken, veri bağlama mimarisi tüm çalışmaları sizin için yapar.

TableAdapter'ları biliyorsanız doğrudan şu konulardan birini atlayın:

|Konu|Description|
|-----------|-----------------|
|[Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)|TableAdapters veya Command nesnelerini kullanarak güncelleştirme ve ekleme gerçekleştirme|
|[TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)|TableAdapter'lar ile güncelleştirme gerçekleştirme|
|[Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)|İki veya daha fazla ilişkili tabloyla bir veri kümesinden güncelleştirme gerçekleştirme|
|[Bir eşzamanlılık özel durumunu işleme](../data-tools/handle-a-concurrency-exception.md)|İki kullanıcı aynı anda veritabanındaki aynı verileri değiştirmeye çalışırken özel durumları işleme|
|[Nasıl kullanılır: İşlem kullanarak veri kaydetme](../data-tools/save-data-by-using-a-transaction.md)|Sistemi kullanarak bir işlemde veri kaydetme. İşlemler ad alanı ve TransactionScope nesnesi|
|[İşleme veri kaydetme](../data-tools/save-data-in-a-transaction.md)|İşlem içindeki bir veritabanına Windows göstermek için bir Windows Forms uygulaması oluşturan izlenecek yol|
|[Bir veritabanına (birden çok tablo) veri kaydetme](../data-tools/save-data-to-a-database-multiple-tables.md)|Kayıtları düzenleme ve birden çok tablodaki değişiklikleri veritabanına geri kaydetme|
|[Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect yöntemi kullanarak veri kümesinde yer alan bir nesneden veritabanına veri geçişi|
|[TableAdapter DBDirect metotlarıyla veri kaydetme](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Doğrudan veritabanına sorgu göndermek için TableAdapter'SQL kullanma|
|[Veri kümelerini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md)|Veri kümelerini XML belgesine kaydetme|

## <a name="two-stage-updates"></a>İki aşamalı güncelleştirmeler

Veri kaynağını güncelleştirmek iki adımlı bir işlemdir. İlk adım, veri kümesini yeni kayıtlar, değiştirilen kayıtlar veya silinen kayıtlar ile güncelleştirmektir. Uygulamanız bu değişiklikleri hiçbir zaman veri kaynağına geri göndermezse, güncelleştirmeyi tamamladınız demektir.

Değişiklikleri veritabanına geri gönderirsiniz, ikinci bir adım gerekir. Veriye bağlı denetimler kullanıyorsanız, veri kümesi doldurmak için kullanılan `Update` TableAdapter'ın (veya veri bağdaştırıcısının) yöntemini el ile çağırmanız gerekir. Ancak, örneğin, verileri bir veri kaynağından diğerine taşımak veya birden çok veri kaynağını güncelleştirmek için farklı bağdaştırıcılar da kullanabilirsiniz. Veri bağlamayı kullanıyorsanız ve ilgili tablolar için değişiklikleri kaydedıyorsanız, otomatik olarak oluşturulan sınıfın bir değişkenini el ile örneği oluşturmalı ve ardından `TableAdapterManager` yöntemini `UpdateAll` çağırmalısınız.

![Veri kümesi güncelleştirmelerinin kavramsal diyagramı](../data-tools/media/vbdatasetupdates.gif)

Veri kümesi, satır koleksiyonları içeren tablo koleksiyonları içerir. Temel alınan bir veri kaynağını daha sonra güncelleştirmeyi planlasanız, satır eklerken veya çıkarırken `DataTable.DataRowCollection` özelliğinde yöntemlerini kullanmalıdır. Bu yöntemler, veri kaynağını güncelleştirmek için gereken değişiklik izleme işlemini gerçekleştirmektedir. Satırlar `RemoveAt` özelliği üzerinde koleksiyonu çağırsanız, silme işlemi veritabanına geri iletlanmaz.

## <a name="merge-datasets"></a>Veri kümelerini birleştirme

Bir veri kümesiyle başka bir veri kümesi *birleştirerek veri kümesi* içeriğini güncelleştirebilirsiniz. Bu, bir kaynak veri kümesi *içeriğini* çağıran veri kümesine (hedef veri kümesi olarak adlandırılır) *kopyalamayı* içerir. Veri kümelerini birleştirin, kaynak veri kümesinde yeni kayıtlar hedef veri kümesine eklenir. Ayrıca, kaynak veri kümesinde hedef veri kümesine ek sütunlar eklenir. Veri kümelerini birleştirme, yerel bir veri kümeye sahip olur ve başka bir uygulamadan ikinci bir veri kümesi elde ediyor olur. Ayrıca, XML web hizmeti gibi bir bileşenden ikinci bir veri kümesi elde edersiniz veya birden çok veri kümesinden verileri tümleştirin.

Veri kümelerini birleştirerek, yönteme hedef veri kümesinde var olan değişiklikleri koruyıp korumay olmadığını söyleyen bir Boole bağımsız değişkeni ( `preserveChanges` ) <xref:System.Data.DataSet.Merge%2A> geçebilirsiniz. Veri kümelerinin birden çok kaydın sürümü olduğundan, kayıtların birden fazla sürümünün birleştirilecek olduğunu unutmayın. Aşağıdaki tabloda, iki veri kümesinde bir kaydın nasıl birleştir olduğu gösterir:

|Datarowversion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James Wilson|James C. Wilson|
|Geçerli|Jim Wilson|James C. Wilson|

Önceki <xref:System.Data.DataSet.Merge%2A> tabloda yönteminin çağrılarak `preserveChanges=false targetDataset.Merge(sourceDataset)` aşağıdaki verilerle sonuçlandı:

|Datarowversion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James C. Wilson|James C. Wilson|
|Geçerli|James C. Wilson|James C. Wilson|

yönteminin <xref:System.Data.DataSet.Merge%2A> `preserveChanges = true targetDataset.Merge(sourceDataset, true)` çağrılarak aşağıdaki verilerle sonuçlandı:

|Datarowversion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James C. Wilson|James C. Wilson|
|Geçerli|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Senaryoda, yöntem hedef veri kümesinde bir kayıtta çağrılsa, kaynak veri `preserveChanges = true` <xref:System.Data.DataSet.RejectChanges%2A> kümesinden  özgün verilere geri döner. Bu, özgün veri kaynağını hedef veri kümesiyle güncelleştirmeye çalışmanız, güncelleştirilen özgün satırın bulunamay olabileceği anlamına gelir. Eşzamanlılık ihlalini önlemek için başka bir veri kümesine veri kaynağından güncelleştirilmiş kayıtlar doldurarak ve ardından birleştirme gerçekleştirerek eşzamanlılık ihlalini önleyebilirsiniz. (Veri kümesi doldurulduktan sonra başka bir kullanıcı veri kaynağında bir kaydı değiştiren bir eşzamanlılık ihlali oluşur.)

## <a name="update-constraints"></a>Kısıtlamaları güncelleştirme

Mevcut veri satırlarında değişiklik yapmak için tek tek sütunlara veri ekleyin veya güncelleştirin. Veri kümesinde kısıtlamalar (yabancı anahtarlar veya null değer verilemez kısıtlamalar gibi) varsa, siz güncelleştiren kayıt geçici olarak hata durumda olabilir. Başka bir ifadeyle, bir sütunu güncelleştirmeyi bitirdikten sonra ancak bir sonrakine varmadan önce hata durumu olabilir.

Erken kısıtlama ihlallerini önlemek için güncelleştirme kısıtlamalarını geçici olarak askıya alın. Bu iki amaca hizmet ediyor:

- Bir sütunu güncelleştirmeyi bitirdikten sonra ancak başka bir sütunu güncelleştirmeye başlamadıktan sonra hatanın atılan bir hataya neden olması önleniyor.

- Belirli güncelleştirme olaylarının (genellikle doğrulama için kullanılan olaylar) güncelleştirmesi engel olur.

> [!NOTE]
> Windows Forms'da, datagrid'de yerleşik olarak yer alan veri bağlama mimarisi, odak bir satırdan dışarı gelene kadar kısıtlama denetimini askıya alır ve , veya yöntemlerini açıkça çağırmanız <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> <xref:System.Data.DataRow.CancelEdit%2A> gerekmez.

<xref:System.Data.DataSet.Merge%2A>Yöntem bir veri kümesi üzerinde çağrıldığında kısıtlamalar otomatik olarak devre dışıdır. Birleştirme tamamlandığında, veri kümesinde etkinleştirilemez bir kısıtlama varsa, bir <xref:System.Data.ConstraintException> oluşturulur. Bu durumda, <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği olarak ayarlanır `false,` ve özelliği öğesine sıfırlamadan önce tüm kısıtlama ihlalleri çözümlenmelidir <xref:System.Data.DataSet.EnforceConstraints%2A> `true` .

Bir güncelleştirmeyi tamamladıktan sonra, ayrıca güncelleştirme olaylarını yeniden etkinleştiren ve bunları başlatan kısıtlama denetimini yeniden etkinleştirebilirsiniz.

Olayları askıya alma hakkında daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

## <a name="dataset-update-errors"></a>Veri kümesi güncelleştirme hataları

Bir veri kümesindeki bir kaydı güncelleştirdiğinizde bir hata olasılığı vardır. Örneğin, yanlışlıkla yanlış türde verileri veya çok uzun verileri veya başka bir bütünlük sorunu olan verileri istemeden yazabilirsiniz. Ya da, bir güncelleştirme olayının herhangi bir aşamasında özel hatalar oluşturabilen uygulamaya özgü doğrulama denetimlerine sahip olabilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Değişikliklerle ilgili bilgileri koruma

Bir veri kümesindeki değişikliklerle ilgili bilgiler iki şekilde tutulur: değiştirildikleri ( <xref:System.Data.DataRow.RowState%2A> ) ve bir kaydın birden çok kopyasını tutarak () ve bir kaydın birden çok kopyasını tutarak satırlara bayrak koyarak <xref:System.Data.DataRowVersion> . Süreçler, bu bilgileri kullanarak veri kümesinde nelerin değiştiğini belirleyebilir ve uygun güncelleştirmeleri veri kaynağına gönderebilir.

### <a name="rowstate-property"></a>RowState özelliği

<xref:System.Data.DataRow.RowState%2A>Bir nesnenin özelliği, <xref:System.Data.DataRow> belirli bir veri satırının durumu hakkında bilgi sağlayan bir değerdir.

Aşağıdaki tabloda, sabit listesinin olası değerlerinin ayrıntıları verilmiştir <xref:System.Data.DataRowState> :

|DataRowState değeri|Description|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Satır, öğesine bir öğe olarak eklenmiştir <xref:System.Data.DataRowCollection> . (Son yöntem çağrıldığında mevcut olmadığından, bu durumdaki bir satır karşılık gelen orijinal bir sürüme sahip değildir <xref:System.Data.DataRow.AcceptChanges%2A> ).|
|<xref:System.Data.DataRowState.Deleted>|Satır, bir nesnesi kullanılarak silindi <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> .|
|<xref:System.Data.DataRowState.Detached>|Satır oluşturuldu ancak hiç bir parçası değil <xref:System.Data.DataRowCollection> . Bir <xref:System.Data.DataRow> nesne, oluşturulduktan hemen sonra, bir koleksiyona eklendikten önce ve bir koleksiyondan kaldırıldıktan sonra bu durumda olur.|
|<xref:System.Data.DataRowState.Modified>|Satırdaki bir sütun değeri bir şekilde değiştirildi.|
|<xref:System.Data.DataRowState.Unchanged>|Satır <xref:System.Data.DataRow.AcceptChanges%2A> son çağrılmasından bu yana değiştirilmedi.|

### <a name="datarowversion-enumeration"></a>DataRowVersion numaralandırması

Veri kümeleri kayıtların birden çok sürümünü tutar. <xref:System.Data.DataRowVersion>Alanlar, bir <xref:System.Data.DataRow> <xref:System.Data.DataRow.Item%2A> veya <xref:System.Data.DataRow.GetChildRows%2A> nesnesinin yöntemi kullanılarak öğesinde bulunan değer alınırken kullanılır <xref:System.Data.DataRow> .

Aşağıdaki tabloda, sabit listesinin olası değerlerinin ayrıntıları verilmiştir <xref:System.Data.DataRowVersion> :

|DataRowVersion değeri|Description|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Bir kaydın geçerli sürümü, en son çağrılmasından bu yana kayıtta gerçekleştirilen tüm değişiklikleri içerir <xref:System.Data.DataRow.AcceptChanges%2A> . Satır silinmişse, geçerli sürüm yoktur.|
|<xref:System.Data.DataRowVersion.Default>|Bir kaydın veri kümesi şeması veya veri kaynağı tarafından tanımlanan varsayılan değeri.|
|<xref:System.Data.DataRowVersion.Original>|Bir kaydın orijinal sürümü, veri kümesinde son değişiklikler işlendiği için kaydın bir kopyasıdır. Pratik koşullarda, bu genellikle bir veri kaynağından okunan bir kaydın sürümüdür.|
|<xref:System.Data.DataRowVersion.Proposed>|Bir güncelleştirmenin ortasındayken geçici olarak kullanılabilir olan bir kaydın önerilen sürümü; Yani, <xref:System.Data.DataRow.BeginEdit%2A> yöntemi ve <xref:System.Data.DataRow.EndEdit%2A> yöntemi ile metodu arasında. Genellikle, gibi bir olay için bir işleyicide bir kaydın önerilen sürümüne erişirsiniz <xref:System.Data.DataTable.RowChanging> . Yöntemi çağırmak <xref:System.Data.DataRow.CancelEdit%2A> değişiklikleri tersine çevirir ve veri satırının önerilen sürümünü siler.|

Özgün ve güncel sürümler, güncelleştirme bilgileri bir veri kaynağına aktarıldığında yararlı olur. Genellikle, veri kaynağına bir güncelleştirme gönderildiğinde, veritabanının yeni bilgileri bir kaydın geçerli sürümüdür. Özgün sürümden alınan bilgiler güncelleştirilecek kaydı bulmak için kullanılır.

Örneğin, bir kaydın birincil anahtarının değiştirildiği bir durumda, değişiklikleri güncelleştirmek için veri kaynağında doğru kaydı bulmanız için bir yol gerekir. Özgün sürüm yoksa, kayıt büyük olasılıkla veri kaynağına eklenebilir, bu da yalnızca fazladan istenmeyen bir kayıtta değil, hatalı ve güncel olmayan bir kayıtta olur. Eşzamanlılık denetiminde iki sürüm de kullanılır. Kayıt kümesine yüklendikten sonra kaydın değişip değişmediğini öğrenmek için özgün sürümü veri kaynağındaki bir kayıtla karşılaştırarak karşılaştırabilirsiniz.

Önerilen sürüm, değişiklikleri aslında veri kümesine kaydetmeden önce doğrulama gerçekleştirmeniz gerektiğinde faydalıdır.

Kayıtlar değişmiş olsa bile, bu satırın her zaman orijinal veya güncel sürümü yoktur. Tabloya yeni bir satır eklediğinizde, özgün sürüm yoktur, yalnızca geçerli bir sürümdür. Benzer şekilde, tablonun yöntemini çağırarak bir satırı silerseniz `Delete` , orijinal bir sürüm vardır ancak geçerli sürüm yoktur.

Bir veri satırının metodunu sorgulayarak bir kaydın belirli bir sürümünün mevcut olup olmadığını görmek için test edebilirsiniz <xref:System.Data.DataRow.HasVersion%2A> . Bir <xref:System.Data.DataRowVersion> sütunun değerini istediğinizde bir numaralandırma değerini isteğe bağlı bağımsız değişken olarak geçirerek, bir kaydın her iki sürümüne erişebilirsiniz.

## <a name="get-changed-records"></a>Değiştirilen kayıtları al

Bir veri kümesindeki her kaydı güncelleştirmeme yaygın bir uygulamadır. örneğin, bir kullanıcı <xref:System.Windows.Forms.DataGridView> birçok kayıt görüntüleyen bir Windows Forms denetimiyle çalışıyor olabilir. Ancak, Kullanıcı yalnızca birkaç kaydı güncelleştirebilir, bir tane silebilir ve yeni bir tane ekleyebilir. Veri kümeleri ve veri tabloları `GetChanges` yalnızca değiştirilen satırları döndürmek için bir Yöntem () sağlar.

`GetChanges`Veri tablosunun () ya da veri kümesinin () yöntemini kullanarak değiştirilen kayıtların alt kümelerini oluşturabilirsiniz <xref:System.Data.DataTable.GetChanges%2A> <xref:System.Data.DataSet.GetChanges%2A> . Veri tablosu için yöntemini çağırırsanız, yalnızca değiştirilen kayıtlarla tablonun bir kopyasını döndürür. Benzer şekilde, yöntemi veri kümesinde çağırırsanız, içinde yalnızca değiştirilmiş kayıtları olan yeni bir veri kümesi alırsınız.

`GetChanges` tek başına değiştirilen tüm kayıtları döndürür. Buna karşılık, istenen <xref:System.Data.DataRowState> bir parametre olarak yöntemine bir parametre olarak geçirerek `GetChanges` , hangi değiştirilen kayıtların hangi alt kümesini istediğinizi belirtebilirsiniz: yeni eklenen kayıtlar, silinmek üzere işaretlenmiş kayıtlar, ya da değiştirilen kayıtlar.

Değiştirilen kayıtların bir alt kümesini almak, kayıtları işlemek için başka bir bileşene göndermek istediğinizde faydalıdır. Veri kümesinin tamamını göndermek yerine, yalnızca bileşenin ihtiyaç duyacağı kayıtları alarak diğer bileşenle iletişim yükünü azaltabilirsiniz.

## <a name="commit-changes-in-the-dataset"></a>Veri kümesindeki değişiklikleri Yürüt

Veri kümesinde değişiklik yapıldıkça, <xref:System.Data.DataRow.RowState%2A> değiştirilen satırların özelliği ayarlanır. Kayıtların orijinal ve geçerli sürümleri oluşturulur, tutulur ve özelliği tarafından kullanılabilir hale getirilir <xref:System.Data.DataRowView.RowVersion%2A> . Bu değiştirilen satırların özelliklerinde depolanan meta veriler, doğru güncelleştirmelerin veri kaynağına gönderilmesi için gereklidir.

Değişiklikler veri kaynağının geçerli durumunu yansıttığından, bu bilgileri artık sürdürmenize gerek kalmaz. Genellikle, veri kümesi ve kaynağı eşitlenmiş olduğunda iki zaman vardır:

- Verileri veri kümesine yükledikten hemen sonra (örneğin, kaynaktan veri okurken).

- Değişiklikleri veri kaynağına gönderdikten sonra (daha önce değil, değişiklikleri veritabanına göndermek için gereken değişiklik bilgilerini kaybedeceğinizi).

Yöntemi çağırarak, bekleyen değişiklikleri veri kümesine kaydedebilirsiniz <xref:System.Data.DataSet.AcceptChanges%2A> . Genellikle, <xref:System.Data.DataSet.AcceptChanges%2A> aşağıdaki saatlerde çağrılır:

- Veri kümesini yükledikten sonra. Bir TableAdapter metodunu çağırarak bir veri kümesi yüklerseniz `Fill` , bağdaştırıcı sizin için değişiklikleri otomatik olarak kaydeder. Ancak, başka bir veri kümesini içine birleştirerek bir veri kümesini yüklerseniz, değişiklikleri el ile yürütmeniz gerekir.

    > [!NOTE]
    > Bağdaştırıcının özelliğini olarak ayarlayarak, yöntemi çağırdığınızda bağdaştırıcının otomatik olarak değişiklikleri almasını engelleyebilirsiniz `Fill` `AcceptChangesDuringFill` `false` . Olarak ayarlanırsa `false` , <xref:System.Data.DataRow.RowState%2A> Fill sırasında eklenen her satır için olarak ayarlanır <xref:System.Data.DataRowState.Added> .

- Veri kümesi değişikliklerini bir XML Web hizmeti gibi başka bir işleme gönderdikten sonra.

    > [!CAUTION]
    > Değişikliği bu şekilde yürütmek, değişiklik bilgilerini siler. Uygulamanızın veri kümesinde hangi değişikliklerin yapıldığını bilmesini gerektiren işlemleri gerçekleştirmeyi bitirene kadar değişiklikleri yürütmeyin.

Bu yöntem şunları gerçekleştirir:

- <xref:System.Data.DataRowVersion.Current>Bir kaydın sürümünü <xref:System.Data.DataRowVersion.Original> sürümüne yazar ve özgün sürümün üzerine yazar.

- Özelliğin ayarlandığı tüm satırları kaldırır <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> .

- <xref:System.Data.DataRow.RowState%2A>Bir kaydın özelliğini olarak ayarlar <xref:System.Data.DataRowState.Unchanged> .

<xref:System.Data.DataSet.AcceptChanges%2A>Yöntemi üç düzeyde kullanılabilir. <xref:System.Data.DataRow>Yalnızca söz konusu satır için değişiklikleri yürütmeleri için bir nesne üzerinde çağırabilirsiniz. Ayrıca, <xref:System.Data.DataTable> bir tablodaki tüm satırları yürütmek için bir nesne üzerinde çağırabilirsiniz. Son olarak, <xref:System.Data.DataSet> veri kümesinin tüm tablolarındaki tüm kayıtlarda bekleyen tüm değişiklikleri kaydetmek için nesneyi nesne üzerinde çağırabilirsiniz.

Aşağıdaki tabloda, yöntemin hangi nesneye çağrıldığı üzerinde hangi değişikliklerin yürütüldüğü açıklanmaktadır:

|Yöntem|Sonuç|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler yalnızca belirli bir satıra kaydedilir.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, belirli bir tablodaki tüm satırlara kaydedilir.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, veri kümesinin tüm tablolarındaki tüm satırlara kaydedilir.|

> [!NOTE]
> Bir TableAdapter metodunu çağırarak bir veri kümesi yüklüyorsanız `Fill` , değişiklikleri açıkça kabul etmeniz gerekmez. Varsayılan olarak yöntemi, `Fill` `AcceptChanges` veri tablosunu doldurmayı tamamladıktan sonra yöntemini çağırır.

İlgili bir yöntem, <xref:System.Data.DataSet.RejectChanges%2A> <xref:System.Data.DataRowVersion.Original> sürümü yeniden kayıt sürümüne kopyalayarak değişikliklerin etkisini geri alır <xref:System.Data.DataRowVersion.Current> . Ayrıca, <xref:System.Data.DataRow.RowState%2A> her kaydın öğesini öğesine geri ayarlar <xref:System.Data.DataRowState.Unchanged> .

## <a name="data-validation"></a>Veri doğrulama

Uygulamanıza verilerin geçirilen işlemlerin gereksinimlerini karşılar olduğunu doğrulamak için genellikle doğrulama eklemeniz gerekir. Bu, bir kullanıcının formda girişinin doğru olup olmadığını denetlemeyi, başka bir uygulama tarafından uygulamanıza gönderilen verileri doğrulamayı veya hatta bileşeninizin içinde hesaplanan bilgilerin veri kaynağı ve uygulama gereksinimlerinizin kısıtlamalarına uygun olup olmadığını denetlemeyi de içerir.

Verileri çeşitli yollarla doğruleyebilirsiniz:

- İş katmanında, verileri doğrulamak için uygulamanıza kod ekleyerek. Veri kümesi, bunu yapmak için tek bir yerdir. Veri kümesi, arka uç doğrulamasının bazı avantajlarını sağlar; örneğin sütun ve satır değerleri değişti olarak değişiklikleri doğrulama olanağı. Daha fazla bilgi için [bkz. Veri kümelerini verileri doğrulama.](../data-tools/validate-data-in-datasets.md)

- Sunum katmanında formlara doğrulama ekleyerek. Daha fazla bilgi için [bkz. Windows Forms'ta kullanıcı girişi doğrulaması.](/dotnet/framework/winforms/user-input-validation-in-windows-forms)

- Veri arka ucunda, verileri veri kaynağına (örneğin, veritabanına) göndererek ve verileri kabul etme veya reddetmeye izin vererek. Verileri doğrulamak ve hata bilgileri sağlamak için gelişmiş olanaklara sahip bir veritabanıyla çalışıyorsanız, verileri nereden geldiğine bakarak doğrulayabilirsiniz çünkü bu pratik bir yaklaşım olabilir. Ancak, bu yaklaşım uygulamaya özgü doğrulama gereksinimlerini karşılamaz. Buna ek olarak, veri kaynağının doğrulanması, uygulamanın arka uç tarafından ortaya çıkan doğrulama hatalarının çözümlerini kolaylaştırma yöntemine bağlı olarak veri kaynağına çok sayıda gidiş dönüşle sonuçlanabilir.

   > [!IMPORTANT]
   > olarak ayarlanmış bir özellik ile veri komutlarını kullanırken, veritabanınıza geçirmeden önce istemciden <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> gönderilen bilgileri dikkatle kontrol <xref:System.Data.CommandType.Text> edin. Kötü amaçlı kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar SQL amacıyla değiştirilmiş veya ek veri deyimleri göndermeye (ekleme) deneyebilir. Kullanıcı girişini bir veritabanına aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Mümkün olduğunda her zaman parametreli sorgular veya saklı yordamlar kullanmak en iyi yöntemdir.

## <a name="transmit-updates-to-the-data-source"></a>Güncelleştirmeleri veri kaynağına iletme

Bir veri kümesinde değişiklikler yapıldıktan sonra, değişiklikleri bir veri kaynağına iletebilirsiniz. En yaygın olarak bunu bir `Update` TableAdapter yöntemini (veya veri bağdaştırıcısı) çağırarak yaparsınız. yöntemi bir veri tablosunda her kayıtta döngüye alır, gerekli güncelleştirme türünü (güncelleştirme, ekleme veya silme) belirler ve varsa uygun komutu çalıştırır.

Güncelleştirmelerin nasıl yapıldıklarının bir çizimi olarak, uygulamanın tek bir veri tablosu içeren bir veri kümesi kullandığını varsayalım. Uygulama veritabanından iki satır getirir. Alma sonrasında bellek içinde veri tablosu şöyle olur:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Uygulamanız Nancy Buchanan'ın durumunu "Preferred" olarak değiştirir. Bu değişikliğin sonucu olarak, bu satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değeri olarak <xref:System.Data.DataRowState.Unchanged> <xref:System.Data.DataRowState.Modified> değişir. İlk satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değeri <xref:System.Data.DataRowState.Unchanged> kalır. Veri tablosu artık şu şekildedir:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Artık uygulamanız, `Update` veri kümelerini veritabanına iletmek için yöntemini çağıran bir yöntemdir. yöntemi, her satırı sırasıyla inceler. İlk satırda yöntemi, SQL deyimini veritabanına iletir çünkü başlangıçta veritabanından getiri olduğundan bu satır değişmemiştir.

Ancak ikinci satırda yöntemi otomatik olarak doğru veri `Update` komutunu çağırır ve bunu veritabanına iletir. SQL deyiminin söz dizimi, temel SQL veri deposu tarafından desteklenen verinin diyalektine bağlıdır. Ancak iletilen ifadenin aşağıdaki genel özellikleri SQL değerdir:

- İletilen SQL deyimi bir UPDATE deyimidir. Özelliğin değeri olduğundan bağdaştırıcı bir UPDATE deyimi <xref:System.Data.DataRow.RowState%2A> kullanmayı <xref:System.Data.DataRowState.Modified> bilir.

- İletilen SQL deyimi, UPDATE deyiminin hedefinin bulunduğu satır olduğunu belirten where yan tümcesini `CustomerID = 'c400'` içerir. SELECT deyiminin bu bölümü hedef tablonun birincil anahtarı olduğundan hedef `CustomerID` satırı diğerlerinden ayırt ediyor. SATıRı tanımlamak için gereken değerlerin değişmesi durumunda WHERE yan tümcesi için bilgiler kaydın özgün sürümünden () `DataRowVersion.Original` türetmiştir.

- İletilen SQL deyimi, değiştirilen sütunların yeni değerlerini ayarlamak için SET yan tümcesini içerir.

   > [!NOTE]
   > TableAdapter'ın özelliği saklı yordamın adına ayarlanmışsa, bağdaştırıcı bir SQL `UpdateCommand` oluşturmaz. Bunun yerine, geçirilen uygun parametrelerle saklı yordamı çağırır.

## <a name="pass-parameters"></a>Parametre geçirme

Parametreleri genellikle veritabanında güncelleştirilen kayıtların değerlerini geçmek için kullanırsınız. TableAdapter'ın `Update` yöntemi update deyimini çalıştıracaksa parametre değerlerini doldurması gerekir. Bu değerleri koleksiyondan `Parameters` uygun veri komutu (bu durumda `UpdateCommand` TableAdapter'daki nesnesi) için alır.

Veri bağdaştırıcısı oluşturmak için Visual Studio araçları kullandıysanız, nesnesi deyiminde her parametre yer tutucusucusunu `UpdateCommand` karşılık gelen bir parametre koleksiyonu içerir.

Her <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> parametrenin özelliği, veri tablosunda bir sütuna gösterir. Örneğin, ve parametrelerinin özelliği, veri tablosunda yazar `SourceColumn` `au_id` kimliğini içeren `Original_au_id` sütuna ayarlanır. Bağdaştırıcının yöntemi çalıştır geldiğinde, güncelleştirilen kayıttan author id sütununu okur ve değerleri `Update` deyimine doldurur.

UPDATE deyiminde hem yeni değerleri (kayda yazılanlar) hem de eski değerleri (kaydın veritabanında yer alamayacak şekilde) belirtmeniz gerekir. Bu nedenle her değer için iki parametre vardır: biri SET yan tümcesi için, biri WHERE yan tümcesi için farklı bir parametre. Her iki parametre de güncelleştirilen kayıttan verileri okur ancak parametrenin özelliğine göre sütun değerinin farklı sürümlerini <xref:System.Data.SqlClient.SqlParameter.SourceVersion> elde ediyor. SET yan tümcesi parametresi geçerli sürümü, WHERE yan tümcesi parametresi de özgün sürümü alır.

> [!NOTE]
> Koleksiyonda bulunan değerleri kod içinde de kendiniz de ayarlayabilirsiniz. Bu, genellikle veri bağdaştırıcısının olayı için bir olay `Parameters` işleyicisinde <xref:System.Data.DataTable.RowChanging> bunu yapar.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](validate-data-in-datasets.md)
- [Nasıl kullanılır: Varlık ekleme, değiştirme ve silme (WCF veri hizmetleri)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
