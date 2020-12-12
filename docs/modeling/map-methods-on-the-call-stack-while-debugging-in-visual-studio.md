---
title: Hata ayıklarken çağrı yığınında eşleştirme yöntemleri
description: Hata ayıklarken çağrı yığınını görsel olarak izlemek için bir kod Haritası oluşturmayı öğrenin. Ayrıca, kodun ne yaptığını izlemek üzere haritada Not alabileceğinizi öğrenin.
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b3d5c531400ddd88cea17b9172f19bf9711105d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362437"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio'da hata ayıklarken çağrı yığınında eşleştirme yöntemleri

Hata ayıklarken çağrı yığınını görsel olarak izlemek için bir kod haritası oluşturun. Hataları bulmaya odaklanabilmeniz amacıyla kodun ne yaptığını izlemek için harita üzerine not alabilirsiniz.

 ![Kod Eşlemlerde çağrı yığınları ile hata ayıklama](../debugger/media/debuggermap_overview.png)

 Şunlara ihtiyacınız var:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Visual C#, Visual Basic, C++, JavaScript veya X + + gibi hata ayıklayabilmeniz gereken kod

  Bkz.

- [Video: kod Haritası hata ayıklayıcısı tümleştirmesiyle görsel olarak hata ayıklayın (Kanal 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Çağrı yığınını eşleme](#MapStack)

- [Kodla ilgili notlar alın](#MakeNotes)

- [Sonraki çağrı yığını ile Haritayı güncelleştirme](#UpdateMap)

- [Haritaya ilgili kod ekleme](#AddRelatedCode)

- [Haritayı kullanarak hataları bulma](#FindBugs)

- [SORU-CEVAP &](#QA)

  Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Çağrı yığınını eşleme

1. Hata ayıklamayı başlatın. (Klavye: **F5**)

2. Uygulamanız kesme moduna girdiğinde veya bir işleve adımladıktan sonra **kod Haritası**' nı seçin. (Klavye: **CTRL**  +  **Shift**  +  **`** )

     ![Çağrı yığınını eşleştirmeye başlamak için kod haritasını seçin](../debugger/media/debuggermap_choosecodemap.png)

     Geçerli çağrı yığını yeni bir kod haritası üzerinde turuncu renkte görüntülenir:

     ![Bkz. kod eşlemesinde çağrı yığını](../debugger/media/debuggermap_seeundocallstack.png)

     Hata ayıklamaya devam ederken harita otomatik olarak güncelleştirilecek. Bkz. [sonraki çağrı yığını ile eşlemeyi güncelleştirme](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Kodla ilgili notlar alın

 Kodda neler olduğunu izlemek için açıklamalar ekleyin. Açıklamaya yeni bir satır eklemek için **SHIFT + Return** tuşlarına basın.

 ![Kod eşlemesinde çağrı yığınına Açıklama Ekle](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Sonraki çağrı yığını ile Haritayı güncelleştirme

 Uygulamanızı sonraki kesme noktasına kadar çalıştırın veya bir işleve adımlayın. Eşleme yeni bir çağrı yığını ekler.

 ![Sonraki çağrı yığını ile kod haritasını Güncelleştir](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Haritaya ilgili kod ekleme

 Artık bir haritanız var. ne kadar ileri? C# veya Visual Basic çalışıyorsanız, kodda neler olduğunu izlemek için alanlar, Özellikler ve diğer yöntemler gibi öğeleri ekleyin.

 Kod tanımını görmek için bir yönteme çift tıklayın veya yöntem için kısayol menüsünü kullanın. (Klavye: haritada yöntemi seçin ve **F12** tuşuna basın)

 ![Kod eşlemesindeki bir yöntem için kod tanımına git](../debugger/media/debuggermap_gotocodedefinition.png)

 Haritada izlemek istediğiniz öğeleri ekleyin.

 ![Çağrı yığını kod eşlemesinde bir yöntemde alanları gösterme](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Varsayılan olarak, haritaya öğe eklemek sınıf, ad alanı ve derleme gibi üst grup düğümlerini da ekler. Bu yararlı olsa da, harita araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanarak veya öğe eklediğinizde **CTRL** tuşuna basarak Haritayı basit tutabilirsiniz.

 ![Çağrı yığını kod eşlemesindeki bir metotla ilgili alanlar](../debugger/media/debuggermap_showedfields.png)

 Hangi yöntemlerin aynı alanları kullandığını kolayca görebilirsiniz. En son eklenen öğeler yeşil görünür.

 Daha fazla kod görmek için haritayı oluşturmaya devam edin.

 ![Bir alan kullanan yöntemlere bakın: çağrı yığını kod eşlemesi](../debugger/media/debuggermap_findallreferences.png)

 ![Çağrı yığını kod eşlemesinde bir alan kullanan Yöntemler](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Haritayı kullanarak hataları bulma

 Kodunuzu görselleştirmeniz, hataları daha hızlı şekilde bulmanıza yardımcı olabilir. Örneğin, bir çizim programında bir hata araştırdığınızı varsayalım. Bir çizgi çizip geri almayı denediğinizde, başka bir çizgi çizinceye kadar hiçbir şey olmaz.

 Bu nedenle,, ve yöntemlerinde kesme noktaları ayarlayın `clear` `undo` `Repaint` , hata ayıklamayı başlatın ve aşağıdakine benzer bir eşleme oluşturun:

 ![Kod eşlemesine başka bir çağrı yığını ekleyin](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Tüm Kullanıcı hareketleri için, eşleme çağrısı üzerinde, hariç olduğunu fark edersiniz `Repaint` `undo` . Bu, neden hemen çalışmadığına ilişkin bir açıklama verebilir `undo` .

 Hatayı düzelttikten ve programı çalıştırmaya devam ettikten sonra, eşleme kaynağından yeni çağrıyı ekler `undo` `Repaint` :

 ![Kod eşlemesinde çağrı yığınına yeni yöntem çağrısı Ekle](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> SORU-CEVAP &

- **Tüm çağrılar haritada görünmez. Kaydol?**

   Varsayılan olarak, haritada yalnızca kendi kodunuz görüntülenir. Dış kodu görmek için, **çağrı yığını** penceresinde açın:

   ![Çağrı yığını penceresini kullanarak dış kodu görüntüle](../debugger/media/debuggermap_callstackmenu.png)

   Visual Studio hata ayıklama seçeneklerinde **yalnızca kendi kodum etkinleştir** ' i devre dışı bırak:

   ![Seçenekler iletişim kutusunu kullanarak dış kodu göster](../debugger/media/debuggermap_debugoptions.png)

- **Haritanın değiştirilmesi kodu etkiler mi?**

   Haritanın değiştirilmesi, kodu herhangi bir şekilde etkilemez. Haritadaki herhangi bir şeyi rahatça yeniden adlandırabilir, taşıyabilir veya kaldırabilirsiniz.

- **Bu ileti ne anlama gelir: "diyagram, kodun eski bir sürümünü temel alabilir"?**

   Kod, haritayı son güncelleştirmenizden sonra değişmiş olabilir. Örneğin, harita üzerindeki bir çağrı artık kodda bulunmayabilir. İletiyi kapatın ve haritayı yeniden güncelleştirmeden önce çözümü yeniden oluşturmayı deneyin.

- **Haritanın düzeni kontrol Nasıl yaparım? mı?**

   Harita araç çubuğunda **Düzen** menüsünü açın:

  - Ekran düzenini değiştirin.

  - Haritayı otomatik olarak yeniden düzenlemeyi durdurmak için, **hata ayıklarken otomatik düzeni** devre dışı bırakın.

  - Öğeleri eklediğinizde, eşlemeyi olabildiğince az yeniden düzenlemek için, **artımlı düzeni** kapatın.

- **Haritayı başkalarıyla paylaşabilir miyim?**

   Haritayı dışarı aktarabilir, Microsoft Outlook varsa başkalarına gönderebilir veya onu kaynak denetimine iade edebilmeniz için çözümünüze kaydedebilirsiniz.

   ![Çağrı yığını kod haritasını başkalarıyla paylaşma](../debugger/media/debuggermap_sharewithothers.png)

- **Nasıl yaparım? haritanın otomatik olarak yeni çağrı yığınları eklemesini mi durdurun?**

   ![Harita araç çubuğunda düğme &#45; kod haritasında çağrı yığınını göster ' i seçin ](../debugger/media/debuggermap_automaticupdateicon.gif) . Geçerli çağrı yığınını haritaya el ile eklemek için **CTRL**  +  **SHIFT** tuşuna basın  +  **`** .

   Eşleme, hata ayıklama sırasında Haritadaki mevcut çağrı yığınlarını vurgulamaya devam edecektir.

- **Öğe simgeleri ve okları ne anlama geliyor?**

   Bir öğe hakkında daha fazla bilgi almak için fare işaretçisini onun üzerine taşıyın ve öğenin araç ipucuna bakın. Ayrıca, her simgenin ne anlama geldiğini öğrenmek için **göstergeye** bakabilirsiniz.

   ![Çağrı yığını kod eşlemesindeki simgeler ne anlama geliyor?](../debugger/media/debuggermap_showlegend.png)

  Bkz.

- [Çağrı yığınını eşleme](#MapStack)

- [Kodla ilgili notlar alın](#MakeNotes)

- [Sonraki çağrı yığını ile Haritayı güncelleştirme](#UpdateMap)

- [Haritaya ilgili kod ekleme](#AddRelatedCode)

- [Haritayı kullanarak hataları bulma](#FindBugs)

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
