---
title: 'Nasıl yapılır: veri temelli birim testi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9dc5ad44a73f517b91562209abfab8b0b3e8d4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660528"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl Yapılır: Veri Temelli Birim Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod için Microsoft birim testi çerçevesini kullanarak, bir veri kaynağından test yönteminde kullanılan değerleri almak için bir birim testi yöntemi ayarlayabilirsiniz. Yöntemi, veri kaynağındaki her satır için oldukça çalışır ve bu da tek bir yöntem kullanarak çeşitli girişleri test etmelerini kolaylaştırır.

 Bu konu aşağıdaki bölümleri içermektedir:

- [Test edilen yöntem](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)

- [Veri kaynağı oluşturma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)

- [Test sınıfına TestContext ekleme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)

- [Test yöntemi yazma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)

  - [DataSourceAttribute belirtme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)

  - [Verilere erişmek için TestContext. DataRow kullanma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)

- [Testi çalıştırma ve sonuçları görüntüleme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)

  Veri odaklı birim testi oluşturmak aşağıdaki adımları içerir:

1. Test yönteminde kullandığınız değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.

2. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>Test sınıfına bir Private alanı ve Public `TestContext` özelliği ekleyin.

3. Bir birim testi yöntemi oluşturun ve buna bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> öznitelik ekleyin.

4. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A>Bir testte kullandığınız değerleri almak için Indexer özelliğini kullanın.

## <a name="the-method-under-test"></a><a name="BKMK_The_method_under_test"></a> Test edilen yöntem
 Örnek olarak, oluşturduğumuz varsayılmaktadır:

1. `MyBank`Farklı türdeki hesapların işlemlerini kabul eden ve işleyen adlı bir çözüm.

2. `MyBank`Çağrılan `BankDb` , hesapların işlemlerini yöneten bir proje.

3. `Maths` `DbBank` Herhangi bir işlemin bankaya avantajlı olduğundan emin olmak için matematik işlevlerini gerçekleştiren projede adlı bir sınıf.

4. `BankDbTests`Bileşenin davranışını test etmek için çağrılan bir birim test projesi `BankDb` .

5. `MathsTests`Sınıfının davranışını doğrulamak için çağrılan bir birim test sınıfı `Maths` .

   `Maths`Bir döngü kullanarak iki tamsayı ekleyen içindeki bir yöntemi test edeceğiz:

```
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="creating-a-data-source"></a><a name="BKMK_Creating_a_data_source"></a> Veri kaynağı oluşturma
 Yöntemi test etmek için `AddIntegers` , parametreler ve döndürülmek üzere bekleneceğiniz toplam değer aralığını belirten bir veri kaynağı oluşturacağız. Örneğimizde, adlı bir SQL Compact veritabanı `MathsData` ve `AddIntegersData` Aşağıdaki sütun adlarını ve değerlerini içeren adlı bir tablo oluşturacağız

|Ilksayı|Ikincisayı|Toplam|
|-----------------|------------------|---------|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="adding-a-testcontext-to-the-test-class"></a><a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Test sınıfına TestContext ekleme
 Birim test çerçevesi veri `TestContext` temelli bir test için veri kaynağı bilgilerini depolamak üzere bir nesne oluşturur. Framework daha sonra bu nesneyi oluşturduğumuz özelliğin değeri olarak ayarlar `TestContext` .

```

private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}

```

 Test yönteminde, ' `DataRow` nin Indexer özelliğinden veriye erişirsiniz `TestContext` .

## <a name="writing-the-test-method"></a><a name="BKMK_Writing_the_test_method"></a> Test yöntemi yazma
 İçin test metodu `AddIntegers` oldukça basittir. Veri kaynağındaki her satır için, `AddIntegers` **firstNumber** ve **secondNumber** sütun değerlerini parametre olarak çağırırız ve döndürülen değeri **Sum** sütun değerine göre doğrulayacağız:

```

[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});

}

```

 `Assert`Yönteminin, `x` başarısız bir yinelemenin ve değerlerini görüntüleyen bir ileti içerdiğine unutmayın `y` . Varsayılan olarak, onaylanan değerler ve, `expected` `actual` Hatalı testin ayrıntılarına zaten dahil edilmiştir.

### <a name="specifying-the-datasourceattribute"></a><a name="BKMK_Specifying_the_DataSourceAttribute"></a> DataSourceAttribute belirtme
 `DataSource`Öznitelik, veri kaynağı için bağlantı dizesini ve test yönteminde kullandığınız tablonun adını belirtir. Bağlantı dizesindeki kesin bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, SqlServerCe veritabanı kullandık.

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

 DataSource özniteliğinde üç Oluşturucu vardır.

```
[DataSource(dataSourceSettingName)]
```

 Tek parametreli bir Oluşturucu, çözüm için app.config dosyasında depolanan bağlantı bilgilerini kullanır. *DataSourceSettingsName* , yapılandırma dosyasındaki bağlantı bilgilerini belirten XML öğesinin adıdır.

 app.config bir dosyanın kullanılması, birim testinde değişiklik yapmadan veri kaynağının konumunu değiştirmenize olanak sağlar. Bir app.config dosyası oluşturma ve kullanma hakkında daha fazla bilgi için bkz [. Izlenecek yol: bir veri kaynağı tanımlamak Için yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```
[DataSource(connectionString, tableName)]
```

 `DataSource`İki parametreli Oluşturucu, veri kaynağı için bağlantı dizesini ve test yöntemi için verileri içeren tablonun adını belirtir.

 Bağlantı dizeleri veri kaynağı türünün türüne bağlıdır, ancak veri sağlayıcısının sabit adını belirten bir sağlayıcı öğesi içermelidir.

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="using-testcontextdatarow-to-access-the-data"></a><a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Verilere erişmek için TestContext. DataRow kullanma
 Tablodaki verilere erişmek için `AddIntegersData` `TestContext.DataRow` Dizin oluşturucuyu kullanın. `DataRow` bir <xref:System.Data.DataRow> nesne olduğundan, sütun değerlerini dizin veya sütun adlarına göre alıyoruz. Değerler nesneler olarak döndürüldüğünden, bunları uygun türe dönüştürmemiz gerekir:

```
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);

```

## <a name="running-the-test-and-viewing-results"></a><a name="BKMK_Running_the_test_and_viewing_results"></a> Testi çalıştırma ve sonuçları görüntüleme
 Bir test yöntemi yazmayı bitirdiğinizde test projesi oluşturun. Test yöntemi, **çalıştırma testleri** grubundaki test Gezgini penceresinde görünür. Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler ve **çalıştırma testleri**gruplarında görüntüler. Tüm testlerinizi çalıştırmak için **Tümünü Çalıştır** ' ı veya çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır...** seçeneğini belirleyebilirsiniz.

 Gezgin 'in üst kısmındaki test sonuçları çubuğu, test çalıştırmalarınız olarak hareketlendirilir. Test çalıştırmasının sonunda, testlerin hepsi başarısız olursa, tüm testler geçtiğinde veya kırmızıysa çubuk yeşil olur. Test çalıştırmasının Özeti, test Gezgini penceresinin alt kısmındaki Ayrıntılar bölmesinde görünür. Alt bölmedeki bu testin ayrıntılarını görüntülemek için bir test seçin.

 `AddIntegers_FromDataSourceTest`Örneğimizde yöntemi çalıştırdıysanız, sonuçlar çubuğu kırmızıya döner ve test yöntemi **başarısız testlere** taşınır, veri kaynağından yinelenen metotlardan herhangi biri başarısız olursa veri odaklı bir test başarısız olur. Test Gezgini penceresinde başarısız veri temelli bir test seçtiğinizde, Ayrıntılar bölmesi veri satırı dizini tarafından tanımlanan her yinelemenin sonuçlarını görüntüler. Örneğimizde, `AddIntegers` algoritmanın negatif değerleri doğru bir şekilde işlememesi görünür.

 Test altındaki Yöntem düzeltildiğinde ve test yeniden çalıştırıldığında, sonuçlar çubuğu yeşil olur ve test yöntemi **geçilen test** grubuna taşınır.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
 [Nasıl yapılır:](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48) [yönetilen kod Için Microsoft birim testi çerçevesi Ile .NET Framework için test Gezgini yazma birim testlerini](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) [Içeren](../test/run-unit-tests-with-test-explorer.md) birim testi [birimi testi](../test/unit-test-your-code.md) oluşturma ve çalıştırma
