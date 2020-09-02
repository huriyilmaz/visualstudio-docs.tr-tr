---
title: 'Hızlı başlangıç: hata ayıklama HTML ve CSS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be85bd5c09d59df576d66cef6cf2d4e7e34876ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687646"
---
# <a name="quickstart-debug-html-and-css"></a>Hızlı başlangıç: HTML ve CSS hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 JavaScript uygulamaları için, Visual Studio, Internet Explorer ve Visual Studio geliştiricilerine tanıdık olan özellikleri içeren kapsamlı bir hata ayıklama deneyimi sunar. Bu özellikler [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , Windows Phone mağaza uygulamaları ve Apache Cordova için Visual Studio araçları kullanılarak oluşturulan uygulamalar için desteklenir  
  
 DOM inceleme araçları tarafından sunulan etkileşimli hata ayıklama modelini kullanarak, işlenmiş HTML ve CSS kodunu görüntüleyebilir ve değiştirebilirsiniz. Bunu, hata ayıklayıcıyı durdurup yeniden başlatmadan yapabilirsiniz.  
  
 Bu konuda:  
  
- [Canlı DOM inceleniyor](#InspectingDOM)  
  
- [Öğe seçme](#SelectingElements)  
  
  DOM Gezginini kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)  
  
- [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)  
  
- [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)  
  
  JavaScript Konsol penceresini kullanma ve kesme noktaları ayarlama gibi diğer JavaScript hata ayıklama özellikleri hakkında bilgi için bkz. [hızlı başlangıç:](../debugger/quickstart-debug-javascript-using-the-console.md) [Visual Studio 'Da](../debugger/debug-store-apps-in-visual-studio.md)JavaScript ve hata ayıklama uygulamaları.  
  
## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Canlı DOM inceleniyor  
 DOM Gezgini, işlenmiş sayfanın bir görünümünü gösterir ve DOM Gezgini 'ni kullanarak değerleri değiştirebilir ve sonuçları hemen görebilirsiniz. Bu, hata ayıklayıcıyı durdurup yeniden başlatmadan değişiklikleri test etmenizi sağlar. Bu yöntemi kullanarak sayfayla etkileşim kurarken, projenizdeki kaynak kodu değişmez, bu nedenle istenen kod düzeltmelerini bulduğunuzda, kaynak kodunuzda değişiklikler yaparsınız.  
  
> [!TIP]
> Kaynak kodunuzda değişiklikler yaptığınızda hata ayıklayıcıyı durdurup yeniden başlatmadan kaçınmak için, hata ayıklama araç çubuğundaki **Windows uygulamasını Yenile** düğmesini kullanarak uygulamanızı yenileyebilirsiniz (veya F4 tuşuna basarak). Daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 DOM Gezgini 'ni kullanarak şunları yapabilirsiniz:  
  
- DOM öğesi alt ağacı ' na gidin ve işlenmiş HTML, CSS ve JavaScript kodunu inceleyin.  
  
- Oluşturulan öğelerin özniteliklerini ve CSS stillerini dinamik olarak düzenleyin ve sonuçları hemen görüntüleyin.  
  
- CSS stillerinin sayfa öğelerine nasıl uygulandığını inceleyin ve uygulanan kuralları izleyin.  
  
  Uygulamalarda hata ayıklarken, genellikle DOM Gezgini 'nde öğe seçmeniz gerekir. Bir öğe seçtiğinizde, DOM Gezgini 'nin sağ tarafındaki sekmelerde görüntülenen değerler, DOM Gezgini 'nde seçilen öğeyi yansıtacak şekilde otomatik olarak güncelleşilir. Sekmeler şunlardır: **Stiller**, **hesaplanan**, **Düzen**. Windows Mağazası uygulamaları da **olayları** ve **değişiklik** sekmelerini destekler. Öğe seçme hakkında daha fazla bilgi için bkz. [öğeleri seçme](#SelectingElements).  
  
> [!TIP]
> DOM Gezgini penceresi kapalıysa, **Debug** > **Windows**  >  yeniden açmak için Windows**DOM Gezgini 'nde** Hata Ayıkla ' yı seçin. Pencere yalnızca bir betik hata ayıklama oturumu sırasında görüntülenir.  
  
 Aşağıdaki yordamda, DOM Gezgini 'ni kullanarak bir uygulamada etkileşimli olarak hata ayıklama işlemini öğreneceksiniz. Bir `FlipView` denetimi kullanan ve sonra hata ayıkladığımız bir uygulama oluşturacağız. Uygulama birkaç hata içeriyor.  
  
> [!WARNING]
> Aşağıdaki örnek uygulama bir Windows Mağazası uygulamasıdır. Cordova için aynı özellikler desteklenir, ancak uygulama farklı olabilir.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Canlı DOM 'ı inceleyerek hata ayıklamak için  
  
1. **Dosya**  >  **Yeni proje**' ye tıklayarak Visual Studio 'da yeni bir çözüm oluşturun.  
  
2. **JavaScript**  >  **deposu**' nu seçin, **Windows uygulamaları** veya **Windows Phone Uygulamalar**' ı seçin ve **boş uygulama**' yı seçin.  
  
3. Proje için bir ad yazın (gibi) `FlipViewApp` ve uygulamayı oluşturmak Için **Tamam** ' ı seçin.  
  
4. default.html 'nin BODY öğesinde şu kodu ekleyin:  
  
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
  
5. Default. css ' yi açın ve aşağıdaki CSS 'yi ekleyin:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. default.js kodundaki kodu şu kodla değiştirin:  
  
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
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
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
  
    Aşağıdaki çizimde, bu uygulamayı Telefon Emulator 'da çalıştırıp çalıştırdığımızda neleri görmek istiyoruz (benzeticide benzer görünüyor). Ancak, uygulamayı bu duruma getirmek için öncelikle bir dizi hatayı düzeltmemiz gerekecektir.  
  
    ![Beklenen sonuçları gösteren FlipView uygulaması](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. **Hata ayıklama** araç çubuğunda **hata ayıklamayı Başlat** düğmesinin yanındaki aşağı açılan listeden **SIMÜLATÖR** veya **Emulator 8,1 WVGA 4 inç 512MB** seçeneklerinden birini seçin:  
  
    ![Hata ayıklama hedef listesini seçin](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Uygulamanızı **Debug**hata ayıklama  >  modunda çalıştırmak için hata**ayıklamayı Başlat**' ı seçin veya F5 tuşuna basın.  
  
    Bu, uygulamayı simülatör veya telefon öykünücüsünde çalıştırır, ancak stil içinde birkaç hata olduğu için çoğunlukla boş bir ekran görürsünüz. İlk `FlipView` görüntü, ekranın ortasında küçük bir karede görünür.  
  
9. Uygulamayı simülatör 'da çalıştırıyorsanız, 1280 x 800 ekran çözünürlüğünü yapılandırmak için Benzeticisinin sağ tarafındaki çözümleme araç çubuğunu **Değiştir** komutunu seçin. Bu, aşağıdaki adımlarda gösterilen değerlerin benzeticide gördüklerinizle eşleştiğinden emin olur.  
  
10. Visual Studio 'ya geçin ve **DOM Gezgini** sekmesini seçin.  
  
    > [!TIP]
    > Visual Studio ile çalışan uygulama arasında geçiş yapmak için Alt + Tab veya F12 tuşlarına basabilirsiniz.  
  
11. DOM Gezgini penceresinde KIMLIĞI olan bölüm için DIV öğesini seçin `"fView"` . Doğru DIV öğesini görüntülemek ve seçmek için ok tuşlarını kullanın. (Sağ ok tuşu, bir öğenin alt öğelerini görüntülemenize olanak sağlar.)  
  
     ![DOM Gezgini](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    > Ayrıca, `select(fView)` >> giriş istemine yazıp ENTER tuşuna basarak, JavaScript Konsol penceresinin sol alt KÖŞESINDEKI DIV öğesini de seçebilirsiniz.  
  
     DOM Gezgini penceresinin sağ tarafındaki sekmelerde görüntülenen değerler, DOM Gezgini 'nde geçerli öğeyi yansıtacak şekilde otomatik olarak günceldir.  
  
12. Sağ tarafta **hesaplanan** sekmesini seçin.  
  
     Bu sekme, seçilen DOM öğesinin her bir özelliği için hesaplanan veya son değeri gösterir.  
  
13. Yükseklik CSS kuralını açın. 100 piksel olarak ayarlanmış bir satır içi stil olduğuna dikkat edin. Bu, CSS Seçicisi için %100 oranında ayarlanmış olan yükseklik değeriyle tutarsız bir şekilde görünür `#fView` . Seçici için üstü çizili metin `#fView` , satır içi stilin bu stille öncelikli olduğunu gösterir.  
  
     Aşağıdaki çizimde, **hesaplanan** sekmesi gösterilmektedir.  
  
     ![DOM Gezgini hesaplanan sekmesi](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. Ana DOM Gezgini penceresinde, DIV öğesinin yükseklik ve genişlik için satır içi stile çift tıklayın `fView` . Artık değerleri burada düzenleyebilirsiniz. Bu senaryoda, bunları tamamen kaldırmak istiyoruz.  
  
15. Seçin `width: 100px;height: 100px;` , DELETE tuşuna basın ve ardından ENTER tuşuna basın. ENTER tuşuna bastıktan sonra, hata ayıklama oturumunuzu durdurmadığınız halde yeni değerler simülatör veya telefon öykünücüsünde hemen yansıtılır.  
  
    > [!IMPORTANT]
    > DOM Gezgini penceresinde öznitelikleri güncelleştirebilmeniz için, **Stiller**, **hesaplanan**ve **Düzen** sekmelerinde görüntülenen değerleri de güncelleştirebilirsiniz. Daha fazla bilgi için bkz. DOM Gezginini kullanarak [CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md) ve [DOM Gezgini kullanarak hata ayıklama düzeni](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Simülatör veya telefon öykünücüsünü seçerek veya alt + TAB tuşlarını kullanarak uygulamaya geçiş yapın.  
  
     Artık `FlipView` Denetim simülatör veya telefon öykünücüsünün ekran boyutundan daha büyük görünüyor. Bu, amaçlanan sonuç değildir. Araştırmak için, Visual Studio 'ya geri dönün.  
  
17. DOM Gezgini 'nde, **hesaplanmış** sekmesini yeniden seçin ve yükseklik kuralını açın. FView öğesi, CSS 'den beklenen %100 değerini hala gösterir, ancak hesaplanan değer bu uygulama için istediğimiz olmayan Benzetici ekran yüksekliğine (örneğin, 800px veya 667.67 px) eşittir. Araştırmak için, DIV öğesinin yüksekliğini ve genişliğini kaldırabilirsiniz `fView` .  
  
18. **Stiller** sekmesinde CSS seçicinin yükseklik ve genişlik özelliklerinin işaretini kaldırın `#fView` .  
  
     **Hesaplanan** sekmede artık 400px bir yükseklik gösterilmektedir. Bilgiler, bu değerin platform CSS dosyası olan ui-Dark. css dosyasında belirtilen. win-flipview seçicisine geldiğini gösterir.  
  
19. Uygulamaya geri dönün.  
  
     Şeyler geliştirilmiştir. Ancak düzeltilmeye devam eden bir sorun var: kenar boşlukları çok büyük görünüyor.  
  
20. Araştırmak için, Visual Studio 'ya geçin ve öğenin kutu modeline bakmak için **Düzen** sekmesini seçin.  
  
     **Düzen** sekmesinde aşağıdaki değerleri görürsünüz:  
  
    - Simülatör için: 320px (konum) ve 320 piksel (kenar boşluğu).  
  
    - Telefon öykünücüsü için: 100 piksel (konum) ve 100 piksel (kenar boşluğu).  
  
      Aşağıdaki çizimde, telefon öykünücüsünü (100px fark ve kenar boşluğu) kullanıyorsanız **Düzen** sekmesinin nasıl göründüğü gösterilmektedir.  
  
      ![DOM Gezgini Düzen sekmesi](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      Bu doğru görünmüyor. **Hesaplanan** sekme aynı kenar boşluğu değerlerini de gösterir.  
  
21. **Stiller** sekmesini seçin ve `#fView` CSS seçiciyi bulun. Burada, **Margin** özelliği için %25 değerini görürsünüz.  
  
22. %25 ' i seçin ve 25px olarak değiştirin ve ENTER tuşuna basın.  
  
23. Ayrıca, **Stiller** sekmesinde. win-flipview seçicisinin yükseklik kuralını seçin ve 400px ' i 500 piksel olarak değiştirin ve ENTER tuşuna basın.  
  
24. Uygulamaya geri dönün ve öğelerin yerleşiminin doğru göründüğünü görürsünüz. Kaynak üzerinde düzeltmeler yapmak ve hata ayıklayıcıyı durdurup yeniden başlatmadan uygulamayı yenilemek için aşağıdaki yordama bakın.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Hata ayıklama sırasında uygulamanızı yenilemek için  
  
1. Uygulama çalışmaya devam ederken Visual Studio 'ya geçin.  
  
2. default.html 'yi açın ve DIV öğesinin Height ve Width değerlerini %100 olarak değiştirerek kaynak kodunuzu değiştirin `"fView"` .  
  
3. Hata ayıklama araç çubuğunda **Windows uygulamasını Yenile** düğmesini seçin (veya F4 tuşuna basın). Düğme şu şekilde görünür: ![Windows uygulamasını Yenile düğmesi](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Uygulama sayfaları yeniden yükleme ve simülatör veya telefon öykünücüsü ön plana geri döner.  
  
     Yenileme özelliği hakkında daha fazla bilgi için bkz. [uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="selecting-elements"></a><a name="SelectingElements"></a> Öğe seçme  
 Bir uygulamada hata ayıklarken DOM öğelerini üç şekilde seçebilirsiniz:  
  
- Doğrudan DOM Gezgini penceresinde (veya ok tuşlarını kullanarak) öğelere tıklayarak.  
  
- **Öğe seç** düğmesini (Ctrl + B) kullanarak.  
  
- `select` [JavaScript Konsol komutlarından](../debugger/javascript-console-commands.md)biri olan komutunu kullanarak.  
  
  Öğeleri seçmek için DOM Gezgini penceresini kullandığınızda ve fare işaretçisini bir öğe üzerine getirdiğinizde, ilgili öğe çalışan uygulamada vurgulanır. Bunu seçmek için DOM Gezgini 'nde öğeye tıklamalısınız veya öğeleri vurgulamak ve seçmek için ok tuşlarını kullanabilirsiniz. DOM Gezgini 'nde **öğe seç** düğmesini kullanarak da öğeleri seçebilirsiniz. Aşağıdaki çizimde **öğe seç** düğmesi gösterilmektedir.  
  
  ![DOM Gezgini 'nde öğe seç düğmesi](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  **Öğe seç** ' e tıkladığınızda (veya CTRL + B tuşlarına basın), bu seçim modu, çalışan uygulamada tıklayarak DOM Gezgini 'nde bir öğe seçebilmeniz için değiştirilir. Tek bir tıklama sonrasında mod normal seçim moduna geri değişir. **Öğe seç**' e tıkladığınızda, uygulama ön plana gelir ve imleç yeni seçim modunu yansıtacak şekilde değişir. Seviyelendirilmiş öğeye tıkladığınızda, DOM Gezgini belirtilen öğe seçili olan ön plana geri döner.  
  
  **Öğe seç**' i seçmeden önce, **Web sayfası vurgulamaları göster** düğmesini değiştirerek çalışan uygulamadaki öğelerin vurgulanmasını belirtebilirsiniz. Aşağıdaki çizimde bu düğme gösterilmektedir. Vurgular varsayılan olarak görüntülenir.  
  
  ![Web sayfası vurgulamaları göster düğmesi](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Öğeleri vurgulamanızı seçtiğinizde benzeticide üzerine geldiğinizde bulunan öğeler vurgulanır. Vurgulanan öğelerin renkleri, DOM Gezgini 'nin **Düzen** sekmesinde görüntülenen kutu modeliyle eşleşir.  
  
> [!NOTE]
> Öğelerin üzerine gelindiğinde vurgulanması yalnızca Windows Phone öykünücüsünde kısmen desteklenir.  
  
 **Öğe seç** düğmesini kullanarak öğelerin nasıl seçeceğinizi gösteren bir örnek için bkz. [DOM Gezginini kullanarak CSS stillerinde hata ayıkla](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Tarayıcı ve platform desteği  
 JavaScript için Visual Studio Araçları, DOM Gezgini ve JavaScript konsol penceresi aşağıdaki platformlarda desteklenir:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] ve JavaScript ve HTML kullanarak uygulama depolama Windows Phone  
  
- Üzerinde çalışan Internet Explorer 11 [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Üzerinde çalışan Internet Explorer 10 [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Visual Studio 'Yu indirmek için [buraya](https://developer.microsoft.com/windows/downloads/sdk-archive) gidin [!INCLUDE[win8](../includes/win8-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio 'da uygulamalarda hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md)   
 [DOM Gezgini 'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM Gezginini kullanarak hata ayıklama düzeni](../debugger/debug-layout-using-dom-explorer.md)   
 [DOM olay dinleyicilerini görüntüle](../debugger/view-dom-event-listeners.md)   
 [Uygulamayı yenileme (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [WebView denetiminde hata ayıklama](../debugger/debug-a-webview-control.md)   
 [Klavye kısayolları](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [JavaScript konsol komutları](../debugger/javascript-console-commands.md)   
 [HTML, CSS ve JavaScript örnek kodunda hata ayıklama](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Ürün desteği ve erişilebilirlik](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)
