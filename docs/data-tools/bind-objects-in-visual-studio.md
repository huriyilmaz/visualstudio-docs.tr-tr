---
title: Veri bağlama özel nesneleri
description: Nesneleri Visual Studio veri kaynakları olarak bağlayın. Uygulamanızda veri kaynağı olarak özel nesnelerle çalışmaya yönelik tasarım zamanı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b837cf77103efa7cf07bdc6f32aabb5028670638
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139598"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Nesneleri Visual Studio veri kaynakları olarak bağlama

Visual Studio, uygulamanızda veri kaynağı olarak özel nesnelerle çalışmaya yönelik tasarım zamanı araçları sağlar. UI denetimlerine bağladığınızda bir nesnedeki verileri bir veritabanından depolamak istediğinizde, önerilen yaklaşım, sınıfı veya sınıfları oluşturmak için Entity Framework kullanmaktır. Entity Framework, tüm ortak değişiklik izleme kodunu otomatik olarak oluşturur, bu da DbSet nesnesinde AcceptChanges çağırdığınızda yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanına kalıcı hale geldiğini gösterir. Daha fazla bilgi için bkz. [Entity Framework belgeleri](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Bu makaledeki nesne bağlamaya yaklaşımlar yalnızca uygulamanız zaten veri kümelerine dayanıyorsa göz önünde bulundurulmalıdır. Bu yaklaşımları, veri kümelerinizi zaten biliyorsanız ve işlemek istediğiniz veriler tablo ve çok karmaşık ya da çok büyük değilse de kullanabilirsiniz. Daha basit bir örnek için, bir DataReader kullanarak doğrudan nesnelere yükleme ve Kullanıcı arabirimini veri bağlama olmadan el ile güncelleştirme dahil olmak üzere, bkz. [ADO.NET kullanarak basit bir veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Nesne gereksinimleri

özel nesnelerin Visual Studio içindeki veri tasarımı araçlarıyla çalışması için tek gereksinim, nesnenin en az bir ortak özelliğe ihtiyacı vardır.

Genellikle, özel nesneler bir uygulama için veri kaynağı olarak görev yapacak belirli arabirimlerin, oluşturucuların veya özniteliklerin gerekli olmasını gerektirmez. Ancak, veri **kaynakları** penceresinden nesneyi bir tasarım yüzeyine sürükleyerek veri bağlantılı bir denetim oluşturun ve nesne <xref:System.ComponentModel.ITypedList> veya arabirimini uygularsa <xref:System.ComponentModel.IListSource> , nesnenin varsayılan bir oluşturucusu olması gerekir. aksi takdirde, Visual Studio veri kaynağı nesnesini örneklemez ve öğeyi tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneleri veri kaynağı olarak kullanma örnekleri

uygulama mantığınızı bir veri kaynağı olarak nesnelerle çalışırken uygulamanın mantığını uygulamak için sayısız yol olsa da, SQL veritabanları için Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak basitleştirilen birkaç standart işlem vardır. Bu sayfada, TableAdapters kullanarak bu standart işlemlerin nasıl uygulanacağı açıklanmaktadır. Özel nesnelerinizi oluşturmaya yönelik bir kılavuz olarak tasarlanmamıştır. Örneğin, genellikle nesnelerinizin belirli bir uygulamasına veya uygulamanın mantığına bakılmaksızın aşağıdaki standart işlemleri gerçekleştirirsiniz:

- Nesnelere veri yükleme (genellikle bir veritabanından).

- Türü belirtilmiş bir nesne koleksiyonu oluşturuluyor.

- Bir koleksiyondan nesne ekleme ve nesneleri kaldırma.

- Bir form üzerinde kullanıcılara nesne verileri görüntüleme.

- Bir nesnedeki verileri değiştirme/düzenlemeyle.

- Nesnelerden verileri veritabanına geri kaydetme.

### <a name="load-data-into-objects"></a>Verileri nesnelere yükleme

Bu örnekte, TableAdapters kullanarak nesnelerinizi veri yüklersiniz. Varsayılan olarak, TableAdapters veritabanından veri getiren ve veri tablolarını dolduran iki tür yöntemle oluşturulur.

- `TableAdapter.Fill`Yöntemi, varolan veri tablosunu döndürülen verilerle doldurur.

- `TableAdapter.GetData`Yöntemi, verilerle doldurulan yeni bir veri tablosu döndürür.

Özel nesnelerinizi verilerle yüklemenin en kolay yolu, `TableAdapter.GetData` yöntemi çağırmak, döndürülen veri tablosundaki satır koleksiyonunda döngü yapmak ve her bir nesneyi her satırdaki değerlerle doldurmaktır. `GetData`Bir TableAdapter 'a eklenen herhangi bir sorgu için, doldurulmuş bir veri tablosu döndüren bir yöntem oluşturabilirsiniz.

> [!NOTE]
> Visual Studio TableAdapter sorgularını `Fill` ve `GetData` varsayılan olarak adlarını, ancak bu adları geçerli bir yöntem adıyla değiştirebilirsiniz.

Aşağıdaki örnek, bir veri tablosundaki satırlarda nasıl döngü yapılacağını ve bir nesneyi verilerle doldurmayı gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>Türü belirtilmiş bir nesne koleksiyonu oluşturma

Nesneleriniz için koleksiyon sınıfları oluşturabilir veya [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)tarafından otomatik olarak sağlanmış olan türsüz koleksiyonları kullanabilirsiniz.

Nesneler için özel bir koleksiyon sınıfı oluştururken, ' den devralmayı öneririz <xref:System.ComponentModel.BindingList%601> . bu genel sınıf, koleksiyonunuzu yönetmek için işlevsellik ve Windows Forms ' de veri bağlama altyapısına bildirim gönderen olayları tetikleyebilme olanağı sağlar.

İçinde otomatik olarak oluşturulan koleksiyon, <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> türü belirlenmiş koleksiyon için bir kullanır. Uygulamanız ek işlevsellik gerektirmiyorsa, koleksiyonunuzu içinde koruyabilirsiniz <xref:System.Windows.Forms.BindingSource> . Daha fazla bilgi için bkz <xref:System.Windows.Forms.BindingSource.List%2A> <xref:System.Windows.Forms.BindingSource> . sınıfının özelliği.

> [!NOTE]
> Koleksiyonunuz öğesinin temel uygulamasıyla sağlanmayan işlevselliği gerektiriyorsa <xref:System.ComponentModel.BindingList%601> , gerekli olduğu gibi sınıfa ekleyebilmeniz için bir özel koleksiyon oluşturmanız gerekir.

Aşağıdaki kod, nesne türü kesin belirlenmiş bir koleksiyon için sınıfının nasıl oluşturulacağını gösterir `Order` :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>Koleksiyona nesne ekleme

Özel koleksiyon sınıfınızın yöntemini çağırarak bir koleksiyona nesneler eklersiniz `Add` <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Yöntemi, ' `Add` den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır <xref:System.ComponentModel.BindingList%601> .

Aşağıdaki kod, içindeki türü belirlenmiş koleksiyona nesnelerin nasıl ekleneceğini gösterir <xref:System.Windows.Forms.BindingSource> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

Aşağıdaki kod, öğesinden devralan türü belirtilmiş bir koleksiyona nesnelerin nasıl ekleneceğini gösterir <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> Bu örnekte, `Orders` koleksiyon nesnesinin bir özelliğidir `Customer` .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>Nesneleri koleksiyondan kaldırma

`Remove` `RemoveAt` Özel koleksiyon sınıfınızın veya yöntemini çağırarak bir koleksiyondan nesne kaldırırsınız <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Remove`Ve yöntemleri, ' `RemoveAt` den devralma sırasında özel koleksiyonunuz için otomatik olarak sağlanır <xref:System.ComponentModel.BindingList%601> .

Aşağıdaki kod, yöntemi ile bir içindeki türü belirlenmiş koleksiyonda nesneleri bulma ve kaldırma işlemlerinin nasıl yapılacağını göstermektedir <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>Nesne verilerini kullanıcılara görüntüleme

Nesnelerdeki verileri kullanıcılara göstermek için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanarak bir nesne veri kaynağı oluşturun ve **veri kaynakları** penceresinden tüm nesneyi veya ayrı özellikleri formunuza sürükleyin.

### <a name="modify-the-data-in-objects"></a>Nesnelerdeki verileri değiştirme

Windows Forms denetimlerine veri bağlanan özel nesnelerdeki verileri düzenlemek için, yalnızca ilgili denetimdeki (veya doğrudan nesnenin özelliklerindeki) verileri düzenleyin. Veri bağlama mimarisi nesnedeki verileri güncelleştirir.

Uygulamanız değişikliklerin izlenmesini gerektiriyorsa ve önerilen değişikliklerin özgün değerlerine geri alınması gerekiyorsa, bu işlevselliği nesne modelinize uygulamanız gerekir. Veri tablolarının önerilen değişiklikleri nasıl izlediğini gösteren örnekler için, bkz <xref:System.Data.DataRowState> ., <xref:System.Data.DataSet.HasChanges%2A> ve <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Nesnelerdeki verileri veritabanına geri kaydetme

Nesnelerinizle olan verileri TableAdapter DBDirect yöntemlerine geçirerek verileri veritabanına geri kaydedin.

Visual Studio doğrudan veritabanına karşı yürütülebilecek dbdirect yöntemleri oluşturur. Bu yöntemler veri kümesi veya DataTable nesneleri gerektirmez.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve tek tek sütun değerlerini Yöntem parametreleri olarak geçirmenize olanak sağlar.|
|`TableAdapter.Update`|Bir veritabanındaki mevcut kayıtları güncelleştirir. Update yöntemi, özgün ve yeni sütun değerlerini Yöntem parametreleri olarak alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler bu kaydı güncelleştirmek için kullanılır.<br /><br /> `TableAdapter.Update`Yöntemi, bir veri kümesindeki değişiklikleri <xref:System.Data.DataSet> <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> yöntem parametresi olarak bir,, veya dizisi alarak veritabanına geri mutabık kılmak için de kullanılır.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen özgün sütun değerlerini temel alarak veritabanından varolan kayıtları siler.|

Nesneleri koleksiyonundan veri kaydetmek için, nesneler koleksiyonunu (örneğin, for-Next döngüsü kullanarak) kullanın. TableAdapter DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

Aşağıdaki örnek, `TableAdapter.Insert` doğrudan veritabanına yeni bir müşteri eklemek için DBDirect yönteminin nasıl kullanılacağını gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
