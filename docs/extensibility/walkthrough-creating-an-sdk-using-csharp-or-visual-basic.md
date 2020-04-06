---
title: 'Walkthrough: C# veya Visual Basic kullanarak SDK oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697550"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Walkthrough: C# veya Visual Basic kullanarak Bir SDK oluşturma
Bu izbinde, Visual C# kullanarak basit bir Matematik Kütüphanesi SDK'sını nasıl oluşturabileceğinizi ve Ardından SDK'yı Visual Studio Extension (VSIX) olarak nasıl paketlendireceğinizi öğreneceksiniz. Aşağıdaki yordamları tamamlarsınız:

- [SimpleMath Windows Runtime bileşenini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>SimpleMath Windows Runtime bileşenini oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablonlar listesinde **Visual C#** veya **Visual Basic'i**genişletin, **Windows Mağazası** düğüm'ü seçin ve ardından **Windows Runtime Bileşeni** şablonunu seçin.

3. **Ad** kutusunda **SimpleMath'i**belirtin ve ardından **Tamam** düğmesini seçin.

4. **Solution Explorer'da** **SimpleMath** proje düğümü için kısayol menüsünü açın ve ardından **Özellikler'i**seçin.

5. **Class1.cs Arithmetic.cs** ve aşağıdaki kodla eşleşecek şekilde güncelleştirmek için **yeniden** adlandırın:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **Solution**Explorer'da, **Solution 'SimpleMath'** düğümü için kısayol menüsünü açın ve ardından **Configuration Manager'ı**seçin.

    **Configuration Manager** iletişim kutusu açılır.

7. Etkin **çözüm yapılandırma** **listesinde, Release'i**seçin.

8. **Yapılandırma** sütununda, **SimpleMath** satırının **Serbest Bırak'a**ayarlı olduğunu doğrulayın ve sonra değişikliği kabul etmek için **Kapat** düğmesini seçin.

   > [!IMPORTANT]
   > SimpleMath bileşeni için SDK yalnızca bir yapılandırma içerir. Bu yapılandırma sürüm yapısı olmalıdır veya bileşeni kullanan uygulamalar [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]için sertifika geçmez.

9. **Solution Explorer'da** **SimpleMath** proje düğümü için kısayol menüsünü açın ve ardından **Oluştur'u**seçin.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>SimpleMathVSIX uzantı projesini oluşturmak için

1. **Çözüm 'SimpleMath'** düğümü için kısayol menüsünde,**Yeni Proje** **Ekle'yi** > seçin.

2. Şablonlar listesinde **Visual C#** veya **Visual Basic'i**genişletin, **Genişletilebilirlik** düğümini seçin ve ardından **VSIX Project şablonunu** seçin.

3. **Ad** kutusunda **SimpleMathVSIX'yi**belirtin ve ardından **Tamam** düğmesini seçin.

4. **Çözüm Gezgini'nde** **source.extension.vsixmanifest** öğesini seçin.

5. Menü çubuğunda**Kodu** **Görüntüle'yi** > seçin.

6. Varolan XML'i aşağıdaki XML ile değiştirin:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **Solution Explorer'da** **SimpleMathVSIX** projesini seçin.

8. Menü çubuğunda **Project** > **Add New Item'i**seçin.

9. **Ortak Öğeler**listesinde, **Verileri**genişletin ve ardından **XML Dosyasını**seçin.

10. **Ad** kutusunda, belirtin `SDKManifest.xml`ve sonra **Ekle** düğmesini seçin.

11. **Çözüm Gezgini'nde,** Özellikler `SDKManifest.xml`için kısayol menüsünü açın, **Özellikler'i**seçin ve ardından **VSIX özelliğine Ekle** değerini **True**olarak değiştirin.

12. Dosyanın içeriğini aşağıdaki XML ile değiştirin:

    **C #**

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

13. **Solution Explorer'da** **SimpleMathVSIX** projesinin kısayol menüsünü açın, **Ekle'yi**seçin ve ardından **Yeni Klasör'ü**seçin.

14. Klasörü ' `references`ye yeniden adlandırın.

15. **Başvurular** klasörünün kısayol menüsünü açın, **Ekle'yi**seçin ve ardından **Yeni Klasör'ü**seçin.

16. Alt klasörü, `commonconfiguration`içinde bir alt klasör oluşturacak ve alt `neutral`klasörü adlamak için yeniden adlandırın.

17. Önceki dört adımı yineleyin, bu kez `redist`ilk klasörü .

     Proje şimdi aşağıdaki klasör yapısını içerir:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **Solution Explorer'da** **SimpleMath** projesinin kısayol menüsünü açın ve **ardından Dosya Gezgini'nde Klasörü Aç'ı**seçin.

19. **Dosya Gezgini'nde,** *bin\Release* klasörüne gidin, **SimpleMath.winmd** dosyası için kısayol menüsünü açın ve ardından **Kopyala'yı**seçin.

20. **Çözüm Gezgini'nde,** **Dosyayı SimpleMathVSIX** projesinde *başvurular\commonconfiguration\neutral* klasörüne yapıştırın.

21. **SimpleMathVSIX** projesinde **SimpleMath.pri** dosyasını *redist\commonconfiguration\neutral* klasörüne yapıştırarak önceki adımı yineleyin.

22. **Çözüm Explorer,** **SimpleMath.winmd**seçin.

23. Menü çubuğunda**Özellikleri** **Görüntüle** > 'yi seçin (Klavye: **F4** tuşunu seçin).

24. **Özellikler** penceresinde, Yapı **Eylemi** özelliğini **İçerik**olarak değiştirin ve ardından **VSIX özelliğine Ekle** özelliğini **True**olarak değiştirin.

25. **Çözüm Gezgini'nde,** **SimpleMath.pri**için bu işlemi tekrarlayın.

26. **Solution Explorer'da** **SimpleMathVSIX** projesini seçin.

27. Menü çubuğunda**Build SimpleMathVSIX'yi** **Build** > seçin.

28. **Solution Explorer'da** **SimpleMathVSIX** projesinin kısayol menüsünü açın ve **ardından Dosya Gezgini'nde Klasörü Aç'ı**seçin.

29. **Dosya Gezgini'nde** *\bin\Release* klasörüne gidin ve yüklemek için *SimpleMathVSIX.vsix* çalıştırın.

30. **Yükle** düğmesini seçin, yüklemenin tamamlanmasını bekleyin ve ardından Visual Studio'yu yeniden başlatın.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablonlar listesinde **Visual C#** veya **Visual Basic'i**genişletin ve ardından **Windows Mağazası** düğümini seçin.

3. Boş **Uygulama** şablonu seçin, proje **AritmetikUI**adını ve sonra **Tamam** düğmesini seçin.

4. **Çözüm Gezgini'nde,** **AritmetikUI** projesinin kısayol menüsünü açın ve ardından**Başvuru** **Ekle'yi** > seçin.

5. Başvuru türleri listesinde, **Windows'u**genişletin ve ardından **Uzantılar'ı**seçin.

6. Ayrıntılar bölmesinde **WinRT Matematik Kitaplığı** uzantısını seçin.

    SDK'nız hakkında ek bilgiler görüntülenir. Bu walkthrough'ta SDKManifest.xml dosyasında belirttiğiniz gibi, açmak https://msdn.microsoft.com/için Daha Fazla **Bilgi** bağlantısını seçebilirsiniz.

7. Başvuru **Yöneticisi** iletişim **kutusunda, WinRT Matematik Kitaplığı** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

8. Menü çubuğunda**Nesne Tarayıcısını** **Görüntüle'yi** > seçin.

9. **Gözat** listesinde Basit **Matematik'i**seçin.

     Artık SDK'da neler olduğunu keşfedebilirsiniz.

10. **Solution Explorer'da** **MainPage.xaml'ı**açın ve içeriğini aşağıdaki XAML ile değiştirin:

    **C #**

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

11. Aşağıdaki kodu eşleştirmek için **MainPage.xaml.cs** güncelleştirin:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Uygulamayı çalıştırmak için **F5** tuşunu seçin.

13. Uygulamada, herhangi iki sayı girin, bir işlem seçin **=** ve sonra düğmeyi seçin.

     Doğru sonuç görüntülenir.

    Bir Uzantı SDK'yı başarıyla oluşturdunuz ve kullandınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: C++ kullanarak bir SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Walkthrough: JavaScript kullanarak bir SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
