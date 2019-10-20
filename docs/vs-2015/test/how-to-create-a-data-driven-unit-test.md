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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
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

2. Test sınıfına bir özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alanı ve ortak `TestContext` özelliği ekleyin.

3. Bir birim testi yöntemi oluşturun ve buna bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> özniteliği ekleyin.

4. Bir testte kullandığınız değerleri almak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Indexer özelliğini kullanın.

## <a name="BKMK_The_method_under_test"></a>Test edilen yöntem
 Örnek olarak, oluşturduğumuz varsayılmaktadır:

1. Farklı türdeki hesapların işlemlerini kabul eden ve işleyen `MyBank` adlı bir çözüm.

2. @No__t_0 bir proje, hesapların işlemlerini yöneten `BankDb` çağırdı.

3. Herhangi bir işlemin bankaya avantajlı olduğundan emin olmak için matematik işlevlerini gerçekleştiren `DbBank` projesinde `Maths` adlı bir sınıf.

4. @No__t_1 bileşenin davranışını test etmek için `BankDbTests` adlı bir birim test projesi.

5. @No__t_1 sınıfının davranışını doğrulamak için `MathsTests` adlı bir birim testi sınıfı.

   Bir döngüsü kullanarak iki tamsayı ekleyen `Maths` bir yöntemi test edeceğiz:

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

## <a name="BKMK_Creating_a_data_source"></a>Veri kaynağı oluşturma
 @No__t_0 yöntemini test etmek için, parametreler ve döndürülmek üzere bekleneceğiniz toplam değer aralığını belirten bir veri kaynağı oluşturacağız. Örneğimizde `MathsData` adlı bir SQL Compact veritabanı ve aşağıdaki sütun adlarını ve değerleri içeren `AddIntegersData` adlı bir tablo oluşturacağız

|Ilksayı|Ikincisayı|Toplamlarını|
|-----------------|------------------|---------|
|0|1\.|1\.|
|1\.|1\.|2|
|2|-3|-1|

## <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a>Test sınıfına TestContext ekleme
 Birim test çerçevesi veri temelli bir test için veri kaynağı bilgilerini depolamak üzere bir `TestContext` nesnesi oluşturur. Framework daha sonra bu nesneyi oluşturduğumuz `TestContext` özelliğinin değeri olarak ayarlar.

```

private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}

```

 Test yönteminde, `TestContext` `DataRow` Indexer özelliği aracılığıyla verilere erişirsiniz.

## <a name="BKMK_Writing_the_test_method"></a>Test yöntemi yazma
 @No__t_0 için test yöntemi oldukça basittir. Veri kaynağındaki her satır için, parametre olarak **firstNumber** ve **secondNumber** sütun değerleriyle birlikte `AddIntegers` çağırırız ve döndürülen değeri **Sum** sütun değerine göre doğrulayacağız:

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

 @No__t_0 yönteminin, başarısız bir yinelemenin `x` ve `y` değerlerini görüntüleyen bir ileti içerdiğine unutmayın. Varsayılan olarak, `expected` ve `actual` onaylanan değerleri, başarısız bir testin ayrıntılarına zaten dahil edilmiştir.

### <a name="BKMK_Specifying_the_DataSourceAttribute"></a>DataSourceAttribute belirtme
 @No__t_0 özniteliği, veri kaynağı için bağlantı dizesini ve test yönteminde kullandığınız tablonun adını belirtir. Bağlantı dizesindeki kesin bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, SqlServerCe veritabanı kullandık.

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

 DataSource özniteliğinde üç Oluşturucu vardır.

```
[DataSource(dataSourceSettingName)]
```

 Tek parametreli bir Oluşturucu, çözüm için App. config dosyasında depolanan bağlantı bilgilerini kullanır. *DataSourceSettingsName* , yapılandırma dosyasındaki bağlantı bilgilerini belirten XML öğesinin adıdır.

 App. config dosyası kullanmak, birim testinin kendisinde değişiklik yapmadan veri kaynağının konumunu değiştirmenize olanak sağlar. Bir App. config dosyası oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [Izlenecek yol: bir veri kaynağı tanımlamak Için yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```
[DataSource(connectionString, tableName)]
```

 İki parametreli `DataSource` Oluşturucu, veri kaynağı için bağlantı dizesini ve test yöntemi için verileri içeren tablonun adını belirtir.

 Bağlantı dizeleri veri kaynağı türünün türüne bağlıdır, ancak veri sağlayıcısının sabit adını belirten bir sağlayıcı öğesi içermelidir.

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a>Verilere erişmek için TestContext. DataRow kullanma
 @No__t_0 tablosundaki verilere erişmek için `TestContext.DataRow` Dizin oluşturucuyu kullanın. `DataRow` bir <xref:System.Data.DataRow> nesnesidir, bu nedenle sütun değerlerini dizin veya sütun adlarına göre alıyoruz. Değerler nesneler olarak döndürüldüğünden, bunları uygun türe dönüştürmemiz gerekir:

```
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);

```

## <a name="BKMK_Running_the_test_and_viewing_results"></a>Testi çalıştırma ve sonuçları görüntüleme
 Bir test yöntemi yazmayı bitirdiğinizde test projesi oluşturun. Test yöntemi, **çalıştırma testleri** grubundaki test Gezgini penceresinde görünür. Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler ve **çalıştırma testleri**gruplarında görüntüler. Tüm testlerinizi çalıştırmak için **Tümünü Çalıştır** ' ı veya çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır...** seçeneğini belirleyebilirsiniz.

 Gezgin 'in üst kısmındaki test sonuçları çubuğu, test çalıştırmalarınız olarak hareketlendirilir. Test çalıştırmasının sonunda, testlerin hepsi başarısız olursa, tüm testler geçtiğinde veya kırmızıysa çubuk yeşil olur. Test çalıştırmasının Özeti, test Gezgini penceresinin alt kısmındaki Ayrıntılar bölmesinde görünür. Alt bölmedeki bu testin ayrıntılarını görüntülemek için bir test seçin.

 Örneğimizde `AddIntegers_FromDataSourceTest` yöntemi çalıştırdıysanız, sonuçlar çubuğu kırmızıya döner ve test yöntemi **başarısız testlere** taşınır, veri kaynağından yinelenen yöntemlerin herhangi biri başarısız olursa veri tabanlı bir test başarısız olur. Test Gezgini penceresinde başarısız veri temelli bir test seçtiğinizde, Ayrıntılar bölmesi veri satırı dizini tarafından tanımlanan her yinelemenin sonuçlarını görüntüler. Örneğimizde, `AddIntegers` algoritmasının negatif değerleri doğru bir şekilde işlememesi gibi görünüyor.

 Test altındaki Yöntem düzeltildiğinde ve test yeniden çalıştırıldığında, sonuçlar çubuğu yeşil olur ve test yöntemi **geçilen test** grubuna taşınır.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
 [Nasıl yapılır:](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48) [yönetilen kod Için Microsoft birim testi çerçevesi Ile .NET Framework için test Gezgini yazma birim testlerini](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) [Içeren](../test/run-unit-tests-with-test-explorer.md) birim testi [birimi testi](../test/unit-test-your-code.md) oluşturma ve çalıştırma
