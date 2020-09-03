---
title: TableAdapters kullanarak veri kümelerini doldur | Microsoft Docs
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fd1dcf464b7628e345845ca9f371ef6de1efe88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672346"
---
# <a name="fill-datasets-by-using-tableadapters"></a>TableAdapter'ları kullanarak veri kümelerini doldurma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter bileşeni, bir veri kümesini bir veya daha fazla sorgu ya da belirttiğiniz saklı yordamlara göre veritabanından verileri doldurur. TableAdapters, veri kümesinde yaptığınız değişiklikleri kalıcı hale getirmek için veritabanında ekleme, güncelleştirme ve silme işlemleri de gerçekleştirebilir. Ayrıca, belirli bir tabloyla ilgisi olmayan genel komutlar da verebilirsiniz.

> [!NOTE]
> TableAdapters, Visual Studio tasarımcıları tarafından oluşturulur. Program aracılığıyla veri kümeleri oluşturuyorsanız, bir .NET Framework sınıfı olan DataAdapter 'ı kullanın.

 TableAdapter işlemleri hakkında ayrıntılı bilgi için doğrudan şu konulardan birine atlayabilirsiniz:

|Konu|Description|
|-----------|-----------------|
|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|TableAdapters oluşturmak ve yapılandırmak için tasarımcıları kullanma|
|[Parametreleştirilmiş TableAdapter sorguları oluşturma](../data-tools/create-parameterized-tableadapter-queries.md)|Kullanıcıların TableAdapter yordamlarına veya sorgularına bağımsız değişkenler vermesini sağlama|
|[Bir TableAdapter ile veritabanına doğrudan erişme](../data-tools/directly-access-the-database-with-a-tableadapter.md)|TableAdapters DBDirect yöntemlerini kullanma|
|[Veri kümesini doldururken kısıtlamaları kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Veriler güncelleştirilirken yabancı anahtar kısıtlamalarıyla çalışma|
|[TableAdapter işlevselliğini genişletme](../data-tools/fill-datasets-by-using-tableadapters.md)|TableAdapters 'e özel kod ekleme|
|[XML verilerini bir veri kümesine okuma](../data-tools/read-xml-data-into-a-dataset.md)|XML ile çalışma|

## <a name="tableadapters-overview"></a>TableAdapter’lara genel bakış
 TableAdapters, bir veritabanına bağlanan, sorguları veya saklı yordamları çalıştıran ve DataTable değerlerini döndürülen verilerle dolduran tasarımcı tarafından oluşturulan bileşenlerdir. TableAdapters Ayrıca, güncelleştirilmiş verileri uygulamanızdan veritabanına geri gönderir. TableAdapter 'ın ilişkilendirildiği tablonun şemasına uygun olan verileri döndürdüğü sürece, TableAdapter üzerinde istediğiniz kadar çok sorgu çalıştırabilirsiniz. Aşağıdaki diyagramda, TableAdapters 'in bellekteki veritabanları ve diğer nesnelerle nasıl etkileşime gireceğini gösterilmektedir:

 ![İstemci uygulamasında veri akışı](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")

 TableAdapters, **veri kümesi Tasarımcısı**ile tasarlanırken, TableAdapter sınıfları iç içe geçmiş sınıfları olarak oluşturulmaz  <xref:System.Data.DataSet> . Her veri kümesine özgü ayrı ad alanlarında bulunur. Örneğin, adlı bir veri kümeniz varsa, `NorthwindDataSet` içinde ile ilişkili olan TableAdapters  <xref:System.Data.DataTable> `NorthwindDataSet` `NorthwindDataSetTableAdapters` ad alanında olur. Belirli bir TableAdapter bağdaştırıcısına program aracılığıyla erişmek için TableAdapter'ın yeni bir örneğini bildirmeniz gerekir. Örneğin:

 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]

## <a name="associated-datatable-schema"></a>İlişkili DataTable şeması
 Bir TableAdapter oluşturduğunuzda, TableAdapter 'ın ilişkili şemasını tanımlamak için ilk sorguyu veya saklı yordamı kullanırsınız <xref:System.Data.DataTable> . Bu ilk sorguyu veya saklı yordamı TableAdapter 'ın `Fill` metodunu çağırarak (TableAdapter 'ın ilişkili öğesini dolduran <xref:System.Data.DataTable> ) çalıştırırsınız. TableAdapter 'ın ana sorgusunda yapılan tüm değişiklikler, ilişkili veri tablosunun şemasına yansıtılır. Örneğin, ana sorgudan bir sütunu kaldırmak, sütunu ilişkili veri tablosundan da kaldırır. TableAdapter üzerinde herhangi bir ek sorgu ana sorguda olmayan sütunları döndüren SQL deyimlerini kullanıyorsa, tasarımcı ana sorgu ve ek sorgular arasındaki sütun değişikliklerini eşitlemeye çalışır. Daha fazla bilgi için bkz. [nasıl yapılır: düzenleme TableAdapters](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).

## <a name="tableadapter-update-commands"></a>TableAdapter güncelleştirme komutları
 TableAdapter 'ın güncelleştirme işlevselliği, TableAdapter sihirbazındaki ana sorguda ne kadar bilgi kullanılabileceğini bağlıdır. Örneğin, değerleri birden çok tablodan (JOIN), skalar değerden veya görünümden ya da toplu işlevlerin sonuçlarından alacak şekilde yapılandırılan TableAdapter bağdaştırıcıları, başlangıçta güncelleştirmeleri temel alınan veritabanına geri gönderebilme özelliğiyle oluşturulmaz. Ancak, **Özellikler** penceresinde INSERT, Update ve DELETE komutlarını el ile yapılandırabilirsiniz.

## <a name="tableadapter-queries"></a>TableAdapter sorguları
 ![Birden çok sorguya sahip TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")

 TableAdapters, ilişkili veri tablolarını dolduracak birden çok sorgu içerebilir. Bir TableAdapter için, her sorgu ilişkili olduğu veri tablosunun şemasına uyan veriler döndürdüğü sürece, uygulamanızın gerektirdiği sayıda sorgu tanımlayabilirsiniz. Bu özellik, bir TableAdapter 'ın farklı ölçütlere göre farklı sonuçlar yüklemesini sağlar.

 Örneğin, uygulamanız müşteri adları içeren bir tablo içeriyorsa, belirli bir harfle başlayan her müşteri adı ile tabloyu dolduran bir sorgu oluşturabilir ve diğer bir deyişle, tabloyu aynı durumda bulunan tüm müşterilerle doldurur. Bir `Customers` tabloyu belirli bir durumdaki müşterilerle doldurmanız için, `FillByState` durum değeri için bir parametreyi aşağıdaki şekilde alan bir sorgu oluşturabilirsiniz: `SELECT * FROM Customers WHERE State = @State` . `FillByState`Yöntemini çağırarak ve parametre değerini şöyle geçirerek sorgu çalıştırırsınız: `CustomerTableAdapter.FillByState("WA")` .

 TableAdapter 'ın veri tablosu ile aynı şemadaki verileri döndüren sorguları eklemenin yanı sıra, skaler (tek) değerler döndüren sorgular da ekleyebilirsiniz. Örneğin, `SELECT Count(*) From Customers` `CustomersTableAdapter,` döndürülen veriler tablonun şemasına uygun olmasa da, müşteri sayısı döndüren bir sorgu (), için geçerlidir.

## <a name="clearbeforefill-property"></a>Clearbefodolum özelliği
 Varsayılan olarak, bir TableAdapter 'ın veri tablosunu dolduracak bir sorguyu her çalıştırdığınızda, var olan veriler temizlenir ve yalnızca sorgunun sonuçları tabloya yüklenir. `ClearBeforeFill` `false` Bir sorgudan döndürülen verileri bir veri tablosundaki mevcut verilere eklemek veya birleştirmek istiyorsanız TableAdapter özelliğini olarak ayarlayın. Verileri temizlemenizden bağımsız olarak, devam etmek istiyorsanız, güncelleştirmeleri veritabanına geri açıkça göndermeniz gerekir. Bu nedenle, tabloyu dolduran başka bir sorgu çalıştırmadan önce tablodaki verilerde yapılan değişiklikleri kaydetmeyi unutmayın. Daha fazla bilgi için bkz. [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter devralma
 TableAdapters yapılandırılmış bir sınıfı kapsülleyerek standart veri bağdaştırıcılarının işlevselliğini genişletir <xref:System.Data.Common.DataAdapter> ? qualifyHint = False&otomatik Upgrade = true. Varsayılan olarak, TableAdapter <xref:System.ComponentModel.Component> sınıfından devralır ve <xref:System.Data.Common.DataAdapter> sınıfa atanamaz. Bir TableAdapter 'ı sınıfa atama <xref:System.Data.Common.DataAdapter> bir <xref:System.InvalidCastException> hatayla sonuçlanır? QualifyHint = false&oto Upgrade = true. Bir TableAdapter 'ın temel sınıfını değiştirmek için, <xref:System.ComponentModel.Component> **veri kümesi Tasarımcısı**TableAdapter 'ın **Base Class** özelliğinden türeten bir sınıf yazabilirsiniz.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter yöntemleri ve özellikleri
 TableAdapter sınıfı öğesinin bir parçası değildir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu, belgelerde veya **nesne tarayıcısı**bakameyeceğiniz anlamına gelir. Daha önce bahsedilen sihirbazlardan birini kullandığınızda tasarım zamanında oluşturulur. Oluşturduğunuz bir TableAdapter 'a atanan ad, üzerinde çalıştığınız tablonun adını temel alır. Örneğin, adlı bir veritabanındaki bir tabloyu temel alan bir TableAdapter oluşturduğunuzda `Orders` , TableAdapter adlandırılır `OrdersTableAdapter` . TableAdapter 'ın sınıf adı, **veri kümesi Tasarımcısı** **ad** özelliği kullanılarak değiştirilebilir.

 Aşağıda, TableAdapters 'in yaygın olarak kullanılan yöntemleri ve özellikleri verilmiştir:

|Üye|Description|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter bağdaştırıcısının ilişkili veri tablosunu TableAdapter'ın SELECT komutunun sonuçlarıyla doldurur.|
|`TableAdapter.Update`|Değişiklikleri veritabanına geri gönderir ve güncelleştirmeden etkilenen satır sayısını temsil eden bir tamsayı döndürür. Daha fazla bilgi için bkz. [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Verilerle doldurulan yeni bir döndürür <xref:System.Data.DataTable> .|
|`TableAdapter.Insert`|Veri tablosunda yeni bir satır oluşturur. Daha fazla bilgi için bkz. [veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|`Fill` yöntemlerinden birini çağırmadan önce veri tablosunun boşaltılıp boşaltılmadığını belirler.|

## <a name="tableadapter-update-method"></a>TableAdapter Update yöntemi
 TableAdapter bağdaştırıcıları veritabanından okuma ve yazma yapmak için veri komutlarını kullanır. TableAdapter 'ın ilk `Fill` (Main) sorgusu, ilişkili veri tablosunun şemasını oluşturmak için temel olarak `InsertCommand` `UpdateCommand` ve yöntemiyle ilişkili olan, ve komutlarının temeli olarak kullanılır `DeleteCommand` `TableAdapter.Update` . TableAdapter 'ın metodunu çağırmak `Update` , TableAdapter **sorgu Yapılandırma Sihirbazı**ile eklenen ek sorgulardan birini değil, TableAdapter ilk yapılandırıldığında oluşturulan deyimleri çalıştırır.

 Bir TableAdapter kullandığınızda, aynı işlemleri genelde uyguladığınız komutlarla etkin bir şekilde gerçekleştirir. Örneğin, bağdaştırıcının `Fill` yöntemini çağırdığınızda, bağdaştırıcı özelliğindeki Data komutunu çalıştırır `SelectCommand` ve <xref:System.Data.SqlClient.SqlDataReader> sonuç kümesini veri tablosuna yüklemek için bir veri okuyucu (örneğin,) kullanır. Benzer şekilde, bağdaştırıcının `Update` yöntemini çağırdığınızda, `UpdateCommand` `InsertCommand` `DeleteCommand` veri tablosundaki her değiştirilmiş kayıt için uygun komutu (,, ve özellikleri) çalıştırır.

> [!NOTE]
> Ana sorguda yeterli bilgi varsa `InsertCommand`, `UpdateCommand` ve `DeleteCommand` komutları TableAdapter oluşturulduğunda varsayılan olarak oluşturulur. TableAdapter 'ın ana sorgusu, tek bir tablo SELECT ifadesiyle daha büyükse, tasarımcı, ve oluşturamayacak  `InsertCommand` `UpdateCommand` `DeleteCommand` . Bu komutlar oluşturulmadığından, yöntemini çalıştırırken bir hata alabilirsiniz `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDBDirectMethods Özelliği
 , Ve ' a ek olarak,  `InsertCommand` `UpdateCommand` `DeleteCommand` TableAdapters doğrudan veritabanına karşı çalıştırılabilen yöntemlerle oluşturulur. Bu yöntemler (`TableAdapter.Insert`, `TableAdapter.Update` ve `TableAdapter.Delete`) veritabanındaki verileri işlemek için doğrudan çağrılabilir. Bu, `TableAdapter.Update` ilişkili veri tablosu için bekleyen ekleme, güncelleştirme ve silme türlerini işlemek için çağırmak yerine kodunuzda bu tek yöntemleri çağırabilmeniz anlamına gelir.

 Bu doğrudan yöntemleri oluşturmak istemiyorsanız, TableAdapter 'ın **GenerateDBDirectMethods** özelliğini olarak ayarlayın `false` ( **Özellikler** penceresinde). TableAdapter 'a eklenen ek sorgular tek başına sorgular; bu yöntemler oluşturmaz.

## <a name="tableadapter-support-for-nullable-types"></a>Nullable türler için TableAdapter desteği
 TableAdapters, nullable türleri `Nullable(Of T)` ve destekler `T?` . Visual Basic null yapılabilir türler hakkında daha fazla bilgi için bkz. [Nullable değer türleri](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). C# ' de Nullable türler hakkında daha fazla bilgi için bkz. [Nullable türler kullanma](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).

## <a name="security"></a>Güvenlik
 Olarak ayarlanmış bir özellik ile veri komutları kullandığınızda `CommandType` <xref:System.Data.CommandType> , veritabanınıza geçirmeden önce istemciden gönderilen bilgileri dikkatle kontrol edin. Kötü niyetli kullanıcılar, yetkisiz erişim elde etmek veya veritabanına zarar vermek için bir denemeye değiştirilmiş veya ek SQL deyimleri göndermeye (eklemeye) çalışabilir. Kullanıcı girişini bir veritabanına aktarmadan önce, bilgilerin geçerli olduğunu her zaman doğrulayın. Mümkün olduğunda her zaman parametreli sorguları veya saklı yordamları kullanmak en iyi uygulamadır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
