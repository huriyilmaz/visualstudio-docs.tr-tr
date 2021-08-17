---
title: Konsol konsolunu kullanarak JavaScript hata | Microsoft Docs
description: JavaScript kullanarak yerleşik Universal Windows Platform (UWP) uygulamalarıyla etkileşim kurmak ve bu uygulamalarda hata ayıklamak için Visual Studio'daki JavaScript Konsolu penceresini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- JavaScript
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6672e164978a97c4801c4d4d4481422a2c093582
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090505"
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Visual Studio'da konsolunu kullanarak JavaScript'te hata ayıklama

JavaScript kullanılarak yerleşik UWP uygulamalarıyla etkileşim kurmak ve bu uygulamalarda hata ayıklamak için JavaScript Konsolu penceresini kullanabilirsiniz. Bu özellikler, Visual Studio Araçları for Apache Cordova. Konsol komut başvurusu için bkz. [JavaScript Konsol komutları.](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)

JavaScript Konsolu penceresi şunları sağlar:

- Uygulamadaki nesneleri, değerleri ve iletileri konsol penceresine gönderin.

- Çalışan uygulamada yerel ve genel değişkenlerin değerlerini görüntüleme ve değiştirme.

- Nesne görselleştiricilerini görüntüleme.

- Geçerli betik bağlamında yürütülen JavaScript kodunu çalıştırın.

- Belge Nesne Modeli (DOM) ve Windows Runtime özel durumlarına ek olarak JavaScript hatalarını ve özel durumlarını görüntüleme.

- Ekranı temizleme gibi diğer görevleri gerçekleştirin. Komutların tam listesi için bkz. [JavaScript](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) Konsol komutları.

> [!TIP]
> JavaScript Konsolu penceresi kapalı ise Yeniden açmak için >  JavaScript **Windows**  >  **Hata Ayıkla'ya** tıklayın. Pencere yalnızca bir betik hata ayıklama oturumu sırasında görünür.

JavaScript Konsolu penceresini kullanarak hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan uygulamayla etkileşim kurabilirsiniz. Daha fazla bilgi için [bkz. Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md). DOM Gezgini kullanma ve kesme noktaları ayarlama gibi diğer JavaScript hata ayıklama özellikleri hakkında bilgi için bkz. Hızlı [Başlangıç:](../debugger/quickstart-debug-html-and-css.md) Html ve CSS'de hata ayıklama ve [Visual Studio.](debugging-windows-store-and-windows-universal-apps.md)

## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a> JavaScript Konsol penceresini kullanarak hata ayıklama
Aşağıdaki adımlarda bir uygulama `FlipView` oluşturularak JavaScript kodlama hatasının nasıl etkileşimli bir şekilde ayıklanası gösterildi.

> [!NOTE]
> Buradaki örnek uygulama bir UWP uygulamasıdır. Ancak, burada açıklanan konsol özellikleri, Visual Studio Araçları için Apache Cordova.

#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>FlipView uygulamasında JavaScript kodunda hata ayıklamak için

1. Dosya Yeni Dosya'Visual Studio seçerek yeni **bir**  >  **çözüm Project.**

2. JavaScript **Windows**  >  **Evrensel'i** ve ardından **WinJS Uygulaması'ı seçin.**

3. Proje için gibi bir ad yazın ve `FlipViewApp` uygulamayı oluşturmak **için Tamam'ı** seçin.

4. index.html öğesinin BODY öğesinde, mevcut HTML kodunu şu kodla değiştirin:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. default.css'yi açın ve seçici için `#fView` CSS'yi ekleyin:

    ```css
    #fView {
        background-color:#0094ff;
        height: 500px;
        margin: 25px;
    }
    ```

6. default.js açın ve kodu aşağıdaki JavaScript koduyla değiştirin:

    ```javascript
    (function () {
        "use strict";

        var app = WinJS.Application;
        var activation = Windows.ApplicationModel.Activation;

        var myData = [];
        for (var x = 0; x < 4; x++) {
            myData[x] = { flipImg: "/images/logo.png" }
        };

        var pages = new WinJS.Binding.List(myData, { proxy: true });

        app.onactivated = function (args) {
            if (args.detail.kind === activation.ActivationKind.launch) {
                if (args.detail.previousExecutionState !==
                activation.ApplicationExecutionState.terminated) {
                    // TODO: . . .
                } else {
                    // TODO: . . .
                }
                args.setPromise(WinJS.UI.processAll());

                updateImages();
            }
        };

        function updateImages() {

            pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });

        };

        app.oncheckpoint = function (args) {
        };

        app.start();

        var publicMembers = {
            items: pages
        };

        WinJS.Namespace.define("Data", publicMembers);

    })();
    ```

7. Hata ayıklama hedefi seçili değilse, Hata  Ayıklama araç çubuğundaki Cihaz düğmesinin yanındaki açılan listeden **Yerel** **Makine'yi** seçin:

    ![Hata ayıklama hedef listesini seçme](../debugger/media/js_select_target.png "JS_Select_Target")

8. Hata ayıklayıcıyı başlatmak için F5 tuşuna basın.

    Uygulama çalışır ancak görüntüler eksiktir. JavaScript Konsolu penceresindeki APPHOST hataları, görüntülerin eksik olduğunu gösterir.

9. Uygulama `FlipView` çalışırken konsol penceresi `Data.items` giriş istemine yazın (">>" simgesinin yanına) ve Enter tuşuna basın.

    Konsol penceresinde nesne `items` için bir görselleştirici görüntülenir. Bu, `items` nesnesinin örneği ekli olduğunu ve geçerli betik bağlamında kullanılabilir olduğunu gösterir. Konsol penceresinde, özellik değerlerini görüntülemek için bir nesnenin düğümlerine tıklarsınız (veya ok tuşlarını kullanabilirsiniz). Bu çizimde gördüğünüz gibi nesneye tıklarsanız, görüntü kaynağı başvurularının beklendiği gibi `items._data` yanlış olduğunu bulabilirsiniz. Varsayılan görüntüler (logo.png) nesnede hala mevcuttur ve beklenen görüntülerle birlikte eksik görüntüler vardır.

    ![JavaScript Konsolu penceresi](../debugger/media/js_console_window.png "JS_Console_Window")

    Ayrıca nesnede beklediğinizden çok daha `items._data` fazla öğe olduğunu unutmayın.

10. İstendiğinde yazın ve `Data.items.push` Enter tuşuna basın. Konsol penceresinde, bir proje dosyasında `push` uygulanan işlev için bir görselleştirici [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] gösterilir. Bu uygulamada, doğru öğeleri `push` eklemek için kullanıyoruz. IntelliSense'i kullanarak biraz araştırmayla, varsayılan görüntüleri değiştirmek için `setAt` kullanmamız gerektiğini anlarız.

11. Hata ayıklama oturumunu durdurmadan bu sorunu etkileşimli olarak düzeltmek için default.js açın ve işlevden şu kodu `updateImages` seçin:

    ```javascript
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

     Bu kodu kopyalayıp JavaScript Konsolu giriş istemine yapıştırın.

    > [!TIP]
    > JavaScript Konsolu giriş istemine birden çok kod satırı yapıştırsanız, konsol giriş istemi otomatik olarak çok satırlı moda geçer. Çok satırlı modu açmak ve kapatmak için Ctrl+Alt+M tuşlarına basabilirsiniz. Bir betiği çok satırlı modda çalıştırmak için Ctrl+Enter tuşlarına basın veya pencerenin sağ alt köşesindeki ok simgesini seçin. Daha fazla bilgi için [Bkz. JavaScript Konsolu penceresinde tek satırlı mod ve çok satırlı mod.](#SinglelineMultilineMode)

12. komut `push` isteminde işlevini ile değiştirerek işlev çağrılarını `pages.push` `Data.items.setAt` düzeltin. Düzeltilmiş kod aşağıdaki gibi olmalı:

    ```javascript
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

    > [!TIP]
    > yerine nesnesini kullanmak istemeniz, nesneyi kapsamda tutmak için kodunda bir `pages` `Data.items` kesme noktası `pages` ayarlamanız gerekir.

13. Betiği çalıştırmak için yeşil ok simgesini seçin.

14. Konsol giriş istemini tek satırlı moda değiştirmek için Ctrl+Alt+M tuşlarına basın ve ardından Girişi temizle **(kırmızı** "X") girişini seçin.

15. İstem `Data.items.length = 3` üzerine yazın ve Enter tuşuna basın. Bu, verilerden fazlalık öğeleri kaldırır.

16. Uygulamayı yeniden kontrol edin; doğru görüntülerin doğru sayfalarda olduğunu `FlipView` görüyorsunuz.

17. Bu DOM Gezgini güncelleştirilmiş DIV öğesini görebilir ve beklenen IMG öğelerini bulmak için alt ağacına gidin.

18. Hata AyıklamaYı **Durdur'u seçerek** veya Shift+F5 tuşlarına basarak hata ayıklamayı  >   durdurun ve kaynak kodu düzeltin.

    Düzeltilmiş örnek kod default.html sayfası için bkz. HTML, CSS ve JavaScript örnek [kodunda hata ayıklama.](../debugger/debug-html-css-and-javascript-sample-code.md)

## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a> Etkileşimli hata ayıklama ve kesme modu
JavaScript Konsol penceresi gibi JavaScript hata ayıklama araçlarını kullanırken kesme noktaları kullanabilir ve koda girebilirsiniz. Hata ayıklayıcıda çalışan bir program bir kesme noktasıyla karşılaştığında, hata ayıklayıcı programın yürütülmesini geçici olarak askıya alır. Yürütme askıya alınırsa programınız çalıştırma modundan kesme moduna geçer. Yürütmeyi herhangi bir zamanda sürdürabilirsiniz.

Bir program kesme modundayken, geçerli betik yürütme bağlamında geçerli olan betikleri ve komutları çalıştırmak için JavaScript Konsolu penceresini kullanabilirsiniz. Bu yordamda, daha önce oluşturduğunuz uygulamanın sabit sürümünü kullanarak kesme `FlipView` modunun kullanımını gösterebilirsiniz.

#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Bir kesme noktası ayarlamak ve uygulamada hata ayıklamak için

1. Uygulamanın default.html dosyasında işlevin kısayol menüsünü açın ve Kesme Noktası Ekle `FlipView` `updateImages()` Kesme **Noktası**  >  **seçeneğini belirleyin.**

2. Hata **Ayıklama araç** çubuğundaki Hata Ayıklamayı Başlat **düğmesinin yanındaki** açılan listeden Yerel **Makine'yi** seçin.

3. Hata **AyıklamaYı Başlat**  >  **Hata Ayıklama'ya seçin** veya F5 tuşuna basın.

    Yürütme işleve ulaştığında uygulama kesme moduna girer ve geçerli `updateImages()` program yürütme satırı sarıyla vurgulanır.

    ![JavaScript Konsolu ile kesme modunu kullanma](../debugger/media/js_breakmode.png "JS_BreakMode")

    Geçerli hata ayıklama oturumunu sonlandırmadan program durumunu hemen etkileyecek şekilde değişkenlerin değerlerini değiştirebilirsiniz.

4. İstem `updateImages` üzerine yazın ve Enter tuşuna basın. Konsol penceresinde işlev için bir görselleştirici görüntülenir.

5. İşlev uygulamasını göstermek için konsol penceresinde işlevini seçin.

    Aşağıdaki çizimde bu noktadaki konsol penceresi gösterilir.

    ![Görselleştiriciyi gösteren JavaScript Konsol Penceresi](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")

6. İşlevin bir satırı çıkış penceresinden giriş istemine kopyalayın ve dizin değerini 3 olarak değiştirir:

    ```javascript
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    ```

7. Kod satırı çalıştırmak için Enter tuşuna basın.

    Kod satırına satır satır gitmek için F11 tuşuna veya program yürütmeye devam etmek için F5 tuşuna basın.

8. Program yürütmeye devam etmek için F5 tuşuna basın. Uygulama `FlipView` görüntülenir ve artık dört sayfada da varsayılan olmayan görüntülerden biri görüntülenir.

    Geri Visual Studio F12 veya Alt+Tab tuşlarına basın.

## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a> JavaScript Konsolu penceresinde tek satırlı mod ve çok satırlı mod
JavaScript Konsol penceresi için giriş istemi hem tek satırlı modu hem de çok satırlı modu destekler. Bu konudaki etkileşimli hata ayıklama yordamı, her iki modun da kullanımına bir örnek sağlar. Modlar arasında geçiş yapmak için Ctrl+Alt+M tuşlarına basabilirsiniz.

Tek satırlı mod giriş geçmişi sağlar. Yukarı Ok ve Aşağı Ok tuşlarını kullanarak giriş geçmişi arasında gezinsiniz. Betikleri çalıştırarak tek satırlı mod giriş istemini temizler. Betiği tek satırlı modda çalıştırmak için Enter tuşuna basın.

Çok satırlı mod, betikleri çalıştırarak giriş istemini temizlemez. Çok satırlı moddan tek satırlı moda geçiş yaparak Girişi temizle **(kırmızı** "X") tuşuna basarak giriş çizgisini temizebilirsiniz. Bir betiği çok satırlı modda çalıştırmak için Ctrl+Enter tuşlarına basın veya pencerenin sağ alt köşesindeki ok simgesini seçin.

## <a name="switching-the-script-execution-context"></a><a name="Switching"></a> Betik yürütme bağlamını değiştirme
JavaScript Konsol penceresi, web platformu ana bilgisayarının (WWAHost.exe) tek bir örneğini temsil eden tek bir yürütme bağlamıyla etkileşim kurmanıza olanak sağlar. Bazı senaryolarda, uygulamanız bir , paylaşım sözleşmesi, web çalışanı veya denetim kullanımı gibi ana bilgisayar başka bir `iframe` örneğini `WebView` başlatabilirsiniz. Konakta başka bir örnek çalışıyorsa, Hedef listesinde yürütme bağlamını seçerek uygulamayı çalıştırma sırasında farklı bir yürütme bağlamı **seçebilirsiniz.**

Aşağıdaki çizimde JavaScript Konsolu penceresindeki Hedef listesi gösterilir.

![JavaScript konsol penceresinde hedef seçimi](../debugger/media/js_console_target.png "JS_Console_Target")

ayrıca komutunu kullanarak yürütme bağlamını da değiştirebilirsiniz, ancak diğer yürütme bağlamının adını biliyor ve kullanmakta olduğu başvuru `cd` kapsamda yer amelidir. Hedef **listesi,** diğer yürütme bağlamlarına daha iyi erişim sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017&preserve-view=true)
- [HTML, CSS ve JavaScript'te hata ayıklama örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)
- [Ürün Desteği ve Erişilebilirliği](https://visualstudio.microsoft.com/vs/support/)
