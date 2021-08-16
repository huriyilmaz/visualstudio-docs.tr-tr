---
title: TableAdapter'ları kullanarak veri kümelerini doldurma
description: TableAdapter'ları kullanarak veri kümelerini doldurun. TableAdapter bileşeni, belirttiğiniz bir veya daha fazla sorguyu veya saklı yordamları temel alarak veri kümelerini veritabanındaki verilerle doldurur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ce4c351bb2226fb1fee5e574b7a35fa7f4d380898d99be1805dce42aed9b0226
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347290"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapter'ları kullanarak veri kümelerini doldurma

TableAdapter bileşeni, belirttiğiniz bir veya daha fazla sorguyu veya saklı yordamları temel alarak veri kümelerini veritabanındaki verilerle doldurur. TableAdapter'lar, veri kümesinde yaptığınız değişiklikleri kalıcı hale almak için veritabanında ekleme, güncelleştirme ve silme işlemleri de gerçekleştirebilirsiniz. Belirli bir tabloyla ilgili olmayan genel komutlar da veebilirsiniz.

> [!NOTE]
> TableAdapter'lar, Visual Studio oluşturulur. Veri kümelerini program aracılığıyla oluşturuyorsanız, .NET sınıfı olan DataAdapter'ı kullanın.

TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan şu konulardan birini atlayabilirsiniz:

|Konu|Açıklama|
|-----------|-----------------|
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|TableAdapter'ları oluşturmak ve yapılandırmak için tasarımcıları kullanma|
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcıların TableAdapter yordamlarına veya sorgularına bağımsız değişkenler teminlerini etkinleştirme|
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapter'ların Dbdirect yöntemlerini kullanma|
|[Veri kümesi doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Verileri güncelleştirmede yabancı anahtar kısıtlamalarıyla çalışma|
|[TableAdapter işlevselliğini genişletme](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapter'lara özel kod ekleme|
|[XML verilerini bir veri kümesine okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter'a genel bakış

TableAdapter'lar, bir veritabanına bağlanarak sorgular veya saklı yordamlar çalıştıran ve DataTable'larını döndürülen verilerle dolduran tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapter'lar, güncelleştirilmiş verileri de uygulamanıza geri gönderir. TableAdapter'ın ilişkili olduğu tablonun şemasına uygun veriler getirtikleri sürece, TableAdapter üzerinde istediğiniz kadar sorgu çalıştırabilirsiniz. Aşağıdaki diyagramda TableAdapter'ların bellekte veritabanları ve diğer nesnelerle nasıl etkileşim kurduğu gösterir:

![İstemci uygulamasında veri akışı](../data-tools/media/clientdatadiagram.gif)

TableAdapter'lar, Veri Kümesi Tasarımcısı ile **tasarlanırken** TableAdapter sınıfları iç içe geçmiş sınıfları olarak  <xref:System.Data.DataSet> oluşturulmaz. Her veri kümesine özgü ayrı ad alanlarında bulunurlar. Örneğin, adlı bir veri küme varsa, içinde ile ilişkili `NorthwindDataSet` TableAdapter'lar  <xref:System.Data.DataTable> `NorthwindDataSet` ad alanı `NorthwindDataSetTableAdapters` olacaktır. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örnek:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb" id="Snippet7":::

## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması

Bir TableAdapter oluştururken, TableAdapter'ın ilişkili şemasını tanımlamak için ilk sorguyu veya saklı yordamı <xref:System.Data.DataTable> kullanırsınız. TableAdapter'ın yöntemini çağırarak bu ilk sorguyu veya saklı yordamı çalıştırabilirsiniz `Fill` (TableAdapter'ın ilişkili olan yöntemini <xref:System.Data.DataTable> doldurur). TableAdapter'ın ana sorgusunda yapılan tüm değişiklikler ilişkili veri tablosu şemasına yansıtıldı. Örneğin, ana sorgudan bir sütunu kaldırmak, sütunu ilişkili veri tablosundan da kaldırır. TableAdapter'daki ek sorgulardan biri ana sorguda yer alan sütunları SQL deyimlerini kullanıyorsa tasarımcı, sütun değişikliklerini ana sorguyla ek sorgular arasında eşitlemeye çalışır.

## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları

TableAdapter'ın güncelleştirme işlevselliği, **TableAdapter** Sihirbazı'nda ana sorguda ne kadar bilgi bulunana bağlıdır. Örneğin, birden çok tablodan (kullanarak), skaler değerler, görünümler veya toplama işlevlerinin sonuçları kullanılarak değerleri getirmek üzere yapılandırılan TableAdapter'lar başlangıçta güncelleştirmeleri temel alınan veritabanına geri gönderebilme özelliğiyle `JOIN` oluşturulmaz. Ancak, Özellikler penceresinde `INSERT` , `UPDATE` ve `DELETE` komutlarını el ile **yapılandırabilirsiniz.**

## <a name="tableadapter-queries"></a>TableAdapter sorguları

![Birden çok sorgu içeren TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapter'lar ilişkili veri tablolarını doldurmak için birden çok sorgu içerebilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, TableAdapter'ın farklı ölçütlere göre farklı sonuçlar yüklemesi sağlar.

Örneğin, uygulamanız müşteri adlarını içeren bir tablo içeriyorsa, tabloyu belirli bir harfle başlayan her müşteri adıyla dolduran bir sorgu ve tabloyu aynı durumdaki tüm müşterilerle dolduran başka bir sorgu oluşturabilirsiniz. Bir tabloyu verilen durumdaki müşterilerle doldurmak için, durum değeri için bir parametre alan `Customers` `FillByState` bir sorgu oluşturabilirsiniz: `SELECT * FROM Customers WHERE State = @State` . sorgusunu çalıştırmak için yöntemini `FillByState` çağırarak ve parametre değerini şu şekilde geçirmeniz gerekir: `CustomerTableAdapter.FillByState("WA")` .

TableAdapter'ın veri tablosuyla aynı şemaya ait verileri geri alan sorgular eklemeye ek olarak, skaler (tek) değerlere sahip sorgular da ekebilirsiniz. Örneğin, döndürülen veriler tablonun şemasına uymasa bile müşteri sayısı ( ) döndüren bir `SELECT Count(*) From Customers` `CustomersTableAdapter,` sorgu için geçerlidir.

## <a name="clearbeforefill-property"></a>ClearBeforeFill özelliği

Varsayılan olarak, TableAdapter'ın veri tablosunu doldurmak için bir sorguyu her çalıştırsanız, mevcut veriler temiz olur ve tabloya yalnızca sorgunun sonuçları yüklenir. Bir sorgudan döndürülen verileri bir veri tablosunda var olan verilere eklemek veya birleştirmek için TableAdapter özelliğini `ClearBeforeFill` `false` olarak ayarlayın. Verileri temizleyenin ne olursa olsun, kalıcı olarak kalıcı olmak için güncelleştirmeleri açıkça veritabanına geri göndermelisiniz. Bu nedenle tabloyu dolduran başka bir sorgu çalıştırmadan önce tablodaki verilerde yapılan değişiklikleri kaydetmeyi unutmayın. Daha fazla bilgi için [bkz. TableAdapter kullanarak verileri güncelleştirme.](../data-tools/update-data-by-using-a-tableadapter.md)

## <a name="tableadapter-inheritance"></a>TableAdapter devralma

TableAdapter'lar, yapılandırılmış bir sınıfı kapsülleerek standart veri bağdaştırıcılarının işlevselliğini <xref:System.Data.Common.DataAdapter> genişleter. Varsayılan olarak, TableAdapter sınıfından <xref:System.ComponentModel.Component> devralınır ve sınıfına türeten <xref:System.Data.Common.DataAdapter> değildir. Sınıfına TableAdapter <xref:System.Data.Common.DataAdapter> ataması hatayla <xref:System.InvalidCastException> sonuçlandı. TableAdapter'ın temel sınıfını değiştirmek için, içinde <xref:System.ComponentModel.Component> TableAdapter'ın Temel **Sınıf** özelliğinden türetilen bir sınıf **Veri Kümesi Tasarımcısı.**

## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri

TableAdapter sınıfı bir .NET türü değildir. Bu, belgelerde veya Object Browser'da bunu alamay **anlamına gelir.** Daha önce bahsedilen sihirbazlardan birini kullanarak tasarım zamanında oluşturulur. Bir TableAdapter'a oluşturma adımlarında atanan ad, üzerinde çalışmakta olduğu tablonun adına göredir. Örneğin, adlı veritabanındaki bir tabloyu temel alan bir TableAdapter oluştururken `Orders` TableAdapter olarak `OrdersTableAdapter` adlandırılmıştır. TableAdapter'ın sınıf adı, Veri Kümesi Tasarımcısı.  

TableAdapter'ların yaygın olarak kullanılan yöntemleri ve özellikleri aşağıda ve listelerde ve listelerde yer almaktadır:

|Üye|Açıklama|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter'ın ilişkili veri tablolarını TableAdapter komutunun sonuçlarıyla `SELECT` doldurmak.|
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir tamsayı döndürür. Daha fazla bilgi için [bkz. TableAdapter kullanarak verileri güncelleştirme.](../data-tools/update-data-by-using-a-tableadapter.md)|
|`TableAdapter.GetData`|Verilerle <xref:System.Data.DataTable> doldurulmuş yeni bir döndürür.|
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için [bkz. Veritabanına yeni kayıtlar ekleme.](../data-tools/insert-new-records-into-a-database.md)|
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|

## <a name="tableadapter-update-method"></a>TableAdapter güncelleştirme yöntemi

TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. TableAdapter'ın ilk (main) sorgusunu, ilişkili veri tablosu şemasının yanı sıra yöntemiyle ilişkili , ve komutlarını oluşturmak için temel olarak `Fill` `InsertCommand` `UpdateCommand` `DeleteCommand` `TableAdapter.Update` kullanın. TableAdapter'ın yöntemini çağırma, TableAdapter ilk yapılandırıldığında oluşturulan deyimlerini `Update` **çalıştırır; TableAdapter** Sorgu Yapılandırma Sihirbazı ile birlikte eklenen ek sorgulardan birini çalıştırmaz.

TableAdapter'i kullanarak normalde gerçekleştirecekleri komutlarla aynı işlemleri etkili bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının yöntemini çağırsanız, bağdaştırıcı özelliğinde veri komutunu çalıştırır ve sonuç kümesi veri tablosuna yüklemek için bir veri okuyucu `Fill` `SelectCommand` (örneğin, <xref:System.Data.SqlClient.SqlDataReader> ) kullanır. Benzer şekilde, bağdaştırıcının yöntemini çağırsanız, veri tablosunda değiştirilen her kayıt için uygun komutu `Update` (, `UpdateCommand` ve `InsertCommand` `DeleteCommand` özelliklerinde) çalıştırır.

> [!NOTE]
> Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter'ın ana sorgusu tek bir tablo deyiminden fazla ise, tasarımcı `SELECT` , ve `InsertCommand` `UpdateCommand` oluşturamayabilecektir. `DeleteCommand` Bu komutlar oluşturulmazsa, yöntemini çalıştırarak bir hata `TableAdapter.Update` alabilirsiniz.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği

, `InsertCommand` ve `UpdateCommand` 'ye ek `DeleteCommand` olarak TableAdapter'lar, doğrudan veritabanında çalıştırabilirsiniz yöntemlerle oluşturulur. Veritabanındaki verileri işlemek için bu yöntemleri ( `TableAdapter.Insert` , ve ) doğrudan `TableAdapter.Update` `TableAdapter.Delete` çağırabilirsiniz. Bu, ilişkili veri tablosu için bekleyen eklemeleri, güncelleştirmeleri ve silmeleri işlemek için çağrısı yapmak yerine bu yöntemleri kodunuzdan `TableAdapter.Update` çağırabilirsiniz.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız TableAdapter'ın **GenerateDbDirectMethods** özelliğini olarak `false` ayarlayın **(Özellikler** penceresinde). TableAdapter'a eklenen ek sorgular tek başına sorgulardır; bu yöntemler oluşturulmaz.

## <a name="tableadapter-support-for-nullable-types"></a>Null değere sahip türler için TableAdapter desteği

TableAdapter'lar ve null değere sahip türleri `Nullable(Of T)` `T?` destekler. Dosyalarda null değere değiştirilebilir türler hakkında daha fazla Visual Basic bkz. [Null Değer Türleri.](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types) C# içinde null değere değiştirilebilir türler hakkında daha fazla bilgi için [bkz. Null değere değiştirilebilir türleri kullanma.](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu

TableAdapterManager sınıfı, ilgili tabloları içeren bir veri kümesi oluşturur. Sınıfın oluşturularak önlenmesi için veri kümesi özelliğinin `Hierarchical Update` değerini false olarak değiştirebilirsiniz. İlişkisi olan bir tabloyu Windows Form veya WPF sayfasının tasarım yüzeyine sürüklerseniz, Visual Studio bir üye değişkeni bildirecektir. Veri bağlamayı kullansanız bile değişkeni el ile tanımlamanız gerekir.

TableAdapterManager sınıfı bir .NET türü değildir. Bu nedenle belgelere bakamazsiniz. Tasarım zamanında, veri kümesi oluşturma işleminin bir parçası olarak oluşturulur.

Aşağıda, sınıfının sık kullanılan yöntemleri ve özellikleri ve `TableAdapterManager` bulunmaktadır:

|Üye|Açıklama|
|------------|-----------------|
|`UpdateAll` yöntemi|Tüm veri tablolarından tüm verileri kaydeder.|
|`BackUpDataSetBeforeUpdate` Özellik|yöntemi yürütülmeden önce veri kümesi yedek kopyasının oluşturulıp oluşturul olmadığını `TableAdapterManager.UpdateAll` belirler. Boolean.|
|*tableName* `TableAdapter` Özellik|TableAdapter'i temsil eder. Oluşturulan TableAdapterManager, yönetirken her biri için `TableAdapter` bir özellik içerir. Örneğin, Customers ve Orders tablosuna sahip bir veri kümesi, ve özelliklerini içeren bir TableAdapterManager `CustomersTableAdapter` ile `OrdersTableAdapter` oluşturulur.|
|`UpdateOrder` Özellik|Tek tek ekleme, güncelleştirme ve silme komutlarının sıralamalarını kontrol eder. Bunu, numaralamada yer alan `TableAdapterManager.UpdateOrderOption` değerlerden biri olarak ayarlayın.<br /><br /> Varsayılan olarak, `UpdateOrder` **InsertUpdateDelete olarak ayarlanır.** Bu, veri kümesinde tüm tablolar için eklemeler, güncelleştirmeler ve silmeler gerçekleştirecekleri anlamına gelir.|

## <a name="security"></a>Güvenlik

Bir CommandType özelliği olarak ayarlanmış veri komutlarını kullanıyorsanız, istemciden veritabanınıza geçirmeden <xref:System.Data.CommandType.Text> önce gönderilen bilgileri dikkatle kontrol edin. Kötü amaçlı kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar SQL amacıyla değiştirilmiş veya ek kullanıcı deyimleri göndermeye (ekleme) deneyebilir. Kullanıcı girişini bir veritabanına aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Mümkün olduğunda her zaman parametreli sorgular veya saklı yordamlar kullanmak en iyi yöntemdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
