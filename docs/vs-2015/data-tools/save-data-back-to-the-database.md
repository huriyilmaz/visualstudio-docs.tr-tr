---
title: Verileri veritabanına geri kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1b1a54d8be5ab4aa9703d318d0b537deff53b6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652877"
---
# <a name="save-data-back-to-the-database"></a>Verileri yeniden veritabanına kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri kümesi, verilerin bellek içi bir kopyasıdır. Bu verileri değiştirirseniz, bu değişiklikleri veritabanına geri kaydetmek iyi bir uygulamadır. Bunu üç farklı şekilde yapabilirsiniz:

- `Update`Bir TableAdapter yöntemlerinden birini çağırarak

- TableAdapter 'ın DBDirect yöntemlerinden birini çağırarak

- `TableAdapterManager`Veri kümesindeki diğer tablolarla ilişkili tablolar içerdiğinde, Visual Studio 'nun sizin için oluşturduğu UpdateAll yöntemini çağırarak

  Veri kümesi tablolarını bir Windows form veya XAML sayfasında denetimlere veri bağladığınızda, veri bağlama mimarisi tüm işleri sizin için yapar.

  TableAdapters hakkında bilgi sahibiyseniz, doğrudan bu konulardan birine atlayabilirsiniz:

|Konu|Description|
|-----------|-----------------|
|[Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)|TableAdapters veya komut nesnelerini kullanarak güncelleştirmeleri ve eklemeleri gerçekleştirme|
|[TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)|TableAdapters ile güncelleştirme gerçekleştirme|
|[Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)|İki veya daha fazla ilişkili tabloyla bir veri kümesinden güncelleştirme gerçekleştirme|
|[Bir eşzamanlılık özel durumunu işleme](../data-tools/handle-a-concurrency-exception.md)|İki kullanıcı aynı anda bir veritabanında aynı verileri değiştirmeyi denediklerinde özel durumları işleme|
|[Bir işlemi kullanarak veri kaydetme](../data-tools/save-data-by-using-a-transaction.md)|System. Transactions ad alanını ve TransactionScope nesnesini kullanarak bir işlemde verileri kaydetme|
|[İşleme veri kaydetme](../data-tools/save-data-in-a-transaction.md)|System. Transactions ad alanını kullanarak bir işlemde verileri kaydetme|
|[Bir veritabanına (birden çok tablo) veri kaydetme](../data-tools/save-data-to-a-database-multiple-tables.md)|Kayıtları düzenleme ve birden çok tablodaki değişiklikleri veritabanına geri kaydetme|
|[Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect yöntemi kullanarak bir veri kümesinde olmayan bir nesneden verileri veritabanına geçirme|
|[TableAdapter DBDirect metotlarıyla veri kaydetme](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|SQL sorgularını doğrudan veritabanına göndermek için TableAdapter 'ı kullanma|
|[Veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md)|Bir veri kümesini bir XML belgesine kaydetme|

## <a name="two-stage-updates"></a>İki aşamalı güncelleştirmeler
 Veri kaynağını güncelleştirme iki adımlı bir işlemdir. İlk adım, veri kümesini yeni kayıtlar, değiştirilen kayıtlar veya silinen kayıtlarla güncelleştirmedir. Uygulamanız bu değişiklikleri hiçbir şekilde veri kaynağına geri gönderdiyseniz, güncelleştirme ile işiniz tamamlanmıştır.

 Değişiklikleri veritabanına geri gönderirseniz ikinci bir adım gereklidir. Veri bağlantılı denetimleri kullanmıyorsanız, veri kümesini doldurmak için kullandığınız aynı TableAdapter (veya veri bağdaştırıcısı) güncelleştirme yöntemini el ile çağırmanız gerekir. Ancak, örneğin, verileri bir veri kaynağından diğerine taşımak veya birden çok veri kaynağını güncelleştirmek için farklı bağdaştırıcılar de kullanabilirsiniz. Veri bağlamayı kullanmıyorsanız ve ilgili tablolar için değişiklikleri kaydediyorsanız, otomatik olarak oluşturulan TableAdapterManager sınıfının bir değişkenini el ile örneklemeli ve sonra UpdateAll yöntemini çağırmanız gerekir.

 ![Visual Basic veri kümesi güncelleştirmeleri](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") İki aşamalı güncelleştirme işlemi ve başarılı bir güncelleştirmede DataRowVersion rolü

 Bir veri kümesi, bir satır koleksiyonu içeren tablo koleksiyonlarını içerir. Temel alınan bir veri kaynağını daha sonra güncelleştirmek istiyorsanız, satırları eklerken veya kaldırırken DataTable. DataRowCollection özelliğindeki yöntemleri kullanmanız gerekir. Bu yöntemler, veri kaynağını güncelleştirmek için gereken değişiklik izlemeyi gerçekleştirir. Rows özelliğinde RemoveAt koleksiyonunu çağırırsanız, silme işlemi veritabanına geri iletilir.

## <a name="merge-datasets"></a>Veri kümelerini birleştirme
 Bir veri kümesinin içeriğini başka bir veri kümesiyle *birleştirerek* güncelleştirebilirsiniz. Bu, *kaynak* veri kümesinin içeriğini çağıran veri kümesine kopyalamayı içerir ( *hedef* veri kümesi olarak adlandırılır). Veri kümelerini birleştirdiğinizde, kaynak veri kümesindeki yeni kayıtlar hedef veri kümesine eklenir. Ayrıca, kaynak veri kümesindeki ek sütunlar hedef veri kümesine eklenir. Veri kümelerini birleştirme, yerel bir veri kümeniz olduğunda ve başka bir uygulamadan ikinci bir veri kümesi alırsanız faydalıdır. Ayrıca, bir XML Web hizmeti gibi bir bileşenden veya birden çok veri kümesinden verileri tümleştirmeniz gerektiğinde de yararlı olur.

 Veri kümelerini birleştirirken, `preserveChanges` <xref:System.Data.DataSet.Merge%2A> yöntemi hedef veri kümesinde var olan değişikliklerin tutulması gerekip gerekmediğini belirten bir Boole bağımsız değişkeni () geçirebilirsiniz. Veri kümeleri kayıtların birden çok sürümünü koruduğundan, kayıtların birden fazla sürümünün birleştirildiğini aklınızda bulundurmanız önemlidir. Aşağıdaki tabloda, iki veri kümesi içindeki bir kaydın nasıl birleştirileceği gösterilmektedir:

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
|--------------------|--------------------|--------------------|
|Özgün|James Wilson|James C. Solson|
|Geçerli|Jim Wilson|James C. Solson|

 <xref:System.Data.DataSet.Merge%2A>Önceki tabloda yöntemi, aşağıdaki sonuçları ile çağırma `preserveChanges=false targetDataset.Merge(sourceDataset)` :

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
|--------------------|--------------------|--------------------|
|Özgün|James C. Solson|James C. Solson|
|Geçerli|James C. Solson|James C. Solson|

 <xref:System.Data.DataSet.Merge%2A>Yöntemi `preserveChanges = true targetDataset.Merge(sourceDataset, true)` aşağıdaki sonuçlarla birlikte çağrılıyor:

|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|
|--------------------|--------------------|--------------------|
|Özgün|James C. Solson|James C. Solson|
|Geçerli|Jim Wilson|James C. Solson|

> [!CAUTION]
> `preserveChanges = true`Senaryoda, <xref:System.Data.DataSet.RejectChanges%2A> yöntemi hedef veri kümesindeki bir kayıt üzerinde çağrılırsa, *kaynak* veri kümesindeki özgün verilere geri döner. Bu, özgün veri kaynağını hedef veri kümesiyle güncelleştirmeye çalışırsanız, güncelleştirilecek orijinal satırı bulamayabilir. Farklı bir veri kümesini veri kaynağından güncelleştirilmiş kayıtlarla doldurarak ve ardından bir eşzamanlılık ihlalinden kaçınmak için birleştirme gerçekleştirerek eşzamanlılık ihlalini engelleyebilirsiniz. (Veri kümesi doldurulduktan sonra, başka bir kullanıcı veri kaynağındaki bir kaydı değiştirdiğinde eşzamanlılık ihlali oluşur.)

## <a name="update-constraints"></a>Güncelleştirme kısıtlamaları
 Var olan bir veri satırında değişiklik yapmak için, sütunları ayrı sütunlara ekleyin veya güncelleştirin. Veri kümesi kısıtlamalar içeriyorsa (örneğin, yabancı anahtarlar veya null yapılamayan kısıtlamalar), bu kayıt sizin güncelleştirdiğinde geçici olarak bir hata durumunda olabilir. Diğer bir deyişle, bir sütunun güncelleştirilmesini tamamladıktan sonra, bir sonrakine geçmeden önce bir hata durumunda olabilir.

 Zamanından önce kısıtlama ihlallerini engellemek için, güncelleştirme kısıtlamalarını geçici olarak askıya alabilirsiniz. Bu iki amaca hizmet eder:

- Bir sütunun güncelleştirilmesini tamamladıktan sonra, başka bir sütunu güncelleştirmeden sonra bir hatanın oluşturulmasını engeller.

- Belirli güncelleştirme olaylarının oluşturulmasını engeller (genellikle doğrulama için kullanılan olaylar).

  Bir güncelleştirmeyi tamamladıktan sonra, ayrıca güncelleştirme olaylarını yeniden etkinleştiren ve bunları başlatan kısıtlama denetimini yeniden etkinleştirebilirsiniz.

> [!NOTE]
> Windows Forms, DataGrid içinde yerleşik veri bağlama mimarisi, odak bir satırın dışına çıkana kadar kısıtlama denetimini askıya alır ve açıkça <xref:System.Data.DataRow.BeginEdit%2A> ,, <xref:System.Data.DataRow.EndEdit%2A> veya yöntemlerini çağırmanız gerekmez <xref:System.Data.DataRow.CancelEdit%2A> .

 <xref:System.Data.DataSet.Merge%2A>Yöntem bir veri kümesi üzerinde çağrıldığında kısıtlamalar otomatik olarak devre dışıdır. Birleştirme tamamlandığında, veri kümesinde etkinleştirilemez bir kısıtlama varsa, bir <xref:System.Data.ConstraintException> oluşturulur. Bu durumda, <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği olarak ayarlanır `false,` ve özelliği öğesine sıfırlamadan önce tüm kısıtlama ihlalleri çözümlenmelidir <xref:System.Data.DataSet.EnforceConstraints%2A> `true` .

 Bir güncelleştirmeyi tamamladıktan sonra, ayrıca güncelleştirme olaylarını yeniden etkinleştiren ve bunları başlatan kısıtlama denetimini yeniden etkinleştirebilirsiniz.

 Olayları askıya alma hakkında daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](../data-tools/turn-off-constraints-while-filling-a-dataset.md)kapatma.

## <a name="dataset-update-errors"></a>Veri kümesi güncelleştirme hataları
 Bir veri kümesindeki bir kaydı güncelleştirdiğinizde bir hata olasılığı vardır. Örneğin, yanlışlıkla yanlış türde verileri veya çok uzun verileri veya başka bir bütünlük sorunu olan verileri istemeden yazabilirsiniz. Ya da bir güncelleştirme olayının herhangi bir aşamasında özel hatalar oluşturabilen uygulamaya özgü doğrulama denetimlerine sahip olabilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Değişikliklerle ilgili bilgileri koruma
 Bir veri kümesindeki değişikliklerle ilgili bilgiler iki şekilde tutulur: değiştirildikleri ( <xref:System.Data.DataRow.RowState%2A> ) ve bir kaydın birden çok kopyasını tutarak () ve bir kaydın birden çok kopyasını tutarak satırlara bayrak koyarak <xref:System.Data.DataRowVersion> . Süreçler, bu bilgileri kullanarak veri kümesinde nelerin değiştiğini belirleyebilir ve uygun güncelleştirmeleri veri kaynağına gönderebilir.

### <a name="rowstate-property"></a>RowState özelliği
 <xref:System.Data.DataRow.RowState%2A>Bir nesnenin özelliği, <xref:System.Data.DataRow> belirli bir veri satırının durumu hakkında bilgi sağlayan bir değerdir.

 Aşağıdaki tabloda, sabit listesinin olası değerlerinin ayrıntıları verilmiştir <xref:System.Data.DataRowState> :

|DataRowState değeri|Description|
|------------------------|-----------------|
|<xref:System.Data.DataRowState>|Satır, öğesine bir öğe olarak eklenmiştir <xref:System.Data.DataRowCollection> . (Son yöntem çağrıldığında mevcut olmadığından, bu durumdaki bir satır karşılık gelen orijinal bir sürüme sahip değildir <xref:System.Data.DataRow.AcceptChanges%2A> ).|
|<xref:System.Data.DataRowState>|Satır, bir nesnesi kullanılarak silindi <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> .|
|<xref:System.Data.DataRowState>|Satır oluşturuldu ancak hiç bir parçası değil <xref:System.Data.DataRowCollection> . Bir <xref:System.Data.DataRow> nesne, oluşturulduktan hemen sonra, bir koleksiyona eklendikten önce ve bir koleksiyondan kaldırıldıktan sonra bu durumda olur.|
|<xref:System.Data.DataRowState>|Satırdaki bir sütun değeri bir şekilde değiştirildi.|
|<xref:System.Data.DataRowState>|Satır <xref:System.Data.DataRow.AcceptChanges%2A> son çağrılmasından bu yana değiştirilmedi.|

### <a name="datarowversion-enumeration"></a>DataRowVersion numaralandırması
 Veri kümeleri kayıtların birden çok sürümünü tutar. <xref:System.Data.DataRowVersion>Bir nesnenin numaralandırması, <xref:System.Data.DataRow> bir nesnenin belirli bir sürümünü döndürmek için kullanılan bir değerdir <xref:System.Data.DataRow> .

 Aşağıdaki tabloda, sabit listesinin olası değerlerinin ayrıntıları verilmiştir <xref:System.Data.DataRowVersion> :

|DataRowVersion değeri|Description|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion>|Bir kaydın geçerli sürümü, en son çağrılmasından bu yana kayıtta gerçekleştirilen tüm değişiklikleri içerir <xref:System.Data.DataRow.AcceptChanges%2A> . Satır silinmişse, geçerli sürüm yoktur.|
|<xref:System.Data.DataRowVersion>|Bir kaydın veri kümesi şeması veya veri kaynağı tarafından tanımlanan varsayılan değeri.|
|<xref:System.Data.DataRowVersion>|Bir kaydın orijinal sürümü, veri kümesinde son değişiklikler işlendiği için kaydın bir kopyasıdır. Pratik koşullarda, bu genellikle bir veri kaynağından okunan bir kaydın sürümüdür.|
|<xref:System.Data.DataRowVersion>|Bir güncelleştirmenin ortasındayken geçici olarak kullanılabilir olan bir kaydın önerilen sürümü; Yani, <xref:System.Data.DataRow.BeginEdit%2A> yöntemi ve <xref:System.Data.DataRow.EndEdit%2A> yöntemi ile metodu arasında. Genellikle, gibi bir olay için bir işleyicide bir kaydın önerilen sürümüne erişirsiniz <xref:System.Data.DataTable.RowChanging> . Yöntemi çağırmak <xref:System.Data.DataRow.CancelEdit%2A> değişiklikleri tersine çevirir ve veri satırının önerilen sürümünü siler.|

 Özgün ve güncel sürümler, güncelleştirme bilgileri bir veri kaynağına aktarıldığında yararlı olur. Genellikle, veri kaynağına bir güncelleştirme gönderildiğinde, veritabanının yeni bilgileri bir kaydın geçerli sürümüdür. Özgün sürümden alınan bilgiler güncelleştirilecek kaydı bulmak için kullanılır.

 Örneğin, bir kaydın birincil anahtarının değiştirildiği bir durumda, değişiklikleri güncelleştirmek için veri kaynağında doğru kaydı bulmanız için bir yol gerekir. Özgün sürüm yoksa, kayıt büyük olasılıkla veri kaynağına eklenebilir, bu da yalnızca fazladan istenmeyen bir kayıtta değil, hatalı ve güncel olmayan bir kayıtta olur. Eşzamanlılık denetiminde iki sürüm de kullanılır. Kayıt kümesine yüklendikten sonra kaydın değişip değişmediğini öğrenmek için özgün sürümü veri kaynağındaki bir kayıtla karşılaştırarak karşılaştırabilirsiniz.

 Önerilen sürüm, değişiklikleri aslında veri kümesine kaydetmeden önce doğrulama gerçekleştirmeniz gerektiğinde faydalıdır.

 Kayıtlar değişmiş olsa bile, bu satırın her zaman orijinal veya güncel sürümü yoktur. Tabloya yeni bir satır eklediğinizde, özgün sürüm yoktur, yalnızca geçerli bir sürümdür. Benzer şekilde, tablonun yöntemini çağırarak bir satırı silerseniz `Delete` , orijinal bir sürüm vardır ancak geçerli sürüm yoktur.

 Bir veri satırının metodunu sorgulayarak bir kaydın belirli bir sürümünün mevcut olup olmadığını görmek için test edebilirsiniz <xref:System.Data.DataRow.HasVersion%2A> . Bir <xref:System.Data.DataRowVersion> sütunun değerini istediğinizde bir numaralandırma değerini isteğe bağlı bağımsız değişken olarak geçirerek, bir kaydın her iki sürümüne erişebilirsiniz.

## <a name="getting-changed-records"></a>Değiştirilen kayıtları alma
 Bir veri kümesindeki her kaydı güncelleştirmeme yaygın bir uygulamadır. Örneğin, bir Kullanıcı <xref:System.Windows.Forms.DataGridView> birçok kayıt görüntüleyen bir Windows Forms denetimiyle çalışıyor olabilir. Ancak, Kullanıcı yalnızca birkaç kaydı güncelleştirebilir, bir tane silebilir ve yeni bir tane ekleyebilir. Veri kümeleri ve veri tabloları `GetChanges` yalnızca değiştirilen satırları döndürmek için bir Yöntem () sağlar.

 `GetChanges`Veri tablosunun () ya da veri kümesinin () yöntemini kullanarak değiştirilen kayıtların alt kümelerini oluşturabilirsiniz <xref:System.Data.DataTable.GetChanges%2A> <xref:System.Data.DataSet.GetChanges%2A> . Veri tablosu için yöntemini çağırırsanız, yalnızca değiştirilen kayıtlarla tablonun bir kopyasını döndürür. Benzer şekilde, yöntemi veri kümesinde çağırırsanız, içinde yalnızca değiştirilmiş kayıtları olan yeni bir veri kümesi alırsınız.

 `GetChanges` tek başına değiştirilen tüm kayıtları döndürür. Buna karşılık, istenen <xref:System.Data.DataRowState> bir parametre olarak yöntemine bir parametre olarak geçirerek `GetChanges` , hangi değiştirilen kayıtların hangi alt kümesini istediğinizi belirtebilirsiniz: yeni eklenen kayıtlar, silinmek üzere işaretlenmiş kayıtlar, ya da değiştirilen kayıtlar.

 Değiştirilen kayıtların bir alt kümesini almak, kayıtları işlemek için başka bir bileşene göndermek istediğinizde faydalıdır. Veri kümesinin tamamını göndermek yerine, yalnızca bileşenin ihtiyaç duyacağı kayıtları alarak diğer bileşenle iletişim yükünü azaltabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: değiştirilen satırları alma](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

## <a name="committing-changes-in-the-dataset"></a>Veri kümesinde değişiklikler yürütülüyor
 Veri kümesinde değişiklik yapıldıkça, <xref:System.Data.DataRow.RowState%2A> değiştirilen satırların özelliği ayarlanır. Kayıtların orijinal ve geçerli sürümleri oluşturulur, tutulur ve özelliği tarafından kullanılabilir hale getirilir <xref:System.Data.DataRowView.RowVersion%2A> . Bu değiştirilen satırların özelliklerinde depolanan meta veriler, doğru güncelleştirmelerin veri kaynağına gönderilmesi için gereklidir.

 Değişiklikler veri kaynağının geçerli durumunu yansıttığından, bu bilgileri artık sürdürmenize gerek kalmaz. Genellikle, veri kümesi ve kaynağı eşitlenmiş olduğunda iki zaman vardır:

- Verileri veri kümesine yükledikten hemen sonra (örneğin, kaynaktan veri okurken).

- Veri kümesindeki değişiklikleri veri kaynağına gönderdikten sonra (daha önce değil, değişiklikleri veritabanına göndermek için gereken değişiklik bilgilerini kaybedeceğinizi).

  Yöntemi çağırarak, bekleyen değişiklikleri veri kümesine kaydedebilirsiniz <xref:System.Data.DataSet.AcceptChanges%2A> . Genellikle, <xref:System.Data.DataSet.AcceptChanges%2A> uygulamanızda aşağıdaki saatlerde çağrılır.

- Veri kümesini yükledikten sonra. Bir TableAdapter metodunu çağırarak bir veri kümesi yüklerseniz `Fill` , bağdaştırıcı sizin için değişiklikleri otomatik olarak kaydeder. Ancak, başka bir veri kümesini içine birleştirerek bir veri kümesini yüklerseniz, değişiklikleri el ile yürütmeniz gerekir.

  > [!NOTE]
  > Bağdaştırıcının özelliğini olarak ayarlayarak, yöntemi çağırdığınızda bağdaştırıcının otomatik olarak değişiklikleri almasını engelleyebilirsiniz `Fill` `AcceptChangesDuringFill` `false` . Olarak ayarlanırsa `false` , <xref:System.Data.DataRow.RowState%2A> Fill sırasında eklenen her satır için olarak ayarlanır <xref:System.Data.DataRowState> .

- Veri kümesi değişikliklerini bir XML Web hizmeti gibi başka bir işleme gönderdikten sonra.

  > [!CAUTION]
  > Değişikliği bu şekilde yürütmek, değişiklik bilgilerini siler. Uygulamanızın veri kümesinde hangi değişikliklerin yapıldığını bilmesini gerektiren işlemleri gerçekleştirmeyi bitirene kadar değişiklikleri yürütmeyin.

  Bu yöntem şunları gerçekleştirir:

- <xref:System.Data.DataRowVersion>Bir kaydın sürümünü <xref:System.Data.DataRowVersion> sürümüne yazar ve özgün sürümün üzerine yazar.

- Özelliğin ayarlandığı tüm satırları kaldırır <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> .

- <xref:System.Data.DataRow.RowState%2A>Bir kaydın özelliğini olarak ayarlar <xref:System.Data.DataRowState> .

  <xref:System.Data.DataSet.AcceptChanges%2A>Yöntemi üç düzeyde kullanılabilir. <xref:System.Data.DataRow>Yalnızca söz konusu satır için değişiklikleri yürütmeleri için bir nesne üzerinde çağırabilirsiniz. Ayrıca, <xref:System.Data.DataTable> bir tablodaki tüm satırları yürütmek için bir nesne üzerinde çağırabilirsiniz. Son olarak, <xref:System.Data.DataSet> veri kümesinin tüm tablolarındaki tüm kayıtlarda bekleyen tüm değişiklikleri kaydetmek için nesneyi nesne üzerinde çağırabilirsiniz.

  Aşağıdaki tabloda, yöntemin hangi nesneye çağrıldığı üzerinde hangi değişikliklerin yürütüldüğü açıklanmaktadır.

|Yöntem|Sonuç|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler yalnızca belirli bir satıra kaydedilir.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, belirli bir tablodaki tüm satırlara kaydedilir.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, veri kümesinin tüm tablolarındaki tüm satırlara kaydedilir.|

> [!NOTE]
> Bir TableAdapter metodunu çağırarak bir veri kümesi yüklüyorsanız `Fill` , değişiklikleri açıkça kabul etmeniz gerekmez. Varsayılan olarak yöntemi, `Fill` `AcceptChanges` veri tablosunu doldurmayı tamamladıktan sonra yöntemini çağırır.

 İlgili bir yöntem, `RejectChanges` <xref:System.Data.DataRowVersion> sürümü yeniden kayıt sürümüne kopyalayarak değişikliklerin etkisini geri alır <xref:System.Data.DataRowVersion> . Ayrıca, <xref:System.Data.DataRow.RowState%2A> her kaydın öğesini öğesine geri ayarlar <xref:System.Data.DataRowState> .

## <a name="data-validation"></a>Veri doğrulama
 Uygulamanızdaki verilerin geçirildiği işlemlerin gereksinimlerini karşıladığından emin olmak için, genellikle doğrulama eklemeniz gerekir. Bu, bir kullanıcının formundaki girişinin doğru olup olmadığını, başka bir uygulama tarafından uygulamanıza gönderilen verileri doğrulamayı ve hatta bileşeninizin içinde hesaplanan bilgilerin veri kaynağı ve uygulama gereksinimlerinizin kısıtlamaları dahilinde olup olmadığını kontrol etmeyi gerektirebilir.

 Verileri çeşitli yollarla doğrulayabilirsiniz:

- İş katmanında, verileri doğrulamak için uygulamanıza kod ekleyerek. Veri kümesi, bunu yapabileceğiniz bir yerdir. DataSet Designer, arka uç doğrulamanın avantajlarından bazılarını sağlar — örneğin, değişiklikleri sütun olarak doğrulama özelliği ve satır değerleri değişiyor. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

- Sunu katmanında, formlara doğrulama ekleyerek. Daha fazla bilgi için [Windows Forms Içindeki Kullanıcı giriş doğrulaması](https://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1)konusuna bakın.

- Veri arka ucunda, veri kaynağına veri göndererek — Örneğin, veritabanı — ve bu verilerin verileri kabul etmesine veya reddetmesine izin verir. Verileri doğrulamak ve hata bilgileri sağlamak için karmaşık tesislere sahip bir veritabanıyla çalışıyorsanız, veri nereden geldiği bağımsız olarak verileri doğrulayabilmeniz için bu pratik bir yaklaşım olabilir. Ancak, bu yaklaşım uygulamaya özgü doğrulama gereksinimlerine uyum sağlayabilir. Ayrıca, veri kaynağı verilerinin doğrulanması, uygulamanızın arka uçta oluşan doğrulama hatalarının çözümlenmesini nasıl kolaylaştırdığına bağlı olarak veri kaynağına çok sayıda gidiş dönüşine yol açabilir.

  > [!IMPORTANT]
  > Olarak ayarlanmış bir özellik ile veri komutları kullanırken <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> <xref:System.Data.CommandType> , veritabanınıza geçirmeden önce istemciden gönderilen bilgileri dikkatle kontrol edin. Kötü niyetli kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar vermek için bir denemeye değiştirilmiş veya ek SQL deyimleri göndermeye (eklemeye) çalışabilir. Kullanıcı girişini bir veritabanına aktarmadan önce, bilgilerin geçerli olduğunu her zaman doğrulayın. Mümkün olduğunda her zaman parametreli sorguları veya saklı yordamları kullanmak en iyi uygulamadır. Daha fazla bilgi için bkz. [komut dosyası açıklardan genel bakış](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

  Bir veri kümesinde değişiklik yapıldıktan sonra, değişiklikleri bir veri kaynağına aktarabilirsiniz. En yaygın olarak, bunu `Update` bir TableAdapter (veya veri bağdaştırıcısı) yöntemini çağırarak yapabilirsiniz. Yöntemi bir veri tablosundaki her kayıt için döngü yapar, varsa ne tür bir güncelleştirme gerektiğini (güncelleştirme, ekleme veya silme) belirler ve ardından uygun komutu çalıştırır.

## <a name="transmitting-updates-to-the-data-source"></a>Güncelleştirmeler veri kaynağına iletiliyor
 Güncelleştirmelerin nasıl yapıldığını gösteren bir çizim olarak, uygulamanızın tek bir veri tablosu içeren bir veri kümesi kullandığını varsayalım. Uygulama, veritabanından iki satır getirir. Alma işleminden sonra, bellek içi veri tablosu şöyle görünür:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Uygulamanız Gamze Uludağ 'ın durumunu "tercih edilen" olarak değiştiriyor. Bu değişikliğin sonucu olarak, bu <xref:System.Data.DataRow.RowState%2A> satırın özelliğinin değeri olarak değişir <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> . <xref:System.Data.DataRow.RowState%2A>İlk satırın özelliğinin değeri kalır <xref:System.Data.DataRowState> . Veri tablosu şu şekilde görünür:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Uygulamanız şimdi `Update` veri kümesini veritabanına aktarma yöntemini çağırır. Yöntemi her satırı sırayla inceler. İlk satır için, bu satır veritabanından getirilmesinden bu yana değişmediğinden, yöntemi veritabanına hiçbir SQL ifadesini iletir.

 Ancak ikinci satır için, `Update` yöntemi otomatik olarak doğru veri komutunu çağırır ve veritabanına iletir. SQL ifadesinin belirli sözdizimi, temel alınan veri deposu tarafından desteklenen SQL 'in lehçine bağlıdır. Ancak aktarılan SQL ifadesinin aşağıdaki genel nitelikleri önemli değildir:

- Aktarılan SQL deyimleri bir UPDATE deyimidir. Özelliğin değeri olduğundan, bağdaştırıcı bir UPDATE ifadesini kullanmayı bilir <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> .

- İletilen SQL deyimi, UPDATE ifadesinin hedefinin WHERE satırı olduğunu gösteren bir WHERE yan tümcesi içerir `CustomerID = 'c400'` . SELECT ifadesinin bu bölümü, hedef tablonun birincil anahtarı olduğundan, hedef satırı diğerlerinden ayırır `CustomerID` . WHERE yan tümcesinin bilgileri, kaydın () orijinal sürümünden türetilir `DataRowVersion.Original` . bu durum, satırı tanımlamak için gereken değerlerin değişmiş olması durumunda.

- Aktarılan SQL deyimi, değiştirilen sütunların yeni değerlerini ayarlamak için SET yan tümcesini içerir.

    > [!NOTE]
    > TableAdapter 'ın `UpdateCommand` özelliği bir saklı yordamın adına ayarlandıysa, bağdaştırıcı BIR SQL açıklaması oluşturmaz. Bunun yerine, saklı yordamı geçirilen uygun parametrelerle çağırır.

## <a name="passing-parameters"></a>Parametreleri geçirme
 Genellikle, veritabanında güncelleştirileceği kayıtların değerlerini geçirmek için parametreleri kullanırsınız.  TableAdapter 'ın `Update` yöntemi BIR Update ifadesini çalıştırdığında parametre değerlerini doldurması gerekir. Bu değerleri `Parameters` , uygun veri komutuna ait koleksiyondan alır — bu durumda `UpdateCommand` TableAdapter içindeki nesne.

 Veri bağdaştırıcısı oluşturmak için Visual Studio araçlarını kullandıysanız, `UpdateCommand` nesnesi, deyimindeki her bir parametre yer tutucusuna karşılık gelen parametrelerin bir koleksiyonunu içerir.

 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>Her parametrenin özelliği, veri tablosundaki bir sütuna işaret eder. Örneğin, `SourceColumn` `au_id` ve parametrelerinin özelliği, `Original_au_id` veri tablosundaki yazar kimliğini içeren herhangi bir sütun olarak ayarlanır. Bağdaştırıcının `Update` yöntemi çalıştırıldığında, güncelleştirilmekte olan kayıttaki yazar kimliği sütununu okur ve değerleri deyimle doldurur.

 Bir UPDATE ifadesinde, hem yeni değerleri (kayda yazılacak olanlar) hem de eski değerleri (kaydın veritabanında konumlandırılabilir olması için) belirtmeniz gerekir. Bu nedenle, her bir değer için iki parametre vardır: SET yan tümcesi ve WHERE yan tümcesi için farklı bir tane. Her iki parametre de, güncelleştirilmekte olan kayıttan verileri okur, ancak parametrenin [SqlParameter. SourceVersion özelliğine](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)göre sütun değerinin farklı sürümlerini alırlar. SET yan tümcesinin parametresi geçerli sürümü alır ve WHERE yan tümcesinin parametresi orijinal sürümü alır.

> [!NOTE]
> Ayrıca `Parameters` , koleksiyondaki değerleri, genellikle veri bağdaştırıcısının olayına bir olay işleyicide yapacağınız kodda da ayarlayabilirsiniz <xref:System.Data.DataTable.RowChanging> .

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md) [Visual Studio 'da veri bağlama denetimleri](../data-tools/bind-controls-to-data-in-visual-studio.md) [almak için uygulamanızı hazırlama](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [verileri doğrulama](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
