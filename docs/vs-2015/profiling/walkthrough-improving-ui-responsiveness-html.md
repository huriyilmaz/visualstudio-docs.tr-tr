---
title: 'İzlenecek yol: UI yanıt hızını geliştirme (HTML) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- performance tools, JavaScript [Store apps]
- performance, JavaScript [Store apps]
- performance, HTML [Store apps]
- performance tools, HTML [Store apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7224dc1ddcffc203c930a3ead01c2f541af2122f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64792885"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>İzlenecek yol: Kullanıcı arabirimi yanıt hızını geliştirme (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, [HTML UI yanıtlama hızı profil oluşturucuyu](../profiling/html-ui-responsiveness.md)kullanarak bir performans sorununu belirleme ve düzeltme sürecinde size yol gösterir. Profil Oluşturucu, JavaScript kullanan Windows Evrensel ve Windows Mağazası uygulamaları için Visual Studio 'da kullanılabilir. Bu senaryoda, DOM öğelerini çok sık güncelleştiren bir performans testi uygulaması oluşturur ve bu sorunu tanımlamak ve gidermek için profil oluşturucuyu kullanırsınız.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Performans testi uygulaması oluşturma ve çalıştırma  
  
1. Visual Studio 'da yeni bir Windows Evrensel JavaScript projesi oluşturun. ( **Dosya/yeni/proje**' yi seçin. Sol bölmedeki **JavaScript** ' i seçin ve ardından **Windows**, **windows 10**, **evrensel**veya **Windows Phone**' yi seçin.  
  
2. > [!IMPORTANT]
    > Bu konuda gösterilen Tanılama sonuçları bir Windows 8 uygulaması için gösterilmiştir.  
  
3. Orta bölmedeki boş bir **uygulama**gibi boş proje şablonlarından birini seçin.  
  
4. **Ad** kutusunda, gibi bir ad belirtin `JS_Perf_Tester` ve ardından **Tamam**' ı seçin.  
  
5. **Çözüm Gezgini**, default.html 'yi açın ve aşağıdaki kodu Etiketler arasına yapıştırın \<body> :  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6. Default. css ' i açın ve aşağıdaki CSS kodunu ekleyin:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7. default.js açın ve tüm kodu şu kodla değiştirin:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8. Hata ayıklamayı başlatmak için F5 tuşunu seçin. Sayfada **değer bekleniyor** düğmesinin göründüğünü doğrulayın.  
  
9. **Değer bekleniyor** ' i seçin ve düğme metninin ve renginin saniyede yaklaşık olarak bir kez güncelleştirilmesini doğrulayın. Bu tasarım gereğidir.  
  
10. Visual Studio 'ya geri dönün (Alt + Tab) ve ardından hata ayıklamayı durdurmak için SHIFT + F5 ' i seçin.  
  
     Uygulamanın çalışıp çalışmadığını doğruladığınıza göre, profil oluşturucuyu kullanarak performansını inceleyebilirsiniz.  
  
### <a name="analyzing-performance-data"></a>Performans verilerinin analizi  
  
1. **Hata** ayıklama araç çubuğunda, **hata ayıklamayı başlat** listesinde, Windows Phone Öykünücüden veya **benzeticisinde**birini seçin.  
  
2. **Hata Ayıkla** menüsünde **performans ve tanılama**' yı seçin.  
  
3. **Kullanılabilir araçlar**' da **HTML UI yanıtlama hızı**' nı seçin ve ardından **Başlat**' ı seçin.  
  
    Bu öğreticide, profil oluşturucuyu başlangıç projesine iliştirirsiniz. Profil oluşturucuyu yüklü bir uygulamaya ekleme gibi diğer seçenekler hakkında bilgi için bkz. [HTML UI yanıt hızı](../profiling/html-ui-responsiveness.md).  
  
    Profil oluşturucuyu başlattığınızda, VsEtwCollector.exe çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi görebilirsiniz. **Evet**' i seçin.  
  
4. Çalışan uygulamada, **değer bekleniyor** ' i seçin ve 10 saniye bekleyin. Düğme metninin ve renginin saniye başına yaklaşık bir kez güncelleştirilmesini doğrulayın.  
  
5. Çalışan uygulamadan, Visual Studio 'ya geçin (Alt + Tab).  
  
6. **Toplamayı durdur**' ı seçin.  
  
    Profiler, bilgileri Visual Studio 'da yeni bir sekmede görüntüler. CPU kullanımı ve görsel işleme (FPS) verilerine baktığınızda, kolayca birkaç eğilim tanımlayabilirsiniz:  
  
   - CPU kullanımı yaklaşık 3 saniye sonra ( **değerler Için bekleniyor** düğmesine basıldığında) önemli ölçüde artar ve bu noktadan itibaren açık bir olay (komut dosyası, stil ve işleme olayları karışımı) gösterir.  
  
   - Görsel işleme etkilenmez ve FPS boyunca 60 konumunda kalır (yani, bırakılan çerçeve yoktur).  
  
     Bu yüksek etkinlik döneminde uygulamanın ne yaptığını öğrenmek için CPU kullanımı grafiğinin tipik bir bölümüne bakalım.  
  
7. CPU kullanım grafiğinin ortasında bir-iki saniyelik bir bölüm seçin (tıklayın-ve-sürükleyin ya da sekme ve ok tuşlarını kullanın). Aşağıdaki çizimde, bir seçim yaptıktan sonra CPU kullanımı grafiği gösterilmektedir. Paylaşılmayan alan seçimdir.  
  
    ![CPU kullanım grafiği](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. **Yakınlaştır '** ı seçin.  
  
    Grafik, seçili süreyi daha ayrıntılı gösterecek şekilde değişir. Aşağıdaki çizimde yakınlaştırdıktan sonra CPU kullanım grafiği gösterilmektedir. (Belirli veriler farklılık gösterebilir, ancak genel desenler görünür olur.)  
  
    ![Görünümde yakınlaştırılmış](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Alt bölmedeki zaman çizelgesi ayrıntıları, seçilen döneme ilişkin ayrıntıların bir örneğini gösterir.  
  
    ![Zaman çizelgesi ayrıntıları](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    Zaman çizelgesi ayrıntılarında bulunan olaylar, CPU kullanım grafiğinde görünür eğilimleri onaylayın: kısa süreler boyunca gerçekleşen çok sayıda olay vardır. Zaman çizelgesi Ayrıntıları görünümü bu olayların `Timer` , `Layout` ve olaylarının olduğunu gösterir `Paint` .  
  
9. Bağlam menüsünü kullanın (veya alt bölmedeki olaylardan birini sağ tıklayın) `Timer` ve **olaya filtrele**' yi seçin. Aşağıdaki çizimde, bu test uygulamasındaki olaylardan biri için tipik bir ayrıntı örneği gösterilmektedir `Timer` .  
  
     ![Süreölçer olayı](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Verilerden farklı bir olgu olabilir. Örneğin:  
  
    - Her `Timer` olay, bir komut dosyası olayı olarak tanımlamak için Color kodlamalı, öğesine bir çağrı `document.createElement` ve ardından bir stil hesaplaması ve ve çağrısı içerir `style.backgroundColor` `appendChild()` .  
  
    - Kısa zaman aralığında (yaklaşık olarak iki saniye), çok sayıda, ve daha fazla etkinlik gerçekleşirken vardır `Timer` `Layout` `Paint` . `Timer`Olaylar, uygulamayı çalıştırdıktan ve **değer bekleniyor** düğmesini seçtikten sonra bir saniyede bir güncelleştirmeden çok daha sık meydana gelir.  
  
10. Araştırmak için, `Timer` sol alt bölmedeki olaylardan biri için anonim işlevin bağlantısını seçin. Aşağıdaki işlev default.js açılır:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Bu özyinelemeli işlev, `setValues()` Kullanıcı arabirimindeki düğmeyi güncelleştiren işlevi çağıran bir döngü ayarlar. Profil Oluşturucu 'daki farklı süreölçer olaylarını inceleyerek, bu kodun en çok veya tüm Süreölçer olayları sonucu olduğunu fark edersiniz. bu nedenle, sorun burada oluşur.  
  
### <a name="fixing-the-performance-issue"></a>Performans sorunu düzeltiliyor  
  
1. `update()`İşlevi şu kodla değiştirin:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Bu kodun düzeltilen sürümü, kodun önceki sürümünden atlanan 1000 milisaniyelik bir gecikme içerir ve varsayılan bir gecikme değeri kullanılmasına neden olur. Profil Oluşturucu verilerinden, varsayılan değerin sıfır milisaniyelik olduğunu, bu da `setValues()` işlevin çok sık çalışmasına neden olur.  
  
2. HTML UI yanıtlama hızı profil oluşturucuyu yeniden çalıştırın ve CPU kullanımı grafiğini kontrol edin. Aşırı olayların geçmiş olduğunu ve CPU kullanımının yaklaşık sıfıra yakın olduğunu fark edersiniz. Düzenle!  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)
