---
title: WebView denetiminde hata ayıklama (UWP) | Microsoft Docs
description: Windows Çalışma Zamanı uygulamasında kullanılan WebView denetimlerini incelemeyi ve hata ayıklamayı öğrenin. DOM Gezgini 'ni ve JavaScript Konsol penceresini kullanabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: cdf7632e28e0055b874ef54ae7c6379f623ca6b365a88018641501f56ab40fa9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345977"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>UWP uygulamasında bir WebView denetiminde hata ayıklama

 Windows Çalışma Zamanı uygulamasındaki denetimleri incelemek ve hatalarını ayıklamak için `WebView` , uygulamanızı başlattığınızda betik hata ayıklayıcısını eklemek üzere Visual Studio yapılandırabilirsiniz. Hata ayıklayıcıyı kullanarak denetimlerle etkileşimde bulunmak için iki yol vardır `WebView` :

- Bir örnek için [DOM Gezginini](../debugger/quickstart-debug-html-and-css.md) açın `WebView` , Dom ÖĞELERINI inceleyin, CSS stili sorunları araştırın ve dinamik olarak işlenen değişiklikleri stillerde test edin.

- `iFrame`JavaScript Konsol penceresinde Web sayfasını seçin veya `WebView` bir hedef olarak örnekte görüntüleniyorsa, [](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) konsol komutlarını kullanarak Web sayfası ile etkileşime geçin. Konsol, geçerli betik yürütme bağlamına erişim sağlar.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcıyı iliştirme (C#, Visual Basic, C++)

1. Visual Studio, `WebView` Windows Çalışma Zamanı uygulamanıza bir denetim ekleyin.

2. Çözüm Gezgini, proje için kısayol menüsünden **Özellikler** ' i seçerek projenin özelliklerini açın.

3. **Hata Ayıkla**' yı seçin. **Uygulama işlemi** listesinde, **komut dosyası**' nı seçin.

     ![Betik hata ayıklayıcısını iliştirme](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. Seçim Visual Studio Express olmayan sürümleri için, tam zamanında (jıt) hata ayıklamayı devre dışı bırakarak **araç > seçeneklerini > hata ayıklama >** ve sonra betik için jıt hata ayıklamayı devre dışı bırakın.

    > [!NOTE]
    > JıT hata ayıklamayı devre dışı bırakarak, bazı Web sayfalarında oluşan işlenmemiş özel durumlar için iletişim kutularını gizleyebilirsiniz. Visual Studio Express, jıt hata ayıklama her zaman devre dışıdır.

5. Hata ayıklamaya başlamak için F5'e basın.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için DOM Gezginini Kullanma

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.

2. Henüz yapmadıysanız, uygulamanıza bir denetim ekleyin `WebView` ve hata ayıklamayı başlatmak Için F5 'e basın.

3. `Webview`Denetim (ler) i içeren sayfaya gidin.

4. `WebView` **hata ayıkla**, **Windows**, **dom gezgini**' ni seçerek denetim için dom gezgini penceresini açın ve ardından incelemek istediğiniz URL 'yi seçin `WebView` .

     ![DOM Gezgini 'ni açma](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     İle İlişkili DOM Gezgini `WebView` Visual Studio yeni bir sekme olarak görünür.

5. [DOM Gezgini 'ni kullanarak CSS stillerinde hata ayıklama](quickstart-debug-html-and-css.md)bölümünde açıklandığı gıbı canlı Dom ÖĞELERINI ve CSS stillerini görüntüleyin ve değiştirin.

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>WebView denetimini incelemek ve hatalarını ayıklamak için JavaScript Konsol penceresini kullanın

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleyin. Yönergeler için ilk bölüme bakın.

2. Henüz yapmadıysanız, uygulamanıza bir denetim ekleyin `WebView` ve hata ayıklamayı başlatmak Için F5 'e basın.

3. `WebView` **hata ayıkla**, **Windows**, **javascript konsolunu** seçerek denetim için javascript konsol penceresini açın.

     JavaScript konsol penceresi görüntülenir.

4. `Webview`Denetim (ler) i içeren sayfaya gidin.

5. Konsol penceresinde, Web sayfasını veya `iFrame` `WebView` **hedef** listedeki denetim tarafından bir görüntülenmiş i seçin.

     ![JavaScript Konsol penceresinde hedef seçimi](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Konsolunu kullanarak tek seferde tek bir, `WebView` `iFrame` paylaşabilir veya Web çalışanı ile etkileşim kurabilirsiniz. Her öğe Web Platformu ana bilgisayarının (WWAHost.exe) ayrı bir örneğini gerektirir. Aynı anda bir ana bilgisayar ile etkileşim kurabilirsiniz.

6. [Hızlı başlangıç: hata ayıklama JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) ve [JavaScript konsol komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)bölümünde açıklandığı gibi uygulamanızdaki değişkenleri görüntüleyin ve değiştirin ya da konsol komutlarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)