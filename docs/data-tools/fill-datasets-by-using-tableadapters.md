---
title: TableAdapter'ları kullanarak veri kümelerini doldurma
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302240"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapter'ları kullanarak veri kümelerini doldurma

TableAdapter bileşeni, belirttiğiniz bir veya daha fazla sorguyu veya depolanmış yordamları temel alarak bir veri kümesini veritabanından gelen verilerle doldurur. TableAdapters ayrıca veri kümesinde yaptığınız değişiklikleri kalıcı hale getirmek için veritabanında eklemeler, güncelleştirmeler ve silmeler de gerçekleştirebilir. Belirli bir tabloyla ilgisi olmayan genel komutlar da düzenleyebilirsiniz.

> [!NOTE]
> TableAdapters Visual Studio tasarımcıları tarafından oluşturulur. Veri kümelerini programlı bir şekilde oluşturuyorsanız, bir .NET sınıfı olan DataAdapter'ı kullanın.

TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan aşağıdaki konulardan birine atlayabilirsiniz:

|Konu başlığı|Açıklama|
|-----------|-----------------|
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|TableAdapters oluşturmak ve yapılandırmak için tasarımcılar nasıl kullanılır|
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcıların TableAdapter yordamlarına veya sorgularına bağımsız değişken sağlamalarını etkinleştirme|
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapters Dbdirect yöntemleri nasıl kullanılır|
|[Veri kümesini doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Verileri güncellerken yabancı anahtar kısıtlamalarıyla nasıl çalışılı?|
|[TableAdapter'ın işlevselliği nasıl genişletilir?](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapters'a özel kod ekleme|
|[XML verilerini veri kümesinde okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter genel bakış

TableAdapters, veritabanına bağlanan, sorguları çalıştıran veya depolanan işlemleri çalıştıran ve DataTable'larını döndürülen verilerle dolduran tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapters ayrıca uygulamanızdan güncelleştirilmiş verileri veritabanına geri gönderir. TableAdapter ile ilişkili tablonun şemasına uygun verileri döndürdükleri sürece, TableAdapter'da istediğiniz kadar sorgu çalıştırabilirsiniz. Aşağıdaki diyagram, TableAdapters'ın bellekteki veritabanları ve diğer nesnelerle nasıl etkileşimde olduğunu gösterir:

![İstemci uygulamasında veri akışı](../data-tools/media/clientdatadiagram.gif)

TableAdapters **Dataset Designer**ile tasarlanmış olsa da, TableAdapter sınıfları <xref:System.Data.DataSet>iç içe sınıfları olarak oluşturulmaz. Bunlar, her veri kümesine özgü ayrı ad alanlarında bulunurlar. Örneğin, `NorthwindDataSet`adlı bir veri kümeniz varsa, s ile <xref:System.Data.DataTable>ilişkili `NorthwindDataSet` TableAdapters `NorthwindDataSetTableAdapters` ad alanında olacaktır. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örnek:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması

Bir TableAdapter oluşturduğunuzda, TableAdapter ilişkili şemasını tanımlamak için ilk sorgu yu veya <xref:System.Data.DataTable>depolanan yordamı kullanırsınız. Bu ilk sorguyu veya depolanan yordamı TableAdapter'ın yöntemini (TableAdapter'ın `Fill` ilişkili <xref:System.Data.DataTable>yöntemini doldurur) çağırarak çalıştırın. TableAdapter'ın ana sorgusunda yapılan tüm değişiklikler ilişkili veri tablosunun şemasına yansıtılır. Örneğin, bir sütunu ana sorgudan kaldırmak da sütunu ilişkili veri tablosundan kaldırır. TableAdapter'daki ek sorgular ana sorguda olmayan sütunları döndüren SQL deyimleri kullanırsa, tasarımcı sütun değişikliklerini ana sorgu ile ek sorgular arasında eşitlemeye çalışır.

## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları

TableAdapter'ın güncelleştirme işlevi, **TableAdapter Sihirbazı'ndaki**ana sorguda ne kadar bilgi nin bulunduğuna bağlıdır. Örneğin, birden çok tablodan (a), `JOIN`skaler değerler, görünümler veya toplu işlevlerin sonuçları ndan değerleri almak üzere yapılandırılan TableAdapters, başlangıçta güncelleştirmeleri temel veritabanına geri gönderme olanağıyla oluşturulmaz. Ancak, **Özellikler** penceresinde `INSERT`el `UPDATE`ile `DELETE` , ve komutları yapılandırabilirsiniz.

## <a name="tableadapter-queries"></a>TableAdapter sorguları

![Birden çok sorguile TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapters ilişkili veri tablolarını doldurmak için birden çok sorgu içerebilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, bir TableAdapter'ın farklı ölçütlere göre farklı sonuçlar yüklemesini sağlar.

Örneğin, uygulamanız müşteri adlarıyla dolu bir tablo içeriyorsa, tabloyu belirli bir harfle başlayan her müşteri adı yla dolduran bir sorgu ve tabloyu aynı durumda bulunan tüm müşterilerle dolduran başka bir sorgu oluşturabilirsiniz. Bir tabloyu `Customers` belirli bir durumdaki müşterilerle doldurmak `FillByState` için, durum değeri için aşağıdaki gibi `SELECT * FROM Customers WHERE State = @State`bir parametre alan bir sorgu oluşturabilirsiniz: . `FillByState` Yöntemi çağırarak ve parametre değerini şu şekilde geçirerek `CustomerTableAdapter.FillByState("WA")`sorguyu çalıştırın: .

TableAdapter'ın veri tablosuyla aynı şema verilerini döndüren sorgular eklemenin yanı sıra, skaler (tek) değerleri döndüren sorgular ekleyebilirsiniz. Örneğin, müşteri sayısını döndüren bir`SELECT Count(*) From Customers`sorgu ( `CustomersTableAdapter,` ) döndürülen veriler tablonun şemasına uymasa da geçerlidir.

## <a name="clearbeforefill-property"></a>ClearBeforeFill özelliği

Varsayılan olarak, bir TableAdapter'ın veri tablosunu doldurmak için her sorgu çalıştırdığınızda, varolan veriler temizlenir ve yalnızca sorgunun sonuçları tabloya yüklenir. Bir sorgudan döndürülen `ClearBeforeFill` verileri `false` veri tablosundaki varolan verilere eklemek veya birleştirmek istiyorsanız TableAdapter'ın özelliğini ayarlayın. Verileri temizleyip temizlemediğine bakılmaksızın, kalıcı hale getirmek istiyorsanız güncelleştirmeleri açıkça veritabanına göndermeniz gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce tablodaki verilerde yapılan değişiklikleri kaydetmeyi unutmayın. Daha fazla bilgi için [tableadapter kullanarak verileri güncelleştir'e](../data-tools/update-data-by-using-a-tableadapter.md)bakın.

## <a name="tableadapter-inheritance"></a>TableAdapter devralma

TableAdapters yapılandırılmış bir <xref:System.Data.Common.DataAdapter> sınıf kapsülleme standart veri bağdaştırıcılarının işlevselliğini genişletir. Varsayılan olarak, TableAdapter <xref:System.ComponentModel.Component> sınıftan devralır ve <xref:System.Data.Common.DataAdapter> sınıfa atılamaz. TabloAdapter'ı <xref:System.Data.Common.DataAdapter> sınıfa vermek <xref:System.InvalidCastException> bir hatayla sonuçlanır. TableAdapter'ın taban sınıfını değiştirmek için, **Dataset Designer'daki**TableAdapter'ın **Taban Sınıf** özelliğinden <xref:System.ComponentModel.Component> türeyen bir sınıf belirtebilirsiniz.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri

TableAdapter sınıfı bir .NET türü değildir. Bu, belgelerde veya **Nesne Tarayıcısında**arama yapabileceğiniz anlamına gelir. Daha önce bahsedilen sihirbazlardan birini kullandığınızda tasarım zamanında oluşturulur. Oluşturduğunuzda TableAdapter'a atanan ad, üzerinde çalıştığınız tablonun adını temel alıntır. Örneğin, adlı `Orders`bir veritabanında bir tabloya dayalı bir TableAdapter oluşturduğunuzda, TableAdapter adlı `OrdersTableAdapter`. TableAdapter'ın sınıf **adı, Dataset Designer'daki** **Ad** özelliği kullanılarak değiştirilebilir.

TableAdapters'ın yaygın olarak kullanılan yöntemleri ve özellikleri şunlardır:

|Üye|Açıklama|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter'ın ilişkili veri tablosunu TableAdapter `SELECT` komutunun sonuçlarıyla doldurur.|
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir karşıcı döndürür. Daha fazla bilgi için [tableadapter kullanarak verileri güncelleştir'e](../data-tools/update-data-by-using-a-tableadapter.md)bakın.|
|`TableAdapter.GetData`|Verilerle <xref:System.Data.DataTable> dolu yeni bir yeni verir.|
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için [bkz.](../data-tools/insert-new-records-into-a-database.md)|
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|

## <a name="tableadapter-update-method"></a>TableAdapter güncelleme yöntemi

TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. `Fill` TableAdapter'ın ilk (ana) sorgusunu, ilişkili veri tablosunun şemasını oluşturmak için `InsertCommand`temel `UpdateCommand`olarak `DeleteCommand` yanı `TableAdapter.Update` sıra, yöntemle ilişkili komutları ve komutları kullanın. TableAdapter'ın `Update` yöntemini çağırmak, TableAdapter'ın ilk olarak yapılandırıldığında oluşturulan ifadeleri çalıştırırken, **TableAdapter Query Configuration Wizard**ile eklediğiniz ek sorgulardan birini değil.

TableAdapter kullandığınızda, genellikle gerçekleştireceğiniz komutlarla aynı işlemleri etkin bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının `Fill` yöntemini çağırdığınızda, bağdaştırıcı `SelectCommand` özelliğindeki veri komutunu <xref:System.Data.SqlClient.SqlDataReader>çalıştırır ve sonuç kümesini veri tablosuna yüklemek için bir veri okuyucusu kullanır . Benzer şekilde, bağdaştırıcının `Update` yöntemini çağırdığınızda, veri `UpdateCommand` `InsertCommand`tablosundaki `DeleteCommand` her değiştirilen kayıt için uygun komutu (, , ve özelliklerde) çalıştırUr.

> [!NOTE]
> Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter'ın ana sorgusu tek bir tablo `SELECT` deyiminden fazlaysa, tasarımcının bunu `InsertCommand`oluşturaması `UpdateCommand`mümkün `DeleteCommand`değildir ve . Bu komutlar oluşturulmazsa, `TableAdapter.Update` yöntemi çalıştırırken bir hata alabilirsiniz.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği

TableAdapters `InsertCommand` `UpdateCommand`ek `DeleteCommand`olarak doğrudan veritabanına karşı çalıştırabilirsiniz yöntemleri ile oluşturulur. Bu yöntemleri doğrudan`TableAdapter.Insert`veritabanındaki `TableAdapter.Delete`verileri işlemek için arayabilirsiniz. `TableAdapter.Update` Bu, ilişkili veri tablosu için bekleyen ekler, güncelleştirmeler ve silmeleri işlemek için aramak `TableAdapter.Update` yerine bu yöntemleri kodunuzdan çağırabileceğiniz anlamına gelir.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter'ın **GenerateDbDirectMethods** özelliğini `false` **(Özellikler** penceresinde) ayarlayın. TableAdapter'a eklenen ek sorgular bağımsız sorgulardır — bu yöntemleri oluşturmaz.

## <a name="tableadapter-support-for-nullable-types"></a>Nullable türleri için TableAdapter desteği

TableAdapters geçersiz türleri `Nullable(Of T)` `T?`destekler ve. Visual Basic'teki nullable türleri hakkında daha fazla bilgi için, [Nullable Value Types'a](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)bakın. C#'daki nullable türleri hakkında daha fazla bilgi için [bkz.](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu

Varsayılan olarak, ilgili tabloları içeren bir veri kümesi oluşturduğunuzda tableadapterManager sınıfı oluşturulur. Sınıfın oluşturulmasını önlemek için, veri kümesinin `Hierarchical Update` özelliğinin değerini false olarak değiştirin. Windows Formu veya WPF sayfasının tasarım yüzeyine ilişkisi olan bir tabloyu sürüklüyorsanız, Visual Studio sınıfın bir üye değişkenini bildirir. Veri bağlama kullanmıyorsanız, değişkeni el ile bildirmeniz gerekir.

TableAdapterManager sınıfı bir .NET türü değildir. Bu nedenle, belgelerde bu kadar bakamazsınız. Veri kümesi oluşturma işleminin bir parçası olarak tasarım zamanında oluşturulur.

Sınıfın sık kullanılan yöntemleri ve özellikleri `TableAdapterManager` şunlardır:

|Üye|Açıklama|
|------------|-----------------|
|`UpdateAll` yöntemi|Tüm veri tablolarından tüm verileri kaydeder.|
|`BackUpDataSetBeforeUpdate`Özellik|`TableAdapterManager.UpdateAll` Yöntemi yürütmeden önce veri kümesinin yedek kopyasını oluşturup oluşturmayacağını belirler. Boolean.|
|*tabloAd* `TableAdapter` özelliği|TableAdapter'ı temsil eder. Oluşturulan TableAdapterManager, yönettiği her `TableAdapter` biri için bir özellik içerir. Örneğin, Müşteriler ve Siparişler tablosuna sahip bir veri kümesi, içeren `CustomersTableAdapter` `OrdersTableAdapter` ve özellikleri olan bir TableAdapterManager ile oluşturur.|
|`UpdateOrder`Özellik|Tek tek ekleme, güncelleştirme ve silme komutlarının sırasını denetler. Bunu numaralandırmadaki `TableAdapterManager.UpdateOrderOption` değerlerden birine ayarlayın.<br /><br /> Varsayılan olarak, `UpdateOrder` **InsertUpdateDelete**olarak ayarlanır. Bu, veri kümesindeki tüm tablolar için ekler, ardından güncelleştirmeler ve ardından silmelerin gerçekleştirildi anlamına gelir.|

## <a name="security"></a>Güvenlik

Komut Türü özelliği ayarlanmış veri komutlarını <xref:System.Data.CommandType.Text>kullandığınızda, veritabanınıza geçirmeden önce istemciden gönderilen bilgileri dikkatle denetleyin. Kötü niyetli kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar vermek amacıyla değiştirilmiş veya ek SQL deyimleri göndermeyi (enjekte etmeyi) deneyebilir. Kullanıcı girişini bir veritabanına aktarmadan önce, her zaman bilgilerin geçerli olduğunu doğrulayın. En iyi yöntem, parametrelendirilmiş sorguları veya depolanmış yordamları mümkün olduğunda her zaman kullanmaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dataset araçları](../data-tools/dataset-tools-in-visual-studio.md)
