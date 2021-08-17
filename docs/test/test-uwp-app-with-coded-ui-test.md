---
title: Kodlanmış ui testiyle UWP uygulamasını test edin
description: Test etmek ve kodlanmış ui testi oluşturmak için bir UWP uygulaması oluşturarak Universal Windows Platform uygulaması için kodlanmış ui testi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 31de252002b8fc4dd3f23d253ac259fcb1000d15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092338"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>UWP uygulamasını test etmek için kodlanmış ui testi oluşturma

Bu makalede, Universal Windows Platform (UWP) uygulaması için kodlanmış ui testi oluşturma açıklanmıştır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Test etmek için UWP uygulaması oluşturma

İlk adım, testi çalıştırmak için basit bir UWP uygulaması oluşturmak.

1. Bu Visual Studio Visual C# veya Windows için Boş Uygulama **(Evrensel Windows)** şablonunu kullanarak yeni bir Visual Basic.

   ::: moniker range="vs-2017"

   ![Boş uygulama Evrensel Windows şablonu](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. Yeni **Evrensel Platform Windows Platform Project** iletişim kutusunda, varsayılan platform **sürümlerini** kabul etmek için Tamam'ı seçin.

1. **'Çözüm Gezgini** *MainPage.xaml'i açın.*

   Dosya, dosyasında **XAML Tasarımcısı.**

1. Bir düğme denetimi ve metin kutusu denetimi araç **kutusundan tasarım** yüzeyine sürükleyin.

     ![UWP uygulamasını tasarlama](../test/media/toolbox-controls.png)

1. Denetimlere adlar verme. Metin kutusu denetimi seçin ve özellikler **penceresine** Ad alanına **textBox** **yazın.** Düğme denetimlerini seçin ve Özellikler **penceresinde** Ad **alanına** **düğmeyi** girin.

1. Düğme denetimine çift tıklayın ve aşağıdaki kodu yönteminin gövdesine `Button_Click` ekleyin. Bu kod, daha sonra oluşturacağız kodlanmış UI testiyle doğrulamamız gereken bir şey vermek için metin kutusundaki metni düğme denetimi adı olarak ayarlar.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Uygulamayı **çalıştırmak için Ctrl** + **F5'e** basın. Aşağıdakine benzer bir şey görmeniz gerekir:

   ![Düğme ve metin kutusu ile UWP uygulaması](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Çözüme bir test projesi eklemek için, Çözüm Gezgini'de **çözüme** sağ tıklayın ve  >  Project.

1. Kodlanmış UI Test **Şablonu (Evrensel Project) şablonunu Windows seçin.**

   ::: moniker range="vs-2017"

   ![Yeni kodlanmış UI test projesi](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Kodlanmış UI Test Project **(Universal Windows)** şablonunu görmüyorsanız, kodlanmış [UI test bileşenini yüklemeniz gerekir.](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)

1. Kodlanmış **UI Testi için Kod Oluştur iletişim kutusunda** Testi el ile **düzenle'yi seçin.**

   ![Kodlanmış UI testi iletişim kutusu için kod oluşturma](../test/media/manually-edit-the-test.png)

1. UWP uygulamanız zaten çalışmıyorsa **Ctrl** F5 tuşlarına basarak + **uygulamayı başlatabilirsiniz.**

1. **İmleci yöntemine yerleştirerek** kodlanmış UI Test Oluşturucusu iletişim kutusunu açın ve ardından Kodlanmış UI Testi Için KodLanmış Ui Test Oluşturucusu'nu `CodedUITestMethod1` **Test**  >    >  **Oluştur'u seçin.**

1. Denetimleri kullanıcı arabirimi denetim haritasına ekleyin. UWP **uygulamasında düğme denetimi seçmek** için Kodlanmış UI Test Oluşturucusu çapraz kıl aracını kullanın. Onay Ekle **iletişim kutusunda** gerekirse KULLANıCı Arabirimi **Denetim** Eşlemesi bölmesini genişletin ve ardından Ui Denetim Eşlemesi'ne **denetim ekle'yi seçin.**

     ![Kullanıcı arabirimi haritasına denetim ekleme](../test/media/add-control-to-ui-control-map.png)

1. Metin kutusu denetimi kullanıcı arabirimi denetim haritasına eklemek için önceki adımı tekrarlayın.

1. Kodlanmış **UI Test Oluşturucusu iletişim kutusunda** Kod Oluştur'u seçin **veya** Ctrl G  + **tuşlarına basın.** Ardından **Oluştur'u** seçerek kullanıcı arabirimi denetim haritasında yapılan değişikliklere kod oluşturun.

     ![Kullanıcı arabirimi haritası için kod oluşturma](../test/media/generate-code-dialog.png)

1. Düğmeye tıkıldığında metin kutusunda yer alan metnin **düğme** olarak değiştiklerini doğrulamak için düğmeye tıklayın.

     ![Metin kutusu değerini ayarlamak için düğme denetimine tıklayın](../test/media/uwp-app-button-textbox.png)

1. Metin kutusu denetiminde metni doğrulamak için onay ekleyin. Çapraz kıllar aracını kullanarak metin kutusu denetimi seçin ve onay ekle iletişim kutusunda **Text** **özelliğini** seçin. Ardından Onay **Ekle'yi seçin veya** Alt A  + **tuşuna basın.** Onay **Hatası İletisi kutusuna Metin** Kutusu **değerinin beklenmeyen olduğunu girin.** ve ardından **Tamam'ı seçin.**

     ![Çapraz kıllar ile metin kutusu seçme ve onay ekleme](../test/media/add-assertion-for-text.png)

1. Onay için test kodu oluşturma. Kodlanmış **UI Test Oluşturucusu iletişim kutusunda** Kod Oluştur'u **seçin.** Kod Oluştur **iletişim kutusunda** Ekle ve **Oluştur'a tıklayın.**

     ![Metin kutusu onaylama için kod oluşturma](../test/media/add-and-generate-assert-method.png)

   Bu **Çözüm Gezgini** assert yöntemi ve denetimleri için eklenen kodu görüntülemek için *UIMap.Designer.cs'yi* açın.

   > [!TIP]
   > Visual Basic kullanıyorsanız *CodedUITest1.vb'yi açın.* Ardından test yöntemi kodunda assert yöntemine yapılan çağrıya sağ tıklayın ve `CodedUITestMethod1()` Tanıma `Me.UIMap.AssertMethod1()` **Git'i seçin.** *UIMap.Designer.vb* kod düzenleyicisinde açılır ve assert yöntemi ve denetimleri için eklenen kodu görüntüebilirsiniz.

    > [!WARNING]
    > *UIMap.designer.cs veya* *UIMap.Designer.vb* dosyalarını doğrudan değiştirmeyin. Bunu yaparsanız, test oluşturulurken değişikliklerinizin üzerine yazılır.

    assert yöntemi şu şekildedir:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Ardından, test etmek istediğiniz [UWP](#create-a-uwp-app-to-test) uygulamasının **AutomationId'lerini** elde etmek gerekir. Uygulamanın Windows **görmek** için Başlat menüsünü açın. Ardından Kodlanmış UI Test Oluşturucusu iletişim kutusundan çapraz kıllar aracı Hedef simgesini sürükleyerek ![ ](media/target-icon.png) uygulamanıza yönelik kutucuğunun üzerine gelin.  Kutucuğun çevresinde mavi bir kutu olduğunda farenizi bırakın.

   ![Çapraz kıl aracı](media/cross-hair-tool.png)

   Onay **Ekle iletişim** kutusu açılır ve uygulamanıza göre **AutomationId** görüntülenir. **AutomationId'ye sağ tıklayın ve** Değeri **Panoya Kopyala'yı seçin.**

   ![Onay Ekle iletişim kutusunda AutomationID](../test/media/automation-id.png)

1. UWP uygulamasını başlatmak için test yöntemine kod ekleyin. Bu **Çözüm Gezgini** *CodedUITest1.cs veya* *CodedUITest1.vb'yi açın.* çağrısının üzerine `AssertMethod1` UWP uygulamasını başlatmak için kod ekleyin:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Örnek koddaki otomasyon kimliğini önceki adımda panoya kopyalanan değerle değiştirin.

   > [!IMPORTANT]
   > P~ gibi karakterleri kaldırmak için otomasyon kimliğinin **başlangıcını kırpın.** Bu karakterleri kırpamazsanız, test uygulamayı `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` başlatmaya çalıştığında bir atar.

1. Ardından, düğmeye tıklamak için test yöntemine kod ekleyin. sonrasındaki `XamlWindow.Launch` satıra, düğme denetimine dokunmak için bir hareket ekleyin:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Kodu ekledikten sonra, test `CodedUITestMethod1` yönteminin tam olarak aşağıdaki gibi görünmesi gerekir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Test projesini derleme ve Test **Gezgini'ni seçerek** **Test**  >  **Gezgini Windows**  >  **açın.**

1. Testi **çalıştırmak için Hepsini** Çalıştır'ı seçin.

   Uygulama açılır, düğmeye tıklar ve metin kutusunun **Text** özelliği doldurulur. assert yöntemi, metin kutusunun Text özelliğini **doğrular.**

   Test tamamlandıktan sonra **Test Gezgini testin** geç olduğunu görüntüler.

   ![Test Gezgini'nde geçen test görüntülemeleri](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>S: Kodlanmış UI Testi için Kod Oluştur iletişim kutusunda neden kodlanmış UI testimi kaydetme seçeneğini göremiyorum?

**A:** Kayıt seçeneği UWP uygulamaları için desteklenmiyor.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>S: WinJS tabanlı UWP uygulamalarım için kodlanmış ui testi oluşturabilir miyim?

**A:** Hayır, yalnızca XAML tabanlı uygulamalar de destekler.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap.Designer dosyasındaki kodu neden değiştire miyim?

**A:** Kodlanmış UI Test Oluşturucusu'nu kullanarak her kod oluşturmada *UIMapDesigner.cs* dosyasında yaptığınız tüm kod **değişikliklerinin üzerine yazılır.** Kayıtlı bir yöntemi değiştirmeniz gerekirse *UIMap.cs* dosyasına kopyalayın ve yeniden adlandırabilirsiniz. *UIMap.cs* dosyası, *UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. *CodedUITest.cs* dosyasındaki özgün yönteme başvuruyu kaldırın ve yeniden adlandırılan yöntem adıyla değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [UWP denetimleri için benzersiz otomasyon özelliklerini ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
