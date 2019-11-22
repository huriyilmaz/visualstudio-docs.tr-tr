---
title: Kodlanmış UI Testleriyle Windows UWP ve 8,1 Phone uygulamalarını test etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f2ac13b62dcc522626fde92b1b29cac9873edec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301839"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle Windows UWP ve 8.1 Phone Uygulamalarını Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mobil cihazda veya Öykünücülerde ve XAML tabanlı Phone 8,1 uygulamalarında çalışan UWP uygulamalarına yönelik UI testleri oluşturmak için bu kılavuzu kullanın.

## <a name="create-a-simple-windows-phone-app"></a>Basit bir Windows Phone uygulaması oluşturma

1. Görsel C# veya Visual Basic şablonu kullanarak boş bir Windows Phone uygulaması için yeni bir proje oluşturun.

     ![Yeni bir Windows Phone uygulaması oluşturma](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")

2. Çözüm Gezgini, MainPage. xaml ' yi açın. Araç kutusundan bir düğme denetimini ve bir TextBox denetimini tasarım yüzeyine sürükleyin.

     ![MainPage. xaml 'e öğelerse ekleme](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")

3. Özellikler penceresi düğme denetimini adlandırın.

     ![Düğme denetimini adlandırın](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")

4. TextBox denetimini adlandırın.

     ![TextBox denetimini adlandırın](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")

5. Tasarımcı yüzeyinde, düğme denetimine çift tıklayın ve aşağıdaki kodu ekleyin:

    ```csharp
    private void button_Click_1(object sender, RoutedEventArgs e)
    {
        this.textBox.Text = this.button.Name;
    }

    ```

    ```vb
    Public NotInheritable Class MainPage
        Inherits Page

        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click
            Me.textBox.Text = Me.button.Name
        End Sub
    End Class
    ```

6. Windows Phone uygulamanızı öykünücüsünde çalıştırmak ve çalıştığını doğrulamak için F5 tuşuna basın.

     ![Windows Phone uygulamasını çalıştırma](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")

7. Öykünücüyü kapatın.

## <a name="deploy-the-windows-phone-app"></a>Windows Phone uygulamasını dağıtma

1. Kodlanmış bir UI testinin bir uygulamanın denetimlerini eşleştirebilmesi için uygulamayı dağıtmanız gerekir.

     ![Windows Phone uygulamasını dağıtma](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")

     Öykünücü başlatılır. Uygulama artık test için kullanılabilir.

     ![Öykünücü üzerinde dağıtılan uygulama](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")

     Kodlanmış UI testinizi oluştururken öykünücüyü çalışır durumda tutun.

## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Windows Phone uygulaması için kodlanmış UI testi oluşturma

[Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri oluşturma Nasıl yaparım??](#uwpapps)

1. Windows Phone uygulamayla çözüme yeni bir kodlanmış UI test projesi ekleyin.

    ![Windows Phone için yeni kodlanmış UI testi oluştur](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")

2. İnce artı aracını kullanarak UI haritasını düzenlemeyi seçin.

    ![Çapraz&#45;saç aracını kullanarak kodlanmış UI testi oluşturun.](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")

3. Uygulamayı seçmek için ince artı aracını kullanın, daha sonra uygulamayı testte başlatmak için kullanılacak olan **AutomationId** özelliğinin değerini kopyalayın.

    ![Uygulamanın AutomationId değerini kopyalayın](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")

4. Öykünücüsünde uygulamayı başlatın ve düğme denetimini seçmek için ince artı aracını kullanın. Ardından UI denetim haritasına düğme denetimini ekleyin.

    ![Denetimleri eşlemek için&#45;ince artı aracını kullanma](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")

5. TextBox denetimini UI denetim haritasına eklemek için önceki adımı yineleyin.

    ![Çapraz&#45;saç aracını ve harita TextBox denetimini kullanma](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")

6. UI denetim haritasında değişiklikler için kod oluşturmak üzere kod oluşturun.

    ![Oluşturucuyu kod üretme](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")

7. TextBox denetimini seçmek için ince artı aracını kullanın ve **Text** özelliğini seçin.

    ![Metin özelliğini seçin](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")

8. Onay ekleyin. Değerin doğru olduğunu doğrulamak için testte kullanılacaktır.

    ![Teste onaylama ekleme](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")

9. Onaylama yöntemi için kod ekleyin ve oluşturun.

     ![Onaylama için kod oluştur](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")

10. **Visual C#**

     Çözüm Gezgini, onaylama yöntemi ve denetimleri için yeni eklediğiniz kodu görüntülemek üzere UIMap.Designer.cs dosyasını açın.

     **Visual Basic**

     Çözüm Gezgini, CodedUITest1. vb dosyasını açın. CodedUITestMethod1 () test yöntemi kodunda, `Me.UIMap.AssertMethod1()` otomatik olarak eklenen onaylama yöntemine yapılan çağrıya sağ tıklayın ve **Tanıma Git**' i seçin. Bu işlem, onay yöntemi ve denetimler için eklediğiniz kodu görüntüleyebilmeniz için, kod düzenleyicisinde UIMap. Designer. vb dosyasını açar.

    > [!WARNING]
    > UIMap.designer.cs veya UIMap. Designer. vb dosyasını doğrudan değiştirmeyin. Bunu yaparsanız, dosya üzerinde yapılan değişikliklerin test her oluşturulduğunda üzerine yazılır.

     **Onaylama yöntemi**

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Denetimler**

    ```csharp
    #region Properties
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues
    {
        get
        {
            if ((this.mAssertMethod1ExpectedValues == null))
            {
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();
            }
            return this.mAssertMethod1ExpectedValues;
        }
    }

    public UIApp1Window UIApp1Window
    {
        get
        {
            if ((this.mUIApp1Window == null))
            {
                this.mUIApp1Window = new UIApp1Window();
            }
            return this.mUIApp1Window;
        }
    }
    #endregion

    #region Fields
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;

    private UIApp1Window mUIApp1Window;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
            End If
            Return Me.mUITextBoxEdit
        End Get
    End Property
    #End Region

    #Region "Fields"
    Private mUIButtonButton As XamlButton

    Private mUITextBoxEdit As XamlEdit
    #End Region
    ```

11. Çözüm Gezgini, CodedUITest1.cs veya CodedUITest1. vb dosyasını açın. Artık, testi çalıştırmak için gereken eylemler için CodedUTTestMethod1 yöntemine kod ekleyebilirsiniz. Kodu eklemek için UIMap 'e eklenen denetimleri kullanın:

    1. Daha önce panoya kopyaladığınız Otomasyon KIMLIĞI özelliğini kullanarak Windows Phone uygulamasını başlatın:

       ```csharp
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

       ```vb
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");
       ```

    2. Düğme denetimine dokunmak için bir hareket ekleyin:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)
       ```

    3. Otomatik olarak oluşturulan onay yöntemine yapılan çağrının, uygulamayı başlattıktan ve düğme üzerindeki hareket ' e dokunduktan sonra geldiğini doğrulayın:

       ```csharp
       this.UIMap.AssertMethod1();
       ```

       ```vb
       Me.UIMap.AssertMethod1()
       ```

       Kod eklendikten sonra, CodedUITestMethod1 test yöntemi aşağıdaki gibi görünmelidir:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.

        // Launch the app.
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '
            ' Launch the app.
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

## <a name="run-the-coded-ui-test"></a>Kodlanmış UI testini çalıştırma

1. Testinizi oluşturun ve test Gezgini 'ni kullanarak testi çalıştırın.

     ![Test Gezgini 'ni kullanarak test oluşturma ve çalıştırma](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")

     Windows Phone uygulama başlatılır, düğmeye dokunmayla gerçekleştirilecek eylem tamamlanır ve TextBox 'ın Text özelliği, onay yöntemi kullanılarak doldurulur ve onaylanır.

     ![Winodws telefon testini çalıştırma](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")

     Test tamamlandıktan sonra test Gezgini testin geçtiğini onaylar.

     ![Test Gezgini sonuçları](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")

## <a name="TestingPhoneAppsCodedUI_DataDriven"></a>Windows Phone uygulamalarda veri odaklı kodlanmış UI testlerini kullanma
 Farklı koşulları test etmek için, kodlanmış bir UI testi, farklı veri kümeleriyle birden çok kez çalıştırılabilir.

 Windows Phone için veri odaklı kodlanmış UI testleri, bir test yönteminde DataRow özniteliği kullanılarak tanımlanır. Aşağıdaki örnekte x ve y, ilk yineleme için 1 ve 2 değerlerini ve testin ikinci yinelemesi için-1 ve-2 değerlerini kullanır.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

## <a name="q--a"></a>Soru - Yanıt

### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>S: UI denetimlerini eşlemek için Windows Phone uygulamasını Öykünücüde dağıtmalıyım?
 Y: Evet, kodlanmış UI test **Oluşturucusu bir öykünücü**çalışıyor ve uygulamanın buna dağıtılması gerekir. Aksi takdirde, çalışan öykünücü bulunamadığını belirten bir hata mesajı oluşturur.

### <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a>S: testler yalnızca öykünücü üzerinde yürütülebilir mi veya fiziksel bir cihaz da kullanabilir miyim?
 **A**: her iki seçenek de desteklenir. Test yürütmesi için hedef, öykünücü türü değiştirilerek veya cihaz araç çubuğunda cihaz seçilerek seçilir. Cihaz seçildiyse, bir telefon mavi cihazının makinenin USB bağlantı noktalarından birine bağlanması gerekir.

 ![Öykünücü sürümünü veya phsscial cihazını seçin](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>S: kodlanmış UI testi iletişim kutusu için kod üret içinde, kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?
 Y **: kayıt**seçeneği Windows Phone uygulamalar için desteklenmez.

### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>S: WinJS, Silverlight veya HTML5 tabanlı Windows Phone Uygulamalarım için kodlanmış UI testi oluşturabilir miyim?
 Y **: Hayır**, yalnızca XAML tabanlı uygulamalar desteklenir.

### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>S: Windows 8.1 veya Windows 10 çalıştırmayan bir sistemde Windows Phone Uygulamalarım için kodlanmış UI testleri oluşturabilir miyim?
 Y **: Hayır**, kodlanmış UI testi proje şablonları yalnızca Windows 8.1 ve Windows 10 ' da kullanılabilir. Evrensel Windows Platformu (UWP) uygulamaları için Otomasyon oluşturmak üzere Windows 10 gerekir.

<a name="uwpapps"></a>
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>S: Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri oluşturma Nasıl yaparım??
 **A**: UWP uygulamanızı test ettiğiniz platforma bağlı olarak, aşağıdaki yollarla kodlanmış UI test projesi oluşturun:

- Yerel makine üzerinde çalışan bir UWP uygulaması, mağaza uygulaması olarak çalışacaktır. Bunu test etmek için **KODLANMıŞ UI test projesi (Windows)** şablonunu kullanmanız gerekir. Yeni bir proje oluşturduğunuzda bu şablonu bulmak için **Windows**, **Universal** düğümüne gidin. Veya **Windows**, **Windows 8**, **Windows** düğümüne gidin.

- Mobil cihaz veya öykünücü üzerinde çalışan bir UWP uygulaması, bir telefon uygulaması olarak çalışacaktır. Bunu test etmek için **KODLANMıŞ UI test projesi (Windows Phone)** şablonunu kullanmanız gerekir. Yeni bir proje oluşturduğunuzda bu şablonu bulmak için **Windows**, **Universal** düğümüne gidin. Veya **Windows**, **windows 8**, **Windows Phone** düğümüne gidin.

  Projeyi oluşturduktan sonra, test yazma işleminden daha önce olduğu gibi kalır.

### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>S: öykünücü dışında olan denetimleri seçebilir miyim?
 Y **: Hayır**, Oluşturucu bu güncelleştirmeleri algılamaz.

### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>S: bir fiziksel telefon cihazını kullanarak denetimleri eşlemek için kodlanmış UI test oluşturucusunu kullanabilir miyim?
 Y **: Hayır**, Oluşturucu yalnızca uygulamanız öykünücüye DAĞıTıLMıŞSA Kullanıcı arabirimi öğelerini eşleyebilirsiniz.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>S: UIMap. Designer dosyasındaki kodu neden değiştiremiyorum?
 Y: UıMAP kodlu UI test oluşturucuyu kullanarak her kod oluşturduğunuzda UIMapDesigner.cs dosyasında yaptığınız tüm kod değişikliklerinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.

### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>S: komut satırından Windows Phone uygulamamda kodlanmış bir UI testi çalıştırabilir miyim?
 Y **: Evet**, test yürütmesi için hedef cihazı belirtmek üzere bir runsettings dosyası kullanın. Örneğin:

 **VSTest. Console. exe "pathToYourCodedUITestDll"/Settings: devicetarget. runsettings**

 Örnek runsettings dosyası:

```
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
<MSPhoneTest>
<!--to specify test execution on device, use a TargetDevice option as follows-->
<TargetDevice>Device</TargetDevice>
<!--to specify an emulator instead, use a TargetDevice option like below-->
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->
</MSPhoneTest>
</RunSettings>
```

### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>S: XAML tabanlı Windows Mağazası uygulamaları ve Windows Phone uygulamaları için kodlanmış UI testleri arasındaki farklar nelerdir?
 Y **: Bunlar**bazı önemli farklılıklardır:

|Özellik|Windows Mağazası uygulamaları|Windows Phone uygulamaları|
|-------------|------------------------|------------------------|
|Testleri çalıştırmak için hedef|Yerel veya uzak bilgisayar. Testleri çalıştırmak için otomatikleştirilmiş bir test çalışması kullandığınızda, uzak bilgisayarlar belirtilebilir. Bkz. [Microsoft Test Yöneticisi bir test çalışmasını otomatikleştirme](https://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Öykünücü veya cihaz. Bkz. [soru-cevap yalnızca öykünücü üzerinde yürütülebilir mi veya bir fiziksel cihaz de kullanabilir miyim?](#TestingPhoneAppsCodedUI_EmulatorDevice) bu konuda.|
|Komut satırından Yürüt|Hedef belirtmek için ayarlar dosyası gerekli değil.|Hedef belirtmek için runsettings dosyası gereklidir.|
|Kabuk denetimleri için özel sınıflar|[Directuiconcontrol](/previous-versions/dn248208(v=vs.140))|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|
|XAML uygulamasındaki WebView denetimi|HTML öğeleriyle etkileşim kurmak için HTML * özelleşmiş sınıfları kullanıyorsanız desteklenir. Bkz. <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Desteklenmez.|
|MTM 'den otomatikleştirilmiş testleri yürütme|Desteklenen.|Desteklenmez.|
|Veri odaklı testler|Dış veri kaynaklarını kullanma ve bir test yönteminde DataSource özniteliğini kullanma hakkında bilgi için bkz. [veri odaklı testler](../test/creating-a-data-driven-coded-ui-test.md) .|Veriler, bir test yönteminde DataRow özniteliği kullanılarak satır içi olarak belirtilir. Bu konudaki [Windows Phone uygulamalarda veri odaklı KODLANMıŞ UI testlerini kullanma](#TestingPhoneAppsCodedUI_DataDriven) konusuna bakın.|

## <a name="external-resources"></a>Dış kaynaklar
 Microsoft Visual Studio uygulama yaşam döngüsü yönetimi blogu: [XAML tabanlı Windows Phone uygulamalarını test etmek Için kodlanmış Kullanıcı arabirimini kullanma](https://devblogs.microsoft.com/devops/using-coded-ui-to-test-xaml-based-windows-phone-apps/#comments)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
