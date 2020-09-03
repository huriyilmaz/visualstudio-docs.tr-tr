---
title: Kodlanmış UI Testleriyle Windows UWP ve 8,1 mağaza uygulamalarını test edin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce4c6ceec9489abcd3573c126aefe98a268187c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660438"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle Windows UWP ve 8.1 Mağaza Uygulamalarını Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWP uygulamaları ve XAML tabanlı mağaza 8,1 uygulamaları için UI testleri oluşturmak için bu kılavuzu kullanın.

## <a name="create-a-simple-windows-store-app"></a>Basit bir Windows Mağazası uygulaması oluşturma

1. XAML tabanlı Windows Mağazası uygulamanız için kodlanmış UI testlerini çalıştırmak istiyorsanız, [her bir denetimi tanımlayan benzersiz bir Otomasyon özelliği ayarlamanız](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)gerekir.

     **Araçlar** menüsünde **Seçenekler** ' in üzerine gelin ve ardından **metin Düzenleyicisi**, sonra **xaml**ve son ' u seçin **Miscellaneous**.

     Etkileşimli öğeleri oluşturma sırasında otomatik olarak adlandırmak için onay kutusunu seçin.

     ![XAML çeşitli seçenekleri](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

2. Visual C# veya Visual Basic şablonu kullanarak boş bir XAML tabanlı Windows Mağazası uygulaması için yeni bir proje oluşturun.

     ![&#40;XAML&#41;Windows Mağazası boş uygulaması oluşturma ](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")

3. Çözüm Gezgini, MainPage. xaml ' yi açın. Araç kutusundan bir düğme denetimini ve bir TextBox denetimini tasarım yüzeyine sürükleyin.

     ![Windows Mağazası uygulamasını tasarlama](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")

4. Düğme denetimine çift tıklayın ve aşağıdaki kodu ekleyin:

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

5. Windows mağazası uygulamanızı çalıştırmak için F5 tuşuna basın.

## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Windows Mağazası uygulaması için kodlanmış UI testi oluşturma ve çalıştırma

[Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri oluşturma Nasıl yaparım??](#uwpapps)

1. Windows Mağazası uygulaması için yeni bir kodlanmış UI test projesi oluşturun.

    ![Windows Mağazası uygulamaları &#40;yeni kodlanmış UI Tet Project&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")

2. İnce artı aracını kullanarak UI haritasını düzenlemeyi seçin.

    ![UI haritasını Düzenle veya onaylama Ekle seçeneğini belirleyin](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")

3. Kodlanmış UI Test Oluşturucusu 'ndaki ince artı aracını kullanarak uygulama kutucuğunu seçin, **AutomationId** ' ye sağ tıklayın ve **değeri panoya kopyala**' yı seçin. Panodaki değer daha sonra, uygulamayı test etmek üzere başlatmak üzere yazma eylemi için kullanılacaktır.

    ![AutomationId 'yi panoya kopyala](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")

4. Çalışan Windows Mağazası uygulamasında düğme denetimini ve TextBox denetimini seçmek için ince artı aracını kullanın. Her denetim eklendikten sonra kodlanmış UI Test Oluşturucusu araç çubuğunda **Kullanıcı arabirimi denetim eşlemesi ' ne Denetim Ekle** düğmesine tıklayın.

    ![Kullanıcı arabirimi eşlemesine denetim ekleme](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")

5. Kodlanmış UI Test Oluşturucusu araç çubuğunda **kod oluştur** düğmesini seçin ve ardından, UI denetim haritasında değişiklikler için kod oluşturmak üzere **Oluştur** ' u seçin.

    ![UI eşlemesi için kod oluştur](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")

6. Metin kutusunda bir değer ayarlamak için düğmeyi seçin.

    ![TextBox değerini ayarlamak için düğme denetimi ' ne tıklayın](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")

7. TextBox denetimini seçmek için ince artı aracını kullanın ve **Text** özelliğini seçin.

    ![Metin özelliğini seçin](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")

8. Onay ekleyin. Değerin doğru olduğunu doğrulamak için testte kullanılacaktır.

    ![Çapraz&#45;saç ve onaylama ekleme ile test kutusu seçin](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")

9. Onaylama için kod ekleyin ve oluşturun.

     ![TextBox onaylama için kod oluştur](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")

10. **Visual C #**

     Çözüm Gezgini, onay yöntemi ve denetimler için eklenen kodu görüntülemek üzere UIMap.Designer.cs dosyasını açın.

     **Visual Basic**

     Çözüm Gezgini, CodedUITest1. vb dosyasını açın ve ardından CodedUITestMethod1 () test yöntemi kodunda, otomatik olarak eklenen onaylama yöntemine yapılan çağrıya sağ tıklayın `Me.UIMap.AssertMethod1()` ve **Tanıma Git**' i seçin. Bu işlem, kod düzenleyicisinde UIMap. Designer. vb dosyasını açar, böylece onay yöntemi ve denetimler için eklenen kodu görüntüleyin.

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
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)
    End Sub
    ```

     **Denetimler**

    ```csharp
    #region Properties
    public XamlButton UIButtonButton
    {
        get
        {
            if ((this.mUIButtonButton == null))
            {
                this.mUIButtonButton = new XamlButton(this);
                #region Search Criteria
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";
                this.mUIButtonButton.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUIButtonButton;
        }
    }

    public XamlEdit UITextBoxEdit
    {
        get
        {
            if ((this.mUITextBoxEdit == null))
            {
                this.mUITextBoxEdit = new XamlEdit(this);
                #region Search Criteria
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";
                this.mUITextBoxEdit.WindowTitles.Add("App1");
                #endregion
            }
            return this.mUITextBoxEdit;
        }
    }
    #endregion

    #region Fields
    private XamlButton mUIButtonButton;

    private XamlEdit mUITextBoxEdit;
    #endregion
    ```

    ```vb
    #Region "Properties"
    Public ReadOnly Property UIButtonButton() As XamlButton
        Get
            If (Me.mUIButtonButton Is Nothing) Then
                Me.mUIButtonButton = New XamlButton(Me)
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"
                Me.mUIButtonButton.WindowTitles.Add("App2")
            End If
            Return Me.mUIButtonButton
        End Get
    End Property

    Public ReadOnly Property UITextBoxEdit() As XamlEdit
        Get
            If (Me.mUITextBoxEdit Is Nothing) Then
                Me.mUITextBoxEdit = New XamlEdit(Me)
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"
                Me.mUITextBoxEdit.WindowTitles.Add("App2")
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

11. Çözüm Gezgini, CodedUITest1.cs veya CodedUITest1. vb dosyasını açın. Artık, UIMap 'e eklenen denetimleri kullanarak testi çalıştırmak için eylemler için CodedUTTestMethod1 yöntemine kod ekleyebilirsiniz:

    1. Daha önce panoya kopyaladığınız Otomasyon KIMLIĞI özelliğini kullanarak Windows Mağazası uygulamasını başlatın:

       ```csharp
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")
       ```

       ```vb
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");
       ```

    2. Düğme denetimine dokunmak için bir hareket ekleyin:

       ```csharp
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);
       ```

       ```vb
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)
       ```

    3. Otomatik olarak oluşturulan onay yöntemine yapılan çağrının, uygulamayı başlattıktan ve düğme üzerindeki hareket ' e dokunduktan sonra geldiğini doğrulayın:

       ```csharp
       this.UIMap.AssertMethod1();
       ```

       ```vb
       Me.UIMap.AssertMethod1()
       ```

       Kodu ekledikten sonra, CodedUITestMethod1 test yöntemi aşağıdaki gibi görünmelidir:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.

        // Launch the app.
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");

        // Tap the button.
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);

        this.UIMap.AssertMethod1();
    }
    ```

    ```vb
    <CodedUITest(CodedUITestType.WindowsStore)>
    Public Class CodedUITest1

        <TestMethod()>
        Public Sub CodedUITestMethod1()
            '
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
            '

            ' Launch the app.
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")

            '// Tap the button.
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)

            Me.UIMap.AssertMethod1()
        End Sub
    ```

12. Testinizi oluşturun ve test Gezgini 'ni kullanarak testi çalıştırın.

     ![Kodlanmış UI testini Test Gezgini 'nden çalıştırma](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")

     Windows Mağazası uygulaması başlatılır, düğmeye dokunmayla gerçekleştirilecek eylem tamamlanır ve TextBox 'ın Text özelliği girilir ve onaylama yöntemi kullanılarak onaylanır.

     ![Kodlanmış UI testini çalıştırma](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")

     Test tamamlandıktan sonra test Gezgini testin geçtiğini gösterir.

     ![Test Gezgini 'nde geçilen test ekranları](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")

## <a name="q--a"></a>Soru-Cevap

- **S: kodlanmış UI testi iletişim kutusu için kod üret içinde, kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?**

     Y **: kayıt**seçeneği Windows Mağazası uygulamaları için desteklenmez.

- **S: WinJS tabanlı Windows Mağazası Uygulamalarım için kodlanmış UI testi oluşturabilir miyim?**

     Y **: Hayır**, yalnızca XAML tabanlı uygulamalar desteklenir.

- **S: Windows 8.1 veya Windows 10 çalıştırmayan bir sistemde Windows Mağazası Uygulamalarım için kodlanmış UI testleri oluşturabilir miyim?**

     Y **: Hayır**, kodlanmış UI testi proje şablonları yalnızca Windows 8.1 ve Windows 10 ' da kullanılabilir. Evrensel Windows Platformu (UWP) uygulamaları için Otomasyon oluşturmak üzere Windows 10 gerekir.

<a name="uwpapps"></a>
- **S: Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri oluşturma Nasıl yaparım??**

   **A**: UWP uygulamanızı test ettiğiniz platforma bağlı olarak, aşağıdaki yollarla kodlanmış UI test projesi oluşturun:

  - Yerel makine üzerinde çalışan bir UWP uygulaması, mağaza uygulaması olarak çalışacaktır. Bunu test etmek için **KODLANMıŞ UI test projesi (Windows)** şablonunu kullanmanız gerekir. Yeni bir proje oluşturduğunuzda bu şablonu bulmak için **Windows**, **Universal** düğümüne gidin. Veya **Windows**, **Windows 8**, **Windows** düğümüne gidin.

  - Mobil cihaz veya öykünücü üzerinde çalışan bir UWP uygulaması, bir telefon uygulaması olarak çalışacaktır. Bunu test etmek için **KODLANMıŞ UI test projesi (Windows Phone)** şablonunu kullanmanız gerekir. Yeni bir proje oluşturduğunuzda bu şablonu bulmak için **Windows**, **Universal** düğümüne gidin. Veya **Windows**, **windows 8**, **Windows Phone** düğümüne gidin.

    Projeyi oluşturduktan sonra, test yazma işleminden daha önce olduğu gibi kalır.

- **S: UIMap. Designer dosyasındaki kodu neden değiştiremiyorum?**

   **A**Y: UıMAP kodlu UI test oluşturucuyu kullanarak her kod oluşturduğunuzda UIMapDesigner.cs dosyasında yaptığınız tüm kod değişikliklerinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [UI otomasyonunu kullanarak kodunuzu test etmek](../test/use-ui-automation-to-test-your-code.md) Için [Windows Mağazası denetimleri Için benzersiz bir Otomasyon özelliği ayarlayın](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
