---
title: Kodlanmış UI test öğreticisini Data-Driven
description: Farklı parametre değerleriyle testlerinizi birden çok kez çalıştırarak farklı koşulları test etmek için veri odaklı kodlanmış UI testlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 38c1a5dc40dde5805ec9d233287b95233585f480
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635526"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Veri odaklı kodlanmış UI testi oluşturma

Farklı koşulları test etmek için testlerinizi farklı parametre değerleriyle birden çok kez çalıştırabilirsiniz. Veri odaklı kodlanmış UI testleri bunu yapmanın kolay bir yoludur. Parametre değerlerini bir veri kaynağında tanımlarsınız ve veri kaynağındaki her satır, kodlanmış UI testinin bir yinelemedir. Testin genel sonucu, tüm yinelemelerin sonucunu temel alır. Örneğin, bir test yinelemesi başarısız olursa, genel test sonucu başarısız olur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="create-a-test-project"></a>Test projesi oluşturma

bu örnek, Windows hesaplayıcı uygulamasında çalışan kodlanmış bir uı testi oluşturur. İki sayıyı birbirine ekler ve toplamın doğru olduğunu doğrulamak için bir onaylama kullanır. Ardından, iki sayının onaylama ve parametre değerleri, veri odaklı ve virgülle ayrılmış bir değer (*.csv*) dosyasında depolanacak şekilde kodlanır.

### <a name="step-1---create-a-coded-ui-test"></a>1. adım-kodlanmış UI testi oluşturma

1. Bir proje oluşturun.

    ![Kodlanmış UI test projesi oluşturma](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > **kodlanmış uı testi Project** şablonu görmüyorsanız, [kodlanmış uı test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. **Eylemleri kaydetmeyi** seçin.

    ![Eylemleri kaydetmeyi seçin](../test/media/cuit_datadriven_generatecodedialog.png)

3. Hesaplayıcı uygulamasını açın ve testi kaydetmeye başlayın.

    ![Kayıt eylemleri](../test/media/cuit_datadriven_cuitbuilder.png)

4. 1 Plus 2 ' yi ekleyin, kaydediciyi duraklatın ve test yöntemi oluşturun. Daha sonra bu kullanıcı girişinin değerlerini bir veri dosyasındaki değerlerle değiştirecek.

    ![Test yöntemi oluştur](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Test oluşturucuyu kapatın. Yöntemi teste eklenir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Testin çalıştığını `AddNumbers()` doğrulamak için yöntemini kullanın. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: **CTRL** + **R**,**T**).

    Test **Gezgini** penceresinde başarılı veya başarısız olan testin görüntülendiğini gösteren test sonucu. test gezgini penceresini açmak için, **test** menüsünden **Windows** ' yi seçin ve ardından **test gezgini**' ni seçin.

6. Bir veri kaynağı, beklenen değerleri doğrulamak için test tarafından kullanılan onaylama parametre değerleri için de kullanılabilir —, iki sayının toplamının doğru olduğunu doğrulamak için bir onaylama ekleyelim. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **KODLANMıŞ UI testi Için kod oluştur**' u seçin ve **kodlanmış UI Test Oluşturucusu**' nu kullanın.

    Toplamı görüntüleyen hesaplayıcıda metin denetimini eşleyin.

    ![UI metin denetimini eşleme](../test/media/cuit_datadriven_addassertion.png)

7. Toplamın değerinin doğru olduğunu doğrulayan bir onaylama ekleyin. **3** değerine sahip **Görüntümetni** özelliğini seçin ve ardından **onay Ekle**' yi seçin. **Areeşitse** karşılaştırıcısı ' nı kullanın ve karşılaştırma değerinin **3** olduğunu doğrulayın.

    ![Onaylama işlemi yapılandırma](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Onaylama 'yı yapılandırdıktan sonra, oluşturucuyu yeniden kod oluşturun. Bu, doğrulama için yeni bir yöntem oluşturur.

    ![Onaylama yöntemini oluşturma](../test/media/cuit_datadriven_assertiongencode.png)

    `ValidateSum`Yöntemi yönteminin sonuçlarını doğruladığından `AddNumbers` , onu kod bloğunun altına taşıyın.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Yöntemi kullanarak testin çalıştığını doğrulayın `ValidateSum()` . İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: **CTRL** + **R**,**T**).

     Bu noktada, tüm parametre değerleri, yöntemlerinde sabitler olarak tanımlanmıştır. Ardından, test veri odaklı bir veri kümesi oluşturalım.

### <a name="step-2---create-a-data-set"></a>2. adım-veri kümesi oluşturma

1. *data.csv* adlı dataDrivenSample projesine bir metin dosyası ekleyin.

     ![Projeye virgülle ayrılmış bir değer dosyası ekleyin](../test/media/cuit_datadriven_addcsvfile.png)

2. *.csv* dosyasını aşağıdaki verilerle doldurun:

    |Num1|Num2|Sum|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Veriler eklendikten sonra, dosya aşağıdaki gibi görünmelidir:

     ![.csv dosyasını veriyle doldurma](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. *.csv* dosyasının doğru kodlamayı kullanarak kaydedilmesi önemlidir. **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** belirleyin ve kodlama olarak **Unicode (imzasız UTF-8 65001)** seçeneğini belirleyin.

4. *.csv* dosyası, çıkış dizinine kopyalanmalıdır veya test çalıştırılamıyor. Kopyalamak için **Özellikler** penceresini kullanın.

     ![.csv dosyasını dağıtma](../test/media/cuit_datadriven_deploycsvfile.png)

     Veri kümesi oluşturulduğuna göre, artık verileri teste bağlayalim.

### <a name="step-3---add-data-source-binding"></a>3. adım-veri kaynağı bağlamayı ekleme

1. Veri kaynağını bağlamak için, `DataSource` `[TestMethod]` test yönteminin hemen üzerinde yer alan var olan özniteliği içine bir öznitelik ekleyin.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     Veri kaynağı artık bu test yönteminde kullanabileceğiniz şekilde kullanılabilir.

    > [!TIP]
    > XML, SQL Express ve Excel gibi diğer veri kaynağı türlerini kullanma örnekleri için soru-& cevap bölümündeki [veri kaynağı öznitelik örneklerine](#CreateDataDrivenCUIT_QA_DataSourceAttributes) bakın.

2. Testi çalıştırın.

     Testin üç yineleme aracılığıyla çalıştığını unutmayın. Bunun nedeni, bağlanan veri kaynağının üç satırlık veri içereceğinden oluşur. Bununla birlikte, testin hala sabit parametre değerlerini kullandığını ve her seferinde 3 ' ten 2 ' ye kadar 1 + 2 ekliyor olduğunu fark edeceksiniz.

     Daha sonra, veri kaynağı dosyasındaki değerleri kullanmak için testi yapılandıracağız.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>4. adım-kodlanmış UI testinde verileri kullanma

1. `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` *CodedUITest. cs* dosyasının en üstüne ekleyin:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2. `TestContext.DataRow[]` `CodedUITestMethod1()` Veri kaynağından değerleri uygulayacak olan yöntemine ekleyin. Veri kaynağı değerleri, denetimleri kullanarak UIMap denetimlerine atanan sabitleri geçersiz kılar `SearchProperties` :

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();
       this.UIMap.UICalculatorWindow.UIItemWindow2.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSumExpectedValues.UIItem3TextDisplayText = TestContext.DataRow["Sum"].ToString();
       this.UIMap.ValidateSum();
    }
    ```

     Verilerin hangi arama özelliklerine göre kodlamasını anlamak için, kodlanmış UI test düzenleyicisini kullanın.

    - *UIMap. UITest* dosyasını açın.

         ![Kodlanmış UI test düzenleyicisini açın](../test/media/cuit_datadriven_opentesteditor.png)

    - UI eylemini seçin ve karşılık gelen UI denetim eşlemesini gözlemleyin. Eşlemenin koda nasıl karşılık geldiğini (örneğin,) unutmayın `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button` .

         ![Koda yardımcı olması için kodlanmış UI test düzenleyicisini kullanın](../test/media/cuit_datadriven_testeditor.png)

    - **Özellikler** penceresinde **arama özellikleri**' ni açın. Arama özellikleri **adı** değeri, veri kaynağı kullanılarak kodda ne tür bir şekilde işlenemekte. Örneğin, her bir `SearchProperties` veri satırının ilk sütunundaki değerler atanmaktadır: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();` . Bu test, üç yineleme için arama özelliğinin **ad** değerini 3, sonra 5 ve son 6 olarak değiştirir.

         ![Kodlamaya yardımcı olması için arama özelliklerini kullanın](../test/media/cuit_datadriven_searchproperties.png)

3. Çözümü kaydedin.

### <a name="step-5---run-the-data-driven-test"></a>5. adım-veri tabanlı testi çalıştırma

Testi yeniden çalıştırarak testin veri odaklı olduğunu doğrulayın.

Test çalıştırmanın,.csvdosyasındaki değerleri kullanarak üç *yinelemeden.csv* gerekir. Doğrulama da çalışmalı ve test Test Gezgini'nde geçirildi olarak görüntüleniyor.

## <a name="q--a"></a>Soru-Cevap

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>SQL Express veya XML gibi diğer veri kaynağı türleri için veri kaynağı öznitelikleri nedir?

**A:** Aşağıdaki tabloda yer alan örnek veri kaynağı dizelerini kodunuza kopyalayıp gerekli özelleştirmeleri yaparak kullanabilirsiniz.

**Veri Kaynağı Türleri ve Öznitelikleri**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Team Foundation Server'de test Team Foundation Server

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap.Designer dosyasındaki kodu neden değiştire miyim?

**A:** UIMap - Kodlanmış UI Test Oluşturucusu'nu kullanarak her kod sanız *UIMapDesigner.cs* dosyasında yaptığınız tüm kod değişikliklerinin üzerine yazılır. Bu örnekte ve çoğu durumda, bir testin veri kaynağını kullanmasına olanak sağlamak için gereken kod değişiklikleri testin kaynak kod dosyasında *(yani CodedUITest1.cs) kullanılabilir.*

Kayıtlı bir yöntemi değiştirmeniz gerekirse *UIMap.cs* dosyasına kopyalayıp yeniden adlandırmanız gerekir. *UIMap.cs* dosyası, *UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış *UITest.cs* dosyasındaki özgün yönteme başvuruyu kaldırmanız ve yeniden adlandırılan yöntem adıyla değiştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uımap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi yöntemler](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
