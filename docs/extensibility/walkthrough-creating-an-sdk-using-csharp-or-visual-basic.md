---
title: 'Adım adım kılavuz: C# veya Visual Basic | kullanarak SDK oluşturma Microsoft Docs'
description: Visual C# kullanarak basit bir Matematik Kitaplığı SDK'sı oluşturma ve ardından bu izlenecek yolu kullanarak SDK'yı Visual Studio Uzantısı olarak paketleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 36afa727498c71892130a352f1c8eac35c84760f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144268"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Adım adım kılavuz: C# veya Visual Basic kullanarak SDK oluşturma
Bu kılavuzda Visual C# kullanarak basit bir Matematik Kitaplığı SDK'sı oluşturma ve ardından SDK'yı bir Visual Studio Uzantısı (VSIX) olarak paketleyebilirsiniz. Aşağıdaki yordamları tamamlarsiniz:

- [SimpleMath Windows Runtime bileşenini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>SimpleMath Windows Runtime bileşenini oluşturmak için

1. Menü çubuğunda Dosya Yeni **dosya'Project.**  >    >  

2. Şablon listesinde **Visual C#** veya Visual Basic'yi **genişletin,** **Windows Store** düğümünü seçin ve Windows **Çalışma Zamanı Bileşeni şablonunu** seçin.

3. Ad **kutusunda** **SimpleMath'i belirtin** ve ardından Tamam **düğmesini** seçin.

4. Bu **Çözüm Gezgini** **SimpleMath** proje düğümünün kısayol menüsünü açın ve Özellikler'i **seçin.**

5. **Class1.cs'yi** **Arithmetic.cs** olarak yeniden adlandırarak aşağıdaki kodla eş olacak şekilde güncelleştirin:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb" id="Snippet3":::

6. Bu **Çözüm Gezgini** Çözüm **'SimpleMath' düğümünün kısayol menüsünü** açın ve ardından Yapılandırma Yöneticisi. 

    Yapılandırma Yöneticisi  iletişim kutusu açılır.

7. Etkin çözüm **yapılandırma listesinde Yayın'ı** **seçin.**

8. Yapılandırma sütununda **SimpleMath** satırı'nın Sürüm olarak ayar olduğunu  **doğrulayın** ve ardından değişikliği kabul **etmek** için Kapat düğmesini seçin.

   > [!IMPORTANT]
   > SimpleMath bileşeninin SDK'sı yalnızca bir yapılandırma içerir. Bu yapılandırma yayın derlemesi olmalı veya bileşeni kullanan uygulamalar için sertifikasyonu [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] geçmemektedir.

9. Bu **Çözüm Gezgini** **SimpleMath** proje düğümünün kısayol menüsünü açın ve Ardından Oluştur'a **tıklayın.**

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> SimpleMathVSIX uzantı projesini oluşturmak için

1. **Çözüm 'SimpleMath' düğümünün kısayol menüsünde** Yeni Ekle'yi **Project.**  >  

2. Şablon listesinde **Visual C#** veya Visual Basic **genişletin,** **Genişletilebilirlik** düğümünü seçin ve ardından **VSIX** Project seçin.

3. Ad **kutusunda** **SimpleMathVSIX'i belirtin** ve ardından Tamam **düğmesini** seçin.

4. Bu **Çözüm Gezgini** **source.extension.vsixmanifest öğesini** seçin.

5. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

6. Mevcut XML'i aşağıdaki XML ile değiştirin:

   ```xml
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Metadata>
       <Identity Id="SimpleMath" Version="1.0" Language="en-US" Publisher="[YourName]" />
       <DisplayName>SimpleMath Library</DisplayName>
       <Description xml:space="preserve">Basic arithmetic operations in a WinRT-compatible library. Implemented in C#.</Description>
     </Metadata>
     <Installation Scope="Global" AllUsers="true">
       <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
     </Installation>
     <Prerequisites>
       <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[14.0,16.0]" />
     </Prerequisites>
     <Dependencies>
       <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
     </Dependencies>
     <Assets>
       <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
     </Assets>
   </PackageManifest>
   ```

7. Bu **Çözüm Gezgini** **SimpleMathVSIX projesini** seçin.

8. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

9. Ortak Öğeler listesinde **Veri'yi** genişletin **ve** XML Dosyası'ı **seçin.**

10. Ad **kutusunda** belirtin ve `SDKManifest.xml` ardından Ekle **düğmesini** seçin.

11. Bu **Çözüm Gezgini** için kısayol menüsünü açın, Özellikler'i seçin ve VSIX özelliğine dahil edin özelliğinin `SDKManifest.xml` değerini True olarak **değiştirin.**  

12. Dosyanın içeriğini aşağıdaki XML ile değiştirin:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. Bu **Çözüm Gezgini** **SimpleMathVSIX** projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni Klasör'ü **seçin.**

14. Klasörü olarak yeniden `references` adlandırabilirsiniz.

15. Başvurular klasörünün kısayol **menüsünü açın,** Ekle'yi **ve** ardından Yeni Klasör'ü **seçin.**

16. Alt klasörü olarak yeniden `commonconfiguration` adlandırarak içinde bir alt klasör oluşturun ve alt klasöre adını `neutral` girin.

17. Önceki dört adımı yinele, bu kez ilk klasörü olarak yeniden yeniden adı. `redist`

     Proje artık aşağıdaki klasör yapısını içerir:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Bu **Çözüm Gezgini** **SimpleMath** projesinin kısayol menüsünü açın ve ardından Klasör Aç'ı **Dosya Gezgini.**

19. Bu **Dosya Gezgini** *bin\Release* klasörüne gidin, **SimpleMath.winmd** dosyasının kısayol menüsünü açın ve Kopyala'yı **seçin.**

20. Bu **Çözüm Gezgini,** **simpleMathVSIX** projesinde *references\commonconfiguration\neural* klasörüne yapıştırın.

21. **SimpleMathVSIX projesinde simpleMath.pri** dosyasını *redist\commonconfiguration\neutral* **klasörüne** yapıştırarak önceki adımı tekrarlayın.

22. Bu **Çözüm Gezgini** **SimpleMath.winmd'yi seçin.**

23. Menü çubuğunda Özellikleri Görüntüle **(Klavye:**  >   **F4 tuşuna basın) öğesini** seçin.

24. Özellikler **penceresinde** Derleme Eylemi özelliğini İçerik  **olarak** değiştirin ve ardından **VSIX'te Dahil Edin** özelliğini True olarak **değiştirin.**

25. Burada **Çözüm Gezgini** **SimpleMath.pri için bu işlemi tekrarlayın.**

26. Bu **Çözüm Gezgini** **SimpleMathVSIX projesini** seçin.

27. Menü çubuğunda Derleme   >  **BasitMathVSIX öğesini seçin.**

28. Bu **Çözüm Gezgini** **SimpleMathVSIX** projesinin kısayol menüsünü açın ve ardından **Dosya Gezgini.**

29. Bu **Dosya Gezgini** *\bin\Release* klasörüne gidin ve *SimpleMathVSIX.vsix'i çalıştırarak* yükleyin.

30. Yükle düğmesini **seçin,** yüklemenin bitip bitimini bekleyin ve ardından yükleme işlemini Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için

1. Menü çubuğunda Dosya Yeni **dosya'Project.**  >    >  

2. Şablon listesinde Visual **C#** veya **Visual Basic'yi genişletin** ve ardından Windows **düğümünü** seçin.

3. Boş Uygulama **şablonunu seçin,** projeye **AritmetikUI** adını ve ardından Tamam **düğmesini** seçin.

4. Bu **Çözüm Gezgini,** **AritmetikUI projesinin** kısayol menüsünü açın ve Başvuru **Ekle'yi**  >  **seçin.**

5. Başvuru türleri listesinde, dosya **adı'Windows** genişletin ve uzantılar'ı **seçin.**

6. Ayrıntılar bölmesinde WinRT Matematik Kitaplığı **uzantısını** seçin.

    SDK'nız hakkında ek bilgiler görüntülenir. Bu kılavuzda **daha önce yer** alan dosyada belirttiğiniz https://msdn.microsoft.com/ gibi, daha fazla bilgi SDKManifest.xml bağlantısını seçebilirsiniz.

7. Başvuru **Yöneticisi iletişim** kutusunda **WinRT** Matematik Kitaplığı onay kutusunu ve ardından Tamam **düğmesini** seçin.

8. Menü çubuğunda Nesne Tarayıcısını  >  **Görüntüle'yi seçin.**

9. Gözat listesinde **Basit** **Matematik'i seçin.**

     Artık SDK'dakileri keşfedebilirsiniz.

10. Bu **Çözüm Gezgini** **MainPage.xaml'i açın** ve içeriğini aşağıdaki XAML ile değiştirin:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. **MainPage.xaml.cs'yi aşağıdaki** kodla eş olacak şekilde güncelleştirin:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

namespace ArithmeticUI
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public static string operation = null;

        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo(NavigationEventArgs e)
        {
        }

        /// <summary>
        /// Sets the operator chosen by the user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnOperatorClick(object sender, RoutedEventArgs e)
        {
            operation = (sender as Button).Content.ToString();
        }

        /// <summary>
        /// Calls the SimpleMath SDK to do simple arithmetic
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void OnResultsClick(object sender, RoutedEventArgs e)
        {
            try
            {
                float firstNumber = float.Parse(this._firstNumber.Text);
                float secondNumber = float.Parse(this._secondNumber.Text);

                SimpleMath.Arithmetic math = new SimpleMath.Arithmetic();

                switch (operation)
                {
                    case "+":
                        this._result.Text = (math.add(firstNumber, secondNumber)).ToString();
                        break;
                    case "-":
                        this._result.Text = (math.subtract(firstNumber, secondNumber)).ToString();
                        break;
                    case "*":
                        this._result.Text = (math.multiply(firstNumber, secondNumber)).ToString();
                        break;
                    case "/":
                        this._result.Text = (math.divide(firstNumber, secondNumber)).ToString();
                        break;
                    default:
                        this._result.Text = "Choose operator";
                        break;
                }
            }
            catch
            {
                this._result.Text = "Enter valid #";
            }
        }
    }
}
```

```vb
' The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238

''' <summary>
''' An empty page that can be used on its own or navigated to within a Frame.
''' </summary>
Public NotInheritable Class MainPage
    Inherits Page

    ''' <summary>
    ''' Invoked when this page is about to be displayed in a Frame.
    ''' </summary>
    ''' <param name="e">Event data that describes how this page was reached.  The Parameter
    ''' property is typically used to configure the page.</param>
    Protected Overrides Sub OnNavigatedTo(e As Navigation.NavigationEventArgs)
    
    End Sub

    Public Shared operation As String = Nothing

    ''' <summary>
    ''' Sets the operator chosen by the user
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnOperatorClick(ByVal sender As Object, ByVal e As RoutedEventArgs)
        operation = If(TypeOf sender Is Button, CType(sender, Button), Nothing).Content.ToString()
    End Sub


    ''' <summary>
    ''' Calls the SimpleMath SDK to do simple arithmetic
    ''' </summary>
    ''' <param name="sender"></param>
    ''' <param name="e"></param>
    Private Sub OnResultsClick(ByVal sender As Object, ByVal e As RoutedEventArgs)

        Try

            Dim firstNumber As Single = Single.Parse(Me._firstNumber.Text)
            Dim secondNumber As Single = Single.Parse(Me._secondNumber.Text)

            Dim math As New SimpleMath.Arithmetic()

            Select Case (operation)

                Case "+"
                    Me._result.Text = (math.Add(firstNumber, secondNumber)).ToString()

                Case "-"
                    Me._result.Text = (math.Subtract(firstNumber, secondNumber)).ToString()
                Case "*"
                    Me._result.Text = (math.Multiply(firstNumber, secondNumber)).ToString()
                Case "/"
                    Me._result.Text = (math.Divide(firstNumber, secondNumber)).ToString()
                Case Else
                    Me._result.Text = "Choose operator"

            End Select

        Catch
            Me._result.Text = "Enter valid #"
        End Try
    End Sub
End Class
```

12. Uygulamayı **çalıştırmak için F5** tuşuna basın.

13. Uygulamada iki sayı girin, bir işlem seçin ve ardından düğmeyi **=** seçin.

     Doğru sonuç görüntülenir.

    Uzantı SDK'sı başarıyla oluşturuldu ve kullanıldı.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Adım adım kılavuz: JavaScript kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
