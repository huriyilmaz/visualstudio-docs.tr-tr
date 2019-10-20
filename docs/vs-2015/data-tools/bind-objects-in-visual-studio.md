---
title: Nesneleri bağla
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c487df5623a233146655593265e15c34a884de3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673003"
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio'da nesne bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, uygulamanızda veri kaynağı olarak özel nesnelerle çalışmaya yönelik tasarım zamanı araçları sağlar. UI denetimlerine bağladığınızda bir nesnedeki verileri bir veritabanından depolamak istediğinizde, önerilen yaklaşım, sınıfı veya sınıfları oluşturmak için Entity Framework kullanmaktır. Varlık, tüm ortak değişiklik izleme kodunu Frameworkautogenerates, bu da DbSet nesnesinde AcceptChanges çağırdığınızda yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanına kalıcı hale geldiğini gösterir.    Daha fazla bilgi için bkz. [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Bu makaledeki nesne bağlamaya yaklaşımlar yalnızca uygulamanız zaten veri kümelerine dayanıyorsa göz önünde bulundurulmalıdır. Bu yaklaşımlar, veri kümeleri hakkında bilginiz varsa ve işlemek istediğiniz veriler tablo ve çok karmaşık ya da çok büyük olduğunda da kullanılabilir. Daha basit bir örnek için, bir DataReader kullanarak doğrudan nesnelere yükleme ve Kullanıcı arabirimini veri bağlama olmadan el ile güncelleştirme dahil olmak üzere, bkz. [ADO.NET kullanarak basit bir veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri
 Özel nesnelerin Visual Studio 'daki veri tasarımı araçlarıyla çalışması için tek gereksinim, nesnenin en az bir ortak özelliğe ihtiyacı vardır.

 Genellikle, özel nesneler bir uygulama için veri kaynağı olarak görev yapacak belirli arabirimlerin, oluşturucuların veya özniteliklerin gerekli olmasını gerektirmez. Ancak, veri **kaynakları** penceresinden nesneyi bir tasarım yüzeyine sürükleyerek veri bağlantılı bir denetim oluşturun ve nesne <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimini uygularsa, nesne varsayılan bir oluşturucuya sahip olmalıdır. Aksi halde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneleri veri kaynağı olarak kullanma örnekleri
 Bir veri kaynağı olarak nesnelerle çalışırken uygulama mantığınızı uygulamak için çok daha az yol olsa da, SQL veritabanları için Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak Basitleştirilen birkaç standart işlem vardır. Bu sayfa, TableAdapters.It kullanarak bu standart işlemlerin nasıl uygulanacağını açıklar ve özel nesneleriniz oluşturmak için kılavuz olarak tasarlanmamıştır. Örneğin, genellikle nesnelerinizin belirli bir uygulamasına veya uygulamanın mantığına bakılmaksızın aşağıdaki standart işlemleri gerçekleştirirsiniz:

- Nesnelere veri yükleme (genellikle bir veritabanından).

- Türü belirtilmiş bir nesne koleksiyonu oluşturuluyor.

- Bir koleksiyondan nesne ekleme ve nesneleri kaldırma.

- Bir form üzerinde kullanıcılara nesne verileri görüntüleme.

- Bir nesnedeki verileri değiştirme/düzenlemeyle.

- Nesnelerden verileri veritabanına geri kaydetme.

> [!NOTE]
> Daha iyi anlamak ve bu sayfadaki örneklerin bağlamını sağlamak için şunları tamamlamanızı öneririz: [Izlenecek yol: nesnelerdeki verilere bağlanma (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Bu izlenecek yol, burada ele alınan nesneleri oluşturur.

### <a name="loaddata-into-objects"></a>Nesnelere LoadData
 Bu örnekte, TableAdapters kullanarak nesnelerinizi veri yüklersiniz. Varsayılan olarak, TableAdapters veritabanından veri getiren ve veri tablolarını dolduran iki tür yöntemle oluşturulur.

- @No__t_0 yöntemi, varolan veri tablosunu döndürülen verilerle doldurur.

- @No__t_0 yöntemi, verilerle doldurulan yeni bir veri tablosu döndürür.

  Özel nesnelerinizi verilerle yüklemenin en kolay yolu, `TableAdapter.GetData` yöntemini çağırmak, döndürülen veri tablosundaki satır koleksiyonunda döngü yapmak ve her bir nesneyi her bir satırdaki değerlerle doldurmaktır. Bir TableAdapter 'a eklenen herhangi bir sorgu için doldurulmuş veri tablosu döndüren bir `GetData` yöntemi oluşturabilirsiniz.

> [!NOTE]
> Visual Studio, TableAdapter `Fill` ve `GetData` varsayılan olarak adlandırır, ancak bu adlar geçerli bir yöntem adına değiştirilebilir.

 Aşağıdaki örnek, bir veri tablosundaki satırlarda nasıl döngü yapılacağını ve bir nesneyi verilerle doldurmayı gösterir:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Türü belirtilmiş bir nesne koleksiyonu oluşturma
 Nesneleriniz için koleksiyon sınıfları oluşturabilir veya [BindingSource bileşeni](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)tarafından otomatik olarak sağlanmış olan türsüz koleksiyonları kullanabilirsiniz.

 Nesneler için özel bir koleksiyon sınıfı oluştururken <xref:System.ComponentModel.BindingList%601> devralmayı öneririz. Bu genel sınıf, koleksiyonunuzu yönetmek için işlevsellik ve Windows Forms ' de veri bağlama altyapısına bildirim gönderen olayları tetikleyebilme olanağı sağlar.

 @No__t_0 otomatik olarak oluşturulan koleksiyon, türü belirlenmiş koleksiyon için bir <xref:System.ComponentModel.BindingList%601> kullanır. Uygulamanız ek işlevsellik gerektirmiyorsa, koleksiyonunuzu <xref:System.Windows.Forms.BindingSource> içinde koruyabilirsiniz. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource> sınıfının <xref:System.Windows.Forms.BindingSource.List%2A> özelliğine bakın.

> [!NOTE]
> Koleksiyonunuz <xref:System.ComponentModel.BindingList%601> temel uygulama tarafından sağlanmayan işlevselliği gerektiriyorsa, sınıfa gereken şekilde eklemek için özel bir koleksiyon oluşturmanız gerekir.

 Aşağıdaki kod, `Order` nesnelerinin kesin türü belirtilmiş bir koleksiyonu için sınıfının nasıl oluşturulacağını gösterir:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Bir koleksiyona AddObjects
 Özel koleksiyon sınıfınızın `Add` yöntemini çağırarak veya <xref:System.Windows.Forms.BindingSource> bir koleksiyona nesneler eklersiniz.

 Bir <xref:System.Windows.Forms.BindingSource> kullanarak koleksiyona ekleme örneği için, [Izlenecek yol: nesnelerdeki verilere bağlanma (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)`LoadCustomers` yöntemine bakın.

 Özel bir koleksiyona nesne ekleme örneği için bkz. `LoadOrders` yöntemi [: nesnelerdeki verilere bağlanma (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> @No__t_1 ' den devralma sırasında özel koleksiyonunuz için `Add` yöntemi otomatik olarak sağlanır.

 Aşağıdaki kod, <xref:System.Windows.Forms.BindingSource> türü belirlenmiş koleksiyona nesnelerin nasıl ekleneceğini gösterir:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Aşağıdaki kod, <xref:System.ComponentModel.BindingList%601> devralan bir tür koleksiyona nesnelerin nasıl ekleneceğini gösterir:

> [!NOTE]
> Bu örnekte `Orders` koleksiyonu `Customer` nesnesinin bir özelliğidir.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Koleksiyondan removeobjects
 Bir koleksiyondaki nesneleri, özel koleksiyon sınıfınızın veya <xref:System.Windows.Forms.BindingSource> `Remove` ya da `RemoveAt` yöntemini çağırarak kaldırırsınız.

> [!NOTE]
> @No__t_0 ve `RemoveAt` yöntemleri, <xref:System.ComponentModel.BindingList%601> ' den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır.

 Aşağıdaki kod, <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> yöntemi ile <xref:System.Windows.Forms.BindingSource> bulunan koleksiyonda nesneleri bulmayı ve kaldırmayı gösterir:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Kullanıcılara veri DisplayObject
 Nesnelerdeki verileri kullanıcılara göstermek için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanarak bir nesne veri kaynağı oluşturun ve **veri kaynakları** penceresinden tüm nesneyi veya ayrı özellikleri formunuza sürükleyin.

### <a name="modify-the-data-in-objects"></a>Nesnelerdeki verileri değiştirme
 Windows Forms denetimlerine veri bağlanan özel nesnelerdeki verileri düzenlemek için, yalnızca ilgili denetimdeki (veya doğrudan nesnenin özelliklerindeki) verileri düzenleyin. Veri bağlama mimarisi nesnedeki verileri güncelleştirir.

 Uygulamanız değişikliklerin izlenmesini gerektiriyorsa ve önerilen değişikliklerin özgün değerlerine geri alınması gerekiyorsa, bu işlevselliği nesne modelinize uygulamanız gerekir. Veri tablolarının önerilen değişiklikleri nasıl izlediğini gösteren örnekler için bkz. <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> ve <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>Nesneleri veritabanına geri dön
 Nesnelerinizle olan verileri TableAdapter DBDirect yöntemlerine geçirerek verileri veritabanına geri kaydedin.

 Visual Studio doğrudan veritabanına karşı yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler veri kümesi veya DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve tek tek sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. Update yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> @No__t_0 yöntemi, bir veri kümesindeki değişiklikleri bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> veya dizi <xref:System.Data.DataRow>s yöntem parametresi olarak geçirerek veritabanına geri yüklemek için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

 Nesneleri koleksiyonundan veri kaydetmek için, nesneler koleksiyonunu (örneğin, for-Next döngüsü kullanarak) kullanın. TableAdapter DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

 Aşağıdaki örnek, yeni bir müşteriyi doğrudan veritabanına eklemek için `TableAdapter.Insert` DBDirect yönteminin nasıl kullanılacağını gösterir:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
