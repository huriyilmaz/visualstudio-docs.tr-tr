---
title: Hiyerarşik güncelleştirme
description: Bilgi tutarlılığı kurallarını koruyarak güncelleştirilmiş verilerin (2 + ilişkili tabloları olan bir veri kümesinden) bir VERITABANıNA geri kaydedilmesini içeren hiyerarşik güncelleştirmeleri gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bfc0c1ca96f5bf6ce58a1b7df9ad0ea10f283e1e
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435162"
---
# <a name="hierarchical-update"></a>Hiyerarşik güncelleştirme

*Hiyerarşik güncelleştirme* , bilgi tutarlılığı kurallarını koruyarak güncelleştirilmiş verileri (iki veya daha fazla ilişkili tablo içeren bir veri kümesinden) veritabanına geri kaydetme sürecini ifade eder. *Başvurusal bütünlük* , bir veritabanında ilgili kayıtları ekleme, güncelleştirme ve silme davranışlarını denetleyen kısıtlamalar tarafından belirtilen tutarlılık kurallarına başvurur. Örneğin, bu müşteri için siparişlerin oluşturulmasına izin vermeden önce müşteri kaydının oluşturulmasını zorlayan bilgi tutarlılığı vardır.  Veri kümelerinde ilişkiler hakkında daha fazla bilgi için bkz. [veri kümelerinde ilişkiler](../data-tools/relationships-in-datasets.md).

Hiyerarşik güncelleştirme özelliği `TableAdapterManager` , `TableAdapter` türü belirlenmiş bir veri kümesindeki s 'yi yönetmek için bir kullanır. `TableAdapterManager`Bileşen, .NET türü değil, Visual Studio tarafından oluşturulan bir sınıftır. **Veri kaynakları** penceresinden bir tabloyu bir Windows form veya WPF sayfasına sürüklediğinizde, Visual Studio form veya sayfaya TableAdapterManager türünde bir değişken ekler ve onu bileşen tepsisinde tasarımcıda görürsünüz. Sınıfıyla ilgili ayrıntılı bilgi için `TableAdapterManager` bkz. TableAdapterManager Reference bölümü [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

Varsayılan olarak, bir veri kümesi ilgili tabloları "yalnızca ilişkiler" olarak değerlendirir ve bu, yabancı anahtar kısıtlamalarını Zorlamayacağı anlamına gelir. Bu ayarı tasarım zamanında **veri kümesi Tasarımcısı** kullanarak değiştirebilirsiniz. **İlişki** iletişim kutusunu açmak için iki tablo arasındaki ilişki satırını seçin. Burada yaptığınız değişiklikler, `TableAdapterManager` ilgili tablolardaki değişiklikleri veritabanına geri gönderirken nasıl davranacağını belirleyeceğini tespit eder.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Veri kümesinde hiyerarşik güncelleştirmeyi etkinleştirme

Varsayılan olarak, Hiyerarşik güncelleştirme bir projede eklenen veya oluşturulan tüm yeni veri kümeleri için etkindir. Veri kümesindeki bir türü belirtilmiş veri kümesinin **Hiyerarşik güncelleştirme** özelliğini **true** veya **false** olarak ayarlayarak hiyerarşik güncelleştirmeyi açın veya kapatın:

![Hiyerarşik güncelleştirme ayarı](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Tablolar arasında yeni bir ilişki oluşturma

İki tablo arasında yeni bir ilişki oluşturmak için, Veri Kümesi Tasarımcısı her tablonun başlık çubuğunu seçin, sonra sağ tıklayıp **Ilişki Ekle** ' yi seçin.

![Hiyerarşik güncelleştirme ilişki Ekle menüsü](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Yabancı anahtar kısıtlamalarını, basamaklı güncelleştirmeleri ve silmeleri anlayın

Veritabanındaki yabancı anahtar kısıtlamalarının ve basamaklı davranışın oluşturulan veri kümesi kodunda nasıl oluşturulduğunu anlamak önemlidir.

Varsayılan olarak, bir veri kümesindeki veri tabloları, <xref:System.Data.DataRelation> veritabanındaki ilişkilerle eşleşen ilişkiler () ile oluşturulur. Ancak, veri kümesindeki ilişki yabancı anahtar kısıtlaması olarak oluşturulmaz. <xref:System.Data.DataRelation>Yalnızca veya etkin olmadan **ilişki** olarak yapılandırılır <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> .

Varsayılan olarak, veritabanı ilişkisi basamaklı güncelleştirmeler ve/veya basamaklı silme açık olarak ayarlanmış olsa bile, basamaklı güncelleştirmeler ve basamaklı silmeler kapalıdır. Örneğin, yeni bir müşteri ve yeni bir sipariş oluşturup verileri kaydetmeye çalışmak, veritabanında tanımlanan yabancı anahtar kısıtlamalarına bir çakışmaya neden olabilir. Daha fazla bilgi için bkz. [veri kümesini doldururken kısıtlamaları](turn-off-constraints-while-filling-a-dataset.md)kapatma.

## <a name="set-the-order-to-perform-updates"></a>Güncelleştirme yapmak için sırayı ayarlama

Güncelleştirme yapılacak sırayı ayarlamak, tüm değiştirilen verileri bir veri kümesinin tüm tablolarında kaydetmek için gereken tek tek ekleme, güncelleştirme ve silme sırasını ayarlar. Hiyerarşik güncelleştirme etkinleştirildiğinde, önce ekleme yapılır, sonra güncelleştirmeler yapılır ve sonra silinir. , `TableAdapterManager` `UpdateOrder` Önce güncelleştirmeleri gerçekleştirmek üzere ayarlanabilir bir özellik sağlar, sonra ekler ve sonra siler.

> [!NOTE]
> Güncelleştirme sırasının tümünün dahil olduğunu anlamak önemlidir. Diğer bir deyişle, güncelleştirmeler gerçekleştirildiğinde, veri kümesindeki tüm tablolar için ekleme ve silme işlemi gerçekleştirilir.

Özelliği ayarlamak için `UpdateOrder` , [veri kaynakları penceresinden](add-new-data-sources.md#data-sources-window) öğeleri bir form üzerine sürükledikten sonra `TableAdapterManager` bileşen tepsisinde öğesini seçin ve ardından `UpdateOrder` **Özellikler** penceresinde özelliğini ayarlayın.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Hiyerarşik bir güncelleştirme gerçekleştirmeden önce bir veri kümesinin yedek kopyasını oluşturma

Verileri kaydettiğinizde ( `TableAdapterManager.UpdateAll()` yöntemini çağırarak), `TableAdapterManager` her tablo için verileri tek bir işlemde güncelleştirmeyi dener. Herhangi bir tablo için güncelleştirmenin herhangi bir bölümü başarısız olursa, tüm işlem geri alınır. Çoğu durumda, geri alma uygulamanızı özgün durumuna geri döndürür.

Ancak, bazen veri kümesini yedek kopyadan geri yüklemek isteyebilirsiniz. Otomatik artış değerlerini kullandığınızda bu durum oluşabilir. Örneğin, bir Kaydet işlemi başarılı olmazsa, otomatik artırma değerleri veri kümesinde sıfırlanmaz ve veri kümesi otomatik artan değerler oluşturmaya devam eder. Bu, uygulamanızda kabul edilebilir olabilecek bir boşluk bırakır. Bunun bir sorun olduğu durumlarda, `TableAdapterManager` `BackupDataSetBeforeUpdate` işlem başarısız olursa, var olan veri kümesini bir yedek kopyasıyla değiştiren bir özellik sağlar.

> [!NOTE]
> Yedekleme kopyası yalnızca, yöntem çalışırken bellekte bulunur `TableAdapterManager.UpdateAll` . Bu nedenle, bu yedekleme veri kümesine programlı erişim yoktur çünkü bu, özgün veri kümesini değiştirir veya `TableAdapterManager.UpdateAll` Yöntem çalışmayı bitirdiğinde kapsam dışına çıkar.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Hiyerarşik güncelleştirmeyi gerçekleştirmek için oluşturulan kaydetme kodunu değiştirin

`TableAdapterManager.UpdateAll`Yöntemini çağırarak ve ilgili tabloları içeren veri kümesinin adını geçirerek veri kümesindeki ilgili veri tablolarından değişiklikleri veritabanına kaydedin. Örneğin, `TableAdapterManager.UpdateAll(NorthwindDataset)` NorthwindDataSet 'teki tüm tablolardaki güncelleştirmeleri arka uç veritabanına göndermek için yöntemini çalıştırın.

Öğeleri **veri kaynakları** penceresinden bıraktığınızda, `Form_Load` her bir tabloyu (Yöntemler) doldurmak için olaya otomatik olarak kod eklenir `TableAdapter.Fill` . Kod, **Save** <xref:System.Windows.Forms.BindingNavigator> veri kümesinden veritabanına geri veri kaydetmek Için ' ın Kaydet düğmesine tıklama olayına de eklenir ( `TableAdapterManager.UpdateAll` yöntemi).

Oluşturulan kaydetme kodu, yöntemi çağıran bir kod satırı da içerir `CustomersBindingSource.EndEdit` . Özellikle, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> forma eklenen ilk öğesinin yöntemini çağırır <xref:System.Windows.Forms.BindingSource> . Diğer bir deyişle, bu kod yalnızca **veri kaynakları** penceresinden form üzerine sürüklenen ilk tablo için oluşturulur. <xref:System.Windows.Forms.BindingSource.EndEdit%2A>Çağrı, şu anda düzenlenmekte olan herhangi bir veri bağlantılı denetimlerde işlemdeki tüm değişiklikleri kaydeder. Bu nedenle, bir veri bağlantılı denetim hala odağa sahipse ve **Kaydet** düğmesine tıklarsanız, o denetimdeki tüm bekleyen düzenlemeler gerçek kaydetme işleminden ( `TableAdapterManager.UpdateAll` yöntemi) önce işlenir.

> [!NOTE]
> **Veri kümesi Tasarımcısı** , yalnızca `BindingSource.EndEdit` form üzerine bırakılan ilk tablonun kodunu ekler. Bu nedenle, `BindingSource.EndEdit` formdaki her ilgili tablo için yöntemi çağırmak üzere bir kod satırı eklemeniz gerekir. Bu izlenecek yol için, metoda bir çağrı eklemeniz gerektiği anlamına gelir `OrdersBindingSource.EndEdit` .

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Kodu kaydedilmeden önce ilgili tablolardaki değişiklikleri yürütmek üzere güncelleştirmek için

1. Kod düzenleyicisinde Form1 ' i açmak için üzerinde **Kaydet** düğmesine çift tıklayın <xref:System.Windows.Forms.BindingNavigator> . **Form1**

2. Yöntemi `OrdersBindingSource.EndEdit` çağıran satırdan sonra yöntemi çağırmak için bir kod satırı ekleyin `CustomersBindingSource.EndEdit` . **Kaydet** düğmesine tıklama olayının kodu aşağıdakine benzemelidir:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Verileri bir veritabanına kaydetmeden önce ilişkili bir alt tabloya değişiklikleri kaydetmenin yanı sıra, yeni alt kayıtları bir veri kümesine eklemeden önce yeni oluşturulan üst kayıtları da kaydetmeniz gerekebilir. Diğer bir deyişle, `Customer` yabancı anahtar kısıtlamaları `Orders` veri kümesine eklenmek üzere yeni alt kayıtları () etkinleştirmeden önce, yeni üst kayıt () veri kümesine eklemeniz gerekebilir. Bunu başarmak için alt `BindingSource.AddingNew` olayı kullanabilirsiniz.

> [!NOTE]
> Yeni üst kayıtları yürütmeniz gerekip gerekmediğini, veri kaynağınıza bağlamak için kullanılan denetimin türüne bağlıdır. Bu kılavuzda, üst tabloya bağlamak için tek tek denetimleri kullanırsınız. Bu, yeni üst kaydı yürütmek için ek kod gerektirir. Üst kayıtlar bunun gibi karmaşık bir bağlama denetiminde görüntüleniyorsa <xref:System.Windows.Forms.DataGridView> , <xref:System.Windows.Forms.BindingSource.EndEdit%2A> üst kayıt için bu ek çağrı gerekli değildir. Bunun nedeni, denetimin temel alınan veri bağlama işlevselliğinin yeni kayıtların yerine işlemesini işlemektedir.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Yeni alt kayıtlar eklemeden önce veri kümesindeki üst kayıtları yürütmek üzere kod eklemek için

1. Olay için bir olay işleyicisi oluşturun `OrdersBindingSource.AddingNew` .

    - Tasarım görünümünde **Form1** ' i açın, bileşen tepsisinde **OrdersBindingSource** ' u seçin, **Özellikler** penceresinde **Olaylar** ' ı seçin ve ardından **AddingNew** olayına çift tıklayın.

2. Yöntemi çağıran olay işleyicisine bir kod satırı ekleyin `CustomersBindingSource.EndEdit` . `OrdersBindingSource_AddingNew`Olay işleyicisindeki kod aşağıdakine benzemelidir:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu

Varsayılan olarak, `TableAdapterManager` ilişkili tabloları içeren bir veri kümesi oluşturduğunuzda bir sınıf oluşturulur. Sınıfın oluşturulmasını engellemek için, `Hierarchical Update` veri kümesinin özelliğinin değerini false olarak değiştirin. Bir Windows form veya WPF sayfasının tasarım yüzeyine ilişki içeren bir tabloyu sürüklediğinizde, Visual Studio sınıfının bir üye değişkenini bildirir. Veri bağlamayı kullanmıyorsanız, değişkeni el ile bildirmeniz gerekir.

`TableAdapterManager`Sınıf bir .NET türü değil. Bu nedenle, belgelerde arama yapamazsınız. Veri kümesi oluşturma sürecinin bir parçası olarak tasarım zamanında oluşturulur.

Aşağıda, sınıfının sık kullanılan yöntemleri ve özellikleri verilmiştir `TableAdapterManager` :

|Üye|Açıklama|
|------------|-----------------|
|`UpdateAll` yöntemi|Tüm veri tablolarından tüm verileri kaydeder.|
|`BackUpDataSetBeforeUpdate` özelliði|Yöntemi yürütmeden önce veri kümesinin yedek kopyasının oluşturulup oluşturulmayacağını belirler `TableAdapterManager.UpdateAll` . Boolean.|
|*TableName* `TableAdapter` özelliði|Bir temsil eder `TableAdapter` . Oluşturulan `TableAdapterManager` her biri için bir özelliği içerir `TableAdapter` . Örneğin, Customers ve Orders tablosu içeren bir veri kümesi, `TableAdapterManager` ve özellikleri içeren bir ile oluşturulur `CustomersTableAdapter` `OrdersTableAdapter` .|
|`UpdateOrder` özelliði|Tek tek ekleme, güncelleştirme ve silme komutlarının sırasını denetler. Bunu, Numaralandırmadaki değerlerden birine ayarlayın `TableAdapterManager.UpdateOrderOption` .<br /><br /> Varsayılan olarak, `UpdateOrder` **InsertUpdateDelete** olarak ayarlanır. Bu, daha sonra, ve sonrasında silinmeler, veri kümesindeki tüm tablolar için gerçekleştirilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
