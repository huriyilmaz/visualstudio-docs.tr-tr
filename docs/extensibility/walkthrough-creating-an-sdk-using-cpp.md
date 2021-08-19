---
title: 'İzlenecek yol: C++ kullanarak SDK oluşturma | Microsoft Docs'
description: yerel bir C++ matematik kitaplığı sdk 'sı oluşturmayı, sdk 'yı Visual Studio uzantısı olarak paketlemeyi ve bu kılavuzu kullanarak bir uygulama oluşturmak için kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6298300127cbcbfec706bb5cf9fcda89a68c12cf
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334641"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>İzlenecek yol: C++ kullanarak SDK oluşturma
bu izlenecek yol, yerel bir C++ matematik kitaplığı sdk 'sı oluşturmayı, SDK 'nın Visual Studio uzantısı (vsıx) olarak paketlemeyi ve sonra bir uygulama oluşturmak için nasıl kullanılacağını gösterir. İzlenecek yol aşağıdaki adımlara ayrılmıştır:

- [yerel ve Windows Çalışma Zamanı kitaplıklarını oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [NativeMathVSIX Extension projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Önkoşullar
 bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [SDK Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>yerel ve Windows Çalışma Zamanı kitaplıklarını oluşturmak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

2. şablonlar listesinde **Visual C++**  >  **Universal Windows**' i genişletin ve ardından **DLL (Windows Universal apps)** şablonunu seçin. **Ad** kutusunda, `NativeMath` öğesini belirtin ve sonra **Tamam** düğmesini seçin.

3. *Nativemath. h* öğesini aşağıdaki kodla eşleşecek şekilde güncelleştirin.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. *Nativemath. cpp* öğesini bu kodla eşleşecek şekilde güncelleştirin:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. **Çözüm Gezgini**' de, **' nativemath ' çözümünün** kısayol menüsünü açın ve   >  **yeni Project** ekle ' yi seçin.

6. şablonlar listesinde **Visual C++**' ı genişletin ve **Windows Çalışma Zamanı bileşen** şablonunu seçin. **Ad** kutusunda, `NativeMathWRT` öğesini belirtin ve sonra **Tamam** düğmesini seçin.

7. *Class1. h* 'yi bu kodla eşleşecek şekilde güncelleştirin:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. *Class1. cpp* ' i bu kodla eşleşecek şekilde güncelleştirin:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> NativeMathVSIX Extension projesi oluşturmak için

1. **Çözüm Gezgini**' de, **' nativemath ' çözümünün** kısayol menüsünü açın ve   >  **yeni Project** ekle ' yi seçin.

2. şablonlar listesinde, **Visual C#**  >  **genişletilebilirlik**' i genişletin ve ardından **vsıx Project**' yi seçin. **Ad** kutusunda, **NativeMathVSIX** belirtin ve sonra **Tamam** düğmesini seçin.

3. **Çözüm Gezgini**, **Source. Extension. valtmanifest** için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

4. Varolan XML 'yi değiştirmek için aşağıdaki XML 'i kullanın.

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/source.extension.vsixmanifest" id="Snippet6":::

5. **Çözüm Gezgini**' de, **NativeMathVSIX** projesi için kısayol menüsünü açın ve   >  **Yeni öğe** Ekle ' yi seçin.

6. **Visual C# öğeleri** listesinde, **veriler**' i genişletin ve ardından **XML dosyası**' nı seçin. **Ad** kutusunda, `SDKManifest.xml` öğesini belirtin ve sonra **Tamam** düğmesini seçin.

7. Dosyanın içeriğini değiştirmek için bu XML 'i kullanın:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. **Çözüm Gezgini**, **NativeMathVSIX** projesi altında, bu klasör yapısını oluşturun:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. **Çözüm Gezgini**' de, **' Nativemath ' çözümünün** kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.

10. **Dosya Gezgini**'nde *$SolutionRoot $ \NativeMath\NativeMath.h* kopyalayın ve ardından **Çözüm Gezgini**' de **NativeMathVSIX** projesi altında *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\* klasörüne yapıştırın.

     *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib* kopyalayın ve sonra *\\ $SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86* klasörüne yapıştırın.

     *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* kopyalayın ve *\\ $SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* klasörüne yapıştırın.

     *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* kopyalayın ve *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* klasörüne yapıştırın.
     *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* kopyalayın ve *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* klasörüne yapıştırın.

     *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* kopyalayın ve *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* klasörüne yapıştırın.

11. *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* klasöründe, *NativeMathSDK. props* adlı bir metin dosyası oluşturun ve ardından içine aşağıdaki içeriği yapıştırın:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. menü çubuğunda   >  **diğer Windows**  >  **özellikler penceresini** görüntüle ' yi seçin (klavye: **F4** anahtarını seçin).

13. **Çözüm Gezgini**, **NativeMathWRT. winmd** dosyasını seçin. **Özellikler** penceresinde, **derleme eylemi** özelliğini **IÇERIK** olarak değiştirin ve ardından **VSIX özelliğindeki içerme** özelliğini **true** olarak değiştirin.

     **Nativemath. h** dosyası için bu işlemi tekrarlayın.

     **NativeMathWRT. pri** dosyası için bu işlemi tekrarlayın.

     **Nativemath. lib** dosyası için bu işlemi tekrarlayın.

     **NativeMathSDK. props** dosyası için bu işlemi tekrarlayın.

14. **Çözüm Gezgini**, **nativemath. h** dosyasını seçin. **Özellikler** penceresinde **VSIX Içindeki Include** özelliğini **true** olarak değiştirin.

     **NativeMath.dll** dosyası için bu işlemi tekrarlayın.

     **NativeMathWRT.dll** dosyası için bu işlemi tekrarlayın.

     **SDKManifest.xml** dosyası için bu işlemi tekrarlayın.

15. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

16. **Çözüm Gezgini**' de, **NativeMathVSIX** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.

17. **Dosya Gezgini**'nde *$SolutionRoot $ \NativeMathVSIX\bin\Debug* klasörüne gidin ve sonra yüklemeyi başlatmak için *NativeMathVSIX. vsix* ' yi çalıştırın.

18. **Yükleme düğmesini seçin** , yüklemenin bitmesini bekleyin ve sonra Visual Studio açın.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

2. şablonlar listesinde **Visual C++**  >  **Universal Windows** ' i genişletin ve **boş uygulama**' yı seçin. **Ad** kutusunda, **NativeMathSDKSample** belirtin ve sonra **Tamam** düğmesini seçin.

3. **Çözüm Gezgini**' de, **NativeMathSDKSample** projesi için kısayol menüsünü açın ve ardından başvuru **Ekle**' yi seçin  >  .

4. **başvuru ekle** iletişim kutusunda, başvuru türleri listesinde, **evrensel Windows**' ı genişletin ve ardından **uzantılar**' ı seçin. Son olarak, **Yerel matematik SDK 'sı** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

5. NativeMathSDKSample için proje özelliklerini görüntüleyin.

    *NativeMathSDK. props* içinde tanımladığınız özellikler, başvuruyu eklediğinizde uygulandı. Projenin **yapılandırma özelliklerinin** **VC + + dizinleri** özelliğini inceleyerek özelliklerin uygulandığını doğrulayabilirsiniz.

6. **Çözüm Gezgini**, **MainPage. xaml**' yi açın ve ardından IÇERIĞINI değiştirmek için aşağıdaki xaml 'yi kullanın:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. *MainPage. xaml. h* öğesini bu kodla eşleşecek şekilde güncelleştirin:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. *MainPage. xaml. cpp* öğesini bu kodla eşleşecek şekilde güncelleştirin:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Uygulamayı çalıştırmak için **F5** tuşunu seçin.

10. Uygulamada, iki sayı girin, bir işlem seçin ve ardından **=** düğmeyi seçin.

     Doğru sonuç görüntülenir.

    Bu izlenecek yol [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] , bir kitaplık ve kitaplık olmayan bir uzantı SDK 'sı oluşturmayı ve kullanmayı gösterdi [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>Sonraki adımlar

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)
