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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2b046eaa4244d08c9fff9e2412471d018203de42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648805"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Nesneleri Visual Studio 'da veri kaynakları olarak bağlama

Visual Studio, uygulamanızda veri kaynağı olarak özel nesnelerle çalışmaya yönelik tasarım zamanı araçları sağlar. UI denetimlerine bağladığınızda bir nesnedeki verileri bir veritabanından depolamak istediğinizde, önerilen yaklaşım, sınıfı veya sınıfları oluşturmak için Entity Framework kullanmaktır. Entity Framework, tüm ortak değişiklik izleme kodunu otomatik olarak oluşturur, bu da DbSet nesnesinde AcceptChanges çağırdığınızda yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanına kalıcı hale geldiğini gösterir. Daha fazla bilgi için bkz. [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Bu makaledeki nesne bağlamaya yaklaşımlar yalnızca uygulamanız zaten veri kümelerine dayanıyorsa göz önünde bulundurulmalıdır. Bu yaklaşımları, veri kümelerinizi zaten biliyorsanız ve işlemek istediğiniz veriler tablo ve çok karmaşık ya da çok büyük değilse de kullanabilirsiniz. Daha basit bir örnek için, bir DataReader kullanarak doğrudan nesnelere yükleme ve Kullanıcı arabirimini veri bağlama olmadan el ile güncelleştirme dahil olmak üzere, bkz. [ADO.NET kullanarak basit bir veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri

Özel nesnelerin Visual Studio 'daki veri tasarımı araçlarıyla çalışması için tek gereksinim, nesnenin en az bir ortak özelliğe ihtiyacı vardır.

Genellikle, özel nesneler bir uygulama için veri kaynağı olarak görev yapacak belirli arabirimlerin, oluşturucuların veya özniteliklerin gerekli olmasını gerektirmez. Ancak, veri **kaynakları** penceresinden nesneyi bir tasarım yüzeyine sürükleyerek veri bağlantılı bir denetim oluşturun ve nesne <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimini uygularsa, nesne varsayılan bir oluşturucuya sahip olmalıdır. Aksi halde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneleri veri kaynağı olarak kullanma örnekleri

Bir veri kaynağı olarak nesnelerle çalışırken uygulama mantığınızı uygulamak için çok daha az yol olsa da, SQL veritabanları için Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak Basitleştirilen birkaç standart işlem vardır. Bu sayfada, TableAdapters kullanarak bu standart işlemlerin nasıl uygulanacağı açıklanmaktadır. Özel nesnelerinizi oluşturmaya yönelik bir kılavuz olarak tasarlanmamıştır. Örneğin, genellikle nesnelerinizin belirli bir uygulamasına veya uygulamanın mantığına bakılmaksızın aşağıdaki standart işlemleri gerçekleştirirsiniz:

- Nesnelere veri yükleme (genellikle bir veritabanından).

- Türü belirtilmiş bir nesne koleksiyonu oluşturuluyor.

- Bir koleksiyondan nesne ekleme ve nesneleri kaldırma.

- Bir form üzerinde kullanıcılara nesne verileri görüntüleme.

- Bir nesnedeki verileri değiştirme/düzenlemeyle.

- Nesnelerden verileri veritabanına geri kaydetme.

### <a name="load-data-into-objects"></a>Verileri nesnelere yükleme

Bu örnekte, TableAdapters kullanarak nesnelerinizi veri yüklersiniz. Varsayılan olarak, TableAdapters veritabanından veri getiren ve veri tablolarını dolduran iki tür yöntemle oluşturulur.

- @No__t_0 yöntemi, varolan veri tablosunu döndürülen verilerle doldurur.

- @No__t_0 yöntemi, verilerle doldurulan yeni bir veri tablosu döndürür.

Özel nesnelerinizi verilerle yüklemenin en kolay yolu, `TableAdapter.GetData` yöntemini çağırmak, döndürülen veri tablosundaki satır koleksiyonunda döngü yapmak ve her bir nesneyi her bir satırdaki değerlerle doldurmaktır. Bir TableAdapter 'a eklenen herhangi bir sorgu için doldurulmuş veri tablosu döndüren bir `GetData` yöntemi oluşturabilirsiniz.

> [!NOTE]
> Visual Studio, TableAdapter `Fill` ve `GetData` varsayılan olarak adlandırır, ancak bu adları geçerli bir yöntem adıyla değiştirebilirsiniz.

Aşağıdaki örnek, bir veri tablosundaki satırlarda nasıl döngü yapılacağını ve bir nesneyi verilerle doldurmayı gösterir:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Türü belirtilmiş bir nesne koleksiyonu oluşturma

Nesneleriniz için koleksiyon sınıfları oluşturabilir veya [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)tarafından otomatik olarak sağlanmış olan türsüz koleksiyonları kullanabilirsiniz.

Nesneler için özel bir koleksiyon sınıfı oluştururken <xref:System.ComponentModel.BindingList%601> devralmayı öneririz. Bu genel sınıf, koleksiyonunuzu yönetmek için işlevsellik ve Windows Forms ' de veri bağlama altyapısına bildirim gönderen olayları tetikleyebilme olanağı sağlar.

@No__t_0 otomatik olarak oluşturulan koleksiyon, türü belirlenmiş koleksiyon için bir <xref:System.ComponentModel.BindingList%601> kullanır. Uygulamanız ek işlevsellik gerektirmiyorsa, <xref:System.Windows.Forms.BindingSource> dahilinde koleksiyonunuzu koruyabilirsiniz. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource> sınıfının <xref:System.Windows.Forms.BindingSource.List%2A> özelliğine bakın.

> [!NOTE]
> Koleksiyonunuz <xref:System.ComponentModel.BindingList%601> temel uygulama tarafından sağlanmayan işlevselliği gerektiriyorsa, sınıfa gereken şekilde eklemek için özel bir koleksiyon oluşturmanız gerekir.

Aşağıdaki kod, `Order` nesnelerinin kesin türü belirtilmiş bir koleksiyonu için sınıfının nasıl oluşturulacağını gösterir:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Koleksiyona nesne ekleme

Özel koleksiyon sınıfınızın `Add` yöntemini çağırarak veya <xref:System.Windows.Forms.BindingSource> bir koleksiyona nesneler eklersiniz.

> [!NOTE]
> @No__t_1 ' den devralma sırasında özel koleksiyonunuz için `Add` yöntemi otomatik olarak sağlanır.

Aşağıdaki kod, <xref:System.Windows.Forms.BindingSource> türü belirlenmiş koleksiyona nesnelerin nasıl ekleneceğini gösterir:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Aşağıdaki kod, <xref:System.ComponentModel.BindingList%601> devralan bir tür koleksiyona nesnelerin nasıl ekleneceğini gösterir:

> [!NOTE]
> Bu örnekte, `Orders` koleksiyonu `Customer` nesnesinin bir özelliğidir.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Nesneleri koleksiyondan kaldırma

Bir koleksiyondaki nesneleri, özel koleksiyon sınıfınızın veya <xref:System.Windows.Forms.BindingSource> `Remove` ya da `RemoveAt` yöntemini çağırarak kaldırırsınız.

> [!NOTE]
> @No__t_0 ve `RemoveAt` yöntemleri, <xref:System.ComponentModel.BindingList%601> ' den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır.

Aşağıdaki kod, <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> yöntemi ile <xref:System.Windows.Forms.BindingSource> bulunan koleksiyonda nesneleri bulmayı ve kaldırmayı gösterir:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Nesne verilerini kullanıcılara görüntüleme

Nesnelerdeki verileri kullanıcılara göstermek için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanarak bir nesne veri kaynağı oluşturun ve **veri kaynakları** penceresinden tüm nesneyi veya ayrı özellikleri formunuza sürükleyin.

### <a name="modify-the-data-in-objects"></a>Nesnelerdeki verileri değiştirme

Windows Forms denetimlerine veri bağlanan özel nesnelerdeki verileri düzenlemek için, yalnızca ilgili denetimdeki (veya doğrudan nesnenin özelliklerindeki) verileri düzenleyin. Veri bağlama mimarisi nesnedeki verileri güncelleştirir.

Uygulamanız değişikliklerin izlenmesini gerektiriyorsa ve önerilen değişikliklerin özgün değerlerine geri alınması gerekiyorsa, bu işlevselliği nesne modelinize uygulamanız gerekir. Veri tablolarının önerilen değişiklikleri nasıl izlediğini gösteren örnekler için bkz. <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> ve <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Nesnelerdeki verileri veritabanına geri kaydetme

Nesnelerinizle olan verileri TableAdapter DBDirect yöntemlerine geçirerek verileri veritabanına geri kaydedin.

Visual Studio doğrudan veritabanına karşı yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler veri kümesi veya DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve tek tek sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. Update yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> @No__t_0 yöntemi, bir veri kümesindeki değişiklikleri bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> veya dizi <xref:System.Data.DataRow>s yöntem parametresi olarak geçirerek veritabanına geri yüklemek için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

Nesneleri koleksiyonundan veri kaydetmek için, nesneler koleksiyonunu (örneğin, for-Next döngüsü kullanarak) kullanın. TableAdapter DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

Aşağıdaki örnek, yeni bir müşteriyi doğrudan veritabanına eklemek için `TableAdapter.Insert` DBDirect yönteminin nasıl kullanılacağını gösterir:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)