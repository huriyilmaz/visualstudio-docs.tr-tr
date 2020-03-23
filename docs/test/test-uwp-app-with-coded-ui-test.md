---
title: Bir UWP uygulamasını kodlanmış bir UI testiyle test edin
ms.date: 05/31/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: fdd3d98bd848bb6fe679809a58f2e316a316f012
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590364"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>UWP uygulamasını test etmek için kodlanmış bir UI testi oluşturma

Bu makalede, Evrensel Windows Platformu (UWP) uygulaması için kodlanmış bir ui testi nasıl oluşturulacak açıklanmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Test etmek için bir UWP uygulaması oluşturma

İlk adım karşı test çalıştırmak için basit bir UWP uygulaması oluşturmaktır.

1. Visual Studio'da Visual C# veya Visual Basic için **Boş Uygulama (Evrensel Windows)** şablonu kullanarak yeni bir proje oluşturun.

   ::: moniker range="vs-2017"

   ![Boş uygulama Evrensel Windows şablonu](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. Yeni **Evrensel Windows Platformu Projesi** iletişim kutusunda, varsayılan platform sürümlerini kabul etmek için **Tamam'ı** seçin.

1. **Çözüm Explorer**gönderen, *açık MainPage.xaml*.

   Dosya **XAML Tasarımcısı**açılır.

1. Bir düğme denetimini ve textbox denetimini **Toolbox'tan** tasarım yüzeyine sürükleyin.

     ![UWP uygulamasını tasarla](../test/media/toolbox-controls.png)

1. Denetimlere ad verin. Textbox denetimini seçin ve ardından **Özellikler** penceresinde **Ad** alanına **textBox** girin. Düğme denetimini seçin ve ardından **Özellikler** penceresinde **Ad** alanına **düğmesini** girin.

1. Düğme denetimini çift tıklatın ve `Button_Click` yöntemin gövdesine aşağıdaki kodu ekleyin. Bu kod, daha sonra oluştureceğimiz kodlanmış Kullanıcı Arabirimi testi ile doğrulamak için bize bir şeyler vermek için textbox'taki metni düğme denetiminin adına ayarlar.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Uygulamayı çalıştırmak için **Ctrl**+**F5** tuşuna basın. Aşağıdakine benzer bir şey görmeniz gerekir:

   ![Düğme ve metin kutusu ile UWP uygulaması](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Kodlanmış bir UI testi oluşturma

1. Çözüme bir test projesi eklemek için **Çözüm Gezgini'ndeki** çözüme sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

1. **Kodlu UI Test Project (Evrensel Windows)** şablonunu arayın ve seçin.

   ::: moniker range="vs-2017"

   ![Yeni kodlu UI test projesi](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > **Kodlanmış UI Test Project (Evrensel Windows)** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

1. **Kodlanmış UI Testi** için Kod Oluştur iletişim kutusunda, **testi El ile yapılandır'ı**seçin.

   ![Kodlanmış UI test iletişim kutusu için kod oluşturma](../test/media/manually-edit-the-test.png)

1. UWP uygulamanız zaten çalışmıyorsa **Ctrl**+**F5**tuşuna basarak başlatın.

1. İmleci `CodedUITestMethod1` yönteme yerleştirerek ve ardından**Kodlanmış UI Test** > **Kullanımı Kodlu UI Test Oluşturucusu**için **Test** > Oluştur Kodu'nu seçerek **Kodlanmış UI Test Builder** iletişim kutusunu açın.

1. Denetimleri UI denetim haritasına ekleyin. UWP uygulamasındaki düğme denetimini seçmek için **Kodlu UI Test Builder** çapraz saç aracını kullanın. **İddiaları Ekle** iletişim kutusunda, gerekirse **UI Denetim Haritası** bölmesini genişletin ve ardından **UI Denetim Haritası'na denetim ekle'yi**seçin.

     ![UI haritasına denetim ekleme](../test/media/add-control-to-ui-control-map.png)

1. Textbox denetimini Kullanıcı Bira denetim eşlemi'ne eklemek için önceki adımı yineleyin.

1. **Kodlanmış UI Test Oluşturucu** iletişim kutusunda Kod **Oluştur'u** seçin veya **Ctrl**+**G**tuşuna basın. Ardından, **Generate** UI denetim haritasında yapılan değişiklikler için kod oluşturmak için Oluştur'u'nu seçin.

     ![UI haritası için kod oluşturma](../test/media/generate-code-dialog.png)

1. Düğme tıklatıldığında metin kutusundaki metnin **düğmeye** değdiğini doğrulamak için düğmeyi tıklatın.

     ![Textbox değerini ayarlamak için düğme denetimine tıklayın](../test/media/uwp-app-button-textbox.png)

1. Textbox denetimindeki metni doğrulamak için bir iddia ekleyin. Textbox denetimini seçmek için çapraz saç aracını kullanın ve ardından **Ekler** Ek iletişim **kutusundaki Metin** özelliğini seçin. Ardından, **İddia Ekle'yi** seçin veya **Alt**+**A tuşuna**basın. İddia **Hatası** kutusundaki İleti'de Textbox değerini girin **beklenmeyen bir şekilde girin.** ve sonra **Tamam'ı**seçin.

     ![Çapraz saçlı textbox seçin ve iddia ekleyin](../test/media/add-assertion-for-text.png)

1. İddia için test kodu oluşturun. **Kodlanmış UI Test Oluşturucu** iletişim kutusunda **Kod Oluştur'u**seçin. Kod **Oluştur** iletişim kutusunda **Ekle ve Oluştur'u**seçin.

     ![Textbox iddiası için kod oluşturma](../test/media/add-and-generate-assert-method.png)

   **Çözüm Gezgini'nde,** assert yöntemi ve denetimler için eklenen kodu görüntülemek için *UIMap.Designer.cs* açın.

   > [!TIP]
   > Visual Basic kullanıyorsanız *CodedUITest1.vb'i*açın. Daha sonra, `CodedUITestMethod1()` test yöntemi kodunda, assert yöntemine `Me.UIMap.AssertMethod1()` çağrıya sağ tıklayın ve **Tanıma Git'i**seçin. *UIMap.Designer.vb* kod düzenleyicisi açılır ve ileriye alma yöntemi ve denetimleri için eklenen kodu görüntüleyebilirsiniz.

    > [!WARNING]
    > *UIMap.designer.cs* veya *UIMap.Designer.vb* dosyalarını doğrudan değiştirmeyin. Bunu yaparsanız, test oluşturulduğunda değişiklikleriniz üzerine yazılır.

    Assert yöntemi aşağıdaki gibi görünür:

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

1. Daha sonra, test etmek istediğimiz UWP [uygulamasının](#create-a-uwp-app-to-test) **AutomationId'ini** edinmemiz gerekir. Uygulamanın döşemesini görmek için Windows **Başlat** menüsünü açın. Ardından, **kodlu UI** Test](media/target-icon.png) Builder iletişim kutusundaki çapraz saç aracı ![Hedef simgesini uygulamanızın döşemesine sürükleyin. Kutucuğun etrafını mavi bir kutu sardığında farenizi serbest bırakın.

   ![Çapraz saç aleti](media/cross-hair-tool.png)

   **İddiaları Ekle** iletişim kutusu açılır ve uygulamanız için **AutomationId'i** görüntüler. **AutomationId'e** sağ tıklayın ve **Panoya Değer Kopyala'yı**seçin.

   ![Ek Leyne iletişim kutusunda AutomationID](../test/media/automation-id.png)

1. UWP uygulamasını başlatmak için test yöntemine kod ekleyin. **Çözüm Gezgini,** *açık CodedUITest1.cs* veya *CodedUITest1.vb*. Çağrının `AssertMethod1`üzerinde , UWP uygulamasını başlatmak için kod ekleyin:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Örnek koddaki otomasyon kimliğini, önceki adımda panoya kopyaladığınız değerle değiştirin.

   > [!IMPORTANT]
   > **P~** gibi karakterleri kaldırmak için otomasyon kimliğinin başlangıcını kırpın. Bu karakterleri kırpmazsanız, uygulamayı başlatmaya çalıştığında `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` test bir adım atar.

1. Ardından, düğmeyi tıklatmak için test yöntemine kod ekleyin. Sonra `XamlWindow.Launch`satırda, düğme denetimine dokunmak için bir hareket ekleyin:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Kodu ekledikten sonra, `CodedUITestMethod1` tam test yöntemi aşağıdaki gibi görünmelidir:

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

1. Test projesini oluşturun ve ardından **Test** > **Test Windows** > **Test Gezgini'ni**seçerek Test **Gezgini'ni** açın.

1. Testi çalıştırmak için **Tümünü Çalıştır'ı** seçin.

   Uygulama açılır, düğme dinlenir ve textbox'ın **Metin** özelliği doldurulur. Öne koyma yöntemi textbox'ın **Metin** özelliğini doğrular.

   Test tamamlandıktan sonra, **Test Gezgini** testin geçtiğini gösterir.

   ![Test Gezgini'nde geçmiş test ekranları](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>S: Kodlanmış UI Testi mi kodlanmış uy testimi kodlanmış bir UI Testi iletişim kutusu için Kod Oluşturma Kodu'na kaydetme seçeneğini neden göremiyorum?

**C**: UWP uygulamaları için kaydetme seçeneği desteklenmez.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>S: WinJS'e dayalı UWP uygulamalarım için kodlanmış bir UI testi oluşturabilir miyim?

**C**: Hayır, yalnızca XAML tabanlı uygulamalar desteklenir.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?

**C**: *UIMapDesigner.cs* dosyasında yaptığınız tüm kod **değişiklikleri, Kodlu UI Test Builder'ı**kullanarak her kod oluşturduğunuzda üzerine yazılır. Kaydedilmiş bir yöntemi değiştirmeniz gerekiyorsa, *UIMap.cs* dosyasına kopyalayın ve yeniden adlandırın. *UIMap.cs* *dosyası, UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. *CodedUITest.cs* dosyasındaki özgün yönteme başvuruyu kaldırın ve yeniden adlandırılmış yöntem adı ile değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [UWP denetimleri için benzersiz otomasyon özellikleri ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
