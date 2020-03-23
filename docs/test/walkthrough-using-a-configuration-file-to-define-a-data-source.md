---
title: Veri kaynağını tanımlamak için config dosyasını kullanma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75776152"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Walkthrough: Veri kaynağını tanımlamak için yapılandırma dosyası kullanma

Bu gözden geçirme, birim testi için *app.config* dosyasında tanımlanan bir veri kaynağının nasıl kullanılacağını gösterir. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> Sınıf tarafından kullanılabilecek bir veri kaynağını tanımlayan bir *app.config* dosyası nın nasıl oluşturulacağını öğreneceksiniz. Bu izbeden sunulan görevler şunlardır:

- *App.config* dosyası oluşturma.

- Özel yapılandırma bölümü tanımlama.

- Bağlantı dizeleri tanımlama.

- Veri kaynaklarını tanımlama.

- Sınıfı kullanarak veri kaynaklarına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> erişme.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu tamamlamak için gerekenler:

- Visual Studio Enterprise

- Test yöntemlerinden en az biri için veri sağlamak için Microsoft Access veya Microsoft Excel'den biri.

- Bir test projesi içeren bir Visual Studio çözümü.

## <a name="add-an-appconfig-file-to-the-project"></a>Projeye app.config dosyası ekleme

1. Test projenizde zaten bir *app.config* dosyası varsa, [özel yapılandırma bölümütanım'a](#define-a-custom-configuration-section)gidin.

2. **Çözüm Gezgini'nde**test projenizi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

     **Yeni Öğe Ekle** penceresi açılır.

3. Uygulama **Yapılandırma Dosyası** şablonu seçin ve **Ekle'yi**tıklatın.

## <a name="define-a-custom-configuration-section"></a>Özel yapılandırma bölümü tanımlama

*App.config* dosyasını inceleyin. En azından XML bildirimi ni ve kök öğesini içerir.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>App.config dosyasına özel yapılandırma bölümünü eklemek için

1. *app.config* kök öğesi **yapılandırma** öğesi olmalıdır. **Yapılandırma** öğesi içinde bir **configSections** öğesi oluşturun. **ConfigSections** *app.config* dosyasında ilk öğe olmalıdır.

2. **ConfigSections** öğesi içinde, bir **bölüm** öğesi oluşturun.

3. **Kesit** öğesine, adı verilen `name` bir öznitelik ekleyin `microsoft.visualstudio.testtools`ve bir değer atayın Çağrılan `type` başka bir öznitelik ekleyin ve `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`bir değer atayın.

**Kesit** öğesi buna benzer olmalıdır:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Derleme adı kullandığınız sürümle eşleşmelidir.

## <a name="define-connection-strings"></a>Bağlantı dizelerini tanımlama

Bağlantı dizeleri, veri kaynaklarına erişmek için sağlayıcıya özgü bilgileri tanımlar. Yapılandırma dosyalarında tanımlanan bağlantı dizeleri, bir uygulama genelinde yeniden kullanılabilir veri sağlayıcısı bilgileri sağlar. Bu bölümde, Özel Yapılandırma Bölümünde tanımlanan veri kaynakları tarafından kullanılacak iki bağlantı dizeleri oluşturursunuz.

### <a name="to-define-connection-strings"></a>Bağlantı dizelerini tanımlamak için

1. **ConfigSections** öğesinden sonra, bir **bağlantıStrings** öğesi oluşturun.

2. **ConnectionStrings** öğesi içinde, iki **öğe ekleyin.**

3. İlk **ekle** öğesinde, Microsoft Access veritabanına bağlantı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

İkinci **ekle** öğesinde, Microsoft Excel elektronik tablosuna bağlantı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** öğesi buna benzer olmalıdır:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama

Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört öznitelik içerir.

- `name`hangi veri kaynağının <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> kullanılacağını belirtmek için kullanılan kimliği tanımlar.

- `connectionString`önceki Bağlantı Dizeleri Tanımla bölümünde oluşturulan bağlantı dizesini tanımlar.

- `dataTableName`testte kullanılacak verileri tutan tabloyu veya sayfayı tanımlar.

- `dataAccessMethod`veri kaynağındaki veri değerlerine erişme tekniğini tanımlar.

Bu bölümde, birim testinde kullanılacak iki veri kaynağı tanımlarsınız.

### <a name="to-define-data-sources"></a>Veri kaynaklarını tanımlamak için

1. **ConnectionStrings** öğesinden sonra bir **microsoft.visualstudio.testtools** öğesi oluşturun. Bu bölüm Özel Yapılandırma Bölümü Tanımla'da oluşturuldu.

2. **microsoft.visualstudio.testtools** öğesi içinde bir **dataSources** öğesi oluşturun.

3. **DataSources** öğesi içinde iki **öğe öğesi** oluşturun.

4. İlk **ekle** öğesinde, bir Microsoft Access veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

İkinci **ekle** öğesinde, bir Microsoft Excel veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**microsoft.visualstudio.testtools** öğesi buna benzer olmalıdır:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Son *app.config* dosyası buna benzer olmalıdır:

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

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>app.config'de tanımlanan veri kaynaklarını kullanan bir birim testi oluşturma

Artık bir *app.config* dosyası tanımlandığına göre, *app.config* dosyasında tanımlanan veri kaynaklarında bulunan verileri kullanan bir birim testi oluşturursunuz. Bu bölümde, biz olacak:

- *app.config* dosyasında bulunan veri kaynaklarını oluşturun.

- Veri kaynaklarını, her veri kaynağındaki değerleri karşılaştıran iki test yönteminde kullanın.

### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access veri kaynağı oluşturmak için

1. *testdatasource.accdb*adlı bir Microsoft Access veritabanı oluşturun.

2. Bir tablo oluşturun `MyDataTable` ve *testdatasource.accdb*adını.

3. Adlandırılmış `Arg1` ve `Arg2` veri türünü kullanarak iki alan oluşturun. `MyDataTable` `Number`

4. (10,50), (3,2), (6,0), (0,8) ve (12312,1000) için `MyDataTable` `Arg1` `Arg2`aşağıdaki değerleri içeren beş varlık ekleyin.

5. Veritabanını kaydedin ve kapatın.

6. Bağlantı dizesini veritabanının konumuna işaret etmek için değiştirin. Veritabanının `Data Source` konumunu yansıtacak şekilde değerini değiştirin.

### <a name="to-create-a-microsoft-excel-data-source"></a>Microsoft Excel veri kaynağı oluşturmak için

1. *data.xlsx*adlı bir Microsoft Excel elektronik tablosu oluşturun.

2. `Sheet1` *data.xlsx'te*zaten yoksa adlı bir sayfa oluşturun.

3. İki sütun üstbilgi oluşturun `Val1` `Val2` ve `Sheet1`bunları adlandırın ve .

4. (1,1), `Sheet1` (2,2), `Val2`(3,3), (4,4) ve (5,0) için `Val1` aşağıdaki değerleri içeren beş varlık ekleyin.

5. Elektronik tabloyu kaydedin ve kapatın.

6. Bağlantı dizesini elektronik tablonun konumuna işaret etmek için değiştirin. Elektronik tablonun `dbq` konumunu yansıtacak şekilde değerini değiştirin.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>app.config veri kaynaklarını kullanarak bir birim testi oluşturmak için

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

3. DataSource özniteliklerini inceleyin. *app.config* dosyasındaki ayar adlarını fark edin.

4. Çözümünüzü oluşturun ve MyTestMethod ve MyTestMethod2 testlerini çalıştırın.

> [!IMPORTANT]
> Dağıtım dizininde test edilebilmeleri için veri kaynakları gibi öğeleri dağıtın.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
- [Nasıl Kullanılır: Veri tabanlı birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md)
