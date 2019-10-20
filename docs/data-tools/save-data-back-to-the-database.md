---
title: Verileri yeniden veritabanına kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ab2bd92b5636c89027c9c5954567be8048c1b152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648219"
---
# <a name="save-data-back-to-the-database"></a>Verileri yeniden veritabanına kaydetme

Veri kümesi, verilerin bellek içi bir kopyasıdır. Bu verileri değiştirirseniz, bu değişiklikleri veritabanına geri kaydetmek iyi bir uygulamadır. Bunu üç farklı şekilde yapabilirsiniz:

- Bir TableAdapter 'ın `Update` yöntemlerinden birini çağırarak

- TableAdapter 'ın `DBDirect` yöntemlerinden birini çağırarak

- Veri kümesi, veri kümesindeki diğer tablolarla ilişkili tablolar içerdiğinde, Visual Studio 'nun sizin için oluşturduğu TableAdapterManager `UpdateAll` yöntemini çağırarak

Veri kümesi tablolarını bir Windows form veya XAML sayfasında denetimlere veri bağladığınızda, veri bağlama mimarisi tüm işleri sizin için yapar.

TableAdapters hakkında bilgi sahibiyseniz, doğrudan bu konulardan birine atlayabilirsiniz:

|Konu|Açıklama|
|-----------|-----------------|
|[Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)|TableAdapters veya komut nesnelerini kullanarak güncelleştirmeleri ve eklemeleri gerçekleştirme|
|[TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)|TableAdapters ile güncelleştirme gerçekleştirme|
|[Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)|İki veya daha fazla ilişkili tabloyla bir veri kümesinden güncelleştirme gerçekleştirme|
|[Bir eşzamanlılık özel durumunu işleme](../data-tools/handle-a-concurrency-exception.md)|İki kullanıcı aynı anda bir veritabanında aynı verileri değiştirmeyi denediklerinde özel durumları işleme|
|[Nasıl yapılır: işlem kullanarak verileri kaydetme](../data-tools/save-data-by-using-a-transaction.md)|Sistemi kullanarak bir işlemde verileri kaydetme. İşlemler ad alanı ve bir TransactionScope nesnesi|
|[Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)|Bir işlem içindeki veritabanına veri kaydetmeyi göstermek için bir Windows Forms uygulaması oluşturan izlenecek yol|
|[Bir veritabanına (birden çok tablo) veri kaydetme](../data-tools/save-data-to-a-database-multiple-tables.md)|Kayıtları düzenleme ve birden çok tablodaki değişiklikleri veritabanına geri kaydetme|
|[Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect yöntemi kullanarak bir veri kümesinde olmayan bir nesneden verileri veritabanına geçirme|
|[TableAdapter DBDirect metotlarıyla veri kaydetme](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|SQL sorgularını doğrudan veritabanına göndermek için TableAdapter 'ı kullanma|
|[Bir veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md)|Bir veri kümesini bir XML belgesine kaydetme|

## <a name="two-stage-updates"></a>İki aşamalı güncelleştirmeler

Veri kaynağını güncelleştirme iki adımlı bir işlemdir. İlk adım, veri kümesini yeni kayıtlar, değiştirilen kayıtlar veya silinen kayıtlarla güncelleştirmedir. Uygulamanız bu değişiklikleri hiçbir şekilde veri kaynağına geri gönderdiyseniz, güncelleştirme ile işiniz tamamlanmıştır.

Değişiklikleri veritabanına geri gönderirseniz ikinci bir adım gereklidir. Veri bağlantılı denetimleri kullanmıyorsanız, veri kümesini doldurmak için kullandığınız aynı TableAdapter (veya veri bağdaştırıcısı) `Update` yöntemini el ile çağırmanız gerekir. Ancak, örneğin, verileri bir veri kaynağından diğerine taşımak veya birden çok veri kaynağını güncelleştirmek için farklı bağdaştırıcılar de kullanabilirsiniz. Veri bağlamayı kullanmıyorsanız ve ilgili tablolar için değişiklikleri kaydediyorsanız, otomatik olarak oluşturulan `TableAdapterManager` sınıfının bir değişkenini el ile oluşturmanız ve ardından `UpdateAll` yöntemini çağırmanız gerekir.

![Veri kümesi güncelleştirmelerinin kavramsal diyagramı](../data-tools/media/vbdatasetupdates.gif)

Bir veri kümesi, bir satır koleksiyonu içeren tablo koleksiyonlarını içerir. Temel bir veri kaynağını daha sonra güncelleştirmek istiyorsanız, satırları eklerken veya kaldırırken `DataTable.DataRowCollection` özelliğindeki yöntemleri kullanmanız gerekir. Bu yöntemler, veri kaynağını güncelleştirmek için gereken değişiklik izlemeyi gerçekleştirir. Rows özelliğinde `RemoveAt` koleksiyonunu çağırırsanız, silme işlemi veritabanına geri iletilir.

## <a name="merge-datasets"></a>Veri kümelerini birleştirme

Bir veri kümesinin içeriğini başka bir veri kümesiyle *birleştirerek* güncelleştirebilirsiniz. Bu, *kaynak* veri kümesinin içeriğini çağıran veri kümesine kopyalamayı içerir ( *hedef* veri kümesi olarak adlandırılır). Veri kümelerini birleştirdiğinizde, kaynak veri kümesindeki yeni kayıtlar hedef veri kümesine eklenir. Ayrıca, kaynak veri kümesindeki ek sütunlar hedef veri kümesine eklenir. Veri kümelerini birleştirme, yerel bir veri kümeniz olduğunda ve başka bir uygulamadan ikinci bir veri kümesi alırsanız faydalıdır. Ayrıca, bir XML Web hizmeti gibi bir bileşenden veya birden çok veri kümesinden verileri tümleştirmeniz gerektiğinde de yararlı olur.

Veri kümeleri birleştirilirken, bir Boole bağımsız değişkeni (`preserveChanges`) geçirebilirsiniz. Bu, <xref:System.Data.DataSet.Merge%2A> yöntemine hedef veri kümesinde var olan değişikliklerin tutulması gerekip gerekmediğini söyler. Veri kümeleri kayıtların birden çok sürümünü koruduğundan, kayıtların birden fazla sürümünün birleştirildiğini aklınızda bulundurmanız önemlidir. Aşağıdaki tabloda, iki veri kümesi içindeki bir kaydın nasıl birleştirileceği gösterilmektedir:

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James Wilson|James C. Solson|
|Geçerli|Jim Wilson|James C. Solson|

Önceki tabloda <xref:System.Data.DataSet.Merge%2A> yönteminin `preserveChanges=false targetDataset.Merge(sourceDataset)` ile çağrılması aşağıdaki verilerle sonuçlanır:

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James C. Solson|James C. Solson|
|Geçerli|James C. Solson|James C. Solson|

@No__t_0 yönteminin `preserveChanges = true targetDataset.Merge(sourceDataset, true)` ile çağrılması aşağıdaki verilere neden olur:

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
| - | - | - |
|Özgün|James C. Solson|James C. Solson|
|Geçerli|Jim Wilson|James C. Solson|

> [!CAUTION]
> @No__t_0 senaryosunda, hedef veri kümesindeki bir kayıt üzerinde <xref:System.Data.DataSet.RejectChanges%2A> yöntemi çağrılırsa, *kaynak* veri kümesindeki özgün verilere geri döner. Bu, özgün veri kaynağını hedef veri kümesiyle güncelleştirmeye çalışırsanız, güncelleştirilecek orijinal satırı bulamayabilir. Farklı bir veri kümesini veri kaynağından güncelleştirilmiş kayıtlarla doldurarak ve ardından bir eşzamanlılık ihlalinden kaçınmak için birleştirme gerçekleştirerek eşzamanlılık ihlalini engelleyebilirsiniz. (Veri kümesi doldurulduktan sonra, başka bir kullanıcı veri kaynağındaki bir kaydı değiştirdiğinde eşzamanlılık ihlali oluşur.)

## <a name="update-constraints"></a>Güncelleştirme kısıtlamaları

Var olan bir veri satırında değişiklik yapmak için, sütunları ayrı sütunlara ekleyin veya güncelleştirin. Veri kümesi kısıtlamalar içeriyorsa (örneğin, yabancı anahtarlar veya null yapılamayan kısıtlamalar), bu kayıt sizin güncelleştirdiğinde geçici olarak bir hata durumunda olabilir. Diğer bir deyişle, bir sütunun güncelleştirilmesini tamamladıktan sonra, bir sonrakine geçmeden önce bir hata durumunda olabilir.

Zamanından önce kısıtlama ihlallerini engellemek için, güncelleştirme kısıtlamalarını geçici olarak askıya alabilirsiniz. Bu iki amaca hizmet eder:

- Bir sütunun güncelleştirilmesini tamamladıktan sonra, başka bir sütunu güncelleştirmeden sonra bir hatanın oluşturulmasını engeller.

- Belirli güncelleştirme olaylarının oluşturulmasını engeller (genellikle doğrulama için kullanılan olaylar).

> [!NOTE]
> Windows Forms, DataGrid içinde yerleşik veri bağlama mimarisi, odak bir satırın dışına çıkana kadar kısıtlama denetimini askıya alır ve <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> veya <xref:System.Data.DataRow.CancelEdit%2A> yöntemlerini açıkça çağırmanız gerekmez.

Bir veri kümesinde <xref:System.Data.DataSet.Merge%2A> yöntemi çağrıldığında kısıtlamalar otomatik olarak devre dışıdır. Birleştirme tamamlandığında, veri kümesinde etkinleştirilemez bir kısıtlama varsa, bir <xref:System.Data.ConstraintException> oluşturulur. Bu durumda <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği `false,` olarak ayarlanır ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği `true` olarak sıfırlanmadan önce tüm kısıtlama ihlalleri çözümlenmelidir.

Bir güncelleştirmeyi tamamladıktan sonra, ayrıca güncelleştirme olaylarını yeniden etkinleştiren ve bunları başlatan kısıtlama denetimini yeniden etkinleştirebilirsiniz.

Olayları askıya alma hakkında daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

## <a name="dataset-update-errors"></a>Veri kümesi güncelleştirme hataları

Bir veri kümesindeki bir kaydı güncelleştirdiğinizde bir hata olasılığı vardır. Örneğin, yanlışlıkla yanlış türde verileri veya çok uzun verileri veya başka bir bütünlük sorunu olan verileri istemeden yazabilirsiniz. Ya da, bir güncelleştirme olayının herhangi bir aşamasında özel hatalar oluşturabilen uygulamaya özgü doğrulama denetimlerine sahip olabilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Değişikliklerle ilgili bilgileri koruma

Bir veri kümesindeki değişikliklerle ilgili bilgiler iki şekilde tutulur: değiştirildikleri (<xref:System.Data.DataRow.RowState%2A>) ve bir kaydın birden çok kopyasını (<xref:System.Data.DataRowVersion>) tutarak satırlara bayrak koyarak. Süreçler, bu bilgileri kullanarak veri kümesinde nelerin değiştiğini belirleyebilir ve uygun güncelleştirmeleri veri kaynağına gönderebilir.

### <a name="rowstate-property"></a>RowState özelliği

Bir <xref:System.Data.DataRow> nesnesinin <xref:System.Data.DataRow.RowState%2A> özelliği, belirli bir veri satırının durumu hakkında bilgi sağlayan bir değerdir.

Aşağıdaki tabloda <xref:System.Data.DataRowState> numaralandırmasının olası değerleri ayrıntılı olarak verilmiştir:

|DataRowState değeri|Açıklama|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Satır bir <xref:System.Data.DataRowCollection> öğe olarak eklendi. (Son <xref:System.Data.DataRow.AcceptChanges%2A> yöntemi çağrıldığında mevcut olmadığından, bu durumdaki bir satırın karşılık gelen bir özgün sürümü yok).|
|<xref:System.Data.DataRowState.Deleted>|Satır, bir <xref:System.Data.DataRow> nesnesinin <xref:System.Data.DataRow.Delete%2A> kullanılarak silindi.|
|<xref:System.Data.DataRowState.Detached>|Satır oluşturuldu ancak hiçbir <xref:System.Data.DataRowCollection> parçası değil. Bir <xref:System.Data.DataRow> nesnesi, oluşturulduktan hemen sonra, bir koleksiyona eklendikten önce ve bir koleksiyondan kaldırıldıktan sonra bu durumda olur.|
|<xref:System.Data.DataRowState.Modified>|Satırdaki bir sütun değeri bir şekilde değiştirildi.|
|<xref:System.Data.DataRowState.Unchanged>|@No__t_0 son çağrılmasından bu yana satır değişmedi.|

### <a name="datarowversion-enumeration"></a>DataRowVersion numaralandırması

Veri kümeleri kayıtların birden çok sürümünü tutar. @No__t_0 alanları, <xref:System.Data.DataRow.Item%2A> özelliği veya <xref:System.Data.DataRow> nesnesinin <xref:System.Data.DataRow.GetChildRows%2A> yöntemi kullanılarak bir <xref:System.Data.DataRow> bulunan değer alınırken kullanılır.

Aşağıdaki tabloda <xref:System.Data.DataRowVersion> numaralandırmasının olası değerleri ayrıntılı olarak verilmiştir:

|DataRowVersion değeri|Açıklama|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Bir kaydın geçerli sürümü, <xref:System.Data.DataRow.AcceptChanges%2A> son kez çağrılmasından bu yana kayıt üzerinde gerçekleştirilen tüm değişiklikleri içerir. Satır silinmişse, geçerli sürüm yoktur.|
|<xref:System.Data.DataRowVersion.Default>|Bir kaydın veri kümesi şeması veya veri kaynağı tarafından tanımlanan varsayılan değeri.|
|<xref:System.Data.DataRowVersion.Original>|Bir kaydın orijinal sürümü, veri kümesinde son değişiklikler işlendiği için kaydın bir kopyasıdır. Pratik koşullarda, bu genellikle bir veri kaynağından okunan bir kaydın sürümüdür.|
|<xref:System.Data.DataRowVersion.Proposed>|Bir güncelleştirmenin ortasındayken geçici olarak kullanılabilen bir kaydın önerilen sürümü (<xref:System.Data.DataRow.BeginEdit%2A> yöntemi ve <xref:System.Data.DataRow.EndEdit%2A> yöntemi arasında). Genellikle <xref:System.Data.DataTable.RowChanging> gibi bir olay için işleyicide bir kaydın önerilen sürümüne erişirsiniz. @No__t_0 yöntemini çağırmak değişiklikleri tersine çevirir ve veri satırının önerilen sürümünü siler.|

Özgün ve güncel sürümler, güncelleştirme bilgileri bir veri kaynağına aktarıldığında yararlı olur. Genellikle, veri kaynağına bir güncelleştirme gönderildiğinde, veritabanının yeni bilgileri bir kaydın geçerli sürümüdür. Özgün sürümden alınan bilgiler güncelleştirilecek kaydı bulmak için kullanılır.

Örneğin, bir kaydın birincil anahtarının değiştirildiği bir durumda, değişiklikleri güncelleştirmek için veri kaynağında doğru kaydı bulmanız için bir yol gerekir. Özgün sürüm yoksa, kayıt büyük olasılıkla veri kaynağına eklenebilir, bu da yalnızca fazladan istenmeyen bir kayıtta değil, hatalı ve güncel olmayan bir kayıtta olur. Eşzamanlılık denetiminde iki sürüm de kullanılır. Kayıt kümesine yüklendikten sonra kaydın değişip değişmediğini öğrenmek için özgün sürümü veri kaynağındaki bir kayıtla karşılaştırarak karşılaştırabilirsiniz.

Önerilen sürüm, değişiklikleri aslında veri kümesine kaydetmeden önce doğrulama gerçekleştirmeniz gerektiğinde faydalıdır.

Kayıtlar değişmiş olsa bile, bu satırın her zaman orijinal veya güncel sürümü yoktur. Tabloya yeni bir satır eklediğinizde, özgün sürüm yoktur, yalnızca geçerli bir sürümdür. Benzer şekilde, tablonun `Delete` yöntemini çağırarak bir satırı silerseniz, orijinal bir sürüm vardır ancak geçerli sürüm yoktur.

Bir veri satırının <xref:System.Data.DataRow.HasVersion%2A> yöntemi sorgulanarak bir kaydın belirli bir sürümünün mevcut olup olmadığını görmek için test edebilirsiniz. Bir sütunun değerini istediğinizde bir <xref:System.Data.DataRowVersion> numaralandırma değerini isteğe bağlı bağımsız değişken olarak geçirerek, bir kaydın her iki sürümüne de erişebilirsiniz.

## <a name="get-changed-records"></a>Değiştirilen kayıtları al

Bir veri kümesindeki her kaydı güncelleştirmeme yaygın bir uygulamadır. Örneğin, bir kullanıcı birçok kayıt görüntüleyen bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimiyle çalışıyor olabilir. Ancak, Kullanıcı yalnızca birkaç kaydı güncelleştirebilir, bir tane silebilir ve yeni bir tane ekleyebilir. Veri kümeleri ve veri tabloları yalnızca değiştirilen satırları döndürmek için bir Yöntem (`GetChanges`) sağlar.

Veri tablosunun (<xref:System.Data.DataTable.GetChanges%2A>) ya da veri kümesinin (<xref:System.Data.DataSet.GetChanges%2A>) `GetChanges` yöntemini kullanarak değiştirilen kayıtların alt kümelerini oluşturabilirsiniz. Veri tablosu için yöntemini çağırırsanız, yalnızca değiştirilen kayıtlarla tablonun bir kopyasını döndürür. Benzer şekilde, yöntemi veri kümesinde çağırırsanız, içinde yalnızca değiştirilmiş kayıtları olan yeni bir veri kümesi alırsınız.

tek başına `GetChanges` tüm değiştirilen kayıtları döndürür. Buna karşılık, istenen <xref:System.Data.DataRowState> `GetChanges` yöntemine parametre olarak geçirerek, hangi değiştirilen kayıtların alt kümesini istediğinizi belirtebilirsiniz: yeni eklenen kayıtlar, silinmek üzere işaretlenmiş kayıtlar, ya da değiştirilen kayıtlar.

Değiştirilen kayıtların bir alt kümesini almak, kayıtları işlemek için başka bir bileşene göndermek istediğinizde faydalıdır. Veri kümesinin tamamını göndermek yerine, yalnızca bileşenin ihtiyaç duyacağı kayıtları alarak diğer bileşenle iletişim yükünü azaltabilirsiniz.

## <a name="commit-changes-in-the-dataset"></a>Veri kümesindeki değişiklikleri Yürüt

Veri kümesinde değişiklik yapıldıkça, değiştirilen satırların <xref:System.Data.DataRow.RowState%2A> özelliği ayarlanır. Kayıtların orijinal ve güncel sürümleri oluşturulur, tutulur ve <xref:System.Data.DataRowView.RowVersion%2A> özelliği tarafından kullanılabilir hale getirilir. Bu değiştirilen satırların özelliklerinde depolanan meta veriler, doğru güncelleştirmelerin veri kaynağına gönderilmesi için gereklidir.

Değişiklikler veri kaynağının geçerli durumunu yansıttığından, bu bilgileri artık sürdürmenize gerek kalmaz. Genellikle, veri kümesi ve kaynağı eşitlenmiş olduğunda iki zaman vardır:

- Verileri veri kümesine yükledikten hemen sonra (örneğin, kaynaktan veri okurken).

- Değişiklikleri veri kaynağına gönderdikten sonra (daha önce değil, değişiklikleri veritabanına göndermek için gereken değişiklik bilgilerini kaybedeceğinizi).

@No__t_0 yöntemini çağırarak, bekleyen değişiklikleri veri kümesine kaydedebilirsiniz. Genellikle <xref:System.Data.DataSet.AcceptChanges%2A> aşağıdaki saatlerde çağrılır:

- Veri kümesini yükledikten sonra. Bir TableAdapter 'ın `Fill` yöntemini çağırarak bir veri kümesi yüklerseniz, bağdaştırıcı değişiklikleri sizin için otomatik olarak kaydeder. Ancak, başka bir veri kümesini içine birleştirerek bir veri kümesini yüklerseniz, değişiklikleri el ile yürütmeniz gerekir.

    > [!NOTE]
    > Bağdaştırıcının `AcceptChangesDuringFill` özelliğini `false` olarak ayarlayarak `Fill` yöntemini çağırdığınızda bağdaştırıcının otomatik olarak değişiklikleri almasını engelleyebilirsiniz. @No__t_0 olarak ayarlandıysa, Fill sırasında eklenen her satırın <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Added> olarak ayarlanır.

- Veri kümesi değişikliklerini bir XML Web hizmeti gibi başka bir işleme gönderdikten sonra.

    > [!CAUTION]
    > Değişikliği bu şekilde yürütmek, değişiklik bilgilerini siler. Uygulamanızın veri kümesinde hangi değişikliklerin yapıldığını bilmesini gerektiren işlemleri gerçekleştirmeyi bitirene kadar değişiklikleri yürütmeyin.

Bu yöntem şunları gerçekleştirir:

- Bir kaydın <xref:System.Data.DataRowVersion.Current> sürümünü <xref:System.Data.DataRowVersion.Original> sürümüne yazar ve özgün sürümün üzerine yazar.

- @No__t_0 özelliğinin <xref:System.Data.DataRowState.Deleted> olarak ayarlandığı tüm satırları kaldırır.

- Bir kaydın <xref:System.Data.DataRow.RowState%2A> özelliğini <xref:System.Data.DataRowState.Unchanged> olarak ayarlar.

@No__t_0 yöntemi üç düzeyde kullanılabilir. Yalnızca söz konusu satır için değişiklikleri kaydetmeleri için bir <xref:System.Data.DataRow> nesnesinde çağırabilirsiniz. Ayrıca, bir tablodaki tüm satırları yürütmek için bir <xref:System.Data.DataTable> nesnesi üzerinde çağırabilirsiniz. Son olarak, veri kümesinin tüm tablolarındaki tüm kayıtlarda bekleyen tüm değişiklikleri kaydetmek için <xref:System.Data.DataSet> nesnesinde çağırabilirsiniz.

Aşağıdaki tabloda, yöntemin hangi nesneye çağrıldığı üzerinde hangi değişikliklerin yürütüldüğü açıklanmaktadır:

|Yöntem|Sonuç|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler yalnızca belirli bir satıra kaydedilir.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, belirli bir tablodaki tüm satırlara kaydedilir.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, veri kümesinin tüm tablolarındaki tüm satırlara kaydedilir.|

> [!NOTE]
> Bir TableAdapter 'ın `Fill` yöntemini çağırarak bir veri kümesi yüklüyorsanız, değişiklikleri açıkça kabul etmeniz gerekmez. Varsayılan olarak `Fill` yöntemi, veri tablosunu doldurmayı tamamladıktan sonra `AcceptChanges` yöntemini çağırır.

@No__t_0 ilgili bir yöntem, <xref:System.Data.DataRowVersion.Original> sürümünü kayıtların <xref:System.Data.DataRowVersion.Current> sürümüne geri kopyalayarak değişikliklerin etkisini geri alır. Ayrıca, her kaydın <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Unchanged> olarak ayarlanır.

## <a name="data-validation"></a>Veri doğrulama

Uygulamanızdaki verilerin geçirildiği işlemlerin gereksinimlerini karşıladığından emin olmak için, genellikle doğrulama eklemeniz gerekir. Bu, bir kullanıcının bir formdaki girişinin doğru olup olmadığını, başka bir uygulama tarafından uygulamanıza gönderilen verileri doğrulamayı ve hatta bileşeninizin içinde hesaplanan bilgilerin veri kaynağınızın kısıtlamaları dahilinde olduğunu kontrol etmeyi gerektirebilir ve uygulama gereksinimleri.

Verileri çeşitli yollarla doğrulayabilirsiniz:

- İş katmanında, verileri doğrulamak için uygulamanıza kod ekleyerek. Veri kümesi, bunu yapabileceğiniz bir yerdir. Veri kümesi, değişikliklerin sütun olarak doğrulanması ve satır değerlerinin değiştirilmesi gibi arka uç doğrulamanın avantajlarından bazılarını sağlar. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

- Sunu katmanında, formlara doğrulama ekleyerek. Daha fazla bilgi için [Windows Forms Içindeki Kullanıcı giriş doğrulaması](/dotnet/framework/winforms/user-input-validation-in-windows-forms)konusuna bakın.

- Veri arka ucunda, veri kaynağına veri göndererek — Örneğin, veritabanı — ve bu verilerin verileri kabul etmesine veya reddetmesine izin verir. Verileri doğrulamak ve hata bilgileri sağlamak için karmaşık tesislere sahip bir veritabanıyla çalışıyorsanız, veri nereden geldiği bağımsız olarak verileri doğrulayabilmeniz için bu pratik bir yaklaşım olabilir. Ancak, bu yaklaşım uygulamaya özgü doğrulama gereksinimlerine uyum sağlayabilir. Ayrıca, veri kaynağı verilerinin doğrulanması, uygulamanızın arka uçta oluşan doğrulama hatalarının çözümlenmesini nasıl kolaylaştırdığına bağlı olarak veri kaynağına çok sayıda gidiş dönüşine yol açabilir.

   > [!IMPORTANT]
   > @No__t_1 olarak ayarlanan bir <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliği ile veri komutları kullanırken, bir istemciden gönderilen bilgileri veritabanınıza geçirmeden önce dikkatle kontrol edin. Kötü niyetli kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar vermek için bir denemeye değiştirilmiş veya ek SQL deyimleri göndermeye (eklemeye) çalışabilir. Kullanıcı girişini bir veritabanına aktarmadan önce, bilgilerin geçerli olduğunu her zaman doğrulayın. Mümkün olduğunda her zaman parametreli sorguları veya saklı yordamları kullanmak en iyi uygulamadır.

## <a name="transmit-updates-to-the-data-source"></a>Güncelleştirmeleri veri kaynağına ilet

Bir veri kümesinde değişiklik yapıldıktan sonra, değişiklikleri bir veri kaynağına aktarabilirsiniz. En yaygın olarak, bunu bir TableAdapter (veya veri bağdaştırıcısı) `Update` yöntemini çağırarak yapabilirsiniz. Yöntemi bir veri tablosundaki her kayıt için döngü yapar, varsa ne tür bir güncelleştirme gerektiğini (güncelleştirme, ekleme veya silme) belirler ve ardından uygun komutu çalıştırır.

Güncelleştirmelerin nasıl yapıldığını gösteren bir çizim olarak, uygulamanızın tek bir veri tablosu içeren bir veri kümesi kullandığını varsayalım. Uygulama, veritabanından iki satır getirir. Alma işleminden sonra, bellek içi veri tablosu şöyle görünür:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Uygulamanız Gamze Uludağ 'ın durumunu "tercih edilen" olarak değiştiriyor. Bu değişikliğin sonucu olarak, bu satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değeri <xref:System.Data.DataRowState.Unchanged> <xref:System.Data.DataRowState.Modified> olarak değişir. İlk satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değeri <xref:System.Data.DataRowState.Unchanged> kalır. Veri tablosu şu şekilde görünür:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Uygulamanız şimdi veri kümesini veritabanına aktarmak için `Update` yöntemini çağırır. Yöntemi her satırı sırayla inceler. İlk satır için, bu satır veritabanından getirilmesinden bu yana değişmediğinden, yöntemi veritabanına hiçbir SQL ifadesini iletir.

Ancak, ikinci satır için `Update` yöntemi doğru veri komutunu otomatik olarak çağırır ve veritabanına iletir. SQL ifadesinin belirli sözdizimi, temel alınan veri deposu tarafından desteklenen SQL 'in lehçine bağlıdır. Ancak, iletilen SQL ifadesinin aşağıdaki genel nitelikleri de dikkate alınır:

- Aktarılan SQL deyimleri bir UPDATE deyimidir. @No__t_0 özelliğinin değeri <xref:System.Data.DataRowState.Modified> olduğundan, bağdaştırıcı bir UPDATE ifadesini kullanmayı bilir.

- İletilen SQL deyimi, UPDATE ifadesinin hedefinin `CustomerID = 'c400'` sıranın olduğunu gösteren bir WHERE yan tümcesi içerir. SELECT ifadesinin bu bölümü, hedef tablonun birincil anahtarı olduğundan, hedef satırı diğerlerinden ayırt eder, çünkü `CustomerID`. WHERE yan tümcesinin bilgileri, kaydın orijinal sürümünden (`DataRowVersion.Original`) türetilir ve bu da, satırı tanımlamak için gereken değerlerin değişmiş olması durumunda.

- Aktarılan SQL deyimi, değiştirilen sütunların yeni değerlerini ayarlamak için SET yan tümcesini içerir.

   > [!NOTE]
   > TableAdapter 'ın `UpdateCommand` özelliği saklı yordamın adına ayarlandıysa, bağdaştırıcı bir SQL deyimleri oluşturmaz. Bunun yerine, saklı yordamı geçirilen uygun parametrelerle çağırır.

## <a name="pass-parameters"></a>Parametreleri geçir

Genellikle, veritabanında güncelleştirileceği kayıtların değerlerini geçirmek için parametreleri kullanırsınız. TableAdapter 'ın `Update` yöntemi bir UPDATE ifadesini çalıştırdığında parametre değerlerini doldurması gerekir. Bu değerleri, uygun veri komutuna ait `Parameters` koleksiyonundan alır — bu durumda TableAdapter içindeki `UpdateCommand` nesnesi.

Veri bağdaştırıcısı oluşturmak için Visual Studio araçlarını kullandıysanız, `UpdateCommand` nesnesi, deyimindeki her bir parametre yer tutucusuna karşılık gelen parametrelerin bir koleksiyonunu içerir.

Her parametrenin <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> özelliği, veri tablosundaki bir sütuna işaret eder. Örneğin, `au_id` ve `Original_au_id` parametrelerinin `SourceColumn` özelliği, veri tablosundaki yazar kimliğini içeren herhangi bir sütun olarak ayarlanır. Bağdaştırıcının `Update` yöntemi çalıştırıldığında, güncelleştirilmekte olan kayıttaki yazar kimliği sütununu okur ve değerleri deyimle doldurur.

Bir UPDATE ifadesinde, hem yeni değerleri (kayda yazılacak olanlar) hem de eski değerleri (kaydın veritabanında konumlandırılabilir olması için) belirtmeniz gerekir. Bu nedenle, her bir değer için iki parametre vardır: bir SET yan tümcesi ve WHERE yan tümcesi için farklı bir tane. Her iki parametre de, güncelleştirilmekte olan kayıttan verileri okur, ancak parametrenin <xref:System.Data.SqlClient.SqlParameter.SourceVersion> özelliğine göre sütun değerinin farklı sürümlerini alırlar. SET yan tümcesinin parametresi geçerli sürümü alır ve WHERE yan tümcesinin parametresi orijinal sürümü alır.

> [!NOTE]
> Ayrıca, `Parameters` koleksiyondaki değerleri, genellikle veri bağdaştırıcısının <xref:System.Data.DataTable.RowChanging> olayına bir olay işleyicide yapacağınız kodda da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](validate-data-in-datasets.md)
- [Nasıl yapılır: varlıkları ekleme, değiştirme ve silme (WCF veri Hizmetleri)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)