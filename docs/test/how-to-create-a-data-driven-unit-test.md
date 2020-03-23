---
title: Veri Odaklı Birim Testleri Oluşturma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589194"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl kullanılır: Veri tabanlı birim testi oluşturma

Yönetilen kod için Microsoft birim test çerçevesini kullanarak bir veri kaynağından değerleri almak için bir birim test yöntemi ayarlayabilirsiniz. Yöntem, veri kaynağındaki her satır için art arda çalıştırılır ve bu da tek bir yöntem kullanarak çeşitli girdilerin test ini kolaylaştırır.

Veri tabanlı birim testi oluşturmak aşağıdaki adımları içerir:

1. Test yönteminde kullandığınız değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.

2. Test sınıfına özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> `TestContext` bir alan ve bir kamu malı ekleyin.

3. Birim test yöntemi oluşturun <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> ve buna bir öznitelik ekleyin.

4. Bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> testte kullandığınız değerleri almak için dizinleyici özelliğini kullanın.

## <a name="the-method-under-test"></a>Test altındaki yöntem

Örnek olarak, şunları varsayalım:

1. Farklı hesap `MyBank` türleri için hareketleri kabul eden ve işleyen bir çözüm.

2. Hesapların hareketlerini `MyBank` `BankDb` yöneten bir proje.

3. Herhangi bir `Maths` işlemin `BankDb` banka için avantajlı olmasını sağlamak için matematiksel işlevleri gerçekleştiren projede çağrılan bir sınıf.

4. Bileşenin davranışını `BankDbTests` `BankDb` sınamak için çağrılan bir birim test projesi.

5. Sınıfın davranışını `Maths` `MathsTests` doğrulamak için çağrılan bir birim test sınıfı.

Bir döngü kullanarak iki `Maths` tamsayı ekleyen bir yöntemi test edeceğiz:

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

`AddIntegers` Yöntemi sınamak için, parametreler ve döndürülmesini beklediğiniz toplam için bir dizi değer belirten bir veri kaynağı oluşturun. Bu örnekte, bir Sql Compact veritabanı `MathsData` ve aşağıdaki `AddIntegersData` sütun adlarını ve değerlerini içeren bir tablo oluştururuz

|İlk Sayı|İkinci Sayi|Toplam|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Test sınıfına TestBağlamı ekleme

Birim test çerçevesi, `TestContext` veri kaynaklı bir test için veri kaynağı bilgilerini depolamak için bir nesne oluşturur. Çerçeve daha sonra bu nesneyi `TestContext` oluşturduğunuz özelliğin değeri olarak ayarlar.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

Test yönteminizde, verilere `DataRow` `TestContext`' nin dizinleyici özelliği nden erişebilirsiniz.

> [!NOTE]
> .NET [Core, DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) özniteliğini desteklemez. Bir .NET Core veya UWP birim test projesinde test verilerine bu şekilde erişmeye çalışırsanız, **"'TestContext' 'DataRow' tanımı içermez ve 'TestContext' türünden ilk bağımsız değişkeni kabul eden erişilebilir bir uzatma yöntemi 'DataRow' bulunamadı (bir yönergeyi veya derleme başvurusunu kaçırıyor musunuz?)"** gibi bir hata görürsünüz.

## <a name="write-the-test-method"></a>Test yöntemini yazma

Test `AddIntegers` yöntemi oldukça basittir. Veri kaynağındaki her satır `AddIntegers` **için, Birinci Numara** ve **SecondNumber** sütun değerlerini parametre olarak arayın ve **toplam** sütun değerine göre geri dönüş değerini doğrulayın:

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

Yöntem, `Assert` başarısız bir `x` yinelemenin `y` değerlerini ve değerlerini görüntüleyen bir ileti içerir. Varsayılan olarak, ileri sayılmakta olan değerler ve `expected` `actual` bunlar zaten başarısız test ayrıntılarına dahil edilir.

### <a name="specify-the-datasourceattribute"></a>DataSourceAttribute belirtin

Öznitelik, `DataSource` veri kaynağının bağlantı dizesini ve test yönteminde kullandığınız tablonun adını belirtir. Bağlantı dizesindeki tam bilgiler, kullandığınız veri kaynağına bağlı olarak değişir. Bu örnekte, bir SqlServerCe veritabanı kullandık.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource özniteliği üç oluşturucuya sahiptir.

```csharp
[DataSource(dataSourceSettingName)]
```

Bir parametreye sahip bir oluşturucu, çözüm için *app.config* dosyasında depolanan bağlantı bilgilerini kullanır. *dataSourceSettingsName,* bağlantı bilgilerini belirten config dosyasındaki Xml öğesinin adıdır.

*App.config* dosyasını kullanmak, birim testinde değişiklik yapmadan veri kaynağının konumunu değiştirmenize olanak tanır. Bir *app.config* dosyasının nasıl oluşturulup kullanılacağı hakkında bilgi için Bkz. [Walkthrough: Veri Kaynağını Tanımlamak için Yapılandırma Dosyasını Kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

İki `DataSource` parametreye sahip oluşturucu, veri kaynağının bağlantı dizesini ve test yönteminin verilerini içeren tablonun adını belirtir.

Bağlantı dizeleri veri kaynağının türüne bağlıdır, ancak veri sağlayıcısının değişmez adını belirten bir Sağlayıcı öğesi içermelidir.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Verilere erişmek için TestContext.DataRow'u kullanma

Tablodaki verilere erişmek `AddIntegersData` için dizinleyiciyi `TestContext.DataRow` kullanın. `DataRow`bir <xref:System.Data.DataRow> nesnedir, bu nedenle sütun değerlerini dizin veya sütun adlarıyla alın. Değerler nesne olarak döndürüldüğü için, bunları uygun türe dönüştürün:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Testi çalıştırın ve sonuçları görüntüleyin

Bir test yöntemi yazmayı tamamladığınızda, test projesini oluşturun. Test **yöntemi, Testler Çalıştırılamayanlar** grubunda **Test Gezgini'nde** görünür. Test Gezgini, testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdırken, Test **Gezgini** sonuçları **Başarısız Testler**, **Geçti Testleri**ve **Çalıştırmama**testgruplarında görüntüler. Tüm testlerinizi çalıştırmak için **Tümlerini Çalıştır'ı** seçebilir veya çalıştırmak için bir test alt kümesi seçmek için **Çalıştır'ı** seçebilirsiniz.

**Test** Gezgini'nin üst kısmındaki test sonuçları çubuğu, testiniz çalışırken animasyonludur. Test çalışmasının sonunda, tüm testler geçtiyse çubuk yeşil veya testlerin herhangi biri başarısız olduysa kırmızı olacaktır. Test çalışmasının bir özeti, **Test Gezgini** penceresinin altındaki ayrıntılar bölmesinde görünür. Alt bölmedeki testin ayrıntılarını görüntülemek için bir test seçin.

> [!NOTE]
> Her veri satırı ve bir özet sonucu için bir sonuç vardır. Test her veri satırında geçtiyse, özet çalışması **Geçti**olarak gösterir. Sınama herhangi bir veri satırında başarısız olduysa, özet çalışması **Başarısız**olarak gösterir.

Örneğimizde `AddIntegers_FromDataSourceTest` yöntemi çalıştırdığınızda, sonuç çubuğu kırmızıya döner ve test yöntemi **Başarısız Testler'e**taşınır. Veri kaynağından gelen yineedilen yöntemlerden herhangi biri başarısız olursa, veri tabanlı bir sınama başarısız olur. **Test Gezgini** penceresinde başarısız bir veri tabanlı test seçtiğinizde, ayrıntılar bölmesi veri satır dizini tarafından tanımlanan her yinelemenin sonuçlarını görüntüler. Örneğimizde, algoritmanın `AddIntegers` negatif değerleri doğru işlemediği görülmektedir.

Test altındaki yöntem düzeltildiğinde ve test yeniden çalıştırıldığında, sonuç çubuğu yeşile döner ve test yöntemi **Geçti Test** grubuna taşınır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
- [Microsoft birim test çerçevesi ile .NET için birim testleri yazma](../test/unit-test-your-code.md)
