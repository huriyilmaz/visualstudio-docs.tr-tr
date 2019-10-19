---
title: WebView denetiminde hata ayıklama (UWP) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 8ba9b0eb17a492bf1912281038ffc35732ece96d
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589068"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>UWP uygulamasında bir WebView denetiminde hata ayıklama

 Bir Windows Çalışma Zamanı uygulamasındaki `WebView` denetimlerini incelemek ve hatalarını ayıklamak için Visual Studio 'Yu, uygulamanızı başlattığınızda betik hata ayıklayıcısını ekleyecek şekilde yapılandırabilirsiniz. Hata ayıklayıcıyı kullanarak `WebView` denetimleriyle etkileşimde bulunmak için iki yol vardır:

- Bir `WebView` örneği için [DOM Gezginini](../debugger/quickstart-debug-html-and-css.md) açın, DOM öğelerini ınceleyın, CSS stili sorunları araştırın ve dinamik olarak işlenen değişiklikleri stillerde test edin.

- [JavaScript Konsol](../debugger/javascript-console-commands.md?view=vs-2017) penceresinde bir hedef olarak `WebView` örneğinde görünen Web sayfasını veya `iFrame` seçin ve ardından konsol komutlarını kullanarak Web sayfası ile etkileşime geçin. Konsol, geçerli betik yürütme bağlamına erişim sağlar.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcıyı iliştirme (C#, Visual Basic, C++)

1. Visual Studio 'da Windows Çalışma Zamanı uygulamanıza `WebView` bir denetim ekleyin.

2. Çözüm Gezgini, proje için kısayol menüsünden **Özellikler** ' i seçerek projenin özelliklerini açın.

3. **Hata Ayıkla**' yı seçin. **Uygulama işlemi** listesinde, **komut dosyası**' nı seçin.

     ![Betik hata ayıklayıcısını iliştirme](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. Seçim Visual Studio 'nun Express olmayan sürümleri için, Araçlar > Seçenekler ' i seçerek tam zamanında (JıT) hata ayıklamayı devre dışı bırakın **> anında hata ayıklama >** ve ardından BETIK için JIT hata ayıklamayı devre dışı bırakabilirsiniz.

    > [!NOTE]
    > JıT hata ayıklamayı devre dışı bırakarak, bazı Web sayfalarında oluşan işlenmemiş özel durumlar için iletişim kutularını gizleyebilirsiniz. Visual Studio Express, JıT hata ayıklama her zaman devre dışıdır.

5. Hata ayıklamayı başlatmak için F5 'e basın.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için DOM Gezginini Kullanma

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.

2. Henüz yapmadıysanız, uygulamanıza bir `WebView` denetimi ekleyin ve hata ayıklamayı başlatmak için F5 'e basın.

3. @No__t_0 denetimleri içeren sayfaya gidin.

4. **Hata Ayıkla**, **Windows**, **Dom gezgini**ve ardından denetlemek istediğiniz `WebView` URL 'Sini seçerek `WebView` denetimine yönelik DOM Gezgini penceresini açın.

     ![DOM Gezgini 'ni açma](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     @No__t_0 ilişkili DOM Gezgini, Visual Studio 'da yeni bir sekme olarak görünür.

5. [DOM Gezgini 'ni kullanarak CSS stillerinde hata ayıklama](/visualstudio/debugger/quickstart-debug-html-and-css)bölümünde açıklandığı gıbı canlı Dom ÖĞELERINI ve CSS stillerini görüntüleyin ve değiştirin.

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için JavaScript Konsol penceresini kullanın

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.

2. Henüz yapmadıysanız, uygulamanıza bir `WebView` denetimi ekleyin ve hata ayıklamayı başlatmak için F5 'e basın.

3. **Hata Ayıkla**, **Windows**, **JavaScript Konsolu**seçeneklerini belirleyerek `WebView` denetimi için JavaScript Konsol penceresini açın.

     JavaScript konsol penceresi görüntülenir.

4. @No__t_0 denetimleri içeren sayfaya gidin.

5. Konsol penceresinde, **hedef** listedeki `WebView` denetimi tarafından görüntülenmiş Web sayfasını veya `iFrame` seçin.

     ![JavaScript Konsol penceresinde hedef seçimi](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Konsolunu kullanarak tek bir `WebView`, `iFrame`, sözleşmeyle veya Web çalışanıyla etkileşim kurabilirsiniz. Her öğe Web Platformu ana bilgisayarının (WWAHost. exe) ayrı bir örneğini gerektirir. Aynı anda bir ana bilgisayar ile etkileşim kurabilirsiniz.

6. [Hızlı başlangıç: hata ayıklama JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) ve [JavaScript konsol komutları](../debugger/javascript-console-commands.md?view=vs-2017)bölümünde açıklandığı gibi uygulamanızdaki değişkenleri görüntüleyin ve değiştirin ya da konsol komutlarını kullanın.

## <a name="see-also"></a>Ayrıca Bkz.

- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)