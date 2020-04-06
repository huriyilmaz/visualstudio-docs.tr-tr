---
title: 'Walkthrough: C++ kullanarak SDK oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697626"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Walkthrough: C++ kullanarak bir SDK oluşturma
Bu gözden geçirme, yerel bir C++ matematik kitaplığı SDK'nın nasıl oluşturulup, SDK'yı Visual Studio Extension (VSIX) olarak nasıl paketleyip bir uygulama oluşturmak için kullanacağımı gösterir. Gözden geçirme şu adımlara ayrılır:

- [Yerel ve Windows Runtime kitaplıklarını oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [NativeMathVSIX uzantı projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Yerel ve Windows Runtime kitaplıklarını oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablonlar listesinde **Visual C++** > **Windows Universal'ı**genişletin ve ardından **DLL (Windows Universal uygulamaları)** şablonuna seçeneğini belirleyin. **Ad** kutusunda, 'yi belirtin `NativeMath`ve ardından **Tamam** düğmesini seçin.

3. Aşağıdaki kodla eşleşecek şekilde *NativeMath.h'yi* güncelleştirin.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Bu kodla eşleşecek şekilde *NativeMath.cpp'yi* güncelleştirin:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. **Solution Explorer'da**, Solution **'NativeMath'** için kısayol menüsünü açın ve ardından**Yeni Proje** **Ekle'yi** > seçin.

6. Şablonlar listesinde **Visual C++** seçeneğini genişletin ve ardından **Windows Runtime Bileşeni** şablonuna seçeneğini belirleyin. **Ad** kutusunda, 'yi belirtin `NativeMathWRT`ve ardından **Tamam** düğmesini seçin.

7. Bu kodu eşleştirmek için *Class1.h'yi* güncelleştirin:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Bu kodla eşleşecek şekilde *Class1.cpp'yi* güncelleştirin:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Menü çubuğunda **Yapı** > **Çözüm'üne**bakın.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>NativeMathVSIX uzantı projesini oluşturmak için

1. **Solution Explorer'da**, Solution **'NativeMath'** için kısayol menüsünü açın ve ardından**Yeni Proje** **Ekle'yi** > seçin.

2. Şablonlar listesinde Visual **C#** > **Genişletilebilirliği genişletin**ve ardından **VSIX Project'i**seçin. **Ad** kutusunda, **NativeMathVSIX'yi**belirtin ve ardından **Tamam** düğmesini seçin.

3. **Solution Explorer'da** **source.extension.vsixmanifest**için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

4. Varolan XML'i değiştirmek için aşağıdaki XML'yi kullanın.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. **Solution Explorer'da,** **NativeMathVSIX** projesi için kısayol menüsünü açın ve ardından Yeni**Öğe** **Ekle'yi** > seçin.

6. **Görsel C# Öğeleri**listesinde, **Verileri**genişletin ve ardından **XML Dosyasını**seçin. **Ad** kutusunda, 'yi belirtin `SDKManifest.xml`ve ardından **Tamam** düğmesini seçin.

7. Dosyanın içeriğini değiştirmek için bu XML'i kullanın:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. **Solution**Explorer'da, **NativeMathVSIX** projesi altında, bu klasör yapısını oluşturun:

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

9. **Solution Explorer'da**, Solution **'NativeMath'** için kısayol menüsünü açın ve ardından **Dosya Gezgini'nde Klasörü Aç'ı**seçin.

10. **Dosya Gezgini'nde**, kopya *$SolutionRoot$\NativeMath\NativeMath.h*, ve sonra **Solution Explorer**, NativeMathVSIX projesi altında, *$SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\ * klasörüne yapıştırın. **NativeMathVSIX**

     *$SolutionRoot$\Debug\NativeMath\NativeMath.lib'i*kopyalayın ve *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86\\ * klasörüne yapıştırın.

     *$SolutionRoot$\Hata Ayıklama\NativeMath.dll* kopyalayın ve *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86\\ * klasörüne yapıştırın.

     *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* kopyalayın ve *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86* klasörüne yapıştırın.
     kopya *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* ve *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral* klasörüne yapıştırın.

     *kopya $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* ve *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral* klasörüne yapıştırın.

11. *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86\\ * klasöründe, *NativeMathSDK.props*adlı bir metin dosyası oluşturun ve ardından aşağıdaki içerikleri yapıştırın:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Menü çubuğunda**Diğer Windows** > Özelliklerini **Görüntüle** > **Penceresini** seçin (Klavye: **F4** tuşunu seçin).

13. **Solution**Explorer'da, **NativeMathWRT.winmd** dosyasını seçin. **Özellikler** penceresinde, Yapı **Eylemi** özelliğini **İçerik**olarak değiştirin ve ardından **VSIX özelliğine Ekle** özelliğini **True**olarak değiştirin.

     **NativeMath.h** dosyası için bu işlemi tekrarlayın.

     **NativeMathWRT.pri** dosyası için bu işlemi yineleyin.

     **NativeMath.Lib** dosyası için bu işlemi yineleyin.

     **NativeMathSDK.props** dosyası için bu işlemi tekrarlayın.

14. **Çözüm Gezgini'nde,** **NativeMath.h** dosyasını seçin. **Özellikler** penceresinde, **VSIX özelliğine Ekle'yi** **True**olarak değiştirin.

     **NativeMath.dll** dosyası için bu işlemi tekrarlayın.

     **NativeMathWRT.dll** dosyası için bu işlemi yineleyin.

     **SDKManifest.xml** dosyası için bu işlemi tekrarlayın.

15. Menü çubuğunda **Yapı** > **Çözüm'üne**bakın.

16. **Solution**Explorer'da, **NativeMathVSIX** projesi için kısayol menüsünü açın ve **ardından Dosya Gezgini'nde Klasörü Aç'ı**seçin.

17. **Dosya Gezgini'nde,** *$SolutionRoot$\NativeMathVSIX\bin\Debug* klasörüne gidin ve yüklemeyi başlatmak için *NativeMathVSIX.vsix'i* çalıştırın.

18. **Yükle** düğmesini seçin, yüklemenin bitmesini bekleyin ve ardından Visual Studio'yu açın.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Sınıf kitaplığını kullanan örnek bir uygulama oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablonlar listesinde Visual **C++** > **Windows Universal'ı** genişletin ve ardından **Boş Uygulama'yı**seçin. **Ad** kutusunda, **NativeMathSDKSample'ı**belirtin ve ardından **Tamam** düğmesini seçin.

3. **Solution Explorer'da,** **NativeMathSDKSample** projesi için kısayol menüsünü açın ve ardından**Referans** **Ekle'yi** > seçin.

4. Başvuru **Ekle** iletişim kutusunda, başvuru türleri listesinde Evrensel **Windows'u**genişletin ve ardından **Uzantılar'ı**seçin. Son olarak, **Yerel Matematik SDK** onay kutusunu seçin ve sonra **Tamam** düğmesini seçin.

5. NativeMathSDKSample için proje özelliklerini görüntüleyin.

    Referansı eklediğinizde *NativeMathSDK.props'ta* tanımladığınız özellikler uygulandı. Projenin **Yapılandırma Özellikleri'nin** **VC++ Dizinleri** özelliğini inceleyerek özelliklerin uygulandığını doğrulayabilirsiniz.

6. **Solution Explorer'da** **MainPage.xaml'ı**açın ve içeriğini değiştirmek için aşağıdaki XAML'yi kullanın:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Bu kodu eşleştirmek için *Mainpage.xaml.h'yi* güncelleştirin:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Bu koda uyacak şekilde *MainPage.xaml.cpp* güncelleştirin:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Uygulamayı çalıştırmak için **F5** tuşunu seçin.

10. Uygulamada, herhangi iki sayı girin, bir işlem seçin **=** ve sonra düğmeyi seçin.

     Doğru sonuç görüntülenir.

    Bu gözden geçirme, [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bir kitaplığa ve[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] kitaplığa çağrı yapmak için uzantı SDK'nın nasıl oluşturulup kullanılacağını gösterdi.

## <a name="next-steps"></a>Sonraki adımlar

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: C# veya Visual Basic kullanarak Bir SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Yazılım geliştirme kiti oluşturma](../extensibility/creating-a-software-development-kit.md)
