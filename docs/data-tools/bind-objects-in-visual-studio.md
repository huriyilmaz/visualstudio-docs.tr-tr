---
title: Veri bağlama özel nesneleri
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 09e3ad2cfc2690c27e4e26e51f6b40d7afd79f54
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586997"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Nesneleri Visual Studio 'da veri kaynakları olarak bağlama

Visual Studio, uygulamanızdaki veri kaynağı olarak özel nesneler ile çalışma için tasarım zamanı aracı sağlar. Kullanıcı Arabirimi denetimlerine bağlamanıza bir nesne veritabanından veri depolamak istediğinizde, önerilen yaklaşım Entity Framework sınıf veya sınıflar oluşturmak için kullanmaktır. Entity Framework, tüm ortak değişiklik izleme kodunu otomatik olarak oluşturur, bu da DbSet nesnesinde AcceptChanges çağırdığınızda yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanına kalıcı hale geldiğini gösterir. Daha fazla bilgi için [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Bu makaledeki nesne bağlamaya yaklaşımlar yalnızca uygulamanız zaten veri kümelerine dayanıyorsa göz önünde bulundurulmalıdır. Bu yaklaşımları, veri kümelerinizi zaten biliyorsanız ve işlemek istediğiniz veriler tablo ve çok karmaşık ya da çok büyük değilse de kullanabilirsiniz. DataReader kullanarak ve kullanıcı Arabirimi olmadan veri bağlama, el ile güncelleştirme doğrudan nesnelerine veri yükleme ile ilgili örneği artık çok daha kolay görmek [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri

Visual Studio Tasarım araçları verilerle çalışmak özel nesneler için tek gereksinim nesne en az bir ortak özelliği gerekiyor.

Genellikle, özel nesneleri herhangi bir belirli arabirimleri, Oluşturucular veya bir uygulama için veri kaynağı olarak görev yapacak öznitelikleri gerektirmez. Ancak, nesneyi sürükleyin istiyorsanız **veri kaynakları** verilere bağlı bir denetim oluşturmak için bir tasarım yüzeyine penceresi ve nesne uyguluyorsa <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi, varsayılan bir nesne olmalıdır Oluşturucu. Aksi takdirde, Visual Studio, veri kaynağı nesnesi başlatılamıyor ve öğe tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneler veri kaynakları olarak kullanma örnekleri

Bir veri kaynağı olarak nesnelerle çalışırken uygulama mantığınızı uygulamak için çok daha az yol olsa da, SQL veritabanları için Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak Basitleştirilen birkaç standart işlem vardır. Bu sayfada, TableAdapters kullanarak bu standart işlemlerin nasıl uygulanacağı açıklanmaktadır. Özel nesnelerinizi oluşturmaya yönelik bir kılavuz olarak tasarlanmamıştır. Örneğin, genellikle nesnelerinizi ya da uygulamanın mantıksal özgü uygulama bağımsız olarak standart aşağıdaki işlemleri gerçekleştirir:

- Veri nesneleri (genellikle bir veritabanından) yükleme.

- Nesne türü belirtilmiş koleksiyonu oluşturuluyor.

- Nesneler ekleme ve nesneleri bir koleksiyonundan kaldırılıyor.

- Nesne verilerini bir formu kullanıcılara görüntüleniyor.

- Değiştirme veya bir nesne verileri düzenleme.

- Veri nesneleri veritabanına geri kaydediliyor.

### <a name="load-data-into-objects"></a>Verileri nesnelere yükleme

Bu örnek için TableAdapter'ı kullanarak, nesneleri verileri yükleyin. Varsayılan olarak, TableAdapter bağdaştırıcıları veritabanından veri getirir ve veri tablolarını doldurmak yöntemleri iki tür oluşturulur.

- `TableAdapter.Fill` Yöntemi, mevcut bir veri tablosu döndürülen verilerle doldurur.

- `TableAdapter.GetData` Yöntemi verilerle doldurulmuş yeni bir veri tablosu döndürür.

Özel nesnelerinizi veri yüklemek için en kolay yolu çağırmaktır `TableAdapter.GetData` yöntemi döndürülen veri tablosundaki satır koleksiyonu aracılığıyla döngü ve her satırdaki değerlerin her nesnesiyle doldurur. Oluşturabileceğiniz bir `GetData` doldurulmuş veri tablosunu TableAdapter bağdaştırıcısına eklenen herhangi bir sorgu için döndüren yöntem.

> [!NOTE]
> Visual Studio, TableAdapter `Fill` ve `GetData` varsayılan olarak adlandırır, ancak bu adları geçerli bir yöntem adıyla değiştirebilirsiniz.

Aşağıdaki örnek, bir veri tablosundaki satırları döngü ve nesneyi verilerle doldurmak gösterilmektedir:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Nesne türü belirtilmiş bir koleksiyon oluşturun

Nesneleriniz için koleksiyon sınıfları oluşturabilir veya [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)tarafından otomatik olarak sağlanmış olan türsüz koleksiyonları kullanabilirsiniz.

Nesneler için özel bir koleksiyon sınıfı oluştururken <xref:System.ComponentModel.BindingList%601>devralmayı öneririz. Bu genel bir sınıf özelliği Windows Forms veri bağlama altyapısında bildirimleri göndermek olay yanı sıra, koleksiyonunuzu yönetmek için işlevsellik sağlar.

<xref:System.Windows.Forms.BindingSource> otomatik olarak oluşturulan koleksiyon, türü belirlenmiş koleksiyon için bir <xref:System.ComponentModel.BindingList%601> kullanır. Uygulamanız ek işlevsellik gerektirmiyorsa, <xref:System.Windows.Forms.BindingSource>dahilinde koleksiyonunuzu koruyabilirsiniz. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource.List%2A> özelliği <xref:System.Windows.Forms.BindingSource> sınıfı.

> [!NOTE]
> Koleksiyonunuz temel uygulaması tarafından sağlanmayan işlevselliği gerektirip gerektirmediğini <xref:System.ComponentModel.BindingList%601>, gerektiğinde sınıfa eklemek için özel bir koleksiyona oluşturmanız gerekir.

Aşağıdaki kod, sınıf için kesin türü belirtilmiş bir koleksiyonunu oluşturma işlemi gösterilmektedir `Order` nesneler:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Koleksiyona nesne ekleme

Çağırarak bir koleksiyona eklediğiniz nesneleri `Add` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Add` Öğesinden devraldığı durumlarda yöntemi özel koleksiyonunuz için otomatik olarak sağlanan <xref:System.ComponentModel.BindingList%601>.

Aşağıdaki kod, belirlenmiş koleksiyonda nesneleri eklemek gösterilmiştir bir <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Aşağıdaki kod, devralınan belirlenmiş bir koleksiyon nesneleri eklemek gösterilmektedir <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> Bu örnekte, `Orders` koleksiyonu `Customer` nesnesinin bir özelliğidir.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Nesneleri koleksiyondan kaldırma

Çağırarak nesneleri bir koleksiyondan Kaldır `Remove` veya `RemoveAt` yöntemi özel bir koleksiyona sınıfınızın veya, <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Remove` Ve `RemoveAt` yöntemleri otomatik olarak sağlanan özel koleksiyonunuz için öğesinden devraldığı durumlarda <xref:System.ComponentModel.BindingList%601>.

Aşağıdaki kodu bulun ve belirlenmiş koleksiyonda nesneleri kaldırmak gösterilmiştir bir <xref:System.Windows.Forms.BindingSource> ile <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> yöntemi:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Nesne verilerini kullanıcılara görüntüleme

Verileri kullanıcılara nesneleri görüntülemek için bir nesne veri kaynağı kullanılarak oluşturma **veri kaynağı yapılandırması** Sihirbazı'nı ve ardından formunuzun içinden üzerine nesnenin tamamını veya tek tek özellikler sürükleyin **veri kaynakları**penceresi.

### <a name="modify-the-data-in-objects"></a>Veri nesneleri değiştirme

Verilere Windows Forms denetimlerine bağlı özel nesneleri verileri düzenlemek için yalnızca veri ilişkili denetim (veya doğrudan bir nesnenin özelliklerinde) düzenleyin. Veri bağlama mimarisi, nesne verileri güncelleştirir.

Uygulamanızı, değişiklikleri izleme ve arkasına önerilen değişiklikler orijinal değerlerine alınıyor gerektiriyorsa, bu işlev, nesne modelinde uygulamalıdır. Nasıl veri tabloları önerdiğiniz değişiklikleri takip örnekleri için bkz: <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, ve <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Nesnelerdeki verileri veritabanına geri kaydetme

Verileri, TableAdapter bağdaştırıcısının DBDirect yöntemleri için bir nesneden değerler geçirerek veritabanına geri kaydedin.

Visual Studio doğrudan veritabanında yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler, veri kümesi ya da DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Yöntem parametreleri olarak ayrı ayrı sütun değerlerine geçirin olanak tanıyan bir veritabanına yeni kayıtlar ekler.|
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. Güncelleştirme yöntemi, yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` Yöntemi dataset içindeki değişiklikleri veritabanına geri alarak karşılaştırmak için kullanılan ayrıca bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya dizi <xref:System.Data.DataRow>yöntem parametreleri olarak s.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|

Nesneleri koleksiyonundan veri kaydetmek için, nesneler koleksiyonunu (örneğin, for-Next döngüsü kullanarak) kullanın. TableAdapter DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

Aşağıdaki örnek nasıl kullanılacağını gösterir `TableAdapter.Insert` DBDirect yöntemi doğrudan veritabanına yeni bir müşteri eklemek için:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
