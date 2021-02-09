---
title: 'İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma | Microsoft Docs'
description: Visual C# kullanarak basit bir matematik kitaplığı SDK 'Sı oluşturmayı ve ardından bu yönergeyi kullanarak SDK 'Yı Visual Studio uzantısı olarak paketlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 1f1ede0e642f14581d13d571acf67a952360bf65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838701"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma
Bu kılavuzda, Visual C# kullanarak basit bir matematik kitaplığı SDK 'Sı oluşturmayı ve sonra SDK 'Yı bir Visual Studio uzantısı (VSıX) olarak paketlemeyi öğreneceksiniz. Aşağıdaki yordamları tamamlayacaksınız:

- [SimpleMath Windows Çalışma Zamanı bileşeni oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX Extension projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Önkoşullar
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> SimpleMath Windows Çalışma Zamanı bileşeni oluşturmak için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. Şablonlar listesinde, **Visual C#** veya **Visual Basic**' i genişletin, **Windows Mağazası** düğümünü seçin ve **Windows çalışma zamanı bileşen** şablonunu seçin.

3. **Ad** kutusunda, **SimpleMath**' i belirtip **Tamam** düğmesini seçin.

4. **Çözüm Gezgini**, **SimpleMath** proje düğümünün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

5. **Class1.cs** öğesini **arithmetic.cs** olarak yeniden adlandırın ve aşağıdaki kodla eşleşecek şekilde güncelleştirin:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **Çözüm Gezgini**' de, **Çözüm ' SimpleMath '** düğümünün kısayol menüsünü açın ve **Configuration Manager** öğesini seçin.

    **Configuration Manager** iletişim kutusu açılır.

7. **Etkin çözüm yapılandırması** listesinde **yayın**' ı seçin.

8. **Yapılandırma** sütununda, **SimpleMath** satırının **Release** olarak ayarlandığını doğrulayın ve ardından değişikliği kabul etmek için **Kapat** düğmesini seçin.

   > [!IMPORTANT]
   > SimpleMath bileşeni için SDK yalnızca bir yapılandırma içerir. Bu yapılandırma yayın derlemesi olmalıdır veya bileşeni kullanan uygulamalar, için sertifika geçirmez [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] .

9. **Çözüm Gezgini**, **SimpleMath** proje düğümünün kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> SimpleMathVSIX Extension projesi oluşturmak için

1. **Çözüm ' SimpleMath '** düğümünün kısayol menüsünde   >  **Yeni proje** Ekle ' yi seçin.

2. Şablonlar listesinde, **Visual C#** veya **Visual Basic**' ı genişletin, **genişletilebilirlik** düğümünü seçin ve **VSIX proje** şablonunu seçin.

3. **Ad** kutusunda, **SimpleMathVSIX** belirtin ve sonra **Tamam** düğmesini seçin.

4. **Çözüm Gezgini**, **Source. Extension. valtmanifest** öğesini seçin.

5. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

6. Mevcut XML 'i aşağıdaki XML ile değiştirin:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **Çözüm Gezgini**, **SimpleMathVSIX** projesini seçin.

8. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

9. **Ortak öğeler** listesinde, **veriler**' i genişletin ve ardından **XML dosyası**' nı seçin.

10. **Ad** kutusunda, `SDKManifest.xml` öğesini belirtin ve sonra **Ekle** düğmesini seçin.

11. **Çözüm Gezgini**' de, için kısayol menüsünü açın `SDKManifest.xml` , **Özellikler**' i seçin ve ardından **VSIX özelliğindeki Ekle** değerini **doğru** olarak değiştirin.

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

13. **Çözüm Gezgini**, **SimpleMathVSIX** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni klasör**' i seçin.

14. Klasörü olarak yeniden adlandırın `references` .

15. **Başvurular** klasörünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni klasör**' i seçin.

16. Alt klasörü olarak yeniden adlandırın `commonconfiguration` , içinde bir alt klasör oluşturun ve alt klasörü adlandırın `neutral` .

17. Önceki dört adımı yineleyin, bu kez ilk klasörü olarak yeniden adlandırın `redist` .

     Proje artık aşağıdaki klasör yapısını içerir:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **Çözüm Gezgini**, **SimpleMath** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.

19. **Dosya Gezgini**'nde *bin\release* klasörüne gidin, **SimpleMath. winmd** dosyası için kısayol menüsünü açın ve **Kopyala**' yı seçin.

20. **Çözüm Gezgini**, dosyayı **SimpleMathVSIX** projesindeki *references\commonconfiguration\neutral* klasörüne yapıştırın.

21. **SimpleMath. pri** dosyasını **SimpleMathVSIX** projesindeki *redist\commonconfiguration\neutral* klasörüne yapıştırarak önceki adımı yineleyin.

22. **Çözüm Gezgini**, **SimpleMath. winmd** öğesini seçin.

23. Menü çubuğunda özellikleri **görüntüle**' yi seçin  >   (klavye: **F4** anahtarını seçin).

24. **Özellikler** penceresinde, **derleme eylemi** özelliğini **IÇERIK** olarak değiştirin ve ardından **VSIX özelliğindeki içerme** özelliğini **true** olarak değiştirin.

25. **Çözüm Gezgini**' de, **SimpleMath. pri** için bu işlemi tekrarlayın.

26. **Çözüm Gezgini**, **SimpleMathVSIX** projesini seçin.

27. Menü **çubuğunda Build**  >  **Build SimpleMathVSIX** öğesini seçin.

28. **Çözüm Gezgini**' de, **SimpleMathVSIX** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.

29. **Dosya Gezgini**'nde, *\bin\Release* klasörü ' ne gidin ve ardından yüklemek için *SimpleMathVSIX. vsix* ' yi çalıştırın.

30. **Yükleme düğmesini seçin** , yüklemenin bitmesini bekleyin ve ardından Visual Studio 'yu yeniden başlatın.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. Şablonlar listesinde, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **Windows Mağazası** düğümünü seçin.

3. **Boş uygulama** şablonunu seçin, projeyi **ArithmeticUI** olarak adlandırın ve **Tamam** düğmesini seçin.

4. **Çözüm Gezgini**' de, **ArithmeticUI** projesi için kısayol menüsünü açın ve ardından başvuru **Ekle**' yi seçin  >  .

5. Başvuru türleri listesinde **Windows**' u ve ardından **Uzantılar**' ı seçin.

6. Ayrıntılar bölmesinde, **WinRT matematik kitaplığı** uzantısı ' nı seçin.

    SDK 'niz hakkında ek bilgiler görüntülenir. Bu kılavuzda daha önce SDKManifest.xml dosyasında belirttiğiniz şekilde, **daha fazla bilgi** için Aç bağlantısını seçebilirsiniz https://msdn.microsoft.com/ .

7. **Başvuru Yöneticisi** iletişim kutusunda, **WinRT matematik kitaplığı** onay kutusunu seçin ve **Tamam** düğmesini seçin.

8. Menü çubuğunda nesne tarayıcısı **görüntüle**' yi seçin  >  .

9. **Gözden** geçirme listesinde **basit matematik**' ı seçin.

     Artık SDK 'da neler olduğunu keşfedebilirsiniz.

10. **Çözüm Gezgini**, **MainPage. xaml**' yi açın ve içeriğini aşağıdaki xaml ile değiştirin:

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

11. **MainPage.xaml.cs** öğesini aşağıdaki kodla eşleşecek şekilde güncelleştirin:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Uygulamayı çalıştırmak için **F5** tuşunu seçin.

13. Uygulamada, iki sayı girin, bir işlem seçin ve ardından **=** düğmeyi seçin.

     Doğru sonuç görüntülenir.

    Bir uzantı SDK 'sını başarıyla oluşturdunuz ve kullandınız.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [İzlenecek yol: JavaScript kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
