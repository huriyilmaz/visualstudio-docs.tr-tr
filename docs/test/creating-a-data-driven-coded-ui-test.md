---
title: Veri odaklı kodlanmış UI test öğreticisi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101b678606febd7cc2a7e2f9cee0c8c281289c9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665091"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Veri odaklı kodlanmış UI testi oluşturma

Farklı koşulları test etmek için testlerinizi farklı parametre değerleriyle birden çok kez çalıştırabilirsiniz. Veri odaklı kodlanmış UI testleri bunu yapmanın kolay bir yoludur. Parametre değerlerini bir veri kaynağında tanımlarsınız ve veri kaynağındaki her satır, kodlanmış UI testinin bir yinelemedir. Testin genel sonucu, tüm yinelemelerin sonucunu temel alır. Örneğin, bir test yinelemesi başarısız olursa, genel test sonucu başarısız olur.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="create-a-test-project"></a>Test projesi oluşturma

Bu örnek, Windows Hesaplayıcı uygulamasında çalışan kodlanmış bir UI testi oluşturur. İki sayıyı birbirine ekler ve toplamın doğru olduğunu doğrulamak için bir onaylama kullanır. Ardından, iki sayının onaylama ve parametre değerleri, veri odaklı ve virgülle ayrılmış değer ( *. csv*) dosyasında depolanacak şekilde kodlanır.

### <a name="step-1---create-a-coded-ui-test"></a>1\. adım-kodlanmış UI testi oluşturma

1. Bir proje oluşturun.

    ![Kodlanmış UI test projesi oluşturma](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > **KODLANMıŞ UI testi proje** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. **Eylemleri kaydetmeyi**seçin.

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

5. Testin çalıştığını doğrulamak için `AddNumbers()` yöntemini kullanın. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: **Ctrl** +**R**,**t**).

    Test **Gezgini** penceresinde başarılı veya başarısız olan testin görüntülendiğini gösteren test sonucu. Test Gezgini penceresini açmak için, **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

6. Bir veri kaynağı, beklenen değerleri doğrulamak için test tarafından kullanılan onaylama parametre değerleri için de kullanılabilir —, iki sayının toplamının doğru olduğunu doğrulamak için bir onaylama ekleyelim. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **KODLANMıŞ UI testi Için kod oluştur**' u seçin ve **kodlanmış UI Test Oluşturucusu**' nu kullanın.

    Toplamı görüntüleyen hesaplayıcıda metin denetimini eşleyin.

    ![UI metin denetimini eşleme](../test/media/cuit_datadriven_addassertion.png)

7. Toplamın değerinin doğru olduğunu doğrulayan bir onaylama ekleyin. **3** değerine sahip **Görüntümetni** özelliğini seçin ve ardından **onay Ekle**' yi seçin. **Areeşitse** karşılaştırıcısı ' nı kullanın ve karşılaştırma değerinin **3**olduğunu doğrulayın.

    ![Onaylama işlemi yapılandırma](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Onaylama 'yı yapılandırdıktan sonra, oluşturucuyu yeniden kod oluşturun. Bu, doğrulama için yeni bir yöntem oluşturur.

    ![Onaylama yöntemini oluşturma](../test/media/cuit_datadriven_assertiongencode.png)

    @No__t_0 yöntemi `AddNumbers` yönteminin sonuçlarını doğruladığından, kodu kod bloğunun en altına taşıyın.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Testin `ValidateSum()` yöntemini kullanarak çalıştığını doğrulayın. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır**' ı seçin. (Klavye kısayolu: **Ctrl** +**R**,**t**).

     Bu noktada, tüm parametre değerleri, yöntemlerinde sabitler olarak tanımlanmıştır. Ardından, test veri odaklı bir veri kümesi oluşturalım.

### <a name="step-2---create-a-data-set"></a>2\. adım-veri kümesi oluşturma

1. *Data. csv*adlı dataDrivenSample projesine bir metin dosyası ekleyin.

     ![Projeye virgülle ayrılmış bir değer dosyası ekleyin](../test/media/cuit_datadriven_addcsvfile.png)

2. *. Csv* dosyasını aşağıdaki verilerle doldurun:

    |Num1|Num2|Toplamlarını|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Veriler eklendikten sonra, dosya aşağıdaki gibi görünmelidir:

     ![. Csv dosyasını verilerle doldurma](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. Doğru kodlamayı kullanarak *. csv* dosyasını kaydetmeniz önemlidir. **Dosya** menüsünde **Gelişmiş Kaydet seçeneklerini** belirleyin ve kodlama olarak **Unicode (imzasız UTF-8 65001)** seçeneğini belirleyin.

4. *. Csv* dosyası, çıkış dizinine kopyalanmalıdır veya test çalıştırılamıyor. Kopyalamak için **Özellikler** penceresini kullanın.

     ![. Csv dosyasını dağıtma](../test/media/cuit_datadriven_deploycsvfile.png)

     Veri kümesi oluşturulduğuna göre, artık verileri teste bağlayalim.

### <a name="step-3---add-data-source-binding"></a>3\. adım-veri kaynağı bağlamayı ekleme

1. Veri kaynağını bağlamak için, test yönteminin hemen üzerinde yer alan var olan `[TestMethod]` özniteliği içine bir `DataSource` özniteliği ekleyin.

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
    > XML, SQL Express ve Excel gibi diğer veri kaynağı türlerini kullanma örnekleri için bkz. soru-& cevap bölümünde [veri kaynağı öznitelik örnekleri](#CreateDataDrivenCUIT_QA_DataSourceAttributes) .

2. Testi çalıştırın.

     Testin üç yineleme aracılığıyla çalıştığını unutmayın. Bunun nedeni, bağlanan veri kaynağının üç satırlık veri içereceğinden oluşur. Bununla birlikte, testin hala sabit parametre değerlerini kullandığını ve her seferinde 3 ' ten 2 ' ye kadar 1 + 2 ekliyor olduğunu fark edeceksiniz.

     Daha sonra, veri kaynağı dosyasındaki değerleri kullanmak için testi yapılandıracağız.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>4\. adım-kodlanmış UI testinde verileri kullanma

1. *CodedUITest.cs* dosyasının en üstüne `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` ekleyin:

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

2. @No__t_1 yöntemine, veri kaynağından değerleri uygulayacak `TestContext.DataRow[]` ekleyin. Veri kaynağı değerleri, `SearchProperties` denetimleri kullanılarak UIMap denetimlerine atanan sabitleri geçersiz kılar:

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

    - UI eylemini seçin ve karşılık gelen UI denetim eşlemesini gözlemleyin. Eşlemenin koda nasıl karşılık geldiğini (örneğin, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`) unutmayın.

         ![Koda yardımcı olması için kodlanmış UI test düzenleyicisini kullanın](../test/media/cuit_datadriven_testeditor.png)

    - **Özellikler** penceresinde **arama özellikleri**' ni açın. Arama özellikleri **adı** değeri, veri kaynağı kullanılarak kodda ne tür bir şekilde işlenemekte. Örneğin, `SearchProperties` her bir veri satırının ilk sütunundaki değerler atanmaktadır: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Bu test, üç yineleme için arama özelliğinin **ad** değerini 3, sonra 5 ve son 6 olarak değiştirir.

         ![Kodlamaya yardımcı olması için arama özelliklerini kullanın](../test/media/cuit_datadriven_searchproperties.png)

3. Çözümü kaydedin.

### <a name="step-5---run-the-data-driven-test"></a>5\. adım-veri tabanlı testi çalıştırma

Testi yeniden çalıştırarak testin artık veri odaklı olduğunu doğrulayın.

Test çalıştırmasını, *. csv* dosyasındaki değerleri kullanarak üç yineleme aracılığıyla görmeniz gerekir. Doğrulamanın de çalışması ve testin test Gezgini 'nde geçti olarak görüntülenmesi gerekir.

## <a name="q--a"></a>soru-cevap &

### <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>SQL Express veya XML gibi diğer veri kaynağı türleri için veri kaynağı öznitelikleri nelerdir?

Y **:** Aşağıdaki tabloda bulunan örnek veri kaynağı dizelerini kodunuza kopyalayarak ve gerekli özelleştirmeleri yaparak kullanabilirsiniz.

**Veri kaynağı türleri ve öznitelikleri**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Team Foundation Server 'de test çalışması

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap. Designer dosyasındaki kodu neden değiştiremiyorum?

Y **:** *UIMapDesigner.cs* dosyasında yaptığınız herhangi bir kod değişikliği, UıMAP kodlu UI test oluşturucusunu kullanarak kod oluşturduğunuzda üzerine yazılır. Bu örnekte ve çoğu durumda, bir testin bir veri kaynağını kullanmak için gereken kod değişiklikleri testin kaynak kodu dosyasına (yani, *CodedUITest1.cs*) yapılabilir.

Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, *UIMap.cs* dosyasına kopyalamanız ve yeniden adlandırmanız gerekir. *UIMap.cs* dosyası, *UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış *UITest.cs* dosyasındaki özgün yönteme başvuruyu kaldırmanız ve yeniden adlandırılmış yöntem adıyla değiştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen konfigürasyonlar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)