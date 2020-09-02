---
title: DOM olay dinleyicilerini görüntüleme | Microsoft Docs
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693583"
---
# <a name="view-dom-event-listeners"></a>DOM olayı dinleyicilerini görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 DOM Gezgini 'nin **Olaylar** SEKMESI bir DOM öğesiyle ilişkili olayları gösterir. **Olaylar** sekmesindeki her bir üst düğüm, etkin aboneler içeren bir olayı temsil eder. En üstteki düğüm, belirli bir olay için kayıtlı olay dinleyicilerini temsil eden alt düğümleri içerir. Olay dinleyicilerini görüntülemenin yanı sıra, JavaScript kodundaki olay dinleyicisinin konumuna gitmek için bu sekmeyi kullanabilirsiniz. Bu konudaki bilgiler, uygulamaları HTML ve JavaScript kullanarak depolamak için geçerlidir.

 **Olaylar** sekmesindeki liste dinamiktir. Uygulama çalışırken bir olay dinleyicisi eklerseniz, yeni olay dinleyicisi bu şekilde görünür. Olay dinleyicilerini ekleme ve kaldırma hakkında bilgi için, bu konudaki [olay dinleyicilerine yönelik sorunları çözümlemek Için ipuçlarına](#Tips) bakın.

> [!NOTE]
> DOM öğeleri olmayan kod öğeleri için olay dinleyicileri, örneğin `xhr` , **Olaylar** sekmesinde görünmez.

## <a name="view-event-listeners-for-dom-elements"></a>DOM öğeleri için olay dinleyicilerini görüntüleme
 Bu örnekte bir Windows Phone Mağazası uygulaması gösterilmektedir. Burada açıklanan DOM Gezgini özellikleri Windows Mağazası uygulamaları için de desteklenir.

#### <a name="to-view-event-listeners"></a>Olay dinleyicilerini görüntülemek için

1. Visual Studio 'da, Windows Phone Pivot uygulaması proje şablonunu kullanan bir JavaScript uygulaması oluşturun.

2. Şablon, Visual Studio 'da açıldığında hata ayıklayıcıdaki hata ayıklama araç çubuğundaki bir aşağı açılan listeden **öykünücü 8,1 WVGA 4'** i seçin:

     ![Hata ayıklama hedefi seçme](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Uygulamayı hata ayıklama modunda çalıştırmak için F5 tuşuna basın.

4. Çalışan uygulamada, **3. Bölüm** Özet öğesine gidin.

5. Visual Studio 'ya geçiş yapın (Alt + Tab veya F12).

6. DOM Gezgini 'nde `Find` sağ üst köşede öğesini seçin.

7. `ListView`yazın ve ardından Enter tuşuna basın.

8. Gerekirse, denetimi temsil eden öğeyi bulmak için **İleri** düğmesini seçin `DIV` `ListView` (Bu öğe bir `data-win-control` değerine sahiptir `WinJS.UI.ListView` ).

     `DIV`Öğe artık DOM Gezgini 'nde seçilmelidir.

9. DOM Gezgini 'nin sağ tarafındaki bölmede **Olaylar** sekmesini seçin.

     Artık, burada gösterildiği gibi, öğesi için etkin aboneleri olan olayları görebilirsiniz `DIV` .

     ![DOM Gezgini 'nin olaylar sekmesi](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Bu olaylara yönelik olay dinleyicilerini bulmak için ilişkili JavaScript dosya bağlantılarını seçin.

11. DOM hiyerarşisinde üst öğelere yönelik olay dinleyicilerini hızlıca tanımlamak için, DOM Gezgini 'nin altındaki hiyerarşi listesinden bir üst öğe seçin.

     ![DOM hiyerarşisinde üst öğeleri seçme](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     **Olaylar** sekmesi, hiyerarşi listesinde seçtiğiniz her öğe için olay dinleyicilerini gösterir.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Olay dinleyicileri sorunlarını çözmeye yönelik ipuçları
 Bazı uygulama senaryolarında, olay dinleyicilerinin [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)kullanılarak açıkça kaldırılması gerekir. Kod çalıştırırken Dom öğelerinden olay dinleyicilerinin kaldırılıp kaldırılmadığını test etmek için DOM Gezgini 'ndeki **Olaylar** sekmesini kullanın. Bu tür sorunları çözmeye yardımcı olmak için bazı ipuçları aşağıda verilmiştir:

- Visual Studio [Proje şablonlarında](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)uygulanan tek sayfalı gezinti modelini kullanan uygulamalarda, genellikle bir sayfanın PARÇASı olan DOM öğeleri gibi nesneler için kaydedilmiş olay dinleyicilerinin kaldırılması gerekmez. Bu senaryoda, bir DOM öğesi ve onunla ilişkili olay dinleyicileri aynı yaşam süresine sahiptir ve bunlar çöp toplamaları olabilir.

- DOM öğesinin veya nesnesinin yaşam süresi ilişkili olay dinleyicisinden farklıysa, yöntemini çağırmanız gerekebilir `removeEventListener` . Örneğin, olayı kullanırsanız `window.onresize` , olayı işleyen sayfadan uzaklaşmanız durumunda olay dinleyicisini kaldırmanız gerekebilir.

- `removeEventListener`Belirtilen dinleyiciyi kaldıramazsa, nesnenin farklı bir örneğine çağrılabilir. Dinleyiciyi eklediğinizde bu sorunu gidermek için [bağlama yöntemi (işlev)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) yöntemini kullanabilirsiniz.

- [Bağlama yöntemi (işlev)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) kullanılarak veya anonim bir işlev kullanarak eklenmiş bir olay dinleyicisini kaldırmak için, dinleyiciyi eklediğinizde işlevin bir örneğini saklayın. Bu düzenin güvenle kullanılması için bir yol aşağıda verilmiştir:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Bir başvuruyu bağlantılı işleve depolamak yerine aşağıdaki kodu kullanırsanız, olay dinleyicisini açıkça kaldıramayacağız:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- Bir olay dinleyicisini `removeEventListener` özniteliğini kullanarak eklediyseniz `obj.on<eventname>` , öğesini kullanarak kaldırabilirsiniz `window.onresize = handlerFunc` .

- Uygulamanızdaki [JavaScript bellek Çözümleyicisi ' ni](../profiling/javascript-memory.md) kullanın. Açıkça kaldırılması gereken olay dinleyicileri, bellek sızıntısı olarak görünebilir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)
- [DOM Gezgini'ni kullanarak CSS stillerinde hata ayıklama](../debugger/debug-css-styles-using-dom-explorer.md)
- [DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](../debugger/debug-layout-using-dom-explorer.md)