---
title: 'İzlenecek yol: C++ kullanarak SDK oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202062"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>İzlenecek Yol: C++ Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, yerel bir C++ matematik kitaplığı SDK 'sı oluşturmayı, SDK 'Yı Visual Studio uzantısı (VSıX) olarak paketlemeyi ve sonra bir uygulama oluşturmak için kullanmayı gösterir. İzlenecek yol aşağıdaki adımlara ayrılmıştır:  
  
- [Yerel ve Windows Çalışma Zamanı kitaplıklarını oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [NativeMathVSIX Extension projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Yerel ve Windows Çalışma Zamanı kitaplıklarını oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. Şablon listesinde **Visual C++**, **Windows Mağazası**' nı genişletin ve ardından **dll (Windows Mağazası uygulamaları)** şablonunu seçin. **Ad** kutusunda, `NativeMath` öğesini belirtin ve sonra **Tamam** düğmesini seçin.  
  
3. NativeMath. h öğesini aşağıdaki kodla eşleşecek şekilde güncelleştirin.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. NativeMath. cpp öğesini bu kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. **Çözüm Gezgini**' de, **' Nativemath ' çözümünün**kısayol menüsünü açın ve **Ekle**, **Yeni proje**' yi seçin.  
  
6. Şablonlar listesinde **Visual C++**' ı genişletin ve **Windows çalışma zamanı bileşen** şablonunu seçin. **Ad** kutusunda, `NativeMathWRT` öğesini belirtin ve sonra **Tamam** düğmesini seçin.  
  
7. Class1. h 'yi bu kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Class1. cpp ' i bu kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Menü çubuğunda **Oluştur**, **çözüm oluştur**' u seçin.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> NativeMathVSIX Extension projesi oluşturmak için  
  
1. **Çözüm Gezgini**' de, **' Nativemath ' çözümünün**kısayol menüsünü açın ve **Ekle**, **Yeni proje**' yi seçin.  
  
2. Şablonlar listesinde, **Visual C#**, **genişletilebilirlik**' i genişletin ve **VSIX paketi**' ni seçin. **Ad** kutusunda, **NativeMathVSIX**belirtin ve sonra **Tamam** düğmesini seçin.  
  
3. VSıX bildirim Tasarımcısı göründüğünde kapatın.  
  
4. **Çözüm Gezgini**, **Source. Extension. valtmanifest**için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.  
  
5. Varolan XML 'yi değiştirmek için aşağıdaki XML 'i kullanın.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. **Çözüm Gezgini**' de, **NativeMathVSIX** projesi için kısayol menüsünü açın ve **Ekle**, **Yeni öğe**' yi seçin.  
  
7. **Visual C# öğeleri**listesinde, **veriler**' i genişletin ve ardından **XML dosyası**' nı seçin. **Ad** kutusunda, `SDKManifest.xml` öğesini belirtin ve sonra **Tamam** düğmesini seçin.  
  
8. Dosyanın içeriğini değiştirmek için bu XML 'i kullanın:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. **Çözüm Gezgini**, **NativeMathVSIX** projesinde, bu klasör yapısını oluşturun:  
  
    ```  
  
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
  
10. **Çözüm Gezgini**' de, **' Nativemath ' çözümünün**kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.  
  
11. **Dosya Gezgini**'nde, \NativeMath\NativeMath.h kopyalayın ve ardından **Çözüm Gezgini**, **NativeMathVSIX** projesinde, \DesignTime\CommonConfiguration\Neutral\Include\ klasörüne yapıştırın.  
  
     \Debug\NativeMath\NativeMath.lib kopyalayın ve \DesignTime\Debug\x86\ klasörüne yapıştırın.  
  
     \Debug\NativeMath\NativeMath.dll kopyalayın ve \Redist\Debug\x86\ klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT.dll kopyalayın ve RedistDebugx86 klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT. winmd kopyalayın ve ReferencesCommonConfigurationNeutral klasörüne yapıştırın.  
  
     DebugNativeMathWRTNativeMathWRT. pri öğesini kopyalayın ve ReferencesCommonConfigurationNeutral klasörüne yapıştırın.  
  
12. \DesignTime\Debug\x86\ klasöründe, NativeMathSDK. props adlı bir metin dosyası oluşturun ve ardından içine aşağıdaki içeriği yapıştırın:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Menü çubuğunda **Görünüm**, **diğer pencereler**, **Özellikler penceresi** (klavye: F4 anahtarını seçin) öğesini seçin.  
  
14. **Çözüm Gezgini**, **NativeMathWRT. winmd** dosyasını seçin. **Özellikler** penceresinde, **derleme eylemi** özelliğini **IÇERIK**olarak değiştirin ve ardından **VSIX özelliğindeki içerme** özelliğini **true**olarak değiştirin.  
  
     **SimpleMath. pri** dosyası için bu işlemi tekrarlayın.  
  
     **Nativemath. lib** dosyası için bu işlemi tekrarlayın.  
  
     **NativeMathSDK. props** dosyası için bu işlemi tekrarlayın.  
  
15. **Çözüm Gezgini**, **nativemath. h** dosyasını seçin. **Özellikler** penceresinde **VSIX Içindeki Include** özelliğini **true**olarak değiştirin.  
  
     **NativeMath.dll** dosyası için bu işlemi tekrarlayın.  
  
     **NativeMathWRT.dll** dosyası için bu işlemi tekrarlayın.  
  
     **SDKManifest.xml** dosyası için bu işlemi tekrarlayın.  
  
16. Menü çubuğunda **Oluştur**, **çözüm oluştur**' u seçin.  
  
17. **Çözüm Gezgini**' de, **NativeMathVSIX** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.  
  
18. **Dosya Gezgini**'nde, \bin\Debug\ klasörüne gidin ve yüklemeyi başlatmak için NativeMathVSIX. vsix ' yi çalıştırın.  
  
19. **Yükleme düğmesini seçin** , yüklemenin bitmesini bekleyin ve ardından Visual Studio 'yu yeniden başlatın.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. Şablon listesinde **Visual C++**, **Windows Mağazası**' nı genişletin ve **boş uygulama**' yı seçin. **Ad** kutusunda, **NativeMathSDKSample**belirtin ve sonra **Tamam** düğmesini seçin.  
  
3. **Çözüm Gezgini**' de, **NativeMathSDKSample** projesi için kısayol menüsünü açın ve **Ekle**, **başvuru**' yı seçin.  
  
4. **Ortak özellikler**, **çerçeve ve başvurular** Özellik sayfasında, başvuru türleri listesinde, **Windows**' u genişletin ve **Uzantılar**' ı seçin. Ayrıntılar bölmesinde, **Yerel matematık SDK** uzantısını seçin ve ardından **Yeni Başvuru Ekle** düğmesini seçin.  
  
5. **Başvuru Ekle** Iletişim kutusunda **Yerel matematik SDK 'sı** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.  
  
6. NativeMathSDKSample için proje özelliklerini görüntüleyin.  
  
    NativeMathSDK. props içinde tanımladığınız özellikler, başvuruyu eklediğinizde uygulandı. Projenin **yapılandırma özelliklerinin** **VC + + dizinleri** özelliğini inceleyerek bunu doğrulayabilirsiniz.  
  
7. **Çözüm Gezgini**, MainPage. xaml ' yi açın ve ardından içeriğini değiştirmek IÇIN aşağıdaki xaml 'yi kullanın:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. MainPage. xaml. h öğesini bu kodla eşleşecek şekilde güncelleştirin:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. MainPage. xaml. cpp öğesini bu kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Uygulamayı çalıştırmak için F5 tuşunu seçin.  
  
11. Uygulamada, iki sayı girin, bir işlem seçin ve ardından **=** düğmeyi seçin.  
  
     Doğru sonuç görüntülenir.  
  
    Bu izlenecek yol [!INCLUDE[wrt](../includes/wrt-md.md)] , bir kitaplık ve kitaplık olmayan bir uzantı SDK 'sı oluşturmayı ve kullanmayı gösterdi [!INCLUDE[wrt](../includes/wrt-md.md)] .  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
