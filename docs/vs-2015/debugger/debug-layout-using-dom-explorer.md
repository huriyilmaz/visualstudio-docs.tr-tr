---
title: DOM Gezginini kullanarak hata ayıklama düzeni | Microsoft Docs
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a3c9b3a6ae2ed11e8512f8cf8857d27b3d0043b
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850069"
---
# <a name="debug-layout-using-dom-explorer"></a>DOM Gezgini'ni kullanarak düzen hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 DOM Gezgini 'nin **Düzen** sekmesi, bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamasında seçili öğe için [CSS kutusu modelini](https://www.w3.org/TR/CSS2/box.html) , Windows Phone mağaza uygulamasını veya Apache Cordova Visual Studio araçları kullanılarak oluşturulan bir uygulamayı gösterir. Öğelerin görünümünü etkileyen düzenle ilgili değerleri belirlemek ve değiştirmek için Box modelinin bu görsel gösterimini kullanabilirsiniz.  
  
> [!TIP]
> **Düzen** sekmesinde yaptığınız değişiklikler kalıcı değildir. Kaynak kodunuzda kalıcı değişiklikler yapabilir ve ardından hata ayıklama araç çubuğunda **Windows uygulamasını Yenile** düğmesini (yalnızca Windows mağazası ve Windows Phone mağaza uygulamaları) kullanarak uygulamanızı yenileyebilirsiniz. Bu şekilde, hata ayıklayıcıyı yeniden başlatmanıza engel olabilirsiniz.  
  
 Box modelinde görüntülenmeyen Düzen yönlerini değiştirmek üzere DOM Gezgini 'ni kullanmak için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) ve [DOM Gezgini kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Düzen sorunu düzeltme örneği  
 Bu örnekte, hub/Pivot şablonunda bir liste öğesinin nasıl görüntüleneceği, **Düzen** sekmesindeki kutu modeli değerlerinin nasıl yorumlanacağı ve sonra bir düzen sorununu giderecek Özellik değerlerinden birinin nasıl değiştirileceği gösterilmektedir.  
  
#### <a name="to-fix-the-layout-issue"></a>Düzen sorununu giderme  
  
1. Visual Studio 'da, Merkez/pivot proje şablonunu kullanan yeni bir mağaza uygulaması oluşturun.  
  
2. Paylaşılan pages\hub klasöründe, hub. css dosyasını açın.  
  
3. Aşağıdaki CSS kodunu değiştirin:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     Şu CSS kodu ile:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. Çözüm Gezgini ' de appName. WindowsPhone projesini veya appName. Windows projesini seçin ve ardından proje için kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.  
  
5. Başlangıç projenize bağlı olarak hata ayıklama araç çubuğundaki **öykünücü 8,1 WVGA 4 Inç 512MB** veya **simülatör** ' i seçin (**yerel makine** varsayılan değerdir).  
  
     ![Hata ayıklama hedefi seçme](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Uygulamanızı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
7. Kaydırma veya titreşerek 4. bölüm açın.  
  
    > [!TIP]
    > Visual Studio penceresinin hemen yanındaki telefon öykünücüsünü veya simülatörünü, CSS stillerinde yaptığınız seçimlerin ve değişikliklerinizin sonuçlarını hemen görebilirsiniz.  
  
     4\. Bölüm yüklendiğinde, küçük görüntülerin doğru olmadığına bakabilirsiniz. Her öğe görüntüsü yarım (sol yarısı eksik) olarak kesilir.  
  
8. Visual Studio 'ya geçin ve DOM Gezgini 'nde **öğe seç** ' i seçin (veya CTRL + B tuşlarına basın). Böylece seçim modu değişir ve öğeyi tıklatarak seçebilirsiniz ve uygulama da önplana gelir. Tek tıklatmadan sonra mod geri döner.  
  
    > [!TIP]
    > Ayrıca, doğrudan DOM Gezgini 'nde HTML öğelerini seçmek için ok tuşlarını veya diğer yöntemleri de kullanabilirsiniz. Öğe seçme hakkında daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. Telefon öykünücüsünde veya simülatör 'da, yarım bir şekilde kesilen görüntülerden birinin gri sağ yarısını seçin. Vurgu, Windows Phone öykünücüsünde aşağıda gösterildiği gibi seçili öğenin etrafında görünür:  
  
     ![DOM öğesi seçme](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > Simülatör, bir tane seçmeden önce DOM öğeleri etrafında kutu vurgulaması göstermek için öğelerin üzerine gelmesinin kullanılmasını destekler. Windows Phone öykünücüsü bunu desteklemez.  
  
     Bir DOM öğesi seçtiğinizde, DOM Gezgini otomatik olarak Visual Studio 'da karşılık gelen IMG öğesini seçer. DOM Gezgini 'nde seçilen öğe şöyle görünür:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. **Düzen** sekmesine tıklayın. Bu sekme, Windows Phone öykünücüsü içinde gösterildiği gibi seçili öğenin kutu modelini gösterir.  
  
     ![DOM Gezgini 'nin Düzen sekmesi](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Bu görünüm öğesi hakkında bazı yararlı bilgiler sağlar:  
  
    - Renkler, öğelerin üzerine gelindiğinde simülatör içinde görüntülenen kutu vurgulaması için karşılık gelir. Mavi renk \<img > öğe boyutlarını temsil eder. Tan rengi, kenar boşluğu değerlerini temsil eder.  
  
    - Sol kenar boşluğu (kenar boşluğu-sol), belirtiyle eşleştiğinden (görüntülerin sol tarafında siyah), bu sorunun nedenini gösteren bir deyişle belirlenir.  
  
    - 0 piksel (örneğin, kenarlık ve doldurma) değerlerini gösteren kutular, karşılık gelen CSS özelliklerinin büyük olasılıkla ayarlanmaması gerektiğini önerir.  
  
11. Kenar boşluğu sol kuralının nasıl uygulandığını görmek için, **hesaplanan** sekmesini seçin ve sol kenar boşluğu kuralı altına bakın. Bu kuralın bir 5em değeri ile ayarlandığını görebilirsiniz, ancak hedef cihazınıza bağlı olarak, hesaplanan değer 66.66 px ya da 146.66 px olur.  
  
    > [!TIP]
    > **Hesaplanan** sekme, sol kenar boşluğunun `..hubpage .hub. section4 .sub-image-row img` CSS seçicisinde ayarlandığı, hub. css dosyasında bulunduğunu gösterir. Bu tanıtım uygulamasında, bu, çözümü yapmanız gereken yerdir.  
  
     Düzen değerlerinde yapılan değişiklikleri test etmek için de **Düzen** sekmesini kullanabilirsiniz.  
  
12. **Düzen** sekmesinde, kutunun sol tarafındaki **kenar boşluğu** kutusunda görünen **66,66** veya **146,66**seçeneklerinden birini belirleyin.  
  
13. `0` yazıp Enter tuşuna basın. (Değeri değiştirmek için yukarı ok ve aşağı ok tuşlarını da kullanabilirsiniz.)  
  
14. DOM Gezgini 'nde diğer \<img > öğelerini seçin ve kenar boşluğu sol değerlerini 0 olarak değiştirin.  
  
15. Telefon öykünücüye veya benzeticide geçiş yapın. Güncelleştirilmiş kenar boşluğu-sol değerleri Bölüm 4 görüntülerine uygulandı. Bu değerler ayrıca, sol taraftaki kenar boşluğu kuralı altındaki **hesaplanan** sekmede de güncelleştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md)   
 [DOM Gezgini 'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)   
 [DOM olayı dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md)
