---
title: Konsolunu kullanarak JavaScript hatalarını ayıklama | Microsoft Docs
description: JavaScript kullanılarak oluşturulan Evrensel Windows Platformu (UWP) uygulamalarıyla etkileşim kurmak için Visual Studio 'da JavaScript Konsol penceresini kullanın.
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 964151b3e674f493eeeeb564d0a449e093cde11f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840944"
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Visual Studio 'da Konsolu kullanarak JavaScript hata ayıklama

JavaScript kullanılarak oluşturulan UWP uygulamalarıyla etkileşim kurmak ve hata ayıklamak için JavaScript Konsol penceresini kullanabilirsiniz. Bu özellikler, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan UWP uygulamaları ve uygulamaları için desteklenir. Konsol komut başvurusu için bkz. [JavaScript konsol komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true).

JavaScript Konsolu penceresi şunları yapmanıza olanak sağlar:

- Uygulamanızdaki nesneleri, değerleri ve iletileri konsol penceresine gönderin.

- Çalışan uygulamadaki yerel ve genel değişkenlerin değerlerini görüntüleyin ve değiştirin.

- Nesne görselleştiricilerini görüntüleyin.

- Geçerli betik bağlamı içinde yürütülen JavaScript kodunu çalıştırın.

- Belge Nesne Modeli (DOM) ve Windows Çalışma Zamanı özel durumlara ek olarak JavaScript hatalarını ve özel durumlarını görüntüleyin.

- Ekranı temizleme gibi diğer görevleri gerçekleştirin. Komutların tam listesi için bkz. [JavaScript konsol komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) .

> [!TIP]
> JavaScript Konsolu penceresi kapalıysa,  >    >  yeniden açmak için Windows **JavaScript Konsolu** Hata Ayıkla ' yı seçin. Pencere yalnızca bir betik hata ayıklama oturumu sırasında görüntülenir.

JavaScript Konsol penceresini kullanarak, hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamanız ile etkileşime geçebilirsiniz. Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md). DOM Gezginini kullanma ve kesme noktaları ayarlama gibi diğer JavaScript hata ayıklama özellikleri hakkında bilgi için bkz. [hızlı başlangıç: Visual Studio 'DA HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) ve [hata ayıklama uygulamalarında](debugging-windows-store-and-windows-universal-apps.md)hata ayıklama.

## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a> JavaScript Konsol penceresini kullanarak hata ayıklama
Aşağıdaki adımlar bir uygulama oluşturur `FlipView` ve bir JavaScript kodlama hatasını etkileşimli olarak nasıl ayıklayacağınız gösterilmektedir.

> [!NOTE]
> Örnek uygulama, UWP uygulaması. Bununla birlikte, burada açıklanan konsol özellikleri, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamalar için de geçerlidir.

#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>FlipView uygulamasındaki JavaScript kodunda hata ayıklamak için

1. **Dosya**  >  **Yeni proje**' ye tıklayarak Visual Studio 'da yeni bir çözüm oluşturun.

2. **JavaScript**  >  **Windows Universal**' i seçin ve ardından **WinJS uygulaması**' nı seçin.

3. Proje için bir ad yazın (gibi) `FlipViewApp` ve uygulamayı oluşturmak Için **Tamam** ' ı seçin.

4. index.html 'nin BODY öğesinde, var olan HTML kodunu şu kodla değiştirin:

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

5. Default. css ' i açın ve seçicinin CSS 'sini ekleyin `#fView` :

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

7. Bir hata ayıklama hedefi zaten seçili değilse, **hata ayıklama** araç çubuğundaki **cihaz** düğmesinin yanındaki açılan listeden **yerel makine** ' yi seçin:

    ![Hata ayıklama hedef listesini seçin](../debugger/media/js_select_target.png "JS_Select_Target")

8. Hata ayıklayıcıyı başlatmak için F5 tuşuna basın.

    Uygulama çalışıyor ancak resimler eksik. JavaScript Konsol penceresinde APPHOST hataları görüntülerin eksik olduğunu gösterir.

9. `FlipView`Uygulama çalışırken, `Data.items` konsol penceresi giriş istemine (">>" sembolünün yanına) yazın ve ENTER tuşuna basın.

    Nesne için bir Görselleştirici `items` konsol penceresinde görünür. Bu, `items` nesnenin örneği oluşturulan ve geçerli betik bağlamında kullanılabilir olduğunu gösterir. Konsol penceresinde, özellik değerlerini görüntülemek için bir nesnenin düğümlerine tıklayabilirsiniz (veya ok tuşlarını kullanabilirsiniz). Nesneye tıklarsanız, `items._data` Bu çizimde gördüğünüz gibi, görüntü kaynağı başvurularının beklendiği gibi yanlış olduğunu fark edeceksiniz. Varsayılan görüntüler (logo.png) nesne içinde hala mevcuttur ve beklenen görüntülerle birlikte eksik görüntüler vardır.

    ![JavaScript konsol penceresi](../debugger/media/js_console_window.png "JS_Console_Window")

    Ayrıca, nesnede bekleeceğiniz kadar çok daha fazla öğe olduğunu unutmayın `items._data` .

10. İstemine yazın `Data.items.push` ve ENTER tuşuna basın. Konsol penceresi, `push` bir proje dosyasında uygulanan işlevi için Görselleştirici gösterir [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] . Bu uygulamada, `push` doğru öğeleri eklemek için kullanıyoruz. IntelliSense kullanarak küçük bir araştırma sayesinde, `setAt` varsayılan görüntüleri değiştirmek için kullanılması gerektiğini öğreniyoruz.

11. Hata ayıklama oturumunu durdurmadan bu sorunu etkileşimli olarak gidermek için, default.js açın ve işlevden bu kodu seçin `updateImages` :

    ```javascript
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

     Bu kodu kopyalayıp JavaScript Konsolu giriş istemine yapıştırın.

    > [!TIP]
    > JavaScript Konsolu giriş istemine birden fazla kod satırı yapıştırdığınızda, konsol giriş istemi otomatik olarak çok satırlı moda geçer. Çoklu satır modunu açmak ve kapatmak için Ctrl + Alt + e tuşlarına basabilirsiniz. Bir betiği çok satırlı modda çalıştırmak için CTRL + ENTER tuşlarına basın veya pencerenin sağ alt köşesinde bulunan ok simgesini seçin. Daha fazla bilgi için bkz. [JavaScript Konsol penceresinde tek satırlık mod ve çok satırlı mod](#SinglelineMultilineMode).

12. `push`Komut isteminde ile değiştirerek işlev çağrılarını düzeltin `pages.push` `Data.items.setAt` . Düzeltilen kod şöyle görünmelidir:

    ```javascript
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

    > [!TIP]
    > `pages`Yerine nesnesini kullanmak istiyorsanız `Data.items` , nesneyi kapsamda tutmak için kodunuzda bir kesme noktası ayarlamanız gerekir `pages` .

13. Betiği çalıştırmak için yeşil ok simgesini seçin.

14. Ctrl + Alt + e tuşlarına basarak konsol giriş istemi 'ni tek satır moduna geçirin ve ardından giriş isteminden kodu silmek için **girişi temizle** (kırmızı "X") seçeneğini belirleyin.

15. `Data.items.length = 3`İstemine yazın ve ENTER tuşuna basın. Bu, gereksiz öğeleri verilerden kaldırır.

16. Uygulamayı yeniden kontrol edin ve doğru görüntülerin doğru sayfalarda olduğunu görürsünüz `FlipView` .

17. DOM Gezgini 'nde, güncelleştirilmiş DIV öğesini görebilir ve beklenen IMG öğelerini bulmak için alt ağaca gidebilirsiniz.

18. Hata **ayıklamayı Durdur hata**  >  **ayıklamayı Durdur** ' u seçerek veya SHIFT + F5 tuşlarına basarak hata ayıklamayı durdurun ve ardından kaynak kodu onarın.

    Düzeltilen örnek kodu içeren tüm default.html sayfasında, bkz. [hata ayıklama HTML, CSS ve JavaScript örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md).

## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a> Etkileşimli hata ayıklama ve kesme modu
JavaScript konsol penceresi gibi JavaScript hata ayıklama araçlarını kullanırken kesme noktaları ve kod içine adımla ' yı kullanabilirsiniz. Hata ayıklayıcıda çalışan bir program bir kesme noktasıyla karşılaştığında, hata ayıklayıcı programın yürütülmesini geçici olarak askıya alır. Yürütme askıya alındığında, programınız çalışma modundan kesme moduna geçer. Yürütmeyi dilediğiniz zaman sürdürebilirsiniz.

Bir program kesme modundayken JavaScript Konsol penceresini kullanarak geçerli betik yürütme bağlamında geçerli olan betikleri ve komutları çalıştırabilirsiniz. Bu yordamda, `FlipView` kesme modunun kullanımını göstermek için daha önce oluşturduğunuz uygulamanın sabit sürümünü kullanacaksınız.

#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Bir kesme noktası ayarlamak ve uygulamada hata ayıklamak için

1. `FlipView`Daha önce oluşturduğunuz uygulamanın default.html dosyasında, işlevin kısayol menüsünü açın ve kesme noktası Ekle kesme noktası ' nı `updateImages()` seçin   >  .

2. **Hata ayıklama** araç çubuğundaki **hata ayıklamayı Başlat** düğmesinin yanındaki açılan listede **yerel makine** ' yi seçin.

3. **Hata**  >  **ayıklamayı Başlat hata** Ayıkla ' yı seçin veya F5 tuşuna basın.

    Uygulama, yürütme işlevine ulaştığında kesme moduna girer `updateImages()` ve geçerli program yürütme satırı sarı renkle vurgulanır.

    ![JavaScript Konsolu ile kesme modunu kullanma](../debugger/media/js_breakmode.png "JS_BreakMode")

    Geçerli hata ayıklama oturumunu sona erdirmeden program durumunu hemen etkilemek için değişkenlerin değerlerini değiştirebilirsiniz.

4. `updateImages`İstemine yazın ve ENTER tuşuna basın. İşlev için bir Görselleştirici konsol penceresinde görünür.

5. İşlev uygulamasını göstermek için konsol penceresinde işlevi seçin.

    Aşağıdaki çizimde bu noktada konsol penceresi gösterilmektedir.

    ![Görselleştirici gösteren JavaScript konsol penceresi](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")

6. Çıkış penceresindeki işlevin bir satırını giriş istemine kopyalayın ve dizin değerini 3 olarak değiştirin:

    ```javascript
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    ```

7. Kod satırını çalıştırmak için ENTER tuşuna basın.

    Kod satırını satıra göre ilerlemek istiyorsanız, F11 tuşuna basın veya program yürütmeye devam etmek için F5 tuşuna basın.

8. Program yürütmeye devam etmek için F5 tuşuna basın. `FlipView`Uygulama görüntülenir ve bundan böyle dört sayfa varsayılan olmayan görüntülerden birini gösterir.

    Visual Studio 'ya geri dönmek için F12 veya Alt + Tab tuşlarına basın.

## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a> JavaScript Konsol penceresinde tek satırlık mod ve çok satırlı mod
JavaScript konsol penceresi için giriş istemi hem tek satırlık modu hem de çok satırlı modunu destekler. Bu konudaki etkileşimli hata ayıklama yordamı her iki modun kullanılmasına bir örnek sağlar. Modlar arasında geçiş yapmak için Ctrl + Alt + e tuşlarına basabilirsiniz.

Tek satırlık mod giriş geçmişi sağlar. Yukarı ok ve aşağı ok tuşlarını kullanarak giriş geçmişine gidebilirsiniz. Betikleri çalıştırdığınızda tek satırlık mod giriş isteğini temizler. Komut dosyasını tek satırlık modda çalıştırmak için ENTER tuşuna basın.

Betikler çalıştırdığınızda çok satırlı mod giriş isteğini temizlemez. Çok satırlı moddan tek satırlık moda geçtiğinizde giriş satırını **clear Input** (kırmızı "X") tuşuna basarak temizleyebilirsiniz. Bir betiği çok satırlı modda çalıştırmak için CTRL + ENTER tuşlarına basın veya pencerenin sağ alt köşesinde bulunan ok simgesini seçin.

## <a name="switching-the-script-execution-context"></a><a name="Switching"></a> Betik Yürütme bağlamını değiştirme
JavaScript konsol penceresi, tek bir Web platformu konağının (WWAHost.exe) tek bir örneğini temsil eden tek bir yürütme bağlamıyla etkileşime geçerek aynı anda bir kez etkileşim kurmanıza olanak tanır. Bazı senaryolarda, uygulamanız, bir `iframe` paylaşılan sözleşme, bir Web çalışanı veya bir denetim kullanırken olduğu gibi, konağın başka bir örneğini başlatabilir `WebView` . Konağın başka bir örneği çalıştırıyorsa, **hedef** listede Yürütme bağlamını seçerek uygulamayı çalıştırırken farklı bir yürütme bağlamı seçebilirsiniz.

Aşağıdaki çizimde JavaScript Konsol penceresinde hedef liste gösterilmektedir.

![JavaScript Konsol penceresinde hedef seçimi](../debugger/media/js_console_target.png "JS_Console_Target")

Ayrıca, komutunu kullanarak yürütme bağlamını değiştirebilirsiniz `cd` , ancak diğer yürütme bağlamının adını bilmeniz ve kullandığınız başvurunun kapsamda olması gerekir. **Hedef** liste, diğer yürütme bağlamlarına daha iyi erişim sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017&preserve-view=true)
- [HTML, CSS ve JavaScript'te hata ayıklama örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)
- [Ürün desteği ve erişilebilirlik](https://visualstudio.microsoft.com/vs/support/)
