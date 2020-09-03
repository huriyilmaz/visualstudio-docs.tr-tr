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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673003"
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio'da nesne bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, uygulamanızda veri kaynağı olarak özel nesnelerle çalışmaya yönelik tasarım zamanı araçları sağlar. UI denetimlerine bağladığınızda bir nesnedeki verileri bir veritabanından depolamak istediğinizde, önerilen yaklaşım, sınıfı veya sınıfları oluşturmak için Entity Framework kullanmaktır. Varlık, tüm ortak değişiklik izleme kodunu Frameworkautogenerates, bu da DbSet nesnesinde AcceptChanges çağırdığınızda yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanına kalıcı hale geldiğini gösterir.    Daha fazla bilgi için bkz. [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Bu makaledeki nesne bağlamaya yaklaşımlar yalnızca uygulamanız zaten veri kümelerine dayanıyorsa göz önünde bulundurulmalıdır. Bu yaklaşımlar, veri kümeleri hakkında bilginiz varsa ve işlemek istediğiniz veriler tablo ve çok karmaşık ya da çok büyük olduğunda da kullanılabilir. Daha basit bir örnek için, bir DataReader kullanarak doğrudan nesnelere yükleme ve Kullanıcı arabirimini veri bağlama olmadan el ile güncelleştirme dahil olmak üzere, bkz. [ADO.NET kullanarak basit bir veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri
 Özel nesnelerin Visual Studio 'daki veri tasarımı araçlarıyla çalışması için tek gereksinim, nesnenin en az bir ortak özelliğe ihtiyacı vardır.

 Genellikle, özel nesneler bir uygulama için veri kaynağı olarak görev yapacak belirli arabirimlerin, oluşturucuların veya özniteliklerin gerekli olmasını gerektirmez. Ancak, veri **kaynakları** penceresinden nesneyi bir tasarım yüzeyine sürükleyerek veri bağlantılı bir denetim oluşturun ve nesne <xref:System.ComponentModel.ITypedList> veya arabirimini uygularsa <xref:System.ComponentModel.IListSource> , nesnenin varsayılan bir oluşturucusu olması gerekir. Aksi halde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

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

- `TableAdapter.Fill`Yöntemi, varolan veri tablosunu döndürülen verilerle doldurur.

- `TableAdapter.GetData`Yöntemi, verilerle doldurulan yeni bir veri tablosu döndürür.

  Özel nesnelerinizi verilerle yüklemenin en kolay yolu, `TableAdapter.GetData` yöntemi çağırmak, döndürülen veri tablosundaki satır koleksiyonunda döngü yapmak ve her bir nesneyi her satırdaki değerlerle doldurmaktır. `GetData`Bir TableAdapter 'a eklenen herhangi bir sorgu için, doldurulmuş bir veri tablosu döndüren bir yöntem oluşturabilirsiniz.

> [!NOTE]
> Visual Studio, TableAdapter sorgularını `Fill` ve `GetData` Varsayılan olarak adlandırır, ancak bu adlar geçerli bir yöntem adı ile değiştirilebilir.

 Aşağıdaki örnek, bir veri tablosundaki satırlarda nasıl döngü yapılacağını ve bir nesneyi verilerle doldurmayı gösterir:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Türü belirtilmiş bir nesne koleksiyonu oluşturma
 Nesneleriniz için koleksiyon sınıfları oluşturabilir veya [BindingSource bileşeni](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)tarafından otomatik olarak sağlanmış olan türsüz koleksiyonları kullanabilirsiniz.

 Nesneler için özel bir koleksiyon sınıfı oluştururken, ' den devralmayı öneririz <xref:System.ComponentModel.BindingList%601> . Bu genel sınıf, koleksiyonunuzu yönetmek için işlevsellik ve Windows Forms ' de veri bağlama altyapısına bildirim gönderen olayları tetikleyebilme olanağı sağlar.

 İçindeki otomatik olarak oluşturulan koleksiyon, <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> türü belirlenmiş koleksiyon için bir kullanır. Uygulamanız ek işlevsellik gerektirmiyorsa, koleksiyonunuzu içinde koruyabilirsiniz <xref:System.Windows.Forms.BindingSource> . Daha fazla bilgi için bkz <xref:System.Windows.Forms.BindingSource.List%2A> <xref:System.Windows.Forms.BindingSource> . sınıfının özelliği.

> [!NOTE]
> Koleksiyonunuz öğesinin temel uygulamasıyla sağlanmayan işlevselliği gerektiriyorsa <xref:System.ComponentModel.BindingList%601> , gerekli olduğu gibi sınıfa ekleyebilmeniz için bir özel koleksiyon oluşturmanız gerekir.

 Aşağıdaki kod, nesne türü kesin belirlenmiş bir koleksiyon için sınıfının nasıl oluşturulacağını gösterir `Order` :

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Bir koleksiyona AddObjects
 Özel koleksiyon sınıfınızın yöntemini çağırarak bir koleksiyona nesneler eklersiniz `Add` <xref:System.Windows.Forms.BindingSource> .

 Kullanarak bir koleksiyona ekleme örneği için <xref:System.Windows.Forms.BindingSource> bkz `LoadCustomers` . [Izlenecek yol: nesnelerdeki verilere bağlanma (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Özel bir koleksiyona nesne ekleme örneği için bkz `LoadOrders` . [izlenecek yol: nesnelerdeki verilere bağlanma (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> Yöntemi, ' `Add` den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır <xref:System.ComponentModel.BindingList%601> .

 Aşağıdaki kod, içindeki türü belirlenmiş koleksiyona nesnelerin nasıl ekleneceğini gösterir <xref:System.Windows.Forms.BindingSource> :

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Aşağıdaki kod, öğesinden devralan türü belirtilmiş bir koleksiyona nesnelerin nasıl ekleneceğini gösterir <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> Bu örnekte, `Orders` koleksiyon nesnesinin bir özelliğidir `Customer` .

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Koleksiyondan removeobjects
 `Remove` `RemoveAt` Özel koleksiyon sınıfınızın veya yöntemini çağırarak bir koleksiyondan nesne kaldırırsınız <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Remove`Ve yöntemleri, ' `RemoveAt` den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır <xref:System.ComponentModel.BindingList%601> .

 Aşağıdaki kod, yöntemi ile bir içindeki türü belirlenmiş koleksiyonda nesneleri bulma ve kaldırma işlemlerinin nasıl yapılacağını göstermektedir <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> :

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Kullanıcılara veri DisplayObject
 Nesnelerdeki verileri kullanıcılara göstermek için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanarak bir nesne veri kaynağı oluşturun ve **veri kaynakları** penceresinden tüm nesneyi veya ayrı özellikleri formunuza sürükleyin.

### <a name="modify-the-data-in-objects"></a>Nesnelerdeki verileri değiştirme
 Windows Forms denetimlerine veri bağlanan özel nesnelerdeki verileri düzenlemek için, yalnızca ilgili denetimdeki (veya doğrudan nesnenin özelliklerindeki) verileri düzenleyin. Veri bağlama mimarisi nesnedeki verileri güncelleştirir.

 Uygulamanız değişikliklerin izlenmesini gerektiriyorsa ve önerilen değişikliklerin özgün değerlerine geri alınması gerekiyorsa, bu işlevselliği nesne modelinize uygulamanız gerekir. Veri tablolarının önerilen değişiklikleri nasıl izlediğini gösteren örnekler için, bkz <xref:System.Data.DataRowState> ., <xref:System.Data.DataSet.HasChanges%2A> ve <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="savedata-in-objects-back-to-the-database"></a>Nesneleri veritabanına geri dön
 Nesnelerinizle olan verileri TableAdapter DBDirect yöntemlerine geçirerek verileri veritabanına geri kaydedin.

 Visual Studio doğrudan veritabanına karşı yürütülebilecek DBDirect yöntemleri oluşturur. Bu yöntemler veri kümesi veya DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve tek tek sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. Update yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> `TableAdapter.Update`Yöntemi, bir veri kümesindeki değişiklikleri <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> yöntem parametresi olarak bir,, veya dizisi alarak veritabanına geri mutabık kılmak için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

 Nesneleri koleksiyonundan veri kaydetmek için, nesneler koleksiyonunu (örneğin, for-Next döngüsü kullanarak) kullanın. TableAdapter DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

 Aşağıdaki örnek, `TableAdapter.Insert` doğrudan veritabanına yeni bir müşteri eklemek için DBDirect yönteminin nasıl kullanılacağını gösterir:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
