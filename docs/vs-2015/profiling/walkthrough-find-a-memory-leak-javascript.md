---
title: 'İzlenecek yol: bellek sızıntısı bulma (JavaScript) | Microsoft Docs'
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
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5617dc6cbe4b7ba096afe1f308d06e7f4aaf9c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785513"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>İzlenecek yol: Bellek sızıntısını bulma (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Bu izlenecek yol, JavaScript bellek Çözümleyicisi 'ni kullanarak basit bir bellek sorununu belirleme ve düzeltme sürecinde size yol gösterir. JavaScript bellek Çözümleyicisi, JavaScript kullanarak Windows için tasarlanan Windows Mağazası uygulamaları için Visual Studio 'da kullanılabilir. Bu senaryoda, öğeleri oluşturuldukları hızda elden atılması yerine, DOM öğelerini bellekte hatalı olarak koruyan bir uygulama oluşturacaksınız.  
  
 Bu uygulamadaki Bellek sızıntısının nedenine çok özgü olsa da, burada gösterilen adımlarda, bellek sızdıran nesneleri yalıtmak için genellikle geçerli olan bir iş akışı gösterilmektedir.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>JavaScript bellek Çözümleyicisi test uygulamasını çalıştırma  
  
1. Visual Studio'da **Dosya**, **Yeni**, **Proje**’yi seçin.  
  
2. Sol bölmedeki **JavaScript** ' i seçin ve ardından **Windows**, **windows 8**, **evrensel** veya **Windows Phone uygulamaları**' nı seçin.  
  
    > [!IMPORTANT]
    > Bu konuda gösterilen bellek kullanımı sonuçları bir Windows 8 uygulamasına göre test edilmiştir.  
  
3. Orta bölmedeki **boş uygulama** projesi şablonunu seçin.  
  
4. **Ad** kutusunda, gibi bir ad belirtin `JS_Mem_Tester` ve ardından **Tamam**' ı seçin.  
  
5. **Çözüm Gezgini**, default.html 'yi açın ve aşağıdaki kodu Etiketler arasına yapıştırın \<body> :  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    > Windows 8.1 Universal App şablonu kullanıyorsanız, HTML ve CSS kodunu her ikisinde de güncelleştirmeniz gerekir. Windows ve. WindowsPhone projeleri.  
  
6. Default. css ' i açın ve aşağıdaki CSS kodunu ekleyin:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7. default.js açın ve tüm kodu şu kodla değiştirin:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8. Hata ayıklamayı başlatmak için F5 tuşunu seçin. Sayfada **sızıntı belleği** düğmesinin göründüğünü doğrulayın.  
  
9. Visual Studio 'ya geri dönün (Alt + Tab) ve ardından hata ayıklamayı durdurmak için SHIFT + F5 ' i seçin.  
  
     Uygulamanın çalışmadığını doğruladığınıza göre, bellek kullanımını inceleyebilirsiniz.  
  
### <a name="analyzing-the-memory-usage"></a>Bellek kullanımını analiz etme  
  
1. **Hata** ayıklama araç çubuğunda, **hata ayıklamayı Başlat** listesinde, güncelleştirilmiş proje için hata ayıklama hedefini seçin: Windows Phone Öykünücüden ya da **simülatörden**biri.  
  
   > [!TIP]
   > Bir Windows Mağazası uygulaması için bu listede **yerel makine** veya **uzak makine** ' yi de seçebilirsiniz. Ancak, öykünücü veya simülatörü kullanmanın avantajı, uygulamayı Visual Studio 'Nun yanına yerleştirmeniz ve çalışan uygulama ile JavaScript bellek Çözümleyicisi arasında kolayca geçiş yapmanız olabilir. Daha fazla bilgi için bkz. [Visual Studio 'dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md) ve [uzak bir makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu...** öğesini seçin.  
  
3. **Kullanılabilir araçlar**' da **JavaScript belleği**' nı seçin ve ardından **Başlat**' ı seçin.  
  
    Bu öğreticide, bellek Çözümleyicisi 'ni başlangıç projesine iliştirirsiniz. Yüklü bir uygulamaya bellek Çözümleyicisi ekleme gibi diğer seçenekler hakkında bilgi için bkz. [JavaScript Memory](../profiling/javascript-memory.md).  
  
    Bellek Çözümleyicisi 'ni başlattığınızda, VsEtwCollector.exe çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi görebilirsiniz. **Evet**' i seçin.  
  
4. Art arda dört kez **sızıntı belleği** düğmesini seçin.  
  
    Düğmeyi seçtiğinizde default.js içindeki olay işleme kodu, bellek sızıntısına neden olacak şekilde çalışır. Bunu tanılama amacıyla kullanacaksınız.  
  
   > [!TIP]
   > Bellek sızıntısı için test etmek istediğiniz senaryonun tekrarlanmasını, uygulamanın başlatılması sırasında veya bir sayfa yüklenirken yığına eklenen nesneler gibi ilginç olmayan bilgileri filtrelemeyi kolaylaştırır.  
  
5. Çalışan uygulamadan, Visual Studio 'ya geçin (Alt + Tab).  
  
    JavaScript bellek Çözümleyicisi, Visual Studio 'da yeni bir sekmede bilgi görüntüler.  
  
    Bu Özet görünümündeki bellek grafiğinde zaman içinde işlem bellek kullanımı gösterilmektedir. Görünüm ayrıca **yığın anlık görüntüsü al**gibi komutlar sağlar. Anlık görüntü, belirli bir zamanda bellek kullanımı hakkında ayrıntılı bilgi sağlar. Daha fazla bilgi için bkz. [JavaScript hafıza](../profiling/javascript-memory.md).  
  
6. **Yığın anlık görüntüsünü Al**' ı seçin.  
  
7. Uygulamaya geçin ve **bellek sızıntısı**' nı seçin.  
  
8. Visual Studio 'ya geçin ve **yığın anlık görüntüsünü yeniden al** ' ı seçin.  
  
    Bu çizimde, taban çizgisi anlık görüntüsü (#1) ve anlık görüntü #2 gösterilmektedir.  
  
    ![Taban çizgisi anlık görüntüsü ve anlık görüntü 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   > Windows Phone öykünücüsü, anlık görüntünün alındığı sırada uygulamanın bir ekran görüntüsünü göstermez.  
  
9. Uygulamaya geçin ve **bellek sızıntısı** düğmesini yeniden seçin.  
  
10. Visual Studio 'ya geçin ve üçüncü kez **yığın anlık görüntüsü al** ' ı seçin.  
  
    > [!TIP]
    > Bu iş akışında üçüncü bir anlık görüntü alarak, taban çizgisi anlık görüntüsünden yapılan değişiklikleri bellek sızıntılarıyla ilişkilendirilmemiş ikinci anlık görüntüye filtreleyebilirsiniz. Örneğin, bir sayfada üstbilgileri ve altbilgileri güncelleştirme gibi beklenen değişiklikler olabilir. Bu, bellek kullanımında bazı değişiklikler oluşturacak ancak bellek sızıntılarıyla ilgisiz olabilir.  
  
     Bu çizimde Snapshot #2 ve Snapshot #3 gösterilmektedir.  
  
     ![Snapshot 2 ve Snapshot 3](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. Visual Studio 'da, profil oluşturmayı durdurmak için **Durdur** ' u seçin.  
  
12. Visual Studio 'da, anlık görüntüleri karşılaştırın. Snapshot #2 aşağıdakileri gösterir:  
  
    - Yığın boyutu (soldaki kırmızı yukarı ok ile gösterilen), anlık görüntü #1 karşılaştırıldığında birkaç KB artmıştır.  
  
      > [!IMPORTANT]
      > Yığın boyutu için tam bellek kullanım değerleri, hata ayıklama hedefine bağlıdır.  
  
    - Yığındaki nesne sayısı (sağdaki kırmızı yukarı ok ile gösterilir), anlık görüntü #1 kıyasla artmıştır. Bir nesne eklendi (+ 1) ve hiçbir nesne kaldırılmadı (-0).  
  
      Snapshot #3 aşağıdakileri gösterir:  
  
    - Yığın boyutu, anlık görüntü #2 kıyasla birkaç yüz bayt daha artmıştır.  
  
    - Yığın üzerindeki nesne sayısı, anlık görüntü #2 kıyasla yeniden arttı. Bir nesne eklendi (+ 1) ve hiçbir nesne kaldırılmadı (-0).  
  
13. Anlık görüntü #3, sağ taraftaki bağlantı metnini seçin ve kırmızı yukarı okun yanında + 1/ -0 değerini gösterir.  
  
     ![Farklı yığın nesneleri görünümüne bağlantı](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Bu, varsayılan olarak gösterilen türler görünümü ile **snapshot #3-snapshot #2**adlı yığın üzerindeki nesnelerin fark görünümünü açar. Varsayılan olarak, anlık görüntü #2 ve anlık görüntü #3 arasında yığına eklenen nesnelerin bir listesini görürsünüz.  
  
14. **Kapsam** filtresinde, **anlık görüntü #2 içinden kalan nesneleri**seçin.  
  
15. Burada gösterildiği gibi, nesne ağacının en üstünde Htmldıvelement nesnesini açın.  
  
     ![Yığında nesne sayısının fark görünümü](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Bu görünüm bellek sızıntısı hakkında aşağıdakiler gibi yararlı bilgileri gösterir:  
  
    - Bu görünüm, KIMLIĞI olan bir DIV öğesi gösterir `item` ve nesnenin elde tutulmuş boyutu birkaç yüz bayttır (tam değer farklılık gösterir).  
  
    - Bu nesne, anlık görüntü #2 bir soltover nesnesidir ve olası Bellek sızıntısını temsil eder.  
  
      Uygulamanın bazı bilgileri şu noktada yardımcı olur: **sızıntı belleği** ' nın SEÇILMESI bir DIV öğesini kaldırıp bir öğe eklememelidir, bu nedenle kod doğru çalışmıyor gibi görünüyor (yani, bellek sızıntısına neden olur). Sonraki bölümde bunun nasıl giderileceği açıklanmaktadır.  
  
    > [!TIP]
    > Bazen nesne ile ilgili bir nesnenin bulunması, `Global` Bu nesnenin tanımlanmasına yardımcı olabilir. Bunu yapmak için, tanımlayıcı için kısayol menüsünü açın ve ardından **kökleri görünümünde göster**' i seçin.  
  
## <a name="fixing-the-memory-issue"></a><a name="FixingMemory"></a> Bellek sorunu düzeltiliyor  
  
1. Profil Oluşturucu tarafından ortaya çıkarılan verileri kullanarak, KIMLIĞI "öğe" olan DOM öğelerinin kaldırılmasından sorumlu kodu inceleyebilirsiniz. Bu, işlevinde meydana gelir `initialize()` .  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` , belki de doğru çalışmıyor. Kodun DOM öğesini önbelleğe alma ve bir sorun bulma işlemlerini inceleyebilirsiniz; önbelleğe alınmış öğe başvurusu güncelleştirilmedi.  
  
2. default.js ' de, şu kod satırını çağrılmadan hemen önce Load işlevine ekleyin `appendChild` :  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Bu kod, **bellek sızıntısı** düğmesini seçtiğinizde öğenin doğru bir şekilde kaldırılması için önbelleğe alınmış öğeye yapılan başvuruyu günceller. Load işlevinin bütün kodu şu şekilde görünür:  
  
   ```javascript  
   function load() {  
  
       wrapper = document.querySelector(".wrapper");  
  
       var newDiv = document.createElement("div");  
  
       newDiv.style.zIndex = "-1";  
       newDiv.id = "item";  
       elem = newDiv;  
  
       wrapper.appendChild(newDiv);  
   }  
   ```  
  
3. **Hata Ayıkla** menüsünde **performans ve tanılama**' yı seçin.  
  
4. **Kullanılabilir araçlar**' da **JavaScript belleği**' nı seçin ve ardından **Başlat**' ı seçin.  
  
5. Üç anlık görüntü almak için aynı yordamı izleyin. Adımlar burada özetlenmiştir:  
  
   1. Uygulamada, art arda dört kez **sızıntı belleği** düğmesini seçin.  
  
   2. Visual Studio 'ya geçin ve taban çizgisi anlık görüntüsü için **yığın anlık görüntüsü al** ' ı seçin.  
  
   3. Uygulamada **sızıntı belleği** düğmesini seçin.  
  
   4. Visual Studio 'ya geçin ve ikinci anlık görüntü için **yığın anlık görüntüsünü Al** ' ı seçin.  
  
   5. Uygulamada **sızıntı belleği** düğmesini seçin.  
  
   6. Visual Studio 'ya geçin ve üçüncü anlık görüntü için **yığın anlık görüntüsü al** ' ı seçin.  
  
      Anlık görüntü #3 artık yığın boyutunu anlık görüntü #2 **artmaz** olarak gösterir ve nesne sayısı + 1/ -1 olarak gösterilir; Bu da bir nesne eklendiğini ve bir nesnenin kaldırıldığını gösterir. Bu, istenen davranıştır.  
  
      Aşağıdaki çizimde Snapshot #2 ve Snapshot #3 gösterilmektedir.  
  
      ![Sabit bellek sızıntısını gösteren anlık görüntüler](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript Belleği](../profiling/javascript-memory.md)
