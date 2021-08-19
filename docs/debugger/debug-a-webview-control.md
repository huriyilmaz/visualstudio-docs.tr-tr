---
title: WebView denetimi (UWP) hata ayıklaması | Microsoft Docs
description: Windows Runtime uygulamasında kullanılan WebView denetimlerini incelemeyi ve hata ayıklamayı öğrenin. DOM Gezgini Ve JavaScript Konsolu penceresini kullanabilirsiniz.
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
ms.openlocfilehash: 3198685acc8ad33a545bf55628c99e78d104d251
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059157"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>UWP Uygulamasında WebView denetiminde hata ayıklama

 Windows Runtime uygulamasında denetimleri incelemek ve hata ayıklamak için Visual Studio betik hata ayıklayıcısını eklemek `WebView` üzere yapılandırabilirsiniz. Hata ayıklayıcıyı kullanarak denetimlerle `WebView` etkileşim kurmanın iki yolu vardır:

- Örnek için [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md) açın, DOM öğelerini inceler, CSS stili sorunlarını araştırarak ve stillerde dinamik `WebView` olarak işlenmiş değişiklikleri test eder.

- Web sayfasını seçin veya örnekte JavaScript Konsolu penceresinde hedef olarak görüntülenir ve ardından konsol komutlarını kullanarak `iFrame` `WebView` web sayfasıyla etkileşime girin. [](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) Konsol, geçerli betik yürütme bağlamına erişim sağlar.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Hata ayıklayıcıyı ekleme (C#, Visual Basic, C++)

1. Bu Visual Studio, Windows `WebView` Runtime uygulamanıza bir denetim ekleyin.

2. Bu Çözüm Gezgini, projenin kısayol menüsünden **Özellikler'i** seçerek projenin özelliklerini açın.

3. Hata **Ayıkla'ya seçin.** Uygulama işlemi **listesinde Betik'i** **seçin.**

     ![Betik hata ayıklayıcısını ekleme](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. (İsteğe bağlı) Visual Studio'nin Express olmayan sürümleri için Araçlar > Seçenekler > Hata Ayıklama **>** Tam Zamanında 'ı seçerek ve ardından Betik için JIT hata ayıklamasını devre dışı bırakarak tam zamanında (JIT) hata ayıklamayı devre dışı edin.

    > [!NOTE]
    > JIT hata ayıklamayı devre dışı bırakarak, bazı web sayfalarında oluşan işlanmamış özel durumlar için iletişim kutularını gizleyebilirsiniz. Bu Visual Studio Express, JIT hata ayıklaması her zaman devre dışı bırakılır.

5. Hata ayıklamaya başlamak için F5'e basın.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>WebView DOM Gezgini incelemek ve hata ayıklamak için web sitesini kullanma

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleme. Yönergeler için ilk bölüme bakın.

2. Henüz uygulamanıza bir denetim ekleyin ve `WebView` hata ayıklamaya başlamak için F5 tuşuna basın.

3. Denetimlerini içeren `Webview` sayfaya gidin.

4. Hata ayıkla DOM Gezgini , Windows , DOM Gezgini ve ardından incelemek istediğiniz URL'nin URL'sini seçerek denetimin DOM Gezgini `WebView` penceresini   `WebView` açın.

     ![DOM Gezgini](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     ile DOM Gezgini, `WebView` yeni bir sekme olarak görüntülenir ve Visual Studio.

5. Kullanarak CSS stillerini ayıklama konusunda açıklandığı gibi canlı DOM öğelerini ve [CSS stillerini DOM Gezgini.](quickstart-debug-html-and-css.md)

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>WebView denetimi incelemek ve hata ayıklamak için JavaScript Konsolu penceresini kullanma

1. (C#, Visual Basic, C++) Betik hata ayıklayıcısını uygulamanıza ekleme. Yönergeler için ilk bölüme bakın.

2. Henüz uygulamanıza bir denetim ekleyin ve `WebView` hata ayıklamaya başlamak için F5 tuşuna basın.

3. Hata ayıkla , Windows , JavaScript Konsolu'nu `WebView` **seçerek denetimin** **JavaScript Konsolu penceresini açın.** 

     JavaScript Konsolu penceresi görüntülenir.

4. Denetimlerini içeren `Webview` sayfaya gidin.

5. Konsol penceresinde, Hedef listesinde denetim tarafından `iFrame` görüntülenen web sayfasını veya bir `WebView` **öğesini** seçin.

     ![JavaScript konsol penceresinde hedef seçimi](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > konsolunu kullanarak tek bir , paylaşım sözleşmesi veya `WebView` web çalışanı ile aynı anda etkileşim `iFrame` kurabilirsiniz. Her öğe, web platformu ana bilgisayarının ayrı bir örneğini gerektirir (WWAHost.exe). Tek tek bir konakla etkileşim kurabilirsiniz.

6. Hızlı [Başlangıç: JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) ve JavaScript Konsol komutlarında hata ayıklama makalesinde açıklandığı gibi uygulamanıza değişkenleri görüntüleyebilirsiniz ve [değiştirebilir veya konsol komutlarını kullanabilirsiniz.](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)