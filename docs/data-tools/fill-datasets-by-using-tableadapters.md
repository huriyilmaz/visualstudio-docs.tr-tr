---
title: TableAdapter'ları kullanarak veri kümelerini doldurma
description: TableAdapters kullanarak veri kümelerini doldur. TableAdapter bileşeni, bir veri kümesini bir veya daha fazla sorgu ya da belirttiğiniz saklı yordamları temel alarak, VERITABANıNDAKI verilerle doldurur.
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
ms.openlocfilehash: 70013e4943e256871dfe12e38b364da1cc67c94f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631388"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapter'ları kullanarak veri kümelerini doldurma

TableAdapter bileşeni, bir veri kümesini bir veya daha fazla sorgu ya da belirttiğiniz saklı yordamlara göre veritabanından verileri doldurur. TableAdapters, veri kümesinde yaptığınız değişiklikleri kalıcı hale getirmek için veritabanında ekleme, güncelleştirme ve silme işlemleri de gerçekleştirebilir. Ayrıca, belirli bir tabloyla ilgisi olmayan genel komutlar da verebilirsiniz.

> [!NOTE]
> TableAdapters, Visual Studio tasarımcıları tarafından oluşturulur. Program aracılığıyla veri kümeleri oluşturuyorsanız, .NET sınıfı olan DataAdapter 'ı kullanın.

TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan şu konulardan birine atlayabilirsiniz:

|Konu|Description|
|-----------|-----------------|
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|TableAdapters oluşturmak ve yapılandırmak için tasarımcıları kullanma|
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcıların TableAdapter yordamlarına veya sorgularına bağımsız değişkenler vermesini sağlama|
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapters DBDirect yöntemlerini kullanma|
|[Veri kümesini doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Veriler güncelleştirilirken yabancı anahtar kısıtlamalarıyla çalışma|
|[TableAdapter işlevselliğini genişletme](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapters 'e özel kod ekleme|
|[XML verilerini bir veri kümesine okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter Genel Bakış

TableAdapters, bir veritabanına bağlanan, sorguları veya saklı yordamları çalıştıran ve DataTable değerlerini döndürülen verilerle dolduran tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapters Ayrıca, güncelleştirilmiş verileri uygulamanızdan veritabanına geri gönderir. TableAdapter 'ın ilişkilendirildiği tablonun şemasına uygun olan verileri döndürdüğü sürece, TableAdapter üzerinde istediğiniz kadar çok sorgu çalıştırabilirsiniz. Aşağıdaki diyagramda, TableAdapters 'in bellekteki veritabanları ve diğer nesnelerle nasıl etkileşime gireceğini gösterilmektedir:

![İstemci uygulamasında veri akışı](../data-tools/media/clientdatadiagram.gif)

TableAdapters, **veri kümesi Tasarımcısı** ile tasarlanırken, TableAdapter sınıfları iç içe geçmiş sınıfları olarak oluşturulmaz  <xref:System.Data.DataSet> . Her veri kümesine özgü ayrı ad alanlarında bulunur. Örneğin, adlı bir veri kümeniz varsa, `NorthwindDataSet` içinde ile ilişkili olan TableAdapters  <xref:System.Data.DataTable> `NorthwindDataSet` `NorthwindDataSetTableAdapters` ad alanında olur. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örnek:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb" id="Snippet7":::

## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması

Bir TableAdapter oluşturduğunuzda, TableAdapter 'ın ilişkili şemasını tanımlamak için ilk sorguyu veya saklı yordamı kullanırsınız <xref:System.Data.DataTable> . Bu ilk sorguyu veya saklı yordamı TableAdapter 'ın `Fill` metodunu çağırarak (TableAdapter 'ın ilişkili öğesini dolduran <xref:System.Data.DataTable> ) çalıştırırsınız. TableAdapter 'ın ana sorgusunda yapılan tüm değişiklikler, ilişkili veri tablosunun şemasına yansıtılır. Örneğin, ana sorgudan bir sütunu kaldırmak, sütunu ilişkili veri tablosundan da kaldırır. TableAdapter üzerinde herhangi bir ek sorgu ana sorguda olmayan sütunları döndüren SQL deyimlerini kullanıyorsa, tasarımcı ana sorgu ve ek sorgular arasındaki sütun değişikliklerini eşitlemeye çalışır.

## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları

TableAdapter 'ın güncelleştirme işlevselliği, **TableAdapter sihirbazındaki** ana sorguda ne kadar bilgi kullanılabileceğini bağlıdır. Örneğin, birden çok tablodan (kullanarak) değerler getirmek üzere yapılandırılan TableAdapters `JOIN` , skaler değerler, görünümler veya toplama işlevlerinin sonuçları, başlangıçta temel alınan veritabanına güncelleştirmeleri geri gönderebilme özelliği ile oluşturulmaz. Ancak,, `INSERT` `UPDATE` ve `DELETE` komutlarını **Özellikler** penceresinde el ile yapılandırabilirsiniz.

## <a name="tableadapter-queries"></a>TableAdapter sorguları

![Birden çok sorguya sahip TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapters, ilişkili veri tablolarını dolduracak birden çok sorgu içerebilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, bir TableAdapter 'ın farklı ölçütlere göre farklı sonuçlar yüklemesine olanak sağlar.

Örneğin, uygulamanız müşteri adları içeren bir tablo içeriyorsa, belirli bir harfle başlayan her müşteri adı ile tabloyu dolduran bir sorgu oluşturabilir ve diğer bir deyişle, tabloyu aynı durumda bulunan tüm müşterilerle doldurur. Bir `Customers` tabloyu belirli bir durumdaki müşterilerle doldurmanız için, `FillByState` durum değeri için bir parametreyi aşağıdaki şekilde alan bir sorgu oluşturabilirsiniz: `SELECT * FROM Customers WHERE State = @State` . `FillByState`Yöntemini çağırarak ve parametre değerini şöyle geçirerek sorgu çalıştırırsınız: `CustomerTableAdapter.FillByState("WA")` .

TableAdapter 'ın veri tablosu ile aynı şemadaki verileri döndüren sorguları eklemenin yanı sıra, skaler (tek) değerler döndüren sorgular da ekleyebilirsiniz. Örneğin, `SELECT Count(*) From Customers` `CustomersTableAdapter,` döndürülen veriler tablonun şemasına uygun olmasa da, müşteri sayısı döndüren bir sorgu (), için geçerlidir.

## <a name="clearbeforefill-property"></a>Clearbefodolum özelliği

Varsayılan olarak, bir TableAdapter 'ın veri tablosunu dolduracak bir sorguyu her çalıştırdığınızda, var olan veriler temizlenir ve yalnızca sorgunun sonuçları tabloya yüklenir. `ClearBeforeFill` `false` Bir sorgudan döndürülen verileri bir veri tablosundaki mevcut verilere eklemek veya birleştirmek istiyorsanız TableAdapter özelliğini olarak ayarlayın. Verileri temizlemenizden bağımsız olarak, devam etmek istiyorsanız, güncelleştirmeleri veritabanına geri açıkça göndermeniz gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce tablodaki verilerde yapılan değişiklikleri kaydetmeyi unutmayın. Daha fazla bilgi için bkz. [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter devralma

TableAdapters, yapılandırılmış bir sınıfı kapsülleyerek standart veri bağdaştırıcılarının işlevselliğini genişletir <xref:System.Data.Common.DataAdapter> . Varsayılan olarak, TableAdapter <xref:System.ComponentModel.Component> sınıfından devralır ve <xref:System.Data.Common.DataAdapter> sınıfa atanamaz. Bir TableAdapter 'ı sınıfa atama <xref:System.Data.Common.DataAdapter> bir <xref:System.InvalidCastException> hatayla sonuçlanır. Bir TableAdapter 'ın temel sınıfını değiştirmek için, <xref:System.ComponentModel.Component> **veri kümesi Tasarımcısı** TableAdapter 'ın **Base Class** özelliğinden türeten bir sınıf belirtebilirsiniz.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri

TableAdapter sınıfı bir .NET türü değil. Bu, belgelerde veya **nesne tarayıcısı** bakameyeceğiniz anlamına gelir. Daha önce bahsedilen sihirbazlardan birini kullandığınızda tasarım zamanında oluşturulur. Oluşturduğunuz bir TableAdapter 'a atanan ad, üzerinde çalıştığınız tablonun adını temel alır. Örneğin, adlı bir veritabanındaki bir tabloyu temel alan bir TableAdapter oluşturduğunuzda `Orders` , TableAdapter adlandırılır `OrdersTableAdapter` . TableAdapter 'ın sınıf adı, **veri kümesi Tasarımcısı** **ad** özelliği kullanılarak değiştirilebilir.

Aşağıda, TableAdapters 'in yaygın olarak kullanılan yöntemleri ve özellikleri verilmiştir:

|Üye|Description|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter 'ın ilişkili veri tablosunu TableAdapter komutunun sonuçlarıyla doldurur `SELECT` .|
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir tamsayı döndürür. Daha fazla bilgi için bkz. [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Verilerle doldurulan yeni bir döndürür <xref:System.Data.DataTable> .|
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için bkz. [veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|

## <a name="tableadapter-update-method"></a>TableAdapter Update yöntemi

TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. TableAdapter 'ın ilk `Fill` (ana) sorgusunu, ilişkili veri tablosunun şemasını oluşturma `InsertCommand` `UpdateCommand` ve `DeleteCommand` yöntemi ile ilişkili olan komutları temel olarak kullanın `TableAdapter.Update` . TableAdapter 'ın metodunu çağırmak `Update` , TableAdapter **sorgu Yapılandırma Sihirbazı** ile eklediğiniz ek sorgulardan birini değil, TableAdapter ilk yapılandırıldığında oluşturulan deyimleri çalıştırır.

TableAdapter kullandığınızda, genellikle gerçekleştirdiğiniz komutlarla aynı işlemleri etkili bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının `Fill` yöntemini çağırdığınızda, bağdaştırıcı özelliğindeki Data komutunu çalıştırır `SelectCommand` ve <xref:System.Data.SqlClient.SqlDataReader> sonuç kümesini veri tablosuna yüklemek için bir veri okuyucu (örneğin,) kullanır. Benzer şekilde, bağdaştırıcının `Update` yöntemini çağırdığınızda, `UpdateCommand` `InsertCommand` `DeleteCommand` veri tablosundaki her değiştirilmiş kayıt için uygun komutu (,, ve özellikleri) çalıştırır.

> [!NOTE]
> Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter 'ın ana sorgusu bir tek tablo deyiminden daha büyükse, `SELECT` Tasarımcı, ve oluşturamayacak `InsertCommand` `UpdateCommand` `DeleteCommand` . Bu komutlar oluşturulmadığından, yöntemini çalıştırırken bir hata alabilirsiniz `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği

, Ve ' a ek olarak, `InsertCommand` `UpdateCommand` `DeleteCommand` TableAdapters doğrudan veritabanına karşı çalıştırabileceğiniz yöntemlerle oluşturulur. `TableAdapter.Insert` `TableAdapter.Update` Veritabanındaki verileri işlemek için bu yöntemleri (, ve `TableAdapter.Delete` ) doğrudan çağırabilirsiniz. Bu, `TableAdapter.Update` ilişkili veri tablosu için bekleyen ekleme, güncelleştirme ve silme türlerini işlemek için çağırmak yerine kodunuzda bu tek yöntemleri çağırabilmeniz anlamına gelir.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter 'ın **GenerateDBDirectMethods** özelliğini olarak ayarlayın `false` ( **Özellikler** penceresinde). TableAdapter 'a eklenen ek sorgular tek başına sorgular; bu yöntemler oluşturmaz.

## <a name="tableadapter-support-for-nullable-types"></a>Nullable türler için TableAdapter desteği

TableAdapter'lar ve null değere değiştirilebilir türleri `Nullable(Of T)` `T?` destekler. Veri verilerinde null değere değiştirilebilir türler hakkında daha fazla Visual Basic bkz. [Null Değer Türleri.](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types) C# içinde null değere değiştirilebilir türler hakkında daha fazla bilgi için [bkz. Null değere değiştirilebilir türleri kullanma.](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu

TableAdapterManager sınıfı, ilgili tabloları içeren bir veri kümesi oluşturur. Sınıfın oluşturularak önlenmesi için veri kümesi özelliğinin `Hierarchical Update` değerini false olarak değiştirebilirsiniz. İlişkisi olan bir tabloyu Windows Form veya WPF sayfasının tasarım yüzeyine sürüklerseniz, Visual Studio bir üye değişkeni bildirecektir. Veri bağlamayı kullansanız bile değişkeni el ile tanımlamanız gerekir.

TableAdapterManager sınıfı bir .NET türü değildir. Bu nedenle belgelere bakamazsiniz. Tasarım zamanında, veri kümesi oluşturma işleminin bir parçası olarak oluşturulur.

Aşağıda, sınıfının sık kullanılan yöntemleri ve özellikleri yer `TableAdapterManager` almaktadır:

|Üye|Description|
|------------|-----------------|
|`UpdateAll` yöntemi|Tüm veri tablolarından tüm verileri kaydeder.|
|`BackUpDataSetBeforeUpdate` Özellik|yöntemi yürütülmeden önce veri kümesi yedek kopyasının oluşturulıp oluşturul olmadığını `TableAdapterManager.UpdateAll` belirler. Boolean.|
|*tableName* `TableAdapter` Özellik|TableAdapter'i temsil eder. Oluşturulan TableAdapterManager, yönetirken her biri için `TableAdapter` bir özellik içerir. Örneğin, Customers ve Orders tablosuna sahip bir veri kümesi, ve özelliklerini içeren bir TableAdapterManager `CustomersTableAdapter` ile `OrdersTableAdapter` oluşturulur.|
|`UpdateOrder` Özellik|Tek tek ekleme, güncelleştirme ve silme komutlarının sıralamalarını kontrol eder. Bunu, numaralamada yer alan `TableAdapterManager.UpdateOrderOption` değerlerden biri olarak ayarlayın.<br /><br /> Varsayılan olarak, `UpdateOrder` **InsertUpdateDelete olarak ayarlanır.** Bu, veri kümesinde tüm tablolar için eklemeler, güncelleştirmeler ve silmeler gerçekleştirecekleri anlamına gelir.|

## <a name="security"></a>Güvenlik

Bir CommandType özelliği olarak ayarlanmış veri komutlarını kullanıyorsanız, istemciden veritabanınıza geçirmeden <xref:System.Data.CommandType.Text> önce gönderilen bilgileri dikkatle kontrol edin. Kötü amaçlı kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar SQL amacıyla değiştirilmiş veya ek veri deyimleri göndermeye (ekleme) deneyebilir. Kullanıcı girişini bir veritabanına aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Mümkün olduğunda her zaman parametreli sorgular veya saklı yordamlar kullanmak en iyi yöntemdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
