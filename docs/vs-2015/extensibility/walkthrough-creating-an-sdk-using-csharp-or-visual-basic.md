---
title: 'İzlenecek yol: veya Visual Basic kullanarak C# SDK oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558213"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>İzlenecek Yol: C# veya Visual Basic Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, Visual C# Studio kullanarak basit bir matematik kitaplığı SDK 'sı oluşturmayı ve sonra SDK 'Yı bir Visual Studio UZANTıSı (VSIX) olarak paketlemeyi öğreneceksiniz. Aşağıdaki yordamları tamamlayacaksınız:  
  
- [SimpleMath Windows Çalışma Zamanı bileşeni oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [SimpleMathVSIX Extension projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a>SimpleMath Windows Çalışma Zamanı bileşeni oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Yeni proje**' yi seçin.  
  
2. Şablonlar listesinde,  **C# Visual** veya **Visual Basic**öğesini genişletin, **Windows Mağazası** düğümünü seçin ve ardından **Windows çalışma zamanı bileşen** şablonunu seçin.  
  
3. **Ad** kutusunda, **SimpleMath**' i belirtip **Tamam** düğmesini seçin.  
  
4. **Çözüm Gezgini**, **SimpleMath** proje düğümünün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
5. **Class1.cs** öğesini **arithmetic.cs** olarak yeniden adlandırın ve aşağıdaki kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. **Çözüm Gezgini**' de, **Çözüm ' SimpleMath '** düğümünün kısayol menüsünü açın ve **Configuration Manager**öğesini seçin.  
  
     **Configuration Manager** iletişim kutusu açılır.  
  
7. **Etkin çözüm yapılandırması** listesinde **yayın**' ı seçin.  
  
8. **Yapılandırma** sütununda, **SimpleMath** satırının **Release**olarak ayarlandığını doğrulayın ve ardından değişikliği kabul etmek için **Kapat** düğmesini seçin.  
  
    > [!IMPORTANT]
    > SimpleMath bileşeni için SDK yalnızca bir yapılandırma içerir. Bu yapılandırma yayın derlemesi olmalıdır veya bileşeni kullanan uygulamalar[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]için sertifika geçirmez.  
  
9. **Çözüm Gezgini**, **SimpleMath** proje düğümünün kısayol menüsünü açın ve ardından **Oluştur**' u seçin.  
  
## <a name="createVSIX"></a>SimpleMathVSIX Extension projesi oluşturmak için  
  
1. **Çözüm ' SimpleMath '** düğümünün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.  
  
2. Şablonlar listesinde, **görsel C#**  veya **Visual Basic**' ı genişletin, **genişletilebilirlik** düğümünü seçin ve **VSIX proje** şablonunu seçin.  
  
3. **Ad** kutusunda, **SimpleMathVSIX**belirtin ve sonra **Tamam** düğmesini seçin.  
  
4. **Çözüm Gezgini**, **Source. Extension. valtmanifest** öğesini seçin.  
  
5. Menü çubuğunda, **Görünüm**, **kod**' ı seçin.  
  
6. Mevcut XML 'i aşağıdaki XML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. **Çözüm Gezgini**, **SimpleMathVSIX** projesini seçin.  
  
8. Menü çubuğunda **Proje**, **Yeni öğe Ekle**' yi seçin.  
  
9. **Ortak öğeler**listesinde, **veriler**' i genişletin ve ardından **XML dosyası**' nı seçin.  
  
10. **Ad** kutusunda, `SDKManifest.xml`belirtin ve sonra **Ekle** düğmesini seçin.  
  
11. **Çözüm Gezgini**' de, `SDKManifest.xml`için kısayol menüsünü açın, **Özellikler**' i seçin ve ardından **VSIX özelliğindeki Ekle** ' nin değerini **true**olarak değiştirin.  
  
12. Dosyanın içeriğini aşağıdaki XML ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. **Çözüm Gezgini**, **SimpleMathVSIX** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni klasör**' i seçin.  
  
14. Klasörü `references`olarak yeniden adlandırın.  
  
15. **Başvurular** klasörünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni klasör**' i seçin.  
  
16. Alt klasörü `commonconfiguration`olarak yeniden adlandırın, içinde bir alt klasör oluşturun ve alt klasörü `neutral`adlandırın.  
  
17. Önceki dört adımı yineleyin, bu kez ilk klasörü `redist`olarak yeniden adlandırın.  
  
     Proje artık aşağıdaki klasör yapısını içerir:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. **Çözüm Gezgini**, **SimpleMath** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.  
  
19. **Dosya Gezgini**'nde bin\release klasörüne gidin, SimpleMath. winmd dosyası için kısayol menüsünü açın ve **Kopyala**' yı seçin.  
  
20. **Çözüm Gezgini**, dosyayı **SimpleMathVSIX** projesindeki references\commonconfiguration\neutral klasörüne yapıştırın.  
  
21. SimpleMath. pri dosyasını **SimpleMathVSIX** projesindeki redist\commonconfiguration\neutral klasörüne yapıştırarak önceki adımı yineleyin.  
  
22. **Çözüm Gezgini**, **SimpleMath. winmd**öğesini seçin.  
  
23. Menü çubuğunda **Görünüm**, **Özellikler** (klavye: F4 anahtarını seçin) öğesini seçin.  
  
24. **Özellikler** penceresinde, **derleme eylemi** özelliğini **IÇERIK**olarak değiştirin ve ardından **VSIX özelliğindeki içerme** özelliğini **true**olarak değiştirin.  
  
25. **Çözüm Gezgini**' de, **SimpleMath. pri**için bu işlemi tekrarlayın.  
  
26. **Çözüm Gezgini**, **SimpleMathVSIX** projesini seçin.  
  
27. Menü çubuğunda **Build**, **Build SimpleMathVSIX**öğesini seçin.  
  
28. **Çözüm Gezgini**' de, **SimpleMathVSIX** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin.  
  
29. **Dosya Gezgini**'nde, \bin\Release klasörü ' ne gidin ve ardından yüklemek için SimpleMathVSIX. vsix ' yi çalıştırın.  
  
30. **Yükleme düğmesini seçin** , yüklemenin bitmesini bekleyin ve ardından Visual Studio 'yu yeniden başlatın.  
  
## <a name="createSample"></a>Sınıf kitaplığını kullanan bir örnek uygulama oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Yeni proje**' yi seçin.  
  
2. Şablonlar listesinde, **Visual C#**  veya **Visual Basic**öğesini genişletin ve ardından **Windows Mağazası** düğümünü seçin.  
  
3. **Boş uygulama** şablonunu seçin, projeyi **ArithmeticUI**olarak adlandırın ve **Tamam** düğmesini seçin.  
  
4. **Çözüm Gezgini**' de, **ArithmeticUI** projesi için kısayol menüsünü açın ve **Ekle**, **başvuru**' yı seçin.  
  
5. Başvuru türleri listesinde **Windows**' u ve ardından **Uzantılar**' ı seçin.  
  
6. Ayrıntılar bölmesinde **basit matematık SDK** uzantısı ' nı seçin.  
  
    SDK 'niz hakkında ek bilgiler görüntülenir. Bu kılavuzda daha önce bulunan SDKManifest. xml dosyasında belirttiğiniz gibi https://docs.microsoft.comaçmak için **daha fazla bilgi** bağlantısını seçebilirsiniz.  
  
7. **Başvuru Yöneticisi** Iletişim kutusunda **basit matematik SDK 'sı** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.  
  
8. Menü çubuğunda **görüntüle**, **nesne tarayıcısı**öğesini seçin.  
  
9. **Gözden** geçirme listesinde **basit matematik**' ı seçin.  
  
     Artık SDK 'da neler olduğunu keşfedebilirsiniz.  
  
10. **Çözüm Gezgini**, MainPage. xaml ' yi açın ve IÇERIĞINI aşağıdaki xaml ile değiştirin:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. MainPage.xaml.cs öğesini aşağıdaki kodla eşleşecek şekilde güncelleştirin:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Uygulamayı çalıştırmak için F5 tuşunu seçin.  
  
13. Uygulamada, iki sayı girin, bir işlem seçin ve sonra **=** düğmesini seçin.  
  
     Doğru sonuç görüntülenir.  
  
    Bir uzantı SDK 'sını başarıyla oluşturdunuz ve kullandınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol:  kullanarak C++ SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)  
 [Izlenecek yol: JavaScript  kullanarak SDK oluşturma](walkthrough-creating-an-sdk-using-javascript.md)  
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
