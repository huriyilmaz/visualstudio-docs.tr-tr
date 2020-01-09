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
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f50dad637d9efa2db347ff9f1b4828abf8c733af
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589194"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl yapılır: veri temelli birim testi oluşturma

Yönetilen kod için Microsoft birim testi çerçevesini, bir veri kaynağından değerleri almak üzere bir birim testi yöntemi ayarlamak için kullanabilirsiniz. Yöntemi, tek bir yöntemi kullanarak giriş çeşitli test kolaylaştırır veri kaynağındaki her satır için sırayla çalıştırılır.

Veri temelli birim testi oluşturma, aşağıdaki adımları içerir:

1. Test yöntemi kullanan değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.

2. Özel bir ekleme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alan ve ortak `TestContext` özelliğini test sınıfı.

3. Bir birim test yöntemi oluşturun ve ekleme bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> için özniteliği.

4. Kullanma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> bir testte kullanılacak değerleri almak için dizin oluşturucu özelliği.

## <a name="the-method-under-test"></a>Test edilen yöntem

Örneğin, olduğunu varsayalım:

1. Bir çözüm olarak `MyBank` kabul eder ve farklı hesap türlerinin hareketlerini işler.

2. Bir projede `MyBank` adlı `BankDb` , hesapları için işlemleri yönetir.

3. Bir sınıfa `Maths` içinde `BankDb` herhangi bir işlem bankaya avantajlı olduğundan emin olmak için matematiksel işlevler gerçekleştiren bir proje.

4. Bir birim test projesi adlı `BankDbTests` davranışını test etmek için `BankDb` bileşeni.

5. Bir birim testi sınıf adı verilen `MathsTests` davranışını doğrulamak için `Maths` sınıfı.

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

## <a name="create-a-data-source"></a>Bir veri kaynağı oluşturun

Test etmek için `AddIntegers` yöntem parametreleri ve döndürülecek beklediğiniz toplamı için değer aralığını belirten bir veri kaynağı oluşturun. Bu örnekte, adlandırılmış bir Sql Compact veritabanı oluşturacağız `MathsData` ve adlı bir tablo `AddIntegersData` aşağıdaki sütun adlarını ve değerlerini içeren

|İlksayı|İkincisayı|Toplam|
|-|------------------|-|
|0|1\.|1\.|
|1\.|1\.|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Bir TestContext test sınıfına ekleyin.

Birim test çerçevesi oluşturur bir `TestContext` veri tabanlı test için veri kaynağı bilgilerini depolamak için nesne. Framework, ardından bu nesne değeri olarak ayarlar `TestContext` oluşturduğunuz özelliği.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

Test yönteminizde aracılığıyla verilere `DataRow` dizin oluşturucu özelliği `TestContext`.

> [!NOTE]
> .NET Core, [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) özniteliğini desteklemez. Bu şekilde bir .NET Core veya UWP birim testi projesinde test verilerine erişmeye çalışırsanız, "' TestContext ' öğesine benzer bir hata görürsünüz ve ' **TestContext ' türünde bir ilk bağımsız değişken kabul eden hiçbir erişilebilir uzantı yöntemi bulunamadı (bir using yönergesi veya derleme başvurunuz eksik olabilir mi?)"** .

## <a name="write-the-test-method"></a>Test yönteminin yazma

Test yöntemi için `AddIntegers` oldukça basittir. Veri kaynağındaki her satır için çağrı `AddIntegers` ile **İlksayı** ve **İkincisayı** sütun değerleri parametreler ve dönüş değeri ile karşılaştırarak doğrulayın **Sum** Sütun değeri:

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

`Assert` Yöntemi içeren bir ileti görüntüler `x` ve `y` başarısız bir yineleme değerleri. Varsayılan olarak, `expected` ve `actual` onaylanan değerleri, başarısız test ayrıntılarına zaten dahil edilmiştir.

### <a name="specify-the-datasourceattribute"></a>DataSourceAttribute belirtin

`DataSource` Özniteliği test yönteminde veri kaynağı ve kullandığınız tablonun adı için bağlantı dizesini belirtir. Bağlantı dizesindeki gördüğü bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, bir SqlServerCe veritabanı kullandık.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource özniteliği üç Oluşturucusu vardır.

```csharp
[DataSource(dataSourceSettingName)]
```

Depolanan bağlantı bilgilerini bir parametre ile bir oluşturucu kullanan *app.config* çözüm dosyası. *DataSourceSettingsName* bağlantı bilgilerini belirten yapılandırma dosyasında Xml öğesi adı.

Kullanarak bir *app.config* dosya, birim testinin kendisi değişiklikler olmadan veri kaynağının konumunu değiştirmek olanak sağlar. Oluşturma ve kullanma hakkında bilgi için bir *app.config* bkz [izlenecek yol: bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource` Oluşturucu iki parametre ile veri kaynağı ve test yöntemi için veri içeren bir tablo adı için bağlantı dizesini belirtir.

Bağlantı dizelerini veri kaynağı türü türüne bağlıdır, ancak veri sağlayıcı değişmez adını belirten bir sağlayıcı öğesi içermelidir.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Verilere erişmek için TestContext. DataRow kullanın

Verilere erişmek için `AddIntegersData` tablo, kullanın `TestContext.DataRow` dizin oluşturucu. `DataRow` olan bir <xref:System.Data.DataRow> nesne, bu nedenle dizini veya sütun adlarına göre sütun değerlerini alma. Değerleri nesneler olarak döndürdüğünden, bunları uygun türe Dönüştür:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Testi çalıştırın ve sonuçları görüntüleme

Bir test yöntemi yazmayı bitirdiğinizde test projesi oluşturun. Test yöntemi, **Test Gezgini** 'Nde, **çalıştırma** testi grubu ' nda görüntülenir. Çalıştırın, yazma ve testlerinizi yeniden çalıştırın **Test Gezgini** sonuçları gruplarında görüntüler **başarısız testler**, **başarılı testler**, ve **çalıştırılmamış testler**. Seçebileceğiniz **tümünü Çalıştır** tüm testleri çalıştırmak veya **çalıştırma** bir alt kümesini Çalıştırılacak testleri seçmek için.

Test **Gezgini** 'nin en üstündeki test sonuçları çubuğu, test çalıştırmalarınız olarak hareketlendirilir. Testler başarısız olursa test çalışmasının sonunda, tüm testler başarılı değilse yeşil veya Kırmızı çubuk olacaktır. Altındaki ayrıntılar bölmesi test çalışmasının özetini görünür **Test Gezgini** penceresi. Bu testin ayrıntılarını alt bölmede görüntülemek için bir test seçin.

> [!NOTE]
> Her veri satırı ve ayrıca bir Özet sonucu için bir sonuç vardır. Test her bir veri satırına geçirilirse, Özet çalıştırması **geçti**olarak gösterilir. Herhangi bir veri satırında test başarısız olursa, Özet çalıştırması **başarısız**olarak gösterilir.

Çalıştırdıysanız `AddIntegers_FromDataSourceTest` yöntemi örneğimizde sonuçlar çubuğunun kırmızıya döner ve test yönteminin taşınır **başarısız testler**. Veri kaynağından tekrarlayan yöntemlerden herhangi birini başarısız olursa, veri odaklı bir test başarısız olur. Başarısız bir veri tabanlı test seçtiğinizde **Test Gezgini** penceresinde veri satır dizini tarafından tanımlanan her yineleme sonuçları Ayrıntılar bölmesinde görüntülenir. Bizim örneğimizde, göründüğü `AddIntegers` algoritması negatif değerler doğru şekilde işlemiyor.

Ne zaman test altındaki yöntemi düzeltildi ve yeniden test sonuçları çubuk yeşile döner ve test yönteminin taşınır **geçirilen Test** grubu.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Birim testi kod](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Microsoft birim testi çerçevesi ile .NET için birim testleri yazma](../test/unit-test-your-code.md)
