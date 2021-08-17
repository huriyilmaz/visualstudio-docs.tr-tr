---
title: UWP uygulamaları içinde HTML ve CSS hata ayıklaması | Microsoft Docs
description: Universal Windows Platform (UWP) uygulamaları içinde HTML ve CSS'de hata ayıklamayı Visual Studio. UWP uygulamaları için JavaScript hata ayıklama özellikleri de kullanılabilir.
ms.custom: SEO-VS-2020
ms.date: 07/17/2018
ms.topic: how-to
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 55e64d2d4c1249efe8306aba8a9279d75b4034ef41c14d6b4f161dee694046c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419369"
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Visual Studio'de UWP uygulamalarıyla HTML ve CSS'de hata ayıklama

JavaScript uygulamaları için Visual Studio geliştiricilere ve geliştiricilere tanıdık özellikler içeren kapsamlı bir hata Internet Explorer Visual Studio sağlar. Bu özellikler UWP uygulamaları ve bu uygulamalar için Visual Studio Araçları kullanılarak oluşturulan Apache Cordova.

DOM inceleme araçları tarafından sağlanan etkileşimli hata ayıklama modelini kullanarak işlenmiş HTML ve CSS kodunu görüntüp değiştirebilirsiniz. Hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan tüm bu işlemi yapabiliriz.

JavaScript Konsol penceresini kullanma ve kesme noktaları ayarlama gibi diğer JavaScript hata ayıklama özellikleri hakkında bilgi için [bkz. Hızlı Başlangıç: JavaScript'te hata](../debugger/quickstart-debug-javascript-using-the-console.md) ayıklama ve [Visual Studio.](debugging-windows-store-and-windows-universal-apps.md)

## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Canlı DOM'ları inceleme
DOM Gezgini sayfanın görünümünü gösterir ve değerleri değiştirmek ve sonuçları hemen DOM Gezgini için bu sayfayı kullanabilirsiniz. Bu, hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan değişiklikleri test etmek için size olanak sağlar. Projenizin kaynak kodu, bu yöntemi kullanarak sayfayla etkileşim kurduğunda değişmez. Bu nedenle, istenen kod düzeltmelerini bulursanız kaynak kodunuz üzerinde değişiklikler yapabilirsiniz.

> [!TIP]
> Kaynak kodunda değişiklik yaptığınız zaman hata ayıklayıcının durdurulması ve yeniden başlatılmasını önlemek için Hata Ayıklama araç **çubuğundaki Windows** uygulamasını yenile düğmesini kullanarak (veya F4 tuşuna basarak) uygulamanızı yenileyebilirsiniz. Daha fazla bilgi için [bkz. Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).

Aşağıdakiler için DOM Gezgini kullanabilirsiniz:

- DOM öğesi alt ağacına gidin ve işlenmiş HTML, CSS ve JavaScript kodunu inceler.

- İşlenen öğeler için öznitelikleri ve CSS stillerini dinamik olarak düzenleyin ve sonuçları hemen görme.

- CSS stillerinin sayfa öğelerine nasıl uygulandığını inceler ve uygulanan kuralları izler.

  Uygulamalarda hata ayıklarken genellikle uygulamanın içinde öğeleri DOM Gezgini. Bir öğeyi seçtiğiniz zaman, öğenin sağ tarafındaki sekmelerde görünen değerler DOM Gezgini öğenin sağ tarafındaki seçili öğeyi yansıtacak şekilde otomatik DOM Gezgini. Bunlar sekmeleridir: **Stiller,** **Hesaplanan**, **Düzen.** UWP uygulamaları, Olaylar ve **Değişiklikler sekmelerini** **de** destekler. Öğeleri seçme hakkında daha fazla bilgi için [bkz. Öğeleri seçme.](#SelectingElements)

> [!TIP]
> DOM Gezgini penceresi kapatılırsa, yeniden açmak **için Hata** > **Windows**  >  **DOM Gezgini** Hata Ayıkla'ya tıklayın. Pencere yalnızca bir betik hata ayıklama oturumu sırasında görüntülenir.

Aşağıdaki yordamda, bir uygulamayı kullanarak etkileşimli olarak hata ayıklama işleminin üzerinden DOM Gezgini. Denetim kullanan bir uygulama oluşturarak `FlipView` hata ayıklaması oluşturuz. Uygulama birkaç hata içeriyor.

> [!WARNING]
> Aşağıdaki örnek uygulama bir UWP uygulamasıdır. Cordova için de aynı özellikler desteklene, ancak uygulama farklı olabilir.

#### <a name="to-debug-by-inspecting-the-live-dom"></a>Canlı DOM'u incelerken hata ayıklamak için

1. Dosya Yeni Dosya'Visual Studio seçerek yeni **bir**  >  **çözüm Project.**

2. JavaScript **Windows**  >  **Evrensel'i** ve ardından **WinJS Uygulaması'ı seçin.**

3. Proje için gibi bir ad yazın ve `FlipViewApp` uygulamayı oluşturmak **için Tamam'ı** seçin.

4. index.html öğesinin BODY öğesine şu kodu ekleyin:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" style="width:100px;height:100px"
        data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. default.css'yi açın ve aşağıdaki CSS'yi ekleyin:

    ```css
    #fView {
        background-color:#0094ff;
        height: 100%;
        width: 100%;
        margin: 25%;
    }
    ```

6. aşağıdaki kodla default.js değiştirin:

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

            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
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

    Aşağıdaki çizimde, bu uygulamayı çalıştıracak olursa ne görmek istediğiniz gösterilmiştir. Ancak, uygulamayı bu durumuna almak için önce bir dizi hatayı düzeltmemiz gerekir.

    ![Beklenen sonuçları gösteren FlipView uygulaması](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")

7. Hata **Ayıklama araç** çubuğundaki Hata Ayıklamayı Başlat **düğmesinin** yanındaki açılan listeden Yerel **Makine'yi** seçin:

    ![Hata ayıklama hedef listesini seçme](../debugger/media/js_select_target.png "JS_Select_Target")

8. Hata **Ayıklamayı**  >  **Başlat Hata Ayıklamayı** Başlat'ı seçin veya F5 tuşuna basarak uygulamanızı hata ayıklama modunda çalıştırın.

    Bu, uygulamayı çalıştırır ancak stilde birkaç hata olduğu için çoğunlukla boş bir ekran görürsünüz. İlk `FlipView` görüntü, ekranın ortasındaki küçük bir karede görünür.

9. Visual Studio'a geçiş yapın ve **DOM Gezgini** seçin.

    > [!TIP]
    > Alt+Tab veya F12 tuşlarına basarak Visual Studio uygulama arasında geçiş yapın.

10. Giriş DOM Gezgini, kimliğine sahip olan bölüm için DIV öğesini `"fView"` seçin. Doğru DIV öğesini görüntülemek ve seçmek için ok tuşlarını kullanın. (Sağ ok tuşu, bir öğenin altındakileri görüntülemeye olanak sağlar.)

    ![DOM Gezgini](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")

    > [!TIP]
    > Ayrıca JavaScript Konsol penceresinin sol alt köşesindeki DIV öğesini seçmek için giriş istemine >> Enter `select(fView)` tuşuna basabilirsiniz.

    Uygulama penceresinin sağ tarafındaki sekmelerde görünen değerler DOM Gezgini otomatik olarak DOM Gezgini.

11. Sağdan **Hesaplanan** sekmesini seçin.

    Bu sekme, seçilen DOM öğesinin her özelliği için hesaplanan veya son değeri gösterir.

12. Height CSS kuralını açın. CSS seçici için %100'lık yükseklik değeriyle tutarsız görünen, 100px olarak ayarlanmış bir satır içi stil olduğunu `#fView` fark etmek. Seçicinin üzerinde `#fView` çizili metin, satır içi stilin bu stilden öncelikli olduğunu gösterir.

    Aşağıdaki çizimde Hesaplanan **sekmesi gösterilmiştir.**

    ![DOM Gezgini Hesaplanan sekmesi](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")

13. Ana DOM Gezgini penceresinde, DIV öğesinin yüksekliği ve genişliği için satır içi stile çift `fView` tıklayın. Artık değerleri burada düzenleyebilirsiniz. Bu senaryoda bunları tamamen kaldırmak istiyoruz.

14. Ana pencerede'ye çift `width: 100px;height: 100px;` tıklayın, Sil **tuşuna basın ve** enter tuşuna **basın.** Enter tuşuna bastıktan sonra, hata ayıklama oturumlarınızı durdurmamış olsa bile yeni değerler uygulamaya hemen yansıtılacaktır.

    > [!IMPORTANT]
    > Yeni görünüm penceresinde öznitelikleri güncelleştire DOM Gezgini, Stiller, Hesaplanan ve Düzen sekmelerinde görünen **değerleri de** **güncelleştirebilirsiniz.**

15. Uygulamayı seçerek veya Alt+Tab kullanarak uygulamaya geçiş yapın.

    Artık `FlipView` denetim Simulator'ın veya Telefon Emulator daha büyük görünür. Amaçlanan sonuç bu değildir. Araştırmak için yeniden Visual Studio.

16. Aşağıdaki DOM Gezgini hesaplanan **sekmesini tekrar** seçin ve yükseklik kuralını açın. fView öğesi css'den beklendiği gibi %100 değerini gösterir, ancak hesaplanan değer uygulamanın ekran yüksekliğine eşittir (örneğin, 800px, 667,67px veya başka bir değer). Bu, bu uygulama için istediğiniz değer değildir. Araştırmak için sonraki adımlarda DIV öğesinin yüksekliğini ve genişliğini `fView` kaldıracağız.

17. Stiller **sekmesinde** CSS seçicisi için yükseklik ve genişlik özelliklerinin `#fView` işaretini kaldırın.

    Hesaplanan **sekmesi artık** 400px yükseklik gösteriyor. Bilgiler, bu değerin bir platform CSS dosyası olan ui-dark.css içinde belirtilen .win-flipview seçiciden geldiğine işaret ediyor.

18. Uygulamaya geri dön.

    İşler gelişti. Ancak düzeltmemiz gereken bir sorun daha vardır: kenar boşlukları çok büyük görünüyor.

19. Araştırmak için, Visual Studio'a **geçiş yapın ve öğenin** kutu modeline bakmak için Düzen sekmesini seçin.

    Düzen **sekmesinde** şunları görebilirsiniz:

    - Cihazınızın çözünürlüğüne bağlı olarak 255px (Uzaklık) ve 255px (Kenar Boşluğu) veya benzer değerler.

      Aşağıdaki çizimde,  100px kaydırma ve kenar boşluğu ile bir öykünücü kullanıyorsanız Düzen sekmesinin nasıl göründüğünü gösterir.

      ![DOM Gezgini Düzeni sekmesi](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")

      Bu doğru görünmüyor. Hesaplanan **sekmesi aynı** dış boşluk değerlerini de gösterir.

20. Stiller **sekmesini** seçin ve `#fView` CSS seçiciyi bulun. Burada margin özelliği için %25 değerini **görüyorsunuz.**

21. %25'i seçin ve 25px olarak değiştirerek Enter tuşuna basın.

22. Ayrıca **Stiller sekmesinde** .win-flipview seçicisi için yükseklik kuralını seçin ve 400px'i 500px olarak değiştirerek Enter tuşuna basın.

23. Uygulamaya geri dönüp öğelerin yerleşimini doğru gördüğünüzde. Kaynakta düzeltmeler yapmak ve hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan uygulamayı yenilemek için aşağıdaki yordama bakın.

#### <a name="to-refresh-your-app-while-debugging"></a>Hata ayıklama sırasında uygulamanızı yenilemek için

1. Uygulama hala çalışırken Uygulama'ya Visual Studio.

2. l default.htmaçın ve DIV öğesinin yüksekliğini ve genişliğini `"fView"` %100 olarak değiştirerek kaynak kodunuzu değiştirebilirsiniz.

3. Hata Ayıklama **araç Windows Uygulamanın** yenile düğmesini seçin (veya F4 tuşuna basın). Düğme şu şekilde görünüyor: ![Uygulama Windows yenileyin.](../debugger/media/js_refresh.png "JS_Refresh")

    Uygulama sayfaları yeniden yük bindirin ve Simulator Telefon Emulator ön plana geri döner.

    Yenileme özelliği hakkında daha fazla bilgi için [bkz. Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).

## <a name="selecting-elements"></a><a name="SelectingElements"></a> Öğe seçme
Bir uygulamada hata ayıklarken DOM öğelerini üç şekilde seçebilirsiniz:

- Doğrudan DOM Gezgini penceresinde (veya ok tuşlarını kullanarak) öğelere tıklayarak.

- **Öğe seç** düğmesini (Ctrl + B) kullanarak.

- `select` [JavaScript Konsol komutlarından](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)biri olan komutunu kullanarak.

  Öğeleri seçmek için DOM Gezgini penceresini kullandığınızda ve fare işaretçisini bir öğe üzerine getirdiğinizde, ilgili öğe çalışan uygulamada vurgulanır. Bunu seçmek için DOM Gezgini 'nde öğeye tıklamalısınız veya öğeleri vurgulamak ve seçmek için ok tuşlarını kullanabilirsiniz. DOM Gezgini 'nde **öğe seç** düğmesini kullanarak da öğeleri seçebilirsiniz. Aşağıdaki çizimde **öğe seç** düğmesi gösterilmektedir.

  ![DOM Gezgini 'nde öğe seç düğmesi](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")

  **Öğe seç** ' e tıkladığınızda (veya CTRL + B tuşlarına basın), bu seçim modu, çalışan uygulamada tıklayarak DOM Gezgini 'nde bir öğe seçebilmeniz için değiştirilir. Tek bir tıklama sonrasında mod normal seçim moduna geri değişir. **Öğe seç**' e tıkladığınızda, uygulama ön plana gelir ve imleç yeni seçim modunu yansıtacak şekilde değişir. Seviyelendirilmiş öğeye tıkladığınızda, DOM Gezgini belirtilen öğe seçili olan ön plana geri döner.

  **Öğe seç**' i seçmeden önce, **Web sayfası vurgulamaları göster** düğmesini değiştirerek çalışan uygulamadaki öğelerin vurgulanmasını belirtebilirsiniz. Aşağıdaki çizimde bu düğme gösterilmektedir. Vurgular varsayılan olarak görüntülenir.

  ![Web sayfası vurgulamaları göster düğmesi](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")

  Öğeleri vurgulamanızı seçtiğinizde benzeticide üzerine geldiğinizde bulunan öğeler vurgulanır. Vurgulanan öğelerin renkleri, DOM Gezgini 'nin **Düzen** sekmesinde görüntülenen kutu modeliyle eşleşir.

> [!NOTE]
> öğelerin üzerine gelindiğinde vurgulanması yalnızca Windows Phone Emulator kısmen desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)
- [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017&preserve-view=true)
- [JavaScript Konsolu komutları](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)
- [HTML, CSS ve JavaScript'te hata ayıklama örnek kodu](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Ürün desteği ve erişilebilirlik](/previous-versions/tzbxw1af(v=vs.120))