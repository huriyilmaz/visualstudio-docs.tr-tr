---
title: Data-Driven birim testleri oluşturma
description: Yönetilen kod için Microsoft birim testi çerçevesini kullanarak bir veri kaynağından değerleri almak için bir birim testi yöntemi ayarlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 31e1fb08d77992e6fb592e286553196928b13ad4
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441202"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl yapılır: veri temelli birim testi oluşturma

Yönetilen kod için Microsoft birim testi çerçevesini, bir veri kaynağından değerleri almak üzere bir birim testi yöntemi ayarlamak için kullanabilirsiniz. Yöntemi, veri kaynağındaki her satır için oldukça çalışır ve bu da tek bir yöntem kullanarak çeşitli girişleri test etmelerini kolaylaştırır.

Veri odaklı birim testi oluşturmak aşağıdaki adımları içerir:

1. Test yönteminde kullandığınız değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.

2. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>Test sınıfına bir Private alanı ve Public `TestContext` özelliği ekleyin.

3. Bir birim testi yöntemi oluşturun ve buna bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> öznitelik ekleyin.

4. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A>Bir testte kullandığınız değerleri almak için Indexer özelliğini kullanın.

## <a name="the-method-under-test"></a>Test edilen yöntem

Örnek olarak, şunları olduğunu varsayalım:

1. `MyBank`Farklı türdeki hesapların işlemlerini kabul eden ve işleyen adlı bir çözüm.

2. `MyBank`Çağrılan `BankDb` , hesapların işlemlerini yöneten bir proje.

3. `Maths` `BankDb` Herhangi bir işlemin bankaya avantajlı olduğundan emin olmak için matematik işlevlerini gerçekleştiren projede adlı bir sınıf.

4. `BankDbTests`Bileşenin davranışını test etmek için çağrılan bir birim test projesi `BankDb` .

5. `MathsTests`Sınıfının davranışını doğrulamak için çağrılan bir birim test sınıfı `Maths` .

`Maths`Bir döngü kullanarak iki tamsayı ekleyen ' de bir yöntemi test edeceğiz:

```csharp
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

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma

Yöntemi test etmek için `AddIntegers` , parametreler için bir değer aralığı ve döndürülmek üzere bekleyen toplam değeri belirten bir veri kaynağı oluşturun. Bu örnekte, adlı bir SQL Compact veritabanı `MathsData` ve `AddIntegersData` Aşağıdaki sütun adlarını ve değerlerini içeren adlı bir tablo oluşturacağız

|Ilksayı|Ikincisayı|Toplam|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Test sınıfına bir TestContext ekleyin

Birim test çerçevesi veri `TestContext` temelli bir test için veri kaynağı bilgilerini depolamak üzere bir nesne oluşturur. Framework daha sonra bu nesneyi oluşturduğunuz özelliğin değeri olarak ayarlar `TestContext` .

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

Test yönteminde, ' `DataRow` nin Indexer özelliğinden veriye erişirsiniz `TestContext` .

> [!NOTE]
> .NET Core, [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) özniteliğini desteklemez. Bu şekilde bir .NET Core veya UWP birim testi projesinde test verilerine erişmeye çalışırsanız, "' TestContext ' öğesine benzer bir hata görürsünüz ve ' **TestContext ' türünde bir ilk bağımsız değişken kabul eden hiçbir erişilebilir uzantı yöntemi bulunamadı (bir using yönergesi veya derleme başvurunuz eksik olabilir mi?)"**.

## <a name="write-the-test-method"></a>Test yöntemini yazma

İçin test metodu `AddIntegers` oldukça basittir. Veri kaynağındaki her satır için, `AddIntegers` parametre olarak **firstNumber** ve **secondNumber** sütun değerleriyle çağrı yapın ve döndürülen değeri **Sum** sütun değerine göre doğrulayın:

```csharp
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

`Assert`Yöntemi, `x` `y` başarısız bir yinelemenin ve değerlerini görüntüleyen bir ileti içerir. Varsayılan olarak, onaylanan değerler `expected` ve `actual` başarısız test ayrıntılarına zaten dahil edilmiştir.

### <a name="specify-the-datasourceattribute"></a>DataSourceAttribute belirtin

`DataSource`Öznitelik, veri kaynağı için bağlantı dizesini ve test yönteminde kullandığınız tablonun adını belirtir. Bağlantı dizesindeki kesin bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, SqlServerCe veritabanı kullandık.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource özniteliğinde üç Oluşturucu vardır.

```csharp
[DataSource(dataSourceSettingName)]
```

Tek parametreli bir Oluşturucu, çözüm için *app.config* dosyasında depolanan bağlantı bilgilerini kullanır. *DataSourceSettingsName* , yapılandırma dosyasındaki bağlantı bilgilerini belirten XML öğesinin adıdır.

*app.config* bir dosyanın kullanılması, birim testinde değişiklik yapmadan veri kaynağının konumunu değiştirmenize olanak sağlar. Bir *app.config* dosyası oluşturma ve kullanma hakkında daha fazla bilgi için bkz [. İzlenecek yol: bir veri kaynağı tanımlamak Için yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource`İki parametreli Oluşturucu, veri kaynağı için bağlantı dizesini ve test yöntemi için verileri içeren tablonun adını belirtir.

Bağlantı dizeleri veri kaynağı türünün türüne bağlıdır, ancak veri sağlayıcısının sabit adını belirten bir sağlayıcı öğesi içermelidir.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Verilere erişmek için TestContext. DataRow kullanın

Tablodaki verilere erişmek için `AddIntegersData` `TestContext.DataRow` Dizin oluşturucuyu kullanın. `DataRow` bir <xref:System.Data.DataRow> nesnedir, bu nedenle sütun değerlerini dizin veya sütun adlarına göre alın. Değerler nesneler olarak döndürüldüğünden, bunları uygun türe dönüştürün:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Testi çalıştırma ve sonuçları görüntüleme

Bir test yöntemi yazmayı bitirdiğinizde test projesi oluşturun. Test yöntemi, **Test Gezgini** 'Nde, **çalıştırma** testi grubu ' nda görüntülenir. Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, **Test Gezgini** sonuçları **başarısız testler**, **başarılı** testler ve **çalıştırma testleri** gruplarında görüntüler. Tüm testlerinizi çalıştırmak için **Tümünü Çalıştır** ' ı seçebilirsiniz veya çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır** ' ı seçin.

Test **Gezgini** 'nin en üstündeki test sonuçları çubuğu, test çalıştırmalarınız olarak hareketlendirilir. Test çalıştırmasının sonunda, testlerin hepsi başarısız olursa, tüm testler geçtiğinde veya kırmızıysa çubuk yeşil olur. Test çalıştırmasının Özeti, **Test Gezgini** penceresinin alt kısmındaki Ayrıntılar bölmesinde görünür. Alt bölmedeki bu testin ayrıntılarını görüntülemek için bir test seçin.

> [!NOTE]
> Her veri satırı ve ayrıca bir Özet sonucu için bir sonuç vardır. Test her bir veri satırına geçirilirse, Özet çalıştırması **geçti** olarak gösterilir. Herhangi bir veri satırında test başarısız olursa, Özet çalıştırması **başarısız** olarak gösterilir.

`AddIntegers_FromDataSourceTest`Örneğimizde yöntemi çalıştırdıysanız, sonuçlar çubuğu kırmızıya döner ve test yöntemi **başarısız testlere** taşınır. Veri kaynağından yinelenen yöntemlerin herhangi biri başarısız olursa veri odaklı bir test başarısız olur. **Test Gezgini** penceresinde başarısız veri temelli bir test seçtiğinizde, Ayrıntılar bölmesi veri satırı dizini tarafından tanımlanan her yinelemenin sonuçlarını görüntüler. Örneğimizde, `AddIntegers` algoritmanın negatif değerleri doğru bir şekilde işlememesi görünür.

Test altındaki Yöntem düzeltildiğinde ve test yeniden çalıştırıldığında, sonuçlar çubuğu yeşil olur ve test yöntemi **geçilen test** grubuna taşınır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Microsoft birim testi çerçevesi ile .NET için birim testleri yazma](../test/unit-test-your-code.md)
