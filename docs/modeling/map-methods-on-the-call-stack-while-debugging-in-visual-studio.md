---
title: Hata ayıklarken çağrı yığınında eşleştirme yöntemleri
description: Hata ayıklama sırasında çağrı yığınını görsel olarak izleme amacıyla kod haritası oluşturma hakkında bilgi. Ayrıca, kodun ne yaptığını izlemek için harita üzerinde notlar da çizebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c2c9a458c1955e999196574ed4fd9a174241f66a
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517293"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio'da hata ayıklarken çağrı yığınında eşleştirme yöntemleri

Hata ayıklama sırasında çağrı yığınını görsel olarak takip etmek için bir kod haritası oluşturun. Hataları bulmaya odaklanabilmeniz amacıyla kodun ne yaptığını izlemek için harita üzerine not alabilirsiniz.

 ![Kod eşlemeleri üzerinde çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap_overview.png)

 Şunlara ihtiyacınız var:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range=">=vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Visual C#, Visual Basic, C++, JavaScript veya X++ gibi hata ayıklayabilirsiniz kod

  Bkz.

- [Çağrı yığınını eşleme](#MapStack)

- [Kod hakkında not alın](#MakeNotes)

- [Haritayı sonraki çağrı yığınıyla güncelleştirme](#UpdateMap)

- [Haritaya ilgili kod ekleme](#AddRelatedCode)

- [Haritayı kullanarak hataları bulma](#FindBugs)

- [Soru& A](#QA)

  Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. Kod [eşlemelerini göz atma ve yeniden düzenleme.](../modeling/browse-and-rearrange-code-maps.md)

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Çağrı yığınını eşleme

1. Hata ayıklamayı başlatın. (Klavye: **F5**)

2. Uygulamanız kesme moduna girdikten veya bir işleve girdikten sonra Kod **Eşlemesi'ne tıklayın.** (Klavye: **Ctrl**  +  **Shift**  +  **`** ile )

     ![Çağrı yığını eşlemesini başlatmak için Kod Eşlemesi'ne tıklayın](../debugger/media/debuggermap_choosecodemap.png)

     Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

     ![Bkz. Kod haritasında çağrı yığını](../debugger/media/debuggermap_seeundocallstack.png)

     Hata ayıklamaya devam ederken eşleme otomatik olarak güncelleştirmesi yapılır. Bkz. [Haritayı sonraki çağrı yığınıyla güncelleştirme.](#UpdateMap)

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Kod hakkında not alın

 Kodda neler olduğunu izlemek için açıklamalar ekleyin. Açıklamaya yeni bir satır eklemek için Shift **+ Return tuşlarına basın.**

 ![Kod haritasında çağrı yığınına açıklama ekleme](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Haritayı sonraki çağrı yığınıyla güncelleştirme

 Uygulamanızı sonraki kesme noktasına kadar çalıştırın veya bir işleve adımlayın. Eşleme yeni bir çağrı yığını ekler.

 ![Kod eşlemesini sonraki çağrı yığınıyla güncelleştirme](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Haritaya ilgili kod ekleme

 Artık bir haritamız var. Sırada ne var? C# veya Visual Basic kodda neler olduğunu izlemek için alanlar, özellikler ve diğer yöntemler gibi öğeler ekleyin.

 Kod tanımını görmek için bir yönteme çift tıklayın veya yöntemin kısayol menüsünü kullanın. (Klavye: Haritada yöntemini seçin ve **F12 tuşuna basın)**

 ![Kod haritasında bir yöntem için kod tanımına gidin](../debugger/media/debuggermap_gotocodedefinition.png)

 Haritada izlemek istediğiniz öğeleri ekleyin.

 ![Çağrı yığını kod eşlemesinde bir yöntemde alanları gösterme](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Varsayılan olarak, eşlemeye öğe eklemek sınıf, ad alanı ve derleme gibi üst grup düğümlerini de ekler. Bu yararlı olabilir ancak harita araç çubuğundaki Üst Öğeleri  Ekle düğmesini kullanarak veya öğe eklerken **CTRL** tuşuna basarak bu özelliği kapatarak haritayı basit tutabilirsiniz.

 ![Çağrı yığını kod eşlemesi üzerinde bir yöntemle ilgili alanlar](../debugger/media/debuggermap_showedfields.png)

 Hangi yöntemlerin aynı alanları kullandığını kolayca görebilirsiniz. En son eklenen öğeler yeşil görünür.

 Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Alan kullanan yöntemlere bakın: yığın kodu eşlemesini çağırma](../debugger/media/debuggermap_findallreferences.png)

 ![Çağrı yığını kod haritasında alan kullanan yöntemler](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Haritayı kullanarak hataları bulma

 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, çizim programında bir hatayı araştırırken düşünün. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 Bu nedenle , ve yöntemlerinde kesme noktaları ayarlayın, hata `clear` `undo` `Repaint` ayıklamayı başlatarak aşağıdakine benzer bir haritayı derlemeniz gerekir:

 ![Kod haritasına başka bir çağrı yığını ekleme](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Harita üzerinde yapılan tüm kullanıcı hareketlerinin dışında çağrısında olduğunu `Repaint` fark ettiysiniz. `undo` Bu, neden `undo` hemen çalışmama nedenlerini açıklayabilir.

 Hatayı düzeltdikten ve programı çalıştırmaya devam ettikten sonra, eşleme yeni çağrıyı 'a `undo` `Repaint` ekler:

 ![Kod haritasında yığın çağrısı yapmak için yeni yöntem çağrısı ekleme](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Soru& A

- **Tüm çağrılar haritada görünmez. Neden?**

   Varsayılan olarak, haritada yalnızca kendi kodunuz görüntülenir. Dış kodu görmek için Çağrı Yığını penceresinde **açın:**

   ![Çağrı Yığını penceresini kullanarak dış kodu görüntüleme](../debugger/media/debuggermap_callstackmenu.png)

   hata ayıklama **seçeneklerinde Yalnızca kendi kodum** etkinleştir'Visual Studio devre dışı bırakabilirsiniz:

   ![Seçenekler iletişim kutusunu kullanarak dış kodu gösterme](../debugger/media/debuggermap_debugoptions.png)

- **Haritayı değiştirmek kodu etkiler mi?**

   Haritanın değiştirilmesi, kodu herhangi bir şekilde etkilemez. Haritadaki herhangi bir şeyi rahatça yeniden adlandırabilir, taşıyabilir veya kaldırabilirsiniz.

- **Bu ileti ne anlama geliyor: "Diyagram, kodun eski bir sürümünü temel alarak olabilir"?**

   Kod, haritayı son güncelleştirmenizden sonra değişmiş olabilir. Örneğin, harita üzerindeki bir çağrı artık kodda bulunmayabilir. İletiyi kapatın ve haritayı yeniden güncelleştirmeden önce çözümü yeniden oluşturmayı deneyin.

- **Nasıl yaparım? düzenini kontrol etmek mi?**

   Harita araç **çubuğunda** Düzen menüsünü açın:

  - Ekran düzenini değiştirin.

  - Haritayı otomatik olarak yeniden düzenlemeyi durdurmak için Hata **Ayıklarken Otomatik Düzen'i kapatın.**

  - Öğeleri eklerken haritayı mümkün olduğunca az yeniden düzenlemek için Artımlı **Düzen'i kapatın.**

- **Haritayı başkalarla paylaşabilir miyim?**

   Haritayı dışarı aktarabilirsiniz, Microsoft Outlook varsa başkalarına gönderebilir veya kaynak denetimine kontrol etmek için çözümünüze kaydedebilirsiniz.

   ![Çağrı yığını kod haritasını başkalarla paylaşma](../debugger/media/debuggermap_sharewithothers.png)

- **Nasıl yaparım? otomatik olarak yeni çağrı yığınları eklemesini durduracak mısınız?**

   Harita ![ araç &#45; kod haritasında çağrı yığınını otomatik olarak ](../debugger/media/debuggermap_automaticupdateicon.gif) göster'i seçin. Geçerli çağrı yığınını el ile haritaya eklemek için **Ctrl Shift tuşlarına**  +    +  **`** basın.

   Siz hata ayıklama sırasında harita üzerinde mevcut çağrı yığınlarını vurgulamaya devam eder.

- **Öğe simgeleri ve okları ne anlama geliyor?**

   Bir öğe hakkında daha fazla bilgi almak için fare işaretçisini üzerine sürükleyin ve öğenin araç ipucuna bakın. Her simgenin ne anlama **geldiğini öğrenmek** için Gösterge'ye de bakabilirsiniz.

   ![Çağrı yığını kod haritasındaki simgeler ne anlama geliyor?](../debugger/media/debuggermap_showlegend.png)

  Bkz.

- [Çağrı yığınını eşleme](#MapStack)

- [Kod hakkında not alın](#MakeNotes)

- [Haritayı sonraki çağrı yığınıyla güncelleştirme](#UpdateMap)

- [Haritaya ilgili kod ekleme](#AddRelatedCode)

- [Haritayı kullanarak hataları bulma](#FindBugs)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
