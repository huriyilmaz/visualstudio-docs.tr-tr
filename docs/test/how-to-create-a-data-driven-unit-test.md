---
title: Veri tabanlı birim testleri oluşturma
ms.date: 05/08/2019
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0a3162dcbbd041a7d2f540a335bd95854afd87d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643477"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl yapılır: veri temelli birim testi oluşturma

Yönetilen kod için Microsoft birim testi çerçevesini, bir veri kaynağından değerleri almak üzere bir birim testi yöntemi ayarlamak için kullanabilirsiniz. Yöntemi, veri kaynağındaki her satır için oldukça çalışır ve bu da tek bir yöntem kullanarak çeşitli girişleri test etmelerini kolaylaştırır.

Veri odaklı birim testi oluşturmak aşağıdaki adımları içerir:

1. Test yönteminde kullandığınız değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.

2. Test sınıfına bir özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alanı ve ortak `TestContext` özelliği ekleyin.

3. Bir birim testi yöntemi oluşturun ve buna bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> özniteliği ekleyin.

4. Bir testte kullandığınız değerleri almak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Indexer özelliğini kullanın.

## <a name="the-method-under-test"></a>Test edilen yöntem

Örnek olarak, şunları olduğunu varsayalım:

1. Farklı türdeki hesapların işlemlerini kabul eden ve işleyen `MyBank` adlı bir çözüm.

2. @No__t_0 bir proje, hesapların işlemlerini yöneten `BankDb` çağırdı.

3. Herhangi bir işlemin bankaya avantajlı olduğundan emin olmak için matematik işlevlerini gerçekleştiren `BankDb` projesinde `Maths` adlı bir sınıf.

4. @No__t_1 bileşenin davranışını test etmek için `BankDbTests` adlı bir birim test projesi.

5. @No__t_1 sınıfının davranışını doğrulamak için `MathsTests` adlı bir birim testi sınıfı.

Bir döngüsü kullanarak iki tamsayı ekleyen `Maths` bir yöntemi test edeceğiz:

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

@No__t_0 yöntemini test etmek için, parametreler için bir değer aralığı ve döndürülmek üzere bekleyen toplam değeri belirten bir veri kaynağı oluşturun. Bu örnekte, `MathsData` adlı bir SQL Compact veritabanı ve aşağıdaki sütun adlarını ve değerlerini içeren `AddIntegersData` adlı bir tablo oluşturacağız

|Ilksayı|Ikincisayı|Toplamlarını|
|-|------------------|-|
|0|1\.|1\.|
|1\.|1\.|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Test sınıfına bir TestContext ekleyin

Birim test çerçevesi veri temelli bir test için veri kaynağı bilgilerini depolamak üzere bir `TestContext` nesnesi oluşturur. Framework daha sonra bu nesneyi oluşturduğunuz `TestContext` özelliğinin değeri olarak ayarlar.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

Test yönteminde, `TestContext` `DataRow` Indexer özelliği aracılığıyla verilere erişirsiniz.

> [!NOTE]
> .NET Core, [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) özniteliğini desteklemez. Test verilerine .NET Core veya UWP birim testi projesinde bu şekilde erişmeyi denerseniz, "' TestContext ' öğesine benzer bir hata görürsünüz ve ' DataRow ' **türünde bir ilk bağımsız değişken kabul eden hiçbir erişilebilir genişletme yöntemi ' DataRow ' yok. TestContext ' bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?) "** .

## <a name="write-the-test-method"></a>Test yöntemini yazma

@No__t_0 için test yöntemi oldukça basittir. Veri kaynağındaki her satır için, parametre olarak **firstNumber** ve **secondNumber** sütun değerleriyle birlikte `AddIntegers` çağırın ve döndürülen değeri **Sum** sütun değerine göre doğrulayın:

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

@No__t_0 yöntemi, başarısız bir yinelemenin `x` ve `y` değerlerini görüntüleyen bir ileti içerir. Varsayılan olarak, `expected` ve `actual` onaylanan değerleri, başarısız test ayrıntılarına zaten dahil edilmiştir.

### <a name="specify-the-datasourceattribute"></a>DataSourceAttribute belirtin

@No__t_0 özniteliği, veri kaynağı için bağlantı dizesini ve test yönteminde kullandığınız tablonun adını belirtir. Bağlantı dizesindeki kesin bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, SqlServerCe veritabanı kullandık.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource özniteliğinde üç Oluşturucu vardır.

```csharp
[DataSource(dataSourceSettingName)]
```

Tek parametreli bir Oluşturucu, çözüm için *app. config* dosyasında depolanan bağlantı bilgilerini kullanır. *DataSourceSettingsName* , yapılandırma dosyasındaki bağlantı bilgilerini belirten XML öğesinin adıdır.

*App. config* dosyası kullanmak, birim testinin kendisinde değişiklik yapmadan veri kaynağının konumunu değiştirmenize olanak sağlar. Bir *app. config* dosyası oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [izlenecek yol: bir veri kaynağı tanımlamak Için yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

İki parametreli `DataSource` Oluşturucu, veri kaynağı için bağlantı dizesini ve test yöntemi için verileri içeren tablonun adını belirtir.

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

@No__t_0 tablosundaki verilere erişmek için `TestContext.DataRow` Dizin oluşturucuyu kullanın. `DataRow` bir <xref:System.Data.DataRow> nesnesidir, bu nedenle sütun değerlerini dizin veya sütun adlarına göre alın. Değerler nesneler olarak döndürüldüğünden, bunları uygun türe dönüştürün:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Testi çalıştırma ve sonuçları görüntüleme

Bir test yöntemi yazmayı bitirdiğinizde test projesi oluşturun. Test yöntemi, **Test Gezgini** 'Nde, **çalıştırma** testi grubu ' nda görüntülenir. Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, **Test Gezgini** sonuçları **başarısız testler**, **başarılı**testler ve **çalıştırma testleri**gruplarında görüntüler. Tüm testlerinizi çalıştırmak için **Tümünü Çalıştır** ' ı seçebilirsiniz veya çalıştırılacak testlerin bir alt kümesini seçmek için **Çalıştır** ' ı seçin.

Test **Gezgini** 'nin en üstündeki test sonuçları çubuğu, test çalıştırmalarınız olarak hareketlendirilir. Test çalıştırmasının sonunda, testlerin hepsi başarısız olursa, tüm testler geçtiğinde veya kırmızıysa çubuk yeşil olur. Test çalıştırmasının Özeti, **Test Gezgini** penceresinin alt kısmındaki Ayrıntılar bölmesinde görünür. Alt bölmedeki bu testin ayrıntılarını görüntülemek için bir test seçin.

> [!NOTE]
> Her veri satırı ve ayrıca bir Özet sonucu için bir sonuç vardır. Test her bir veri satırına geçirilirse, Özet çalıştırması **geçti**olarak gösterilir. Herhangi bir veri satırında test başarısız olursa, Özet çalıştırması **başarısız**olarak gösterilir.

Örneğimizde `AddIntegers_FromDataSourceTest` yöntemini çalıştırdıysanız, sonuçlar çubuğu kırmızıya döner ve test yöntemi **başarısız testlere**taşınır. Veri kaynağından yinelenen yöntemlerin herhangi biri başarısız olursa veri odaklı bir test başarısız olur. **Test Gezgini** penceresinde başarısız veri temelli bir test seçtiğinizde, Ayrıntılar bölmesi veri satırı dizini tarafından tanımlanan her yinelemenin sonuçlarını görüntüler. Örneğimizde, `AddIntegers` algoritmasının negatif değerleri doğru bir şekilde işlememesi gibi görünüyor.

Test altındaki Yöntem düzeltildiğinde ve test yeniden çalıştırıldığında, sonuçlar çubuğu yeşil olur ve test yöntemi **geçilen test** grubuna taşınır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Microsoft birim testi çerçevesi ile .NET için birim testleri yazma](../test/unit-test-your-code.md)
