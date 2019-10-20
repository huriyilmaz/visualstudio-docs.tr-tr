---
title: Hiyerarşik güncelleştirme | Microsoft Docs
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670016"
---
# <a name="hierarchical-update"></a>Hiyerarşik güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hiyerarşik güncelleştirme *, bilgi tutarlılığı kurallarını koruyarak güncelleştirilmiş verileri (iki veya daha fazla ilişkili tablo içeren bir veri kümesinden) veritabanına geri kaydetme sürecini ifade eder. *Başvurusal bütünlük* , bir veritabanında ilgili kayıtları ekleme, güncelleştirme ve silme davranışlarını denetleyen kısıtlamalar tarafından belirtilen tutarlılık kurallarına başvurur. Örneğin, bu müşteri için siparişlerin oluşturulmasına izin vermeden önce müşteri kaydının oluşturulmasını zorlayan bilgi tutarlılığı vardır.  Veri kümelerinde ilişkiler hakkında daha fazla bilgi için bkz. [veri kümelerinde ilişkiler](../data-tools/relationships-in-datasets.md)

 Hiyerarşik güncelleştirme özelliği, türü belirtilmiş bir veri kümesindeki `TableAdapter`s yönetmek için bir `TableAdapterManager` kullanır. @No__t_0 bileşen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tarafından oluşturulan bir sınıftır, bu nedenle [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] parçası değildir. Veri kaynakları penceresinden bir tabloyu bir Windows form veya WPF sayfasına sürüklediğinizde, Visual Studio form veya sayfaya TableAdapterManager türünde bir değişken ekler ve onu bileşen tepsisinde tasarımcıda görürsünüz. @No__t_0 sınıfı hakkında ayrıntılı bilgi için, [TableAdapterManager genel bakış](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)konusunun TableAdapterManager Reference bölümüne bakın.

 Varsayılan olarak, bir veri kümesi ilgili tabloları "yalnızca ilişkiler" olarak değerlendirir ve bu, yabancı anahtar kısıtlamalarını Zorlamayacağı anlamına gelir. Bu ayarı tasarım zamanında Veri Kümesi Tasarımcısı kullanarak değiştirebilirsiniz. **İlişki** iletişim kutusunu açmak için iki tablo arasındaki ilişki satırını seçin. Burada yaptığınız değişiklikler, ilgili tablolardaki değişiklikleri veritabanına geri gönderirken TableAdapterManager 'in nasıl davranacağını belirlemektir.

## <a name="enablehierarchical-update-in-a-dataset"></a>Bir veri kümesinde enablesıradüzensel güncelleştirme
 Varsayılan olarak, Hiyerarşik güncelleştirme bir projede eklenen veya oluşturulan tüm yeni veri kümeleri için etkindir. Veri kümesi tasarımcısında bir türü belirtilmiş veri kümesinin **Hiyerarşik güncelleştirme** özelliğini **true** veya **false**olarak ayarlayarak hiyerarşik güncelleştirmeyi açın veya kapatın:

 ![Hiyerarşik güncelleştirme ayarı](../data-tools/media/hierarchical-update-setting.png "Hiyerarşik güncelleştirme ayarı")

## <a name="create-a-new-relation-between-tables"></a>Tablolar arasında yeni bir ilişki oluşturma
 İki tablo arasında yeni bir ilişki oluşturmak için, Veri Kümesi Tasarımcısı her tablonun başlık çubuğunu seçin, sonra sağ tıklayıp**Ilişki Ekle**' yi seçin.

 ![Hiyerarşik güncelleştirme ilişki Ekle menüsü](../data-tools/media/hierarchical-update-add-relation-menu.png "Hiyerarşik güncelleştirme ilişki Ekle menüsü")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Yabancı anahtar kısıtlamalarını, basamaklı güncelleştirmeleri ve silmeleri anlayın
 Veritabanındaki yabancı anahtar kısıtlamalarının ve basamaklı davranışın oluşturulan veri kümesi kodunda nasıl oluşturulduğunu anlamak önemlidir.

 Varsayılan olarak, bir veri kümesindeki veri tabloları, veritabanındaki ilişkilerle eşleşen ilişkilerle (<xref:System.Data.DataRelation>) oluşturulur. Ancak, veri kümesindeki ilişki yabancı anahtar kısıtlaması olarak oluşturulmaz. @No__t_0, yalnızca <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> veya <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> olmadan **ilişki** olarak yapılandırılır.

 Varsayılan olarak, veritabanı ilişkisi basamaklı güncelleştirmeler ve/veya basamaklı silme açık olarak ayarlanmış olsa bile, basamaklı güncelleştirmeler ve basamaklı silmeler kapalıdır. Örneğin, yeni bir müşteri ve yeni bir sipariş oluşturup verileri kaydetmeye çalışmak, veritabanında tanımlanan yabancı anahtar kısıtlamalarına bir çakışmaya neden olabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir veri kümesinde yabancı anahtar kısıtlamalarını yapılandırma](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).

## <a name="set-the-order-to-perform-updates"></a>Güncelleştirme yapmak için sırayı ayarlama
 Güncelleştirme yapılacak sırayı ayarlamak, tüm değiştirilen verileri bir veri kümesinin tüm tablolarında kaydetmek için gereken tek tek ekleme, güncelleştirme ve silme sırasını ayarlar. Hiyerarşik güncelleştirme etkinleştirildiğinde, önce ekleme yapılır, sonra güncelleştirmeler yapılır ve sonra silinir. @No__t_0, önce güncelleştirmeleri gerçekleştirmek üzere ayarlanabilir bir `UpdateOrder` özelliği sağlar, sonra ekler ve sonra siler.

> [!NOTE]
> Güncelleştirme sırasının tümünün dahil olduğunu anlamak önemlidir. Diğer bir deyişle, güncelleştirmeler gerçekleştirildiğinde, ekleme ve sonra silme işlemi, veri kümesindeki tüm tablolar için gerçekleştirilir.

 @No__t_0 özelliğini ayarlamak için, [veri kaynakları penceresinden](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) öğeleri bir form üzerine sürükledikten sonra bileşen tepsisindeki `TableAdapterManager` seçin ve ardından **Özellikler** penceresinde `UpdateOrder` özelliğini ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: hiyerarşik bir güncelleştirme gerçekleştirirken sırayı ayarlama](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Hiyerarşik bir güncelleştirme gerçekleştirmeden önce bir veri kümesinin yedek kopyasını oluşturma
 Verileri kaydettiğinizde (`TableAdapterManager.UpdateAll()` yöntemini çağırarak), `TableAdapterManager` her tablo için verileri tek bir işlemde güncelleştirmeyi dener. Herhangi bir tablo için güncelleştirmenin herhangi bir bölümü başarısız olursa, tüm işlem geri alınır. Çoğu durumda, geri alma uygulamanızı özgün durumuna geri döndürür.

 Ancak, bazen veri kümesini yedek kopyadan geri yüklemek isteyebilirsiniz. Otomatik artış değerlerini kullandığınızda bu durum oluşabilir. Örneğin, bir Kaydet işlemi başarılı olmazsa, otomatik artırma değerleri veri kümesinde sıfırlanmaz ve veri kümesi otomatik artan değerler oluşturmaya devam eder. Bu, uygulamanızda kabul edilebilir olabilecek bir boşluk bırakır. Bunun bir sorun olduğu durumlarda `TableAdapterManager`, işlem başarısız olursa, mevcut veri kümesinin yerine bir yedek kopya ile yerini alan bir `BackupDataSetBeforeUpdate` özelliği sağlar.

> [!NOTE]
> Yedekleme kopyası yalnızca `TableAdapterManager.UpdateAll` yöntemi çalışırken bellekte bulunur. Bu nedenle, bu yedekleme veri kümesine programlı erişim yoktur çünkü bu, özgün veri kümesini değiştirir ya da `TableAdapterManager.UpdateAll` yöntemi çalışmayı bitirdiğinde kapsam dışına çıkar.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Hiyerarşik güncelleştirmeyi gerçekleştirmek için oluşturulan kaydetme kodunu değiştirin
 @No__t_0 yöntemini çağırarak ve ilgili tabloları içeren veri kümesinin adını geçirerek veri kümesindeki ilgili veri tablolarından değişiklikleri veritabanına kaydedin. Örneğin, NorthwindDataset 'teki tüm tablolardaki güncelleştirmeleri arka uç veritabanına göndermek için `TableAdapterManager.UpdateAll(NorthwindDataset)` yöntemini çalıştırın.

 Öğeleri **veri kaynakları** penceresinden bıraktığınızda, her bir tabloyu doldurmak için `Form_Load` olayına otomatik olarak kod eklenir (`TableAdapter.Fill` yöntemleri). Kod, veri kümesinden veritabanına (`TableAdapterManager.UpdateAll` yöntemi) geri kaydetmek için <xref:System.Windows.Forms.BindingNavigator> **Kaydet** düğmesine tıklama olayına de eklenir.

 Oluşturulan kaydetme kodu, `CustomersBindingSource.EndEdit` yöntemini çağıran bir kod satırı da içerir. Özellikle, forma eklenen ilk <xref:System.Windows.Forms.BindingSource>that <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırır. Diğer bir deyişle, bu kod yalnızca **veri kaynakları** penceresinden form üzerine sürüklenen ilk tablo için oluşturulur. @No__t_0 çağrısı, şu anda düzenlenmekte olan herhangi bir veri bağlantılı denetimlerde işlemdeki tüm değişiklikleri kaydeder. Bu nedenle, veri bağlantılı bir denetim hala odağa sahipse ve **Kaydet** düğmesine tıklarsanız, bu denetimdeki tüm bekleyen düzenlemeler gerçek kaydetme işleminden önce (`TableAdapterManager.UpdateAll` yöntemi) kaydedilir.

> [!NOTE]
> Veri Kümesi Tasarımcısı, yalnızca forma bırakılan ilk tablo için `BindingSource.EndEdit` kodunu ekler. Bu nedenle, formdaki her ilgili tablo için `BindingSource.EndEdit` yöntemini çağırmak üzere bir kod satırı eklemeniz gerekir. Bu izlenecek yol için, `OrdersBindingSource.EndEdit` yöntemine bir çağrı eklemeniz gerektiği anlamına gelir.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Kodu kaydedilmeden önce ilgili tablolardaki değişiklikleri yürütmek üzere güncelleştirmek için

1. Kod düzenleyicisinde **Form1** ' i açmak Için <xref:System.Windows.Forms.BindingNavigator> **Kaydet** düğmesine çift tıklayın.

2. @No__t_1 yöntemini çağıran satırdan sonra `OrdersBindingSource.EndEdit` yöntemini çağırmak için bir kod satırı ekleyin. **Kaydet** düğmesine tıklama olayının kodu aşağıdakine benzemelidir:

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   Verileri bir veritabanına kaydetmeden önce ilişkili bir alt tabloya değişiklikleri kaydetmenin yanı sıra, yeni alt kayıtları bir veri kümesine eklemeden önce yeni oluşturulan üst kayıtları da kaydetmeniz gerekebilir. Diğer bir deyişle, yabancı anahtar kısıtlamaları veri kümesine eklenmek üzere yeni alt kayıtları (siparişler) etkinleştirmeden önce, yeni üst kaydı (müşteri) veri kümesine eklemeniz gerekebilir. Bunu gerçekleştirmek için alt `BindingSource.AddingNew` olayını kullanabilirsiniz.

> [!NOTE]
> Yeni üst kayıtları yürütmeniz gerekip gerekmediğini, veri kaynağınıza bağlamak için kullanılan denetimin türüne bağlıdır. Bu kılavuzda, üst tabloya bağlamak için tek tek denetimleri kullanırsınız. Bu, yeni üst kaydı yürütmek için ek kod gerektirir. Üst kayıtlar <xref:System.Windows.Forms.DataGridView> gibi karmaşık bir bağlama denetiminde görüntüleniyorsa, üst kayıt için bu ek <xref:System.Windows.Forms.BindingSource.EndEdit%2A> çağrısı gerekli değildir. Bunun nedeni, denetimin temel alınan veri bağlama işlevselliğinin yeni kayıtların yerine işlemesini işlemektedir.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Yeni alt kayıtlar eklemeden önce veri kümesindeki üst kayıtları yürütmek üzere kod eklemek için

1. @No__t_0 olayı için bir olay işleyicisi oluşturun.

    - Tasarım görünümünde **Form1** ' i açın, bileşen tepsisinde **OrdersBindingSource** ' u seçin, **Özellikler** penceresinde **Olaylar** ' ı seçin ve ardından **AddingNew** olayına çift tıklayın.

2. Olay işleyicisine `CustomersBindingSource.EndEdit` yöntemi çağıran bir kod satırı ekleyin. @No__t_0 olay işleyicisindeki kod aşağıdakine benzemelidir:

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu
 Varsayılan olarak, ilgili tabloları içeren bir veri kümesi oluşturduğunuzda bir `TableAdapterManager` sınıfı oluşturulur. Sınıfın oluşturulmasını engellemek için, veri kümesinin `Hierarchical Update` özelliğinin değerini false olarak değiştirin. Bir Windows form veya WPF sayfasının tasarım yüzeyine ilişki içeren bir tabloyu sürüklediğinizde, Visual Studio sınıfının bir üye değişkenini bildirir. Veri bağlamayı kullanmıyorsanız, değişkeni el ile bildirmeniz gerekir.

 @No__t_0 sınıfı [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bir parçası değil. Bu nedenle, belgelerde bu belgede arama yapılamaz. Veri kümesi oluşturma sürecinin bir parçası olarak tasarım zamanında oluşturulur.

 Aşağıda, `TableAdapterManager` sınıfının sık kullanılan yöntemleri ve özellikleri verilmiştir:

|Üye|Açıklama|
|------------|-----------------|
|`UpdateAll` yöntemi|Tüm veri tablolarından tüm verileri kaydeder.|
|`BackUpDataSetBeforeUpdate` özelliği|@No__t_0 yöntemini yürütmeden önce veri kümesinin yedek kopyasının oluşturulup oluşturulmayacağını belirler. Boolean.|
|*tableName* `TableAdapter` özelliği|Bir `TableAdapter` temsil eder. Oluşturulan `TableAdapterManager`, yönettiği her bir `TableAdapter` için bir özellik içerir. Örneğin, Customers ve Orders tablosu içeren bir veri kümesi, `CustomersTableAdapter` ve `OrdersTableAdapter` özellikleri içeren bir `TableAdapterManager` oluşturulur.|
|`UpdateOrder` özelliği|Tek tek ekleme, güncelleştirme ve silme komutlarının sırasını denetler. Bunu `TableAdapterManager.UpdateOrderOption` Numaralandırmadaki değerlerden birine ayarlayın.<br /><br /> @No__t_0, varsayılan olarak **InsertUpdateDelete**olarak ayarlanır. Bu, daha sonra, ve sonrasında silinmeler, veri kümesindeki tüm tablolar için gerçekleştirilir. Daha fazla bilgi için bkz. [nasıl yapılır: hiyerarşik bir güncelleştirme gerçekleştirirken sırayı ayarlama](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
