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
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8376884f72aeca2f3bf56f0d7bbc1636379a18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847303"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio'da hata ayıklarken çağrı yığınında eşleştirme yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama sırasında çağrı yığınını görsel olarak izlemek için bir kod haritası oluşturun. Hataları bulmaya odaklanabilmeniz amacıyla kodun ne yaptığını izlemek için harita üzerine not alabilirsiniz.

 ![Kod Eşlemlerde çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Şunları yapmanız gerekir:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Visual C# .NET, Visual Basic .NET, C++, JavaScript veya X + + gibi hata ayıklayabilmeniz gereken kod

  Bkz. [video: kod Haritası hata ayıklayıcısı tümleştirmesiyle görsel hata ayıkla (Kanal 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • [çağrı yığınını eşleyin](#MapStack) • [kodla ilgili notlar alın](#MakeNotes) • [sonraki çağrı yığını ile eşlemeyi güncelleştirin](#UpdateMap) • haritaya [ilgili kodu ekleyin](#AddRelatedCode) • [eşlemeyi kullanarak hataları bulun](#FindBugs) • [Q & A](#QA)

  Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Çağrı yığınını eşleme

1. Hata ayıklamayı başlatın. (Klavye: **F5**)

2. Uygulamanız kesme moduna girdiğinde veya bir işleve adımladıktan sonra **kod Haritası**' nı seçin. (Klavye: **CTRL**  +  **Shift**  +  **`** )

     ![Çağrı yığınını eşleştirmeye başlamak için kod haritasını seçin](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

     ![Bkz. kod eşlemesinde çağrı yığını](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Hata ayıklamaya devam ederken harita otomatik olarak güncelleştirilecek. Bkz. [sonraki çağrı yığını ile eşlemeyi güncelleştirme](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Kodla ilgili notlar alın
 Kod içinde neler olduğunu izlemek için açıklamalar ekleyin. Açıklamaya yeni bir satır eklemek için **SHIFT + Return**tuşlarına basın.

 ![Kod eşlemesinde çağrı yığınına Açıklama Ekle](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Sonraki çağrı yığını ile Haritayı güncelleştirme
 Uygulamanızı sonraki kesme noktasına kadar çalıştırın veya bir işleve adımlayın. Eşleme yeni bir çağrı yığını ekler.

 ![Sonraki çağrı yığını ile kod haritasını Güncelleştir](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Haritaya ilgili kod ekleme
 Şimdi bir eşlemeniz var - sırada ne var? Visual C# .NET veya Visual Basic .NET ile çalışıyorsanız, alanlar, özellikler ve kodda neler olduğunu izlemek için diğer yöntemler gibi öğeleri ekleyin.

 Kod tanımını görmek için bir yönteme çift tıklayın veya yöntem için kısayol menüsünü kullanın. (Klavye: haritada yöntemi seçin ve **F12**tuşuna basın)

 ![Kod eşlemesindeki bir yöntem için kod tanımına git](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Haritada izlemek istediğiniz öğeleri ekleyin.

 ![Çağrı yığını kod eşlemesinde bir yöntemde alanları gösterme](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Varsayılan olarak, haritaya öğe eklemek sınıf, ad alanı ve derleme gibi üst grup düğümlerini da ekler. Bu yararlı olsa da, harita araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanarak veya öğe eklediğinizde **CTRL** tuşuna basarak Haritayı basit tutabilirsiniz.

 ![Çağrı yığını kod eşlemesindeki bir metotla ilgili alanlar](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Hangi yöntemlerin aynı alanları kullandığını kolayca görebilirsiniz. En son eklenen öğeler yeşil görünür.

 Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Bir alan kullanan yöntemlere bakın: çağrı yığını kod eşlemesi](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Çağrı yığını kod eşlemesinde bir alan kullanan Yöntemler](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Haritayı kullanarak hataları bulma
 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, bir çizim programında bir hata araştırdığınızı varsayın. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 Bu nedenle,, ve yöntemlerinde kesme noktaları ayarlayın `clear` `undo` `Repaint` , hata ayıklamayı başlatın ve aşağıdakine benzer bir eşleme oluşturun:

 ![Kod eşlemesine başka bir çağrı yığını ekleyin](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Tüm Kullanıcı hareketleri için, eşleme çağrısı üzerinde, hariç olduğunu fark edersiniz `Repaint` `undo` . Bu, neden hemen çalışmadığına ilişkin bir açıklama verebilir `undo` .

 Hatayı düzelttikten ve programı çalıştırmaya devam ettikten sonra, eşleme kaynağından yeni çağrıyı ekler `undo` `Repaint` :

 ![Kod eşlemesinde çağrı yığınına yeni yöntem çağrısı Ekle](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="q--a"></a><a name="QA"></a> SORU-CEVAP &

- **Tüm çağrılar haritada görünmez. Kaydol?**

   Varsayılan olarak, haritada yalnızca kendi kodunuz görüntülenir. Dış kodu görmek için, **çağrı yığını** penceresinde açın:

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

   Harita araç çubuğunda ![düğme &#45; kod haritasında çağrı yığınını göster](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") ' i seçin. Geçerli çağrı yığınını haritaya el ile eklemek için **CTRL**  +  **SHIFT**tuşuna basın  +  **`** .

   Eşleme, hata ayıklama işlemi sırasında eşlemede varolan çağrı yığınlarını vurgulamaya devam edecektir.

- **Öğe simgeleri ve okları ne anlama geliyor?**

   Bir öğe hakkında daha fazla bilgi almak için fare işaretçisini onun üzerine taşıyın ve öğenin araç ipucuna bakın. Ayrıca, her simgenin ne anlama geldiğini öğrenmek için **göstergeye** bakabilirsiniz.

   ![Çağrı yığını kod eşlemesindeki simgeler ne anlama geliyor?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Bkz. [çağrı yığınını eşleme](#MapStack) • [kodla ilgili notlar alın](#MakeNotes) • [sonraki çağrı yığını ile eşlemeyi güncelleştirin](#UpdateMap) • haritaya [ilgili kodu ekleyin](#AddRelatedCode) • eşlemeyi [kullanarak hataları bulun](#FindBugs)

## <a name="see-also"></a>Ayrıca Bkz.
 [Çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) [kod eşlemelerini kullanarak, uygulamalarınızda hata ayıklamak için kod haritaları kullanın](../modeling/use-code-maps-to-debug-your-applications.md) [kod Haritası Çözümleyicileri kullanarak olası sorunları bulun](../modeling/find-potential-problems-using-code-map-analyzers.md) kod [haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md)
