---
title: WebView denetiminde hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817156"
---
# <a name="debug-a-webview-control"></a>WebView denetiminde hata ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Windows Çalışma Zamanı uygulamasındaki denetimleri incelemek ve hatalarını ayıklamak için `WebView` Visual Studio 'yu, uygulamanızı başlattığınızda betik hata ayıklayıcısını ekleyecek şekilde yapılandırabilirsiniz. Visual Studio 2013 güncelleştirme 2 ' den itibaren, `WebView` hata ayıklayıcıyı kullanarak denetimlerle etkileşimde bulunmak için iki yol vardır:  
  
- Bir örnek için [DOM Gezginini](../debugger/quickstart-debug-html-and-css.md) açın `WebView` , Dom ÖĞELERINI inceleyin, CSS stili sorunları araştırın ve dinamik olarak işlenen değişiklikleri stillerde test edin.  
  
- `iFrame`JavaScript Konsol penceresinde Web sayfasını seçin veya `WebView` bir hedef olarak örnekte görüntüleniyorsa, [JavaScript Console](../debugger/javascript-console-commands.md) konsol komutlarını kullanarak Web sayfası ile etkileşime geçin. Konsol, geçerli betik yürütme bağlamına erişim sağlar.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcıyı iliştirme (C#, Visual Basic, C++)  
  
1. Visual Studio 'da `WebView` Windows çalışma zamanı uygulamanıza bir denetim ekleyin.  
  
2. Çözüm Gezgini, proje için kısayol menüsünden **Özellikler** ' i seçerek projenin özelliklerini açın.  
  
3. **Hata Ayıkla**' yı seçin. **Uygulama işlemi** listesinde, **komut dosyası**' nı seçin.  
  
     ![Betik hata ayıklayıcısını iliştirme](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Seçim Visual Studio 'nun Express olmayan sürümleri için **Araçlar**, **Seçenekler**, **hata ayıklama**, **tam zamanında**ve ardından betik için JIT hata ayıklamayı devre dışı bırakarak tam zamanında (JIT) hata ayıklamayı devre dışı bırakın.  
  
    > [!NOTE]
    > JıT hata ayıklamayı devre dışı bırakarak, bazı Web sayfalarında oluşan işlenmemiş özel durumlar için iletişim kutularını gizleyebilirsiniz. Visual Studio Express, JıT hata ayıklama her zaman devre dışıdır.  
  
5. Hata ayıklamaya başlamak için F5'e basın.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için DOM Gezginini Kullanma  
  
1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.  
  
2. Henüz yapmadıysanız, uygulamanıza bir denetim ekleyin `WebView` ve hata ayıklamayı başlatmak Için F5 'e basın.  
  
3. `Webview`Denetim (ler) i içeren sayfaya gidin.  
  
4. `WebView` **Hata Ayıkla**, **Windows**, **Dom GEZGINI**' ni seçerek denetim için DOM Gezgini penceresini açın ve ardından incelemek istediğiniz URL 'yi seçin `WebView` .  
  
     ![DOM Gezgini 'ni açma](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     İle İlişkili DOM Gezgini, `WebView` Visual Studio 'da yeni bir sekme olarak görünür.  
  
5. [DOM Gezgini 'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)bölümünde açıklandığı gıbı canlı Dom ÖĞELERINI ve CSS stillerini görüntüleyin ve değiştirin.  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için JavaScript Konsol penceresini kullanın  
  
1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.  
  
2. Henüz yapmadıysanız, uygulamanıza bir denetim ekleyin `WebView` ve hata ayıklamayı başlatmak Için F5 'e basın.  
  
3. `WebView` **Hata Ayıkla**, **Windows**, **JavaScript Konsolu**' nu seçerek denetim için JavaScript Konsol penceresini açın.  
  
     JavaScript konsol penceresi görüntülenir.  
  
4. `Webview`Denetim (ler) i içeren sayfaya gidin.  
  
5. Konsol penceresinde, Web sayfasını veya `iFrame` `WebView` **hedef** listedeki denetim tarafından bir görüntülenmiş i seçin.  
  
     ![JavaScript Konsol penceresinde hedef seçimi](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > Konsolunu kullanarak tek seferde tek bir, `WebView` `iFrame` paylaşabilir veya Web çalışanı ile etkileşim kurabilirsiniz. Her öğe Web Platformu ana bilgisayarının (WWAHost.exe) ayrı bir örneğini gerektirir. Aynı anda bir ana bilgisayar ile etkileşim kurabilirsiniz.  
  
6. [Hızlı başlangıç: hata ayıklama JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) ve [JavaScript konsol komutları](../debugger/javascript-console-commands.md)bölümünde açıklandığı gibi uygulamanızdaki değişkenleri görüntüleyin ve değiştirin ya da konsol komutlarını kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
