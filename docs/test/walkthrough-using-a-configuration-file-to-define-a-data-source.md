---
title: Veri kaynağını tanımlamak için yapılandırma dosyasını kullanma
description: Bir veri kaynağını tanımlayan bir app.config dosyası oluşturmakla başlayarak birim testi için app.config veri kaynağını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 82a711e21d75486fb7217d1f831831fd3476b06b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106594"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Adım adım kılavuz: Veri kaynağı tanımlamak için yapılandırma dosyası kullanma

Bu kılavuzda, birim testi için bir veriapp.config *veri* kaynağının nasıl kullanımı açıklanır. sınıfı tarafından *kullanılaapp.config* bir veri kaynağını tanımlayan bir veri dosyası oluşturma hakkında bilgi ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> bilgiler ve bilgiler içerir. Bu kılavuzda sunulan görevler aşağıdakileri içerir:

- Bir *app.config* oluşturma.

- Özel yapılandırma bölümü tanımlama.

- Bağlantı dizelerini tanımlama.

- Veri kaynaklarını tanımlama.

- sınıfını kullanarak veri kaynaklarına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> erişme.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu tamamlamak için gerekenler:

- Visual Studio Enterprise

- Microsoft Access veya Microsoft Excel test yöntemlerinden en az biri için veri sağlamak için kullanabilirsiniz.

- Test Visual Studio içeren bir çözüm.

## <a name="add-an-appconfig-file-to-the-project"></a>Projeye app.config dosya ekleme

1. Test projenizin zaten bir *app.config* dosyası varsa Özel yapılandırma tanımlama bölümüne [gidin.](#define-a-custom-configuration-section)

2. içinde test projenize sağ tıklayın **Çözüm Gezgini** Yeni Öğe **Ekle'yi**  >  **seçin.**

     Yeni **Öğe Ekle penceresi** açılır.

3. Uygulama Yapılandırma **Dosyası şablonunu seçin ve** Ekle'ye **tıklayın.**

## <a name="define-a-custom-configuration-section"></a>Özel yapılandırma bölümü tanımlama

app.config *inceleme.* En azından XML bildirimini ve kök öğesini içerir.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Özel yapılandırma bölümünü app.config eklemek için

1. Uygulamanın kök *app.config* yapılandırma öğesi **olması** gerekir. Yapılandırma öğesi **içinde bir configSections** **öğesi** oluşturun. **configSections,** dosyanın ilk öğesi *app.config* gerekir.

2. **configSections öğesinin** içinde bir bölüm **öğesi** oluşturun.

3. bölüm **öğesinde** adlı bir öznitelik ekleyin `name` ve değerine atfedin. `microsoft.visualstudio.testtools` adlı başka bir öznitelik `type` ekleyin ve değerine atfedin. `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`

Bölüm **öğesi** şuna benzer şekilde görünüyor:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Derleme adı, kullanmakta olduğu sürümle eşleşmeli.

## <a name="define-connection-strings"></a>Bağlantı dizelerini tanımlama

Bağlantı dizeleri, veri kaynaklarına erişmek için sağlayıcıya özgü bilgileri tanımlar. Yapılandırma dosyalarında tanımlanan bağlantı dizeleri, bir uygulama genelinde yeniden kullanılabilir veri sağlayıcısı bilgileri sağlar. Bu bölümde, Özel Yapılandırma Bölümünde tanımlanan veri kaynakları tarafından kullanılacak iki bağlantı dizesi oluşturabilirsiniz.

### <a name="to-define-connection-strings"></a>Bağlantı dizelerini tanımlamak için

1. **configSections öğesindan** sonra bir **connectionStrings öğesi** oluşturun.

2. **connectionStrings öğesinin** içinde iki ek **öğe** oluşturun.

3. İlk add **öğesinde,** bir Microsoft Access veritabanına bağlantı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

İkinci add **öğesinde,** bir elektronik tabloyla bağlantı için aşağıdaki öznitelikleri ve Microsoft Excel oluşturun:

|Öznitelik|Değerler|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**connectionStrings öğesi** şuna benzer şekilde görünüyor:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama

Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört öznitelik içerir.

- `name` , kullanılacak veri kaynağını <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> belirtmek için tarafından kullanılan kimliği tanımlar.

- `connectionString` önceki Bağlantı Dizelerini Tanımla bölümünde oluşturulan bağlantı dizesini tanımlar.

- `dataTableName` , testte kullanmak üzere verileri tutan tabloyu veya sayfayı tanımlar.

- `dataAccessMethod` , veri kaynağında veri değerlerine erişme tekniğini tanımlar.

Bu bölümde, birim testinde kullanmak üzere iki veri kaynağı tanımlayabilirsiniz.

### <a name="to-define-data-sources"></a>Veri kaynaklarını tanımlamak için

1. **connectionStrings öğesinin** ardından bir **microsoft.visualstudio.testtools öğesi** oluşturun. Bu bölüm Özel Yapılandırma Tanımlama Bölümünde oluşturulmuş.

2. **microsoft.visualstudio.testtools öğesinde** bir **dataSources öğesi** oluşturun.

3. **dataSources öğesinin** içinde iki ek **öğe** oluşturun.

4. İlk add **öğesinde,** Microsoft Access veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

İkinci add **öğesinde,** bir veri kaynağı için aşağıdaki öznitelikleri ve Microsoft Excel oluşturun:

|Öznitelik|Değerler|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**microsoft.visualstudio.testtools öğesi** şuna benzer şekilde görüntü gerekir:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Son *app.config* dosyası şuna benzer şekilde görünüyor:

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

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Veri kaynaklarında tanımlanan veri kaynaklarını kullanan bir birim testi app.config

Bir *app.config* dosyası tanımlandığına göre,app.configdosyasında tanımlanan veri kaynaklarında bulunan verileri kullanan *bir birim testiapp.config* oluşturabilirsiniz. Bu bölümde şunları olacak:

- app.configdosyasında *bulunan veri kaynaklarını* oluşturun.

- Veri kaynaklarını her veri kaynağında değerleri karşılaştıran iki test yönteminde kullanın.

### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access veri kaynağı oluşturmak için

1. *testdatasource.accdb adlı bir* Microsoft Access veritabanı oluşturun.

2. Bir tablo oluşturun ve `MyDataTable` *testdatasource.accdb içinde bu tabloyu olarak adlandırın.*

3. içinde veri türünü `MyDataTable` kullanarak ve adlı iki alan `Arg1` `Arg2` `Number` oluşturun.

4. ve için sırasıyla şu değerlerle beş varlık `MyDataTable` `Arg1` `Arg2` ekleyin: (10,50), (3,2), (6,0), (0,8) ve (12312,1000).

5. Veritabanını kaydedin ve kapatın.

6. Bağlantı dizesini veritabanının konumunu işaret etmek için değiştirme. değerini `Data Source` veritabanının konumunu yansıtacak şekilde değiştirme.

### <a name="to-create-a-microsoft-excel-data-source"></a>Bir veri Microsoft Excel oluşturmak için

1. data.xlsxadlı Microsoft Excel elektronik *data.xlsx.*

2. içinde zaten yoksa `Sheet1` adlı bir sayfa *data.xlsx.*

3. İki sütun üst bilgisi oluşturun ve bunları içinde `Val1` ve olarak `Val2` `Sheet1` adlar.

4. ve için sırasıyla şu değerlerle beş varlık `Sheet1` `Val1` `Val2` ekleyin: (1,1), (2,2), (3,3), (4,4) ve (5,0).

5. Elektronik tabloyu kaydedin ve kapatın.

6. Bağlantı dizesini elektronik tablonun konumunu işaret etmek için değiştirme. değerini elektronik `dbq` tablonun konumunu yansıtacak şekilde değiştirebilirsiniz.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Veri kaynaklarını kullanarak birim testi app.config için

1. Test projesine bir birim testi ekleyin.

2. Birim testinin otomatik olarak oluşturulan içeriğini aşağıdaki kodla değiştirin:

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

3. DataSource özniteliklerini inceleme. Dosyanın ayar *adlarından* app.config.

4. Çözümlerinizi derleme ve MyTestMethod ve MyTestMethod2 testlerini çalıştırma.

> [!IMPORTANT]
> Dağıtım dizinindeki test için erişilebilir olması için veri kaynakları gibi öğeleri dağıtın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Nasıl kullanılır: Veri odaklı birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md)
