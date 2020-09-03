---
title: Veri kaynağını tanımlamak için yapılandırma dosyası kullan
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a4f5731a828eb04e57f56a46fe399125b5ded2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75776152"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>İzlenecek yol: bir veri kaynağı tanımlamak için yapılandırma dosyası kullanma

Bu izlenecek yol, birim testi için bir *app.config* dosyasında tanımlanan bir veri kaynağını nasıl kullanacağınızı gösterir. Sınıfı tarafından kullanılabilecek bir veri kaynağını tanımlayan bir *app.config* dosyası oluşturmayı öğreneceksiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> . Bu izlenecek yolda sunulan görevler şunları içerir:

- *app.config* dosyası oluşturuluyor.

- Özel yapılandırma bölümü tanımlama.

- Bağlantı dizelerini tanımlama.

- Veri kaynaklarını tanımlama.

- Sınıfını kullanarak veri kaynaklarına erişme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> .

## <a name="prerequisites"></a>Ön koşullar

Bu kılavuzu tamamlamak için gerekenler:

- Visual Studio Enterprise

- En az bir test yönteminden veri sağlamak için Microsoft Access veya Microsoft Excel.

- Test projesi içeren bir Visual Studio çözümü.

## <a name="add-an-appconfig-file-to-the-project"></a>Projeye bir app.config dosyası ekleyin

1. Test projenizin zaten bir *app.config* dosyası varsa, [özel yapılandırma tanımla bölümüne](#define-a-custom-configuration-section)gidin.

2. **Çözüm Gezgini**' de test projenize sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

     **Yeni öğe Ekle** penceresi açılır.

3. **Uygulama yapılandırma dosyası** şablonunu seçin ve **Ekle**' ye tıklayın.

## <a name="define-a-custom-configuration-section"></a>Özel yapılandırma bölümü tanımlama

*app.config* dosyasını inceleyin. En azından XML bildirimi ve bir kök öğesi içerir.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>app.config dosyasına özel yapılandırma bölümünü eklemek için

1. *app.config* kök öğesi **yapılandırma** öğesi olmalıdır. **Yapılandırma** öğesi Içinde bir **configSections** öğesi oluşturun. **ConfigSections** *app.config* dosyasındaki ilk öğe olmalıdır.

2. **ConfigSections** öğesi içinde bir **section** öğesi oluşturun.

3. **Bölüm** öğesinde adlı bir öznitelik ekleyin `name` ve değeri atayın `microsoft.visualstudio.testtools` . Adlı başka bir öznitelik ekleyin `type` ve değeri atayın `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions` .

**Section** öğesi şuna benzer görünmelidir:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Derleme adı, kullanmakta olduğunuz sürümle aynı olmalıdır.

## <a name="define-connection-strings"></a>Bağlantı dizelerini tanımlama

Bağlantı dizeleri, veri kaynaklarına erişmek için sağlayıcıya özgü bilgileri tanımlar. Yapılandırma dosyalarında tanımlanan bağlantı dizeleri bir uygulama genelinde yeniden kullanılabilir veri sağlayıcı bilgileri sağlar. Bu bölümde, özel yapılandırma bölümünde tanımlanan veri kaynakları tarafından kullanılacak iki bağlantı dizesi oluşturursunuz.

### <a name="to-define-connection-strings"></a>Bağlantı dizelerini tanımlamak için

1. **ConfigSections** öğesinden sonra bir **connectionStrings** öğesi oluşturun.

2. **ConnectionStrings** öğesi içinde, iki **ekleme** öğesi oluşturun.

3. İlk **Add** öğesinde, bir Microsoft Access veritabanı bağlantısı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

İkinci **Add** öğesinde, bir Microsoft Excel elektronik tablosu bağlantısı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** öğesi şuna benzer görünmelidir:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama

Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört özniteliği içerir.

- `name`<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>hangi veri kaynağının kullanılacağını belirtmek için tarafından kullanılan kimliği tanımlar.

- `connectionString` önceki bağlantı dizelerini tanımlama bölümünde oluşturulan bağlantı dizesini tanımlar.

- `dataTableName` Testte kullanılacak verileri tutan tabloyu veya sayfayı tanımlar.

- `dataAccessMethod` veri kaynağındaki veri değerlerine erişim tekniğini tanımlar.

Bu bölümde, bir birim testinde kullanılacak iki veri kaynağı tanımlayacaksınız.

### <a name="to-define-data-sources"></a>Veri kaynaklarını tanımlamak için

1. **ConnectionStrings** öğesinden sonra bir **Microsoft. VisualStudio. TestTools** öğesi oluşturun. Bu bölüm özel bir yapılandırma bölümü tanımlar bölümünde oluşturulmuştur.

2. **Microsoft. VisualStudio. TestTools** öğesi Içinde bir **DataSources** öğesi oluşturun.

3. **DataSources** öğesi içinde, iki **ekleme** öğesi oluşturun.

4. İlk **Add** öğesinde, bir Microsoft Access veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

İkinci **Add** öğesinde, Microsoft Excel veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**Microsoft. VisualStudio. TestTools** öğesi şuna benzer görünmelidir:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Son *app.config* dosyası şuna benzemelidir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>app.config tanımlı veri kaynaklarını kullanan bir birim testi oluşturma

Artık bir *app.config* dosyası tanımlandığına göre, *app.config* dosyasında tanımlanan veri kaynaklarında bulunan verileri kullanan bir birim testi oluşturacaksınız. Bu bölümde şunları göndereceğiz:

- *app.config* dosyasında bulunan veri kaynaklarını oluşturun.

- Veri kaynaklarını her bir veri kaynağındaki değerleri karşılaştıran iki test yöntemlerinde kullanın.

### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access veri kaynağı oluşturmak için

1. *Testdatasource. accdb*adlı bir Microsoft Access veritabanı oluşturun.

2. Bir tablo oluşturun ve `MyDataTable` *testdatasource. accdb*içinde adlandırın.

3. `MyDataTable`Adında `Arg1` ve `Arg2` `Number` veri türünü kullanarak iki alan oluşturun.

4. `MyDataTable`Ve için aşağıdaki değerleri sırasıyla öğesine beş varlık ekleyin `Arg1` `Arg2` : (10, 50), (3, 2), (6, 0), (0, 8) ve (12312, 1000).

5. Veritabanını kaydedin ve kapatın.

6. Bağlantı dizesini, veritabanının konumunu işaret etmek üzere değiştirin. Değerini, `Data Source` veritabanının konumunu yansıtacak şekilde değiştirin.

### <a name="to-create-a-microsoft-excel-data-source"></a>Microsoft Excel veri kaynağı oluşturmak için

1. *data.xlsx*adlı bir Microsoft Excel elektronik tablosu oluşturun.

2. `Sheet1` *data.xlsx*içinde zaten mevcut değilse adlı bir sayfa oluşturun.

3. İki sütunlu üst bilgi oluşturun ve bunları `Val1` `Val2` içinde ve olarak adlandırın `Sheet1` .

4. `Sheet1`Ve için aşağıdaki değerleri sırasıyla öğesine beş varlık ekleyin `Val1` `Val2` : (1, 1), (2, 2), (3, 3), (4, 4) ve (5, 0).

5. Elektronik tabloyu kaydedin ve kapatın.

6. Bağlantı dizesini elektronik tablonun konumunu işaret etmek üzere değiştirin. Değerini `dbq` Elektronik tablonun konumunu yansıtacak şekilde değiştirin.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>app.config veri kaynaklarını kullanarak birim testi oluşturmak için

1. Test projesine bir birim testi ekleyin.

2. Birim testinin otomatik olarak oluşturulan içeriğini şu kodla değiştirin:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. DataSource özniteliklerini inceleyin. *app.config* dosyasından ayar adlarına dikkat edin.

4. Çözümünüzü derleyin ve MyTestMethod ve MyTestMethod2 testlerini çalıştırın.

> [!IMPORTANT]
> Dağıtım dizinindeki teste erişilebilmesi için veri kaynakları gibi öğeleri dağıtın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Nasıl yapılır: veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md)
