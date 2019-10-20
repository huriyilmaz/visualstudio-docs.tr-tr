---
title: 'İzlenecek yol: bir veri kaynağı tanımlamak için yapılandırma dosyası kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 64ac9835a085908645713f95f1f07c283d807852
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657054"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>İzlenecek Yol: Bir Veri Kaynağı Tanımlamak için Yapılandırma Dosyası Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, birim testi için App. config dosyasında tanımlanan bir veri kaynağını nasıl kullanacağınızı gösterir. @No__t_0 sınıfı tarafından kullanılabilecek bir veri kaynağını tanımlayan bir App. config dosyası oluşturmayı öğreneceksiniz. Bu izlenecek yolda sunulan görevler şunları içerir:

- App. config dosyası oluşturuluyor.

- Özel yapılandırma bölümü tanımlama.

- Bağlantı dizelerini tanımlama.

- Veri kaynaklarını tanımlama.

- @No__t_0 sınıfını kullanarak veri kaynaklarına erişme.

## <a name="prerequisites"></a>Prerequisites
 Bu kılavuzu tamamlamak için şunlara ihtiyacınız olacak:

- Visual Studio Enterprise

- En az bir test yönteminden veri sağlamak için Microsoft Access veya Microsoft Excel.

- Test projesi içeren bir Visual Studio çözümü.

## <a name="create-the-appconfig-file"></a>App. config dosyasını oluşturma

#### <a name="to-add-an-appconfig-file-to-the-project"></a>Projeye bir App. config dosyası eklemek için

1. Test projenizin zaten bir App. config dosyası varsa, [özel yapılandırma tanımla bölümüne](#DefineCustomConfigurationSection)gidin.

2. **Çözüm Gezgini**test projenize sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

     **Yeni öğe Ekle** penceresi açılır.

3. **Uygulama yapılandırma dosyası** şablonunu seçin ve **Ekle**' ye tıklayın.

## <a name="DefineCustomConfigurationSection"></a>Özel yapılandırma bölümü tanımlama
 App. config dosyasını inceleyin. En azından XML bildirimi ve bir kök öğesi içerir.

#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Özel yapılandırma bölümünü App. config dosyasına eklemek için

1. App. config 'in kök öğesi `configuration` öğesi olmalıdır. @No__t_1 öğesi içinde `configSections` öğesi oluşturun. @No__t_0 App. config dosyasındaki ilk öğe olmalıdır.

2. @No__t_0 öğesi içinde, bir `section` öğesi oluşturun.

3. @No__t_0 öğesinde, `name` adlı bir öznitelik ekleyin ve ona eşit bir değer `microsoft.visualstudio.testtools` atayın. @No__t_0 adlı başka bir öznitelik ekleyin ve buna eşit bir değer atayın `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

   @No__t_0 öğesi şuna benzemelidir:

```
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Bütünleştirilmiş kod adı, kullanmakta olduğunuz Microsoft Visual Studio .NET Framework derlemesi ile aynı olmalıdır. Visual Studio .NET Framework 3,5 kullanıyorsanız sürümü 9.0.0.0 olarak ayarlayın. Visual Studio .NET Framework 2,0 kullanıyorsanız, sürümü 8.0.0.0 olarak ayarlayın.

## <a name="define-connection-strings"></a>Bağlantı dizelerini tanımlama
 Bağlantı dizeleri, veri kaynaklarına erişmek için sağlayıcıya özgü bilgileri tanımlar. Yapılandırma dosyalarında tanımlanan bağlantı dizeleri bir uygulama genelinde yeniden kullanılabilir veri sağlayıcı bilgileri sağlar. Bu bölümde, özel yapılandırma bölümünde tanımlanan veri kaynakları tarafından kullanılacak iki bağlantı dizesi oluşturursunuz.

#### <a name="to-define-connection-strings"></a>Bağlantı dizelerini tanımlamak için

1. @No__t_0 öğeden sonra, bir `connectionStrings` öğesi oluşturun.

2. @No__t_0 öğesi içinde iki `add` öğesi oluşturun.

3. İlk `add` öğesinde, Microsoft Access veritabanı bağlantısı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|---------------|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

 İkinci `add` öğesinde, bir Microsoft Excel elektronik tablosu bağlantısı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|||
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

 @No__t_0 öğesi şuna benzemelidir:

```
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama
 Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört özniteliği içerir.

- `name`, hangi veri kaynağının kullanılacağını belirtmek için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> tarafından kullanılan kimliği tanımlar.

- `connectionString`, önceki bağlantı dizelerini tanımlama bölümünde oluşturulan bağlantı dizesini tanımlar.

- `dataTableName` testte kullanılacak verileri tutan tabloyu veya sayfayı tanımlar.

- `dataAccessMethod` veri kaynağındaki veri değerlerine erişim tekniğini tanımlar.

  Bu bölümde, bir birim testinde kullanılacak iki veri kaynağı tanımlayacaksınız.

#### <a name="to-define-data-sources"></a>Veri kaynaklarını tanımlamak için

1. @No__t_0 öğeden sonra, bir `microsoft.visualstudio.testtools` öğesi oluşturun. Bu bölüm özel bir yapılandırma bölümü tanımlar bölümünde oluşturulmuştur.

2. @No__t_0 öğesi içinde, bir `dataSources` öğesi oluşturun.

3. @No__t_0 öğesi içinde iki `add` öğesi oluşturun.

4. İlk `add` öğesinde, bir Microsoft Access veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|Öznitelik|Değerler|
|---------------|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

 İkinci `add` öğesinde, Microsoft Excel veri kaynağı için aşağıdaki öznitelikleri ve değerleri oluşturun:

|||
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

 @No__t_0 öğesi şuna benzemelidir:

```
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

 Son App. config dosyası şuna benzemelidir:

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>App. config dosyasında tanımlanan veri kaynaklarını kullanarak birim testi oluşturma
 Artık bir App. config dosyası tanımlandığına göre, App. config dosyasında tanımlanan veri kaynaklarında bulunan verileri kullanan bir birim testi oluşturacaksınız. Bu bölümde şunları göndereceğiz:

- App. config dosyasında bulunan veri kaynaklarını oluşturun.

- Veri kaynaklarını her bir veri kaynağındaki değerleri karşılaştıran iki test yöntemlerinde kullanın.

#### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access veri kaynağı oluşturmak için

1. @No__t_0 adlı bir Microsoft Access veritabanı oluşturun.

2. @No__t_1 `MyDataTable` tablo oluşturun ve adlandırın.

3. @No__t_0 adlı `Arg1` ve `Arg2` `Number` veri türünü kullanarak iki alan oluşturun.

4. Aşağıdaki değerleri sırasıyla `Arg1` ve `Arg2` `MyDataTable` için beş varlık ekleyin: (10, 50), (3, 2), (6, 0), (0, 8) ve (12312, 1000).

5. Veritabanını kaydedin ve kapatın.

6. Bağlantı dizesini, veritabanının konumunu işaret etmek üzere değiştirin. @No__t_0 değerini, veritabanının konumunu yansıtacak şekilde değiştirin.

#### <a name="to-create-a-microsoft-excel-data-source"></a>Microsoft Excel veri kaynağı oluşturmak için

1. @No__t_0 adlı bir Microsoft Excel elektronik tablosu oluşturun.

2. @No__t_1 zaten yoksa `Sheet1` adlı bir sayfa oluşturun.

3. İki sütunlu üst bilgi oluşturun ve `Sheet1` `Val1` ve `Val2` adlandırın.

4. Aşağıdaki değerleri sırasıyla `Val1` ve `Val2` `Sheet1` için beş varlık ekleyin: (1, 1), (2, 2), (3, 3), (4, 4) ve (5, 0).

5. Elektronik tabloyu kaydedin ve kapatın.

6. Bağlantı dizesini elektronik tablonun konumunu işaret etmek üzere değiştirin. @No__t_0 değerini, elektronik tablonun konumunu yansıtacak şekilde değiştirin.

#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>App. config veri kaynaklarını kullanarak birim testi oluşturmak için

1. Test projesine bir birim testi ekleyin.

     Daha fazla bilgi için bkz. [var olan kod Için birim testleri oluşturma ve çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).

2. Birim testinin otomatik olarak oluşturulan içeriğini şu kodla değiştirin:

    ```
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

3. DataSource özniteliklerini inceleyin. App. config dosyasından ayar adlarına dikkat edin.

4. Çözümünüzü derleyin ve MyTestMethod ve MyTestMethod2 testlerini çalıştırın.

> [!IMPORTANT]
> Dağıtım dizinindeki teste erişilebilmesi için veri kaynakları gibi öğeleri dağıtın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod testi kodunuzu test](../test/unit-test-your-code.md) etme [ve çalıştırma mevcut kod testi için birim testleri oluşturma ve çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [uygulama](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [nasıl yapılır: veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md)
