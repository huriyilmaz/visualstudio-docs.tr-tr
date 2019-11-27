---
title: Hata ayıklarken çağrı yığınında eşleştirme yöntemleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a2c6e95822794394dbdfc7f53104b31b7c17ea9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296069"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio'da hata ayıklarken çağrı yığınında eşleştirme yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama sırasında çağrı yığınını görsel olarak izlemek için bir kod haritası oluşturun. Hataları bulmaya odaklanabilmeniz amacıyla kodun ne yaptığını izlemek için harita üzerine not alabilirsiniz.

 ![Kod Eşlemlerde çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Şunları yapmanız gerekir:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Visual C# .NET, Visual Basic .NET, C++, JavaScript veya X ++ gibi hatalarını ayıklayabileceğiniz kod

  Bkz. [video: kod Haritası hata ayıklayıcısı tümleştirmesiyle görsel hata ayıkla (Kanal 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [çağrı yığınını eşleyin](#MapStack) • [kodla ilgili notlar alın](#MakeNotes) • [sonraki çağrı yığını ile eşlemeyi güncelleştirin](#UpdateMap) • haritaya [ilgili kodu ekleyin](#AddRelatedCode) • [eşlemeyi kullanarak hataları bulun](#FindBugs) • [Q & A](#QA)

  Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a>Çağrı yığınını eşleme

1. Hata ayıklama başlatılamıyor. (Klavye: **F5**)

2. Uygulamanız kesme moduna girdiğinde veya bir işleve adımladıktan sonra **kod Haritası**' nı seçin. (Klavye: **Ctrl** + **SHIFT** +  **`** )

     ![Çağrı yığınını eşleştirmeye başlamak için kod haritasını seçin](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

     ![Bkz. kod eşlemesinde çağrı yığını](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Hata ayıklamaya devam et sırasında haritada otomatik olarak güncelleştirecektir. Bkz. [sonraki çağrı yığını ile eşlemeyi güncelleştirme](#UpdateMap).

## <a name="MakeNotes"></a>Kodla ilgili notlar alın
 Kod içinde neler olduğunu izlemek için açıklamalar ekleyin. Açıklamaya yeni bir satır eklemek için **SHIFT + Return**tuşlarına basın.

 ![Kod eşlemesinde çağrı yığınına Açıklama Ekle](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a>Sonraki çağrı yığını ile Haritayı güncelleştirme
 Uygulamanızı sonraki kesme noktasına kadar çalıştırın veya bir işleve adımlayın. Eşleme yeni bir çağrı yığını ekler.

 ![Sonraki çağrı yığını ile kod haritasını Güncelleştir](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a>Haritaya ilgili kod ekleme
 Şimdi bir eşlemeniz var - sırada ne var? Visual C# .NET veya Visual Basic .NET ile çalışıyorsanız, alanlar, özellikler ve kodda neler olduğunu izlemek için diğer yöntemler gibi öğeleri ekleyin.

 Kod tanımını görmek için bir yöntemi çift tıklayın ya da yöntem için kısayol menüsünü kullanın. (Klavye: haritada yöntemi seçin ve **F12**tuşuna basın)

 ![Kod eşlemesindeki bir yöntem için kod tanımına git](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Haritada izlemek istediğiniz öğeleri ekleyin.

 ![Çağrı yığını kod eşlemesinde bir yöntemde alanları gösterme](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Varsayılan olarak, öğeleri haritaya ekleme sınıfı, ad alanı ve derlemeye gibi üst düğümleri gruplandırma ekler. Bu yararlı olsa da, harita araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanarak veya öğe eklediğinizde **CTRL** tuşuna basarak Haritayı basit tutabilirsiniz.

 ![Çağrı yığını kod eşlemesindeki bir metotla ilgili alanlar](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Hangi yöntemlerin aynı alanları kullandığını kolayca görebilirsiniz. En son eklenen öğeler yeşil görünür.

 Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Bir alan kullanan yöntemlere bakın: çağrı yığını kod eşlemesi](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Çağrı yığını kod eşlemesinde bir alan kullanan Yöntemler](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a>Haritayı kullanarak hataları bulma
 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, bir çizim programında bir hata araştırdığınızı varsayın. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 `clear`, `undo`ve `Repaint` yöntemlerinde kesme noktaları ayarlayın, hata ayıklamayı başlatın ve bunun gibi bir eşleme oluşturun:

 ![Kod eşlemesine başka bir çağrı yığını ekleyin](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Eşleme çağrısındaki tüm Kullanıcı hareketlerine `undo`hariç `Repaint`fark edersiniz. Bu, `undo` neden hemen çalışmadığına ilişkin bir açıklama verebilir.

 Hatayı düzelttikten ve programı çalıştırmaya devam ettikten sonra, eşleme `undo` yeni çağrıyı `Repaint`öğesine ekler:

 ![Kod eşlemesinde çağrı yığınına yeni yöntem çağrısı Ekle](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a>soru-cevap &

- **Tüm çağrılar haritada görünmez. Kaydol?**

   Varsayılan olarak, yalnızca kendi kodunuzu harita üzerinde görüntülenir. Dış kodu görmek için, **çağrı yığını** penceresinde açın:

   ![Çağrı yığını penceresini kullanarak dış kodu görüntüle](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   Visual Studio hata ayıklama seçeneklerinde **yalnızca kendi kodum etkinleştir** ' i devre dışı bırak:

   ![Seçenekler iletişim kutusunu kullanarak dış kodu göster](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Haritanın değiştirilmesi kodu etkiler mi?**

   Haritanın değiştirilmesi, kodu herhangi bir şekilde etkilemez. Haritadaki herhangi bir şeyi rahatça yeniden adlandırabilir, taşıyabilir veya kaldırabilirsiniz.

- **Bu ileti ne anlama gelir: "diyagram, kodun eski bir sürümünü temel alabilir"?**

   Kod, haritayı son güncelleştirmenizden sonra değişmiş olabilir. Örneğin, harita üzerindeki bir çağrı artık kodda bulunmayabilir. İletiyi kapatın ve haritayı yeniden güncelleştirmeden önce çözümü yeniden oluşturmayı deneyin.

- **Haritanın düzeni kontrol Nasıl yaparım? mı?**

   Harita araç çubuğunda **Düzen** menüsünü açın:

  - Ekran düzenini değiştirin.

  - Haritayı otomatik olarak yeniden düzenlemeyi durdurmak için, **hata ayıklarken otomatik düzeni**devre dışı bırakın.

  - Öğeleri eklediğinizde, eşlemeyi olabildiğince az yeniden düzenlemek için, **artımlı düzeni**kapatın.

- **Haritayı başkalarıyla paylaşabilir miyim?**

   Haritayı dışarı aktarabilir, Microsoft Outlook'unuz varsa başkalarına gönderebilir veya çözümünüze kaydedebilir, böylece Team Foundation sürüm denetimine iade edebilirsiniz.

   ![Çağrı yığını kod haritasını başkalarıyla paylaşma](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Nasıl yaparım? haritanın otomatik olarak yeni çağrı yığınları eklemesini mi durdurun?**

   Harita araç çubuğunda ![ &#45; düğme otomatik olarak kod eşlemesinde çağrı yığınını göster](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") ' i seçin. Geçerli çağrı yığınını haritaya el ile eklemek için, **Ctrl** + **SHIFT** +  **`** tuşlarına basın.

   Eşleme, hata ayıklama işlemi sırasında eşlemede varolan çağrı yığınlarını vurgulamaya devam edecektir.

- **Öğe simgeleri ve okları ne anlama geliyor?**

   Bir öğe hakkında daha fazla bilgi almak için fare işaretçisini üzerine taşıyın ve öğenin ipucuna bakın. Ayrıca, her simgenin ne anlama geldiğini öğrenmek için **göstergeye** bakabilirsiniz.

   ![Çağrı yığını kod eşlemesindeki simgeler ne anlama geliyor?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Bkz. [çağrı yığınını eşleme](#MapStack) • [kodla ilgili notlar alın](#MakeNotes) • [sonraki çağrı yığını ile eşlemeyi güncelleştirin](#UpdateMap) • haritaya [ilgili kodu ekleyin](#AddRelatedCode) • eşlemeyi [kullanarak hataları bulun](#FindBugs)

## <a name="see-also"></a>Ayrıca Bkz.
 [Çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) [kod eşlemelerini kullanarak, uygulamalarınızda hata ayıklamak için kod haritaları kullanın](../modeling/use-code-maps-to-debug-your-applications.md) [kod Haritası Çözümleyicileri kullanarak olası sorunları bulun](../modeling/find-potential-problems-using-code-map-analyzers.md) kod [haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md)
