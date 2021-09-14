---
title: Veri bağlama özel nesneleri
description: Nesneleri veri kaynağı olarak Visual Studio. Uygulamanıza veri kaynağı olarak özel nesnelerle çalışmak için tasarım zamanı araçlarını kullanın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631593"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Nesneleri veri kaynağı olarak Visual Studio

Visual Studio uygulamanıza veri kaynağı olarak özel nesnelerle çalışmak için tasarım zamanı araçları sağlar. Kullanıcı arabirimi denetimlerine bağlanmış bir nesnede veritabanındaki verileri depolamak istediğiniz zaman, sınıf veya sınıfları oluşturmak için Entity Framework yaklaşım önerilir. Entity Framework tüm ortak değişiklik izleme kodunu otomatik olarak oluşturur. Bu, dbSet nesnesinde AcceptChanges çağrısı yaptığınız zaman yerel nesnelerdeki tüm değişikliklerin otomatik olarak veritabanında kalıcı olduğu anlamına gelir. Daha fazla bilgi için [bkz. Entity Framework Belgeleri.](https://ef.readthedocs.org/en/latest/)

> [!TIP]
> Bu makaledeki nesne bağlama yaklaşımları, yalnızca uygulamanız zaten veri kümelerini temel aldı ise dikkate alınmalıdır. Veri kümelerini zaten biliyorsanız ve işleyecek verileriniz tablosal ise ve çok karmaşık veya çok büyük değilse de bu yaklaşımları kullanabilirsiniz. DataReader kullanarak verileri doğrudan nesnelere yükleme ve veri bağlama olmadan kullanıcı arabirimini el ile güncelleştirme gibi daha da basit bir örnek için bkz. [ADO.NET.](../data-tools/create-a-simple-data-application-by-using-adonet.md)

## <a name="object-requirements"></a>Nesne gereksinimleri

Özel nesnelerin veri tasarımı araçlarıyla birlikte çalışması için tek gereksinim Visual Studio en az bir ortak özellik olmasıdır.

Genel olarak, özel nesneler bir uygulama için veri kaynağı olarak hareket etmek üzere belirli arabirimler, oluşturucular veya öznitelikler gerektirmez. Ancak, veriye bağlı denetim oluşturmak  için nesneyi Veri Kaynakları penceresinden tasarım yüzeyine sürüklemek ve nesne veya arabirimini uygulayıyorsa nesnenin varsayılan oluşturucusu <xref:System.ComponentModel.ITypedList> olması <xref:System.ComponentModel.IListSource> gerekir. Aksi Visual Studio, veri kaynağı nesnesinin örneğini oluşturmaz ve öğeyi tasarım yüzeyine sürüklerken bir hata görüntüler.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Özel nesneleri veri kaynağı olarak kullanma örnekleri

Veri kaynağı olarak nesnelerle çalışırken uygulama mantığınızı uygulamanın sayısız yolu vardır, ancak SQL veritabanları için, Visual Studio tarafından oluşturulan TableAdapter nesneleri kullanılarak basitleştirilemeyen birkaç standart işlem vardır. Bu sayfada TableAdapter'ları kullanarak bu standart işlemlerin nasıl uygulanacakları açıkmektedir. Özel nesnelerinizi oluşturmaya yönelik bir kılavuz olarak amaçlanmaz. Örneğin, nesnelerinizin veya uygulama mantığının belirli bir uygulamasına bakılmaksızın genellikle aşağıdaki standart işlemleri gerçekleştirebilirsiniz:

- Verileri nesnelere yükleme (genellikle bir veritabanından).

- Türe sahip nesne koleksiyonu oluşturma.

- Bir koleksiyona nesne ekleme ve koleksiyondan nesneleri kaldırma.

- Nesne verilerini bir formda kullanıcılara görüntüleme.

- Bir nesnede verileri değiştirme/düzenleme.

- Nesnelerden veritabanına veri kaydetme.

### <a name="load-data-into-objects"></a>Nesnelere veri yükleme

Bu örnekte, TableAdapter'ları kullanarak nesnelerinize veri yükleyebilirsiniz. Varsayılan olarak, TableAdapter'lar bir veritabanından veri alıp veri tablolarını doldurmak için iki tür yöntem ile oluşturulur.

- yöntemi, `TableAdapter.Fill` mevcut veri tablolarını döndürülen verilerle doldurur.

- yöntemi, `TableAdapter.GetData` verilerle doldurulmuş yeni bir veri tablosu döndürür.

Özel nesnelerinizi verilerle yüklemenin en kolay yolu yöntemini çağırarak döndürülen veri tablosunda satır koleksiyonunda döngü yapmak ve her nesneyi her satırdaki değerlerle `TableAdapter.GetData` doldurmaktır. `GetData`TableAdapter'a eklenen tüm sorgular için doldurulmuş veri tablosu döndüren bir yöntem oluşturabilirsiniz.

> [!NOTE]
> Visual Studio TableAdapter sorgularını varsayılan olarak olarak adlar, ancak bu adları herhangi bir `Fill` `GetData` geçerli yöntem adıyla değiştirebilirsiniz.

Aşağıdaki örnekte, bir veri tablosunda satırlar arasında döngü oluşturma ve bir nesneyi verilerle doldurmak için nasıl bir yol olduğu gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>Türe sahip nesne koleksiyonu oluşturma

Nesneleriniz için koleksiyon sınıfları oluşturabilir veya BindingSource bileşeni tarafından otomatik olarak sağlanan türe sahip [koleksiyonları kullanabilirsiniz.](/dotnet/framework/winforms/controls/bindingsource-component)

Nesneler için özel bir koleksiyon sınıfı oluştururken, 'den devralmanızı <xref:System.ComponentModel.BindingList%601> öneririz. Bu genel sınıf, koleksiyonlarınızı yönetmek için işlevselliğin yanı sıra Windows Forms'daki veri bağlama altyapısına bildirim gönderen olaylar Windows sağlar.

içinde otomatik olarak oluşturulan <xref:System.Windows.Forms.BindingSource> koleksiyon, türü oluşturulan <xref:System.ComponentModel.BindingList%601> koleksiyonu için kullanır. Uygulamanıza ek işlevsellik gerekli yoksa, koleksiyonunuz içinde <xref:System.Windows.Forms.BindingSource> korunabilirsiniz. Daha fazla bilgi için <xref:System.Windows.Forms.BindingSource.List%2A> sınıfının özelliğine <xref:System.Windows.Forms.BindingSource> bakın.

> [!NOTE]
> Koleksiyonunuz temel uygulaması tarafından sağlanmaz işlevsellik gerektiriyorsa, gerektiğinde sınıfına ekleyebilecek bir özel koleksiyon <xref:System.ComponentModel.BindingList%601> oluşturmanız gerekir.

Aşağıdaki kod, türü kesin olarak belirli bir nesne koleksiyonu için sınıfı oluşturma adımları `Order` gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>Koleksiyona nesne ekleme

Özel koleksiyon sınıfı veya yöntemini `Add` çağırarak bir koleksiyona nesneleri <xref:System.Windows.Forms.BindingSource> eklersiniz.

> [!NOTE]
> yöntemi, `Add` 'den devralınca özel koleksiyonunuz için otomatik olarak <xref:System.ComponentModel.BindingList%601> sağlanır.

Aşağıdaki kod, bir içinde türüne sahip koleksiyona nesne eklemeyi <xref:System.Windows.Forms.BindingSource> gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

Aşağıdaki kod, türünden devralınan bir koleksiyona nesne eklemeyi <xref:System.ComponentModel.BindingList%601> gösterir:

> [!NOTE]
> Bu örnekte, `Orders` koleksiyon nesnesinin bir `Customer` özelliğidir.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>Bir koleksiyondan nesneleri kaldırma

Nesneleri koleksiyondan kaldırmak için özel koleksiyon `Remove` sınıfı veya `RemoveAt` yöntemini <xref:System.Windows.Forms.BindingSource> çağırabilirsiniz.

> [!NOTE]
> ve `Remove` `RemoveAt` yöntemleri, 'den devralınarak özel koleksiyonunuz için otomatik olarak <xref:System.ComponentModel.BindingList%601> sağlanır.

Aşağıdaki kod, yöntemiyle bir içinde türüne sahip koleksiyondaki nesneleri bulma <xref:System.Windows.Forms.BindingSource> ve kaldırmayı <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> gösterir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>Nesne verilerini kullanıcılara görüntüleme

Nesnelerdeki verileri kullanıcılara görüntülemek için Veri Kaynağı  Yapılandırma sihirbazını kullanarak bir nesne veri kaynağı oluşturun ve ardından Veri Kaynakları penceresinden nesnenin veya tek tek özelliklerin tamamını form **üzerine** sürükleyin.

### <a name="modify-the-data-in-objects"></a>Nesnelerdeki verileri değiştirme

Windows Forms denetimlerine bağlı özel nesnelerdeki verileri düzenlemek için, bağlı denetimdeki (veya doğrudan nesnenin özelliklerinde) verileri düzenlemeniz gerekir. Veri bağlama mimarisi nesnesinde verileri günceller.

Uygulamanıza değişikliklerin izlemesi ve önerilen değişikliklerin özgün değerlerine geri uygulanması gerekiyorsa, bu işlevi nesne modelinize uygulamanız gerekir. Veri tablolarının önerilen değişiklikleri nasıl takip etmek için bkz. <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> , ve <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Nesnelerdeki verileri veritabanına geri kaydetme

Nesnenizin değerlerini TableAdapter'ın DBDirect yöntemlerine aktararak verileri veritabanına geri kaydedin.

Visual Studio doğrudan veritabanında yürütülen DBDirect yöntemleri oluşturur. Bu yöntemler Için DataSet veya DataTable nesneleri gerekli değildir.

|TableAdapter DBDirect yöntemi|Description|
| - |-----------------|
|`TableAdapter.Insert`|Veritabanına yeni kayıtlar ekler ve bu da tek tek sütun değerlerini yöntem parametreleri olarak geçmeniz için kullanılır.|
|`TableAdapter.Update`|Veritabanındaki mevcut kayıtları güncelleştirme. Update yöntemi, yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Özgün değerler özgün kaydı bulmak için kullanılır ve yeni değerler de bu kaydı güncelleştirmek için kullanılır.<br /><br /> yöntemi, bir , , veya dizisini yöntem parametreleri olarak alarak bir veri kümesinde yapılan değişiklikleri veritabanına geri almak `TableAdapter.Update` <xref:System.Data.DataSet> için de <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> kullanılır.|
|`TableAdapter.Delete`|Yöntem parametresi olarak geçirilen özgün sütun değerlerini temel alarak veritabanındaki mevcut kayıtları siler.|

Bir nesne koleksiyonundan veri kaydetmek için, nesne koleksiyonunda döngü (örneğin, for-next döngüsü kullanarak). TableAdapter'ın DBDirect yöntemlerini kullanarak her nesnenin değerlerini veritabanına gönderin.

Aşağıdaki örnekte, doğrudan veritabanına yeni bir `TableAdapter.Insert` müşteri eklemek için DBDirect yönteminin nasıl kullanılası açıkmektedir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
