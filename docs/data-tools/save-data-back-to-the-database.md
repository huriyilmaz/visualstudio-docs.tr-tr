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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075066"
---
# <a name="save-data-back-to-the-database"></a>Verileri yeniden veritabanına kaydetme

Veri kümesi, verilerin bellek içinde bir kopyasıdır. Bu verileri değiştirirsiniz, bu değişiklikleri veritabanına geri kaydetmek iyi bir uygulamadır. Bunu üç farklı şekilde yapabilirsiniz:

- `Update`TableAdapter'ın yöntemlerinden birini çağırarak

- `DBDirect`TableAdapter'ın yöntemlerinden birini çağırarak

- TableAdapterManager üzerinde yöntemini çağırarak Visual Studio kümesi veri kümesinde diğer tablolarla ilgili tablolar içerdiğinde sizin için `UpdateAll` oluşturur

Veri kümesi tablolarını form veya XAML sayfasındaki denetimlere Windows, veri bağlama mimarisi tüm çalışmaları sizin için yapar.

TableAdapter'ları biliyorsanız doğrudan şu konulardan birini atlayın:

|Konu|Açıklama|
|-----------|-----------------|
|[Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)|TableAdapters veya Command nesnelerini kullanarak güncelleştirmeler ve eklemeler gerçekleştirme|
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

Değişiklikleri veritabanına geri gönderirsiniz, ikinci bir adım gerekir. Veriye bağlı denetimler kullanıyorsanız, veri kümesi doldurmak için kullanılan `Update` TableAdapter'ın (veya veri bağdaştırıcısının) yöntemini el ile çağırmanız gerekir. Ancak, verileri bir veri kaynağından diğerine taşımak veya birden çok veri kaynağını güncelleştirmek gibi farklı bağdaştırıcılar da kullanabilirsiniz. Veri bağlamayı kullanıyorsanız ve ilgili tablolar için değişiklikleri kaydedıyorsanız, otomatik olarak oluşturulan sınıfın bir değişkenini el ile örneği oluşturmalı ve ardından `TableAdapterManager` yöntemini `UpdateAll` çağırmalısınız.

![Veri kümesi güncelleştirmelerinin kavramsal diyagramı](../data-tools/media/vbdatasetupdates.gif)

Veri kümesi, satır koleksiyonları içeren tablo koleksiyonları içerir. Temel alınan bir veri kaynağını daha sonra güncelleştirmeyi planlasanız, satır eklerken veya çıkarırken `DataTable.DataRowCollection` özelliğinde yöntemlerini kullanmalıdır. Bu yöntemler, veri kaynağını güncelleştirmek için gereken değişiklik izleme işlemini gerçekleştirmektedir. Satırlar `RemoveAt` özelliği üzerinde koleksiyonu çağırsanız, silme işlemi veritabanına geri iletlanmaz.

## <a name="merge-datasets"></a>Veri kümelerini birleştirme

Bir veri kümesi içeriğini başka bir veri *kümesiyle birleştirerek* güncelleştirebilirsiniz. Bu, bir kaynak veri kümesi içeriğini *çağıran* veri kümesine (hedef veri kümesi olarak adlandırılır) *kopyalamayı* içerir. Veri kümelerini birleştirin, kaynak veri kümesinde yeni kayıtlar hedef veri kümesine eklenir. Ayrıca, kaynak veri kümesinde hedef veri kümesine ek sütunlar eklenir. Veri kümelerini birleştirme, yerel bir veri kümeye sahip olduğunda ve başka bir uygulamanın ikinci bir veri kümesine sahip olduğunda yararlıdır. Ayrıca, XML web hizmeti gibi bir bileşenden ikinci bir veri kümesi elde edersiniz veya birden çok veri kümesinden verileri tümleştirin.

Veri kümelerini birleştirerek, yönteme hedef veri kümesinde var olan değişiklikleri koruyıp korumay olmadığını söyleyen bir Boole bağımsız değişkeni ( `preserveChanges` ) <xref:System.Data.DataSet.Merge%2A> geçebilirsiniz. Veri kümelerinin birden çok kaydın sürümü olduğundan, kayıtların birden fazla sürümünün birleştirilecek olduğunu unutmayın. Aşağıdaki tabloda, iki veri kümesinde bir kaydın nasıl birleştirildikleri gösterir:

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
> Senaryoda, yöntem hedef veri kümesinde bir kayıtta çağrılırsa, kaynak veri `preserveChanges = true` <xref:System.Data.DataSet.RejectChanges%2A> kümesinden özgün verilere geri döner.  Bu, özgün veri kaynağını hedef veri kümesiyle güncelleştirmeye çalışmanız, güncelleştirilen özgün satırın bulunamay olabileceği anlamına gelir. Eşzamanlılık ihlalini önlemek için başka bir veri kümesine veri kaynağından güncelleştirilmiş kayıtlar doldurarak ve ardından birleştirme gerçekleştirerek eşzamanlılık ihlalini önleyebilirsiniz. (Veri kümesi doldurulduktan sonra başka bir kullanıcı veri kaynağında bir kaydı değiştiren bir eşzamanlılık ihlali oluşur.)

## <a name="update-constraints"></a>Kısıtlamaları güncelleştirme

Mevcut veri satırlarında değişiklik yapmak için tek tek sütunlara veri ekleyin veya güncelleştirin. Veri kümesinde kısıtlamalar (yabancı anahtarlar veya null değer verilemez kısıtlamalar gibi) varsa, siz güncelleştiren kaydı geçici olarak hata durumuna alabilirsiniz. Başka bir ifadeyle, bir sütunu güncelleştirmeyi bitirdikten sonra ancak bir sonrakine varmadan önce hata durumu olabilir.

Erken kısıtlama ihlallerini önlemek için güncelleştirme kısıtlamalarını geçici olarak askıya alın. Bu iki amaca hizmet ediyor:

- Bir sütunu güncelleştirmeyi bitirdikten sonra ancak başka bir sütunu güncelleştirmeye başlamadıktan sonra hatanın atılan bir hataya neden olması önleniyor.

- Belirli güncelleştirme olaylarının (genellikle doğrulama için kullanılan olaylar) güncelleştirmesi engel olur.

> [!NOTE]
> Windows Forms'da, datagrid'de yerleşik olarak yer alan veri bağlama mimarisi, odak bir satırdan çıkıp , veya yöntemlerini açıkça çağırmanız gerekinceye kadar kısıtlama denetimini askıya <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> <xref:System.Data.DataRow.CancelEdit%2A> alır.

Bir veri kümesinde yöntem <xref:System.Data.DataSet.Merge%2A> çağrıldığında kısıtlamalar otomatik olarak devre dışı bırakılır. Birleştirme tamamlandığında, veri kümesi üzerinde etkinleştirilmemiş kısıtlamalar varsa, <xref:System.Data.ConstraintException> bir atlanır. Bu durumda özelliği <xref:System.Data.DataSet.EnforceConstraints%2A> olarak ayarlanır ve özelliğine sıfırlamadan önce tüm kısıtlama `false,` ihlalleri <xref:System.Data.DataSet.EnforceConstraints%2A> `true` çözümlenir.

Bir güncelleştirmeyi tamamlandıktan sonra kısıtlama denetimlerini yeniden etkinleştirdikten sonra güncelleştirme olaylarını yeniden etkinleştirdikten sonra yeniden etkinleştirin ve bunları yükseltin.

Olayları askıya alma hakkında daha fazla bilgi [için bkz. Veri kümesi doldururken kısıtlamaları kapatma.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

## <a name="dataset-update-errors"></a>Veri kümesi güncelleştirme hataları

Bir veri kümesinde bir kaydı güncelleştirin, hata olasılığı vardır. Örneğin yanlışlıkla bir sütuna yanlış türde veriler veya çok uzun olan veya başka bir bütünlük sorunu olan veriler yazabilirsiniz. Veya bir güncelleştirme olayında herhangi bir aşamada özel hatalara neden olan uygulamaya özgü doğrulama denetimleriniz olabilir. Daha fazla bilgi için [bkz. Veri kümelerini verileri doğrulama.](../data-tools/validate-data-in-datasets.md)

## <a name="maintain-information-about-changes"></a>Değişikliklerle ilgili bilgileri koruma

Bir veri kümesinde yapılan değişikliklerle ilgili bilgiler iki şekilde korunur: değiştiğini belirten satırlar işaret ediyor ( ) ve bir kaydın birden çok kopyası <xref:System.Data.DataRow.RowState%2A> korunarak ( <xref:System.Data.DataRowVersion> ). İşlemler bu bilgileri kullanarak veri kümesinde nelerin değiştiğini belirler ve veri kaynağına uygun güncelleştirmeleri gönderebilir.

### <a name="rowstate-property"></a>RowState özelliği

Bir <xref:System.Data.DataRow.RowState%2A> nesnenin <xref:System.Data.DataRow> özelliği, belirli bir veri satırı durumu hakkında bilgi sağlayan bir değerdir.

Aşağıdaki tabloda, numaralamanın olası <xref:System.Data.DataRowState> değerleri ayrıntılı olarak ve ayrıntılı olarak listelemektedir:

|DataRowState Değeri|Açıklama|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Satır, öğesi olarak bir öğesi olarak <xref:System.Data.DataRowCollection> eklendi. (Bu durumdaki bir satırın özgün sürümüne karşılık gelen bir satır yoktur çünkü son yöntem <xref:System.Data.DataRow.AcceptChanges%2A> çağrıldıklarında mevcut değildir).|
|<xref:System.Data.DataRowState.Deleted>|Satır, nesnesinin <xref:System.Data.DataRow.Delete%2A> kullanılarak <xref:System.Data.DataRow> silindi.|
|<xref:System.Data.DataRowState.Detached>|Satır oluşturuldu ancak herhangi bir parçası <xref:System.Data.DataRowCollection> değil. Bir nesne, oluşturulduktan hemen sonra, bir koleksiyona eklenmeden önce ve bir koleksiyondan kaldırıldıktan hemen <xref:System.Data.DataRow> sonra bu durumdadır.|
|<xref:System.Data.DataRowState.Modified>|Satırdaki bir sütun değeri bir şekilde değişmiştir.|
|<xref:System.Data.DataRowState.Unchanged>|Son çağrılmadan bu <xref:System.Data.DataRow.AcceptChanges%2A> yana satır değişmemiştir.|

### <a name="datarowversion-enumeration"></a>DataRowVersion numaralama

Veri kümeleri, kayıtların birden çok sürümünü sürdürür. alanlar, nesnesinin özelliği veya yöntemi kullanılarak içinde <xref:System.Data.DataRowVersion> <xref:System.Data.DataRow> bulunan değer <xref:System.Data.DataRow.Item%2A> <xref:System.Data.DataRow.GetChildRows%2A> alınırken <xref:System.Data.DataRow> kullanılır.

Aşağıdaki tabloda, numaralamanın olası <xref:System.Data.DataRowVersion> değerleri ayrıntılı olarak ve ayrıntılı olarak listelemektedir:

|DataRowVersion Değeri|Açıklama|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Bir kaydın geçerli sürümü, son çağrıldımdan bu yana kayıtta gerçekleştirilen tüm <xref:System.Data.DataRow.AcceptChanges%2A> değişiklikleri içerir. Satır silinmişse geçerli bir sürüm yoktur.|
|<xref:System.Data.DataRowVersion.Default>|Veri kümesi şeması veya veri kaynağı tarafından tanımlanan varsayılan kayıt değeri.|
|<xref:System.Data.DataRowVersion.Original>|Kaydın özgün sürümü, veri kümesinde en son yapılan değişiklikler olduğu için kaydın bir kopyasıdır. Pratikte bu genellikle bir kaydın veri kaynağından okunan sürümüdür.|
|<xref:System.Data.DataRowVersion.Proposed>|Bir kaydın, bir güncelleştirmenin ortasındayken geçici olarak kullanılabilen önerilen sürümü; diğer bir ifadeyle yöntemini çağıran <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> zaman arasında. Genellikle gibi bir olay için işleyicide bir kaydın önerilen sürümüne <xref:System.Data.DataTable.RowChanging> erişersiniz. yönteminin <xref:System.Data.DataRow.CancelEdit%2A> iptali değişiklikleri tersine çevirebilir ve veri satırı için önerilen sürümü siler.|

Güncelleştirme bilgileri bir veri kaynağına aktarıldı olduğunda özgün ve geçerli sürümler yararlıdır. Genellikle, veri kaynağına bir güncelleştirme gönder geldiğinde, veritabanına ilişkin yeni bilgiler bir kaydın geçerli sürümündedir. Özgün sürümden alınan bilgiler, güncelleştirilen kaydı bulmak için kullanılır.

Örneğin, bir kaydın birincil anahtarının değiştir olduğu bir durumda, değişiklikleri güncelleştirmek için veri kaynağında doğru kaydı bulmanın bir yolunu bulmanız gerekir. Özgün sürüm yoksa, kayıt büyük olasılıkla veri kaynağına eklenir ve bu da yalnızca fazladan istenmeyen bir kayıtla değil, hatalı ve güncel olmayan tek bir kayıtta da ortaya çıkar. İki sürüm de eşzamanlılık denetiminde kullanılır. Kaydın veri kümesine yüklendiğinden beri değiş olup olmadığını belirlemek için özgün sürümü veri kaynağında bir kayıtla karşılaştırabilirsiniz.

Önerilen sürüm, değişiklikleri veri kümesine gerçekten işlemeden önce doğrulama gerçekleştirmeniz gereken durumlarda kullanışlıdır.

Kayıtlar değişmiş olsa bile, bu satırın her zaman özgün veya geçerli sürümleri olmaz. Tabloya yeni bir satır eklerken özgün sürüm yoktur, yalnızca geçerli bir sürüm vardır. Benzer şekilde, tablonun yöntemini çağırarak bir satırı silersiniz, özgün bir sürüm vardır `Delete` ancak geçerli sürüm yoktur.

Bir veri satırı yöntemini sorgular ve bir kaydın belirli bir sürümünün mevcut olup olduğunu test <xref:System.Data.DataRow.HasVersion%2A> edersiniz. Bir sütunun değerini isteğiniz sırasında bir numaralama değerini isteğe bağlı bağımsız değişken olarak geçerek kaydın <xref:System.Data.DataRowVersion> herhangi bir sürümüne erişebilirsiniz.

## <a name="get-changed-records"></a>Değiştirilen kayıtları al

Bir veri kümesinde her kaydı güncelleştirmenin yaygın bir uygulamadır. Örneğin, bir kullanıcı birçok kayıt görüntüleyen Windows Forms <xref:System.Windows.Forms.DataGridView> denetimiyle çalışıyor olabilir. Ancak, kullanıcı yalnızca birkaç kaydı güncelleştirin, bir kaydı silebilir ve yeni bir kayıt ekler. Veri kümeleri ve veri tabloları yalnızca değiştirilmiş satırları döndüren bir yöntem ( `GetChanges` ) sağlar.

Veri tablosu ( ) veya veri kümesinin ( ) yöntemini kullanarak değiştirilen kayıtların `GetChanges` <xref:System.Data.DataTable.GetChanges%2A> alt kümelerini <xref:System.Data.DataSet.GetChanges%2A> oluşturabilirsiniz. Veri tablosu için yöntemini çağırmanız, tablonun yalnızca değiştirilen kayıtların bir kopyasını döndürür. Benzer şekilde, veri kümesinde yöntemini çağırsanız, yalnızca değiştirilmiş kayıtları olan yeni bir veri kümesi elde olur.

`GetChanges` , değiştirilen tüm kayıtları tek başına döndürür. Buna karşılık, isteneni yöntemine parametre olarak aktararak, istediğiniz değiştirilmiş kayıt alt kümesini belirtebilirsiniz: yeni eklenen kayıtlar, silme için işaretlenen kayıtlar, ayrılmış kayıtlar <xref:System.Data.DataRowState> `GetChanges` veya değiştirilmiş kayıtlar.

Değiştirilen kayıtların bir alt kümesini almak, işleme için başka bir bileşene kayıt göndermek istediğiniz zaman yararlıdır. Veri kümelerinin tamamını göndermek yerine, yalnızca bileşenin ihtiyacı olan kayıtları alarak diğer bileşenle iletişim kurma yükünü azaltabilirsiniz.

## <a name="commit-changes-in-the-dataset"></a>Veri kümesinde değişiklikleri işleme

Veri kümesinde değişiklikler yapıldı mı, <xref:System.Data.DataRow.RowState%2A> değiştirilen satırların özelliği ayarlanır. Kayıtların özgün ve geçerli sürümleri özelliği tarafından kurulur, korunur ve size <xref:System.Data.DataRowView.RowVersion%2A> kullanılabilir yapılır. Bu değiştirilen satırların özelliklerinde depolanan meta veriler, veri kaynağına doğru güncelleştirmeleri göndermek için gereklidir.

Değişiklikler veri kaynağının geçerli durumunu yansıtacaksa, artık bu bilgileri korumanız gerekmeyecektir. Genellikle, veri kümesi ve kaynağı eşitlenen iki kez olur:

- Veri kümesine, örneğin kaynaktan veri okuduğunda bilgileri yükledikten hemen sonra.

- Veri kümesinden veri kaynağına değişiklik gönderdikten sonra (ancak daha önce değil, çünkü veritabanına değişiklik göndermek için gereken değişiklik bilgilerini kaybedersiniz).

yöntemini çağırarak bekleyen değişiklikleri veri kümesine <xref:System.Data.DataSet.AcceptChanges%2A> işebilirsiniz. Genellikle, <xref:System.Data.DataSet.AcceptChanges%2A> aşağıdaki zamanlarda çağrılır:

- Veri kümesi yükledikten sonra. TableAdapter'ın yöntemini çağırarak bir veri kümesi `Fill` yükleyebilirsiniz, bağdaştırıcı değişiklikleri sizin için otomatik olarak işler. Ancak, başka bir veri kümesi birleştirerek bir veri kümesi yükleyebilirsiniz, değişiklikleri el ile işlemeniz gerekir.

    > [!NOTE]
    > Bağdaştırıcının özelliğini olarak ayarerek yöntemini çağırarak bağdaştırıcının değişiklikleri otomatik `Fill` `AcceptChangesDuringFill` olarak işlemesini önleyebilirsiniz. `false` olarak ayarlanırsa, dolgu sırasında eklenen her `false` <xref:System.Data.DataRow.RowState%2A> satırın olarak <xref:System.Data.DataRowState.Added> ayarlanır.

- Veri kümesi değişikliklerini xml web hizmeti gibi başka bir işleme gönderdikten sonra.

    > [!CAUTION]
    > Değişikliği bu şekilde işlemek tüm değişiklik bilgilerini siler. Veri kümesinde yapılan değişiklikleri uygulamanıza gerektiren işlemleri gerçekleştirmeyi bitirene kadar değişiklikleri işlemeyin.

Bu yöntem şunları başarır:

- Bir <xref:System.Data.DataRowVersion.Current> kaydın sürümünü kendi sürümüne <xref:System.Data.DataRowVersion.Original> yazar ve özgün sürümün üzerine yazar.

- özelliğinin olarak ayar <xref:System.Data.DataRow.RowState%2A> bulunduğu herhangi bir satırı <xref:System.Data.DataRowState.Deleted> kaldırır.

- Bir <xref:System.Data.DataRow.RowState%2A> kaydın özelliğini olarak <xref:System.Data.DataRowState.Unchanged> ayarlar.

yöntemi <xref:System.Data.DataSet.AcceptChanges%2A> üç düzeyde kullanılabilir. Yalnızca bu satırdaki değişiklikleri <xref:System.Data.DataRow> işlemek için bir nesne üzerinde çağırabilirsiniz. Tablodaki tüm satırları işlemek <xref:System.Data.DataTable> için bunu bir nesnesinde de çağırabilirsiniz. Son olarak, veri kümesi tüm <xref:System.Data.DataSet> tablolarının tüm kayıtlarında bekleyen tüm değişiklikleri işlemek için nesnesinde çağırabilirsiniz.

Aşağıdaki tabloda, yöntemin hangi nesne üzerinde çağrıldıklarına bağlı olarak hangi değişikliklerin işlendikleri açık almaktadır:

|Yöntem|Sonuç|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler yalnızca belirli bir satırda işlendi.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, belirli bir tablodaki tüm satırlarda işlendi.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, veri kümesi tablolarının tüm tablolarında tüm satırlarda işlendi.|

> [!NOTE]
> TableAdapter'ın yöntemini çağırarak bir veri kümesi `Fill` yükleyebilirsiniz, değişiklikleri açıkça kabul etmek zorunda değildir. Varsayılan olarak `Fill` yöntemi, veri `AcceptChanges` tablosu doldurmak tamam olduktan sonra yöntemini çağıran.

İlgili bir yöntem <xref:System.Data.DataSet.RejectChanges%2A> olan , sürümü kayıtların sürümüne <xref:System.Data.DataRowVersion.Original> geri kopyalayıp değişikliklerin etkisini geri <xref:System.Data.DataRowVersion.Current> alar. Ayrıca her <xref:System.Data.DataRow.RowState%2A> kaydın kaydını olarak <xref:System.Data.DataRowState.Unchanged> ayarlar.

## <a name="data-validation"></a>Veri doğrulama

Uygulamanıza verilerin geçirilen işlemlerin gereksinimlerini karşılar olduğunu doğrulamak için genellikle doğrulama eklemeniz gerekir. Bu, bir kullanıcının formda girişinin doğru olup olmadığını denetlemeyi, başka bir uygulama tarafından uygulamanıza gönderilen verileri doğrulamayı ve hatta bileşeniniz içinde hesaplanan bilgilerin veri kaynağı ve uygulama gereksinimlerinizin kısıtlamalarına denk gelir.

Verileri çeşitli yollarla doğruleyebilirsiniz:

- İş katmanında, verileri doğrulamak için uygulamanıza kod ekleyerek. Veri kümesi bunu tek bir yerde yapar. Veri kümesi, arka uç doğrulamasının bazı avantajlarını sağlar; örneğin sütun ve satır değerleri değişti olarak değişiklikleri doğrulama olanağı. Daha fazla bilgi için [bkz. Veri kümelerini verileri doğrulama.](../data-tools/validate-data-in-datasets.md)

- Sunum katmanında formlara doğrulama ekleyerek. Daha fazla bilgi için [bkz. Windows Forms'ta kullanıcı girişi doğrulaması.](/dotnet/framework/winforms/user-input-validation-in-windows-forms)

- Veri arka ucunda, verileri veri kaynağına (örneğin, veritabanına) göndererek ve verileri kabul etme veya reddetmeye izin vererek. Verileri doğrulamak ve hata bilgileri sağlamak için gelişmiş olanaklara sahip bir veritabanıyla çalışıyorsanız, verileri nereden geldiği fark etmez doğrulayabilirsiniz çünkü bu pratik bir yaklaşım olabilir. Ancak, bu yaklaşım uygulamaya özgü doğrulama gereksinimlerini karşılamaz. Ayrıca, veri kaynağının doğrulanması, uygulamanın arka uç tarafından ortaya çıkan doğrulama hatalarının çözümlerini nasıl kolaylaştırmalarına bağlı olarak veri kaynağına çok sayıda gidiş dönüşle sonuçlanabilir.

   > [!IMPORTANT]
   > olarak ayarlanmış bir özellik ile veri komutlarını kullanırken, veritabanınıza geçirmeden önce istemciden <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> gönderilen bilgileri dikkatle kontrol <xref:System.Data.CommandType.Text> edin. Kötü amaçlı kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar SQL amacıyla değiştirilmiş veya ek deyimler göndermeye (ekleme) deneyebilir. Kullanıcı girişini bir veritabanına aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Mümkün olduğunda her zaman parametreli sorgular veya saklı yordamlar kullanmak en iyi yöntemdir.

## <a name="transmit-updates-to-the-data-source"></a>Güncelleştirmeleri veri kaynağına aktarma

Bir veri kümesinde değişiklikler yapıldıktan sonra, değişiklikleri bir veri kaynağına iletebilirsiniz. En yaygın olarak bunu bir `Update` TableAdapter yöntemini (veya veri bağdaştırıcısı) çağırarak yaparsınız. yöntemi, veri tablodaki her kayıtta döngüye alır, gerekli güncelleştirme türünü belirler (güncelleştirme, ekleme veya silme), varsa uygun komutu çalıştırır.

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

Artık uygulamanız, `Update` veri kümelerini veritabanına iletmek için yöntemini çağıran bir yöntemdir. yöntemi, her satırı sırasıyla inceler. İlk satırda yöntemi, SQL deyimini veritabanına iletir çünkü başlangıçta veritabanından getiril olduğundan bu satır değişmemiştir.

Ancak ikinci satır için yöntemi otomatik olarak doğru veri `Update` komutunu çağırır ve veritabanına iletir. SQL deyiminin söz dizimi, temel SQL veri deposu tarafından desteklenen verinin diyalektine bağlıdır. Ancak iletilen ifadenin aşağıdaki genel özellikleri SQL değerdir:

- İletilen SQL deyimi bir UPDATE deyimidir. Özelliğin değeri olduğundan bağdaştırıcı bir UPDATE deyimi <xref:System.Data.DataRow.RowState%2A> kullanmayı <xref:System.Data.DataRowState.Modified> bilir.

- İletilen SQL deyimi, UPDATE deyiminin hedefinin bulunduğu satır olduğunu belirten bir WHERE yan tümcesi `CustomerID = 'c400'` içerir. SELECT deyiminin bu bölümü, hedef tablonun birincil anahtarı olduğundan hedef satırı `CustomerID` diğerlerinden ayırt ediyor. SATıRı tanımlamak için gereken değerlerin değişmesi durumunda WHERE yan tümcesi için bilgiler kaydın özgün sürümünden () `DataRowVersion.Original` türetmiştir.

- İletilen SQL deyimi, değiştirilen sütunların yeni değerlerini ayarlamak için SET yan tümcesini içerir.

   > [!NOTE]
   > TableAdapter'ın özelliği saklı yordamın adına ayarlanmışsa, bağdaştırıcı bir SQL `UpdateCommand` oluşturmaz. Bunun yerine, geçirilen uygun parametrelerle saklı yordamı çağırır.

## <a name="pass-parameters"></a>Parametre geçirme

Parametreleri genellikle veritabanında güncelleştirilen kayıtların değerlerini geçmek için kullanırsınız. TableAdapter'ın `Update` yöntemi update deyimini çalıştıracaksa parametre değerlerini doldurması gerekir. Bu değerleri uygun veri komutu için koleksiyondan alır ( bu `Parameters` durumda `UpdateCommand` TableAdapter'daki nesne).

Veri bağdaştırıcısı oluşturmak için Visual Studio araçları kullandıysanız, nesnesi deyiminde her parametre yer tutucusucusunu `UpdateCommand` karşılık gelen bir parametre koleksiyonu içerir.

Her <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> parametrenin özelliği, veri tablosunda bir sütunu gösterir. Örneğin, ve parametrelerinin özelliği, veri tablosunda yazar `SourceColumn` `au_id` kimliğini içeren `Original_au_id` sütuna ayarlanır. Bağdaştırıcının yöntemi çalıştır geldiğinde, güncelleştirilen kayıttan author id sütununu okur ve değerleri `Update` deyimine doldurur.

UPDATE deyiminde hem yeni değerleri (kayda yazılanlar) hem de eski değerleri (kaydın veritabanında yer alamayacak şekilde) belirtmeniz gerekir. Bu nedenle, her değer için iki parametre vardır: biri SET yan tümcesi için, biri WHERE yan tümcesi için farklı bir parametre. Her iki parametre de güncelleştirilen kayıttan verileri okur ancak parametrenin özelliğine göre sütun değerinin farklı sürümlerini <xref:System.Data.SqlClient.SqlParameter.SourceVersion> elde ediyor. SET yan tümcesi parametresi geçerli sürümü, WHERE yan tümcesi parametresi de özgün sürümü alır.

> [!NOTE]
> Koleksiyonda bulunan değerleri kod içinde de kendiniz de ayarlayabilirsiniz. Bu, genellikle veri bağdaştırıcısının olayı için bir `Parameters` olay işleyicisinde bunu <xref:System.Data.DataTable.RowChanging> yapar.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](validate-data-in-datasets.md)
- [Nasıl kullanılır: Varlık ekleme, değiştirme ve silme (WCF veri hizmetleri)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
