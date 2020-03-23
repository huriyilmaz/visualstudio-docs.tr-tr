---
title: Veri Odaklı Kodlu UI Testi öğretici
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ada1f297bbb30fbe636042c87aae42849c1b6b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595364"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Veri tabanlı kodlu ui testi oluşturma

Farklı koşulları sınamak için, testlerinizi farklı parametre değerleriyle birden çok kez çalıştırabilirsiniz. Veri tabanlı kodlu webs testleri bunu yapmak için kullanışlı bir yoldur. Bir veri kaynağında parametre değerlerini tanımlarsınız ve veri kaynağındaki her satır kodlanmış UI testinin yinelemesidir. Testin genel sonucu, tüm yinelemelerin sonucuna göre olacaktır. Örneğin, bir test yinelemebaşarısız olursa, genel test sonucu başarısızlıktır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise
- Kodlanmış UI test bileşeni

## <a name="create-a-test-project"></a>Test projesi oluşturma

Bu örnek, Windows Hesap Makinesi uygulamasında çalışan kodlanmış bir Kullanıcı Birleşme süreni oluşturdu. İki sayıyı bir araya getirir ve toplamın doğru olduğunu doğrulamak için bir iddia kullanır. Daha sonra, iki sayının ayırış ve parametre değerleri veri odaklı olacak şekilde kodlanır ve virgülle ayrılmış bir değer *(.csv)* dosyasında depolanır.

### <a name="step-1---create-a-coded-ui-test"></a>Adım 1 - Kodlanmış bir UI testi oluşturma

1. Bir proje oluşturun.

    ![Kodlanmış bir UI test projesi oluşturma](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > **Kodlanmış UI Test Project** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

2. Eylemleri **kaydetmeyi**seçin.

    ![Eylemleri kaydetmeyi seçin](../test/media/cuit_datadriven_generatecodedialog.png)

3. Hesap makinesi uygulamasını açın ve testi kaydetmeye başlayın.

    ![Eylemleri kaydetme](../test/media/cuit_datadriven_cuitbuilder.png)

4. 1 artı 2 ekleyin, kaydediciyi duraklatın ve test yöntemini oluşturun. Daha sonra bu kullanıcı girişideğerlerini bir veri dosyasındaki değerlerle değiştiririz.

    ![Test yöntemi oluşturma](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Test oluşturucuyu kapatın. Yöntem teste eklenir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Testin `AddNumbers()` çalıştığını doğrulamak için yöntemi kullanın. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır'ı**seçin. (Klavye kısayolu: **Ctrl**+**R**,**T**).

    Testin geçip geçemediğini veya başarısız olup olmadığını gösteren test sonucu **Test Gezgini** penceresinde görüntülenir. Test Gezgini penceresini açmak **için, Test** menüsünden **Windows'u** seçin ve ardından **Sına Gezgini'ni**seçin.

6. Beklenen değerleri doğrulamak için test tarafından kullanılan bir veri kaynağı da test tarafından kullanılan değer parametre değerleri için de kullanılabildiği için, iki sayının toplamının doğru olduğunu doğrulamak için bir iddia ekleyelim. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Kodlu UI Testi için Kod Oluştur'u**seçin ve ardından **Kodlanmış UI Test Oluşturucu'yu kullanın.**

    Toplamı görüntüleyen hesap makinesinde metin denetimini eşle.

    ![Kullanıcı Aracı metin denetimini haritala](../test/media/cuit_datadriven_addassertion.png)

7. Toplamın değerinin doğru olduğunu doğrulayan bir iddia ekleyin. **3** değerine sahip **DisplayText** özelliğini seçin ve ardından **İddia Ekle'yi**seçin. **AreEqual** karşıattını kullanın ve karşılaştırma değerinin **3**olduğunu doğrulayın.

    ![İddiayı yapılandırma](../test/media/cuit_datadriven_builderaddassertion2.png)

8. İddiayı yapılandırıldıktan sonra, oluşturucudan yeniden kod oluşturun. Bu doğrulama için yeni bir yöntem oluşturur.

    ![İddia yöntemini oluşturma](../test/media/cuit_datadriven_assertiongencode.png)

    `ValidateSum` Yöntem `AddNumbers` yöntemin sonuçlarını doğruladığı için, kodun alt bölümüne taşıyın.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. `ValidateSum()` Testin yöntemi kullanarak çalıştığından doğrulayın. İmleci yukarıda gösterilen test yöntemine yerleştirin, sağ tıklama menüsünü açın ve **Testleri Çalıştır'ı**seçin. (Klavye kısayolu: **Ctrl**+**R**,**T**).

     Bu noktada, tüm parametre değerleri kendi yöntemlerinde sabitler olarak tanımlanır. Ardından, test veri odaklı yapmak için bir veri kümesi oluşturalım.

### <a name="step-2---create-a-data-set"></a>Adım 2 - Veri kümesi oluşturma

1. dataDrivenSample projesine *data.csv*adlı bir metin dosyası ekleyin.

     ![Projeye virgülle ayrılmış değer dosyası ekleme](../test/media/cuit_datadriven_addcsvfile.png)

2. *.csv* dosyasını aşağıdaki verilerle doldurma:

    |Sayısal Olarak 1|Sayısal Olarak 2|Toplam|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Verileri ekledikten sonra, dosya aşağıdaki gibi görünmelidir:

     ![.csv dosyasını verilerle doldurma](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. *.csv* dosyasını doğru kodlamayı kullanarak kaydetmek önemlidir. **Dosya** menüsünde **Gelişmiş Kaydet Seçenekleri'ni** seçin ve kodlama olarak **Unicode'u (imzasız UTF-8) - Codepage 65001'i** seçin.

4. *.csv* dosyası, çıktı dizinine kopyalanmalıdır veya test çalıştırılamaz. Kopyalamak için **Özellikler** penceresini kullanın.

     ![.csv dosyasını dağıt](../test/media/cuit_datadriven_deploycsvfile.png)

     Şimdi veri kümesini oluşturduğumuza göre, verileri teste bağlayalım.

### <a name="step-3---add-data-source-binding"></a>Adım 3 - Veri kaynağı bağlama ekleme

1. Veri kaynağını bağlamak için, `DataSource` varolan `[TestMethod]` öznitelik içinde test yönteminin hemen üzerinde bir öznitelik ekleyin.

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
    > XML, SQL Express ve Excel gibi diğer veri kaynağı türlerini kullanma örnekleri için Q & A [bölümündeki veri kaynağı özniteliği örneklerine](#CreateDataDrivenCUIT_QA_DataSourceAttributes) bakın.

2. Testi çalıştırın.

     Testin üç yinelemeden geçtiğine dikkat edin. Bunun nedeni, bağlı olan veri kaynağının üç satır veri içermesidir. Ancak, testin hala sabit parametre değerlerini kullandığını ve her seferinde 3 toplamla 1 + 2 eklediğini de fark edeceksiniz.

     Ardından, testin veri kaynağı dosyasındaki değerleri kullanacak şekilde yapılandırAcağız.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>Adım 4 - Kodlanmış UI testindeki verileri kullanma

1. CodedUITest.cs `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` dosyasının üstüne *CodedUITest.cs* ekleyin:

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

2. Veri `TestContext.DataRow[]` kaynağından değerleri uygulayacak `CodedUITestMethod1()` yöntemi ekleyin. Veri kaynağı değerleri, denetimleri `SearchProperties`kullanarak UIMap denetimlerine atanan sabitleri geçersiz kılar:

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

     Verileri kodlamak için hangi arama özelliklerini bulabilirsiniz, Kodlanmış UI Test Düzenleyicisi'ni kullanın.

    - *UIMap.uitest* dosyasını açın.

         ![Kodlu UI Test Düzenleyicisini Aç](../test/media/cuit_datadriven_opentesteditor.png)

    - UI eylemini seçin ve ilgili UI denetim eşlemeyi gözlemleyin. Eşlemenin koda nasıl karşılık gelir, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`örneğin.

         ![Kodla yardımcı olmak için Kodlu UI Test Düzenleyicisini kullanma](../test/media/cuit_datadriven_testeditor.png)

    - **Özellikler** Penceresinde, **Arama Özelliklerini**açın. Arama özellikleri **Ad** değeri, veri kaynağını kullanarak kodda manipüle edilen değerdir. Örneğin, `SearchProperties` her veri satırının ilk sütunundaki değerler `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`atanır: . Üç yineleme için bu test, arama özelliğinin **Ad** değerini 3, sonra 5 ve son olarak 6 olarak değiştirir.

         ![Kodlamaya yardımcı olmak için arama özelliklerini kullanma](../test/media/cuit_datadriven_searchproperties.png)

3. Çözümü kaydedin.

### <a name="step-5---run-the-data-driven-test"></a>Adım 5 - Veri odaklı testi çalıştırın

Testi yeniden çalıştırarak testin artık veri odaklı olduğunu doğrulayın.

*.csv* dosyasındaki değerleri kullanarak testin üç yineleme de çalıştırışta olduğunu görmeniz gerekir. Doğrulama da çalışmalı ve test Test Gezgini'nde geçmiş gibi gösterilmelidir.

## <a name="q--a"></a>Soru-Cevap

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>SQL Express veya XML gibi diğer veri kaynağı türleri için veri kaynağı öznitelikleri nelerdir?

**A:** Aşağıdaki tablodaki örnek veri kaynağı dizelerini kodunuza kopyalayarak ve gerekli özelleştirmeleri yaparak kullanabilirsiniz.

**Veri Kaynağı Türleri ve Öznitelikleri**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Team Foundation Server'da test çalışması

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?

**A:** *UIMapDesigner.cs* dosyasında yaptığınız tüm kod değişiklikleri, UIMap - Kodlu UI Test Builder kullanarak kod oluşturduğunuz her seferde üzerine yazılır. Bu örnekte ve çoğu durumda, bir veri kaynağını kullanmak için bir testi etkinleştirmek için gereken kod değişiklikleri testin kaynak kodu dosyasına yapılabilir (diğer bir *deyişle, CodedUITest1.cs).*

Kaydedilen bir yöntemi değiştirmeniz gerekiyorsa, dosyayı *UIMap.cs* kopyalamanız ve yeniden adlandırmanız gerekir. *UIMap.cs* *dosyası, UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış *UITest.cs* dosyasındaki özgün yönteme yapılan başvuruyu kaldırmanız ve yeniden adlandırılmış yöntem adı ile değiştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uımap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış Ara Birimi testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
