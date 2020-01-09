---
title: Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e01857878f927c619529d3bbfc63728f84f0b81d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594116"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma

Kod haritaları, büyük kod tabanlarında, bilmediğiniz kodda veya eski kodda kaybolmadığınız önlemenize yardımcı olabilir. Örneğin, hata ayıklama yaparken birçok dosya ve proje arasında koda bakmanız gerekebilir. Kod parçalarının etrafında gezinmek ve aralarındaki ilişkileri anlamak için kod eşlemelerini kullanın. Bu şekilde, bu kodu başınızdan izlemenize veya ayrı bir diyagram çizmenize gerek kalmaz. Bu nedenle, çalışmanız kesintiye uğradığında, kod haritaları üzerinde çalıştığınız kodla ilgili belleğinizin yenilenmesine yardımcı olur.

![Koddaki kod &#45; Haritası eşleme ilişkileri](../modeling/media/codemapstoryboardpaint.png)

**Bir yeşil ok, imlecinizin düzenleyicide nerede göründüğünü gösterir**

Komutlar ve kod haritaları ile çalışırken kullanabileceğiniz eylemler için bilgi [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Kod haritaları oluşturmak ve düzenlemek için Visual Studio Enterprise sürümüne ihtiyacınız vardır. Visual Studio Community ve Professional sürümlerinde, Enterprise Edition 'da oluşturulan diyagramları açabilir, ancak düzenleyemezsiniz.

## <a name="understand-the-problem"></a>Sorunu anlama
 Üzerinde çalıştığınız bir çizim programında bir hata olduğunu varsayın. Hatayı yeniden oluşturmak için Visual Studio 'da çözümü açın ve hata ayıklamayı başlatmak için **F5** 'e basın.

 Bir çizgi çizdiğinizde ve **son vuruşumu geri al**' ı seçtiğinizde, bir sonraki satırı çizene kadar hiçbir şey olmaz.

 ![Kod Haritası &#45; yeniden üretme hatası](../modeling/media/codemapstoryboardpaint0.png)

 Bu nedenle, `Undo` yöntemini arayarak araştırmaya başlayabilirsiniz. `PaintCanvas` sınıfında bulabilirsiniz.

 ![Kod Haritası &#45; kod bulma](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Kodu eşleştirmeyi başlat
 Şimdi `undo` yöntemi ve ilişkilerini eşleştirmeye başlayın. Kod düzenleyicisinden, `undo` yöntemini ve başvurduğu alanları yeni bir kod haritasına eklersiniz. Yeni bir eşleme oluşturduğunuzda, kodun dizinini oluşturmak biraz zaman alabilir. Bu, sonraki işlemlerin daha hızlı çalışmasını sağlar.

 ![Kod Haritası &#45; yöntemi ve ilgili alanları göster](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Yeşil vurgu eşlemeye eklenen son öğeleri gösterir. Yeşil ok, imlecinizin koddaki konumunu gösterir. Öğeler arasındaki oklar farklı ilişkileri temsil eder. Fareyi üzerlerine taşıyarak ve araç ipuçlarını inceleyerek haritadaki öğeler hakkında daha fazla bilgi edinebilirsiniz.

 ![Kod Haritası &#45; araç ipuçlarını göster](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Eşlemeden koda gitme ve kodu inceleme
 Her bir alanın kod tanımını görmek için, haritadaki alana çift tıklayın veya alanı seçip **F12**tuşuna basın. Yeşil ok eşlemedeki öğeler arasında hareket eder. Ayrıca kod düzenleyicisindeki imleciniz de otomatik olarak hareket eder.

 ![Kod Haritası &#45; inceleme alanı tanımı](../modeling/media/codemapstoryboardpaint5.png)

 ![Kod Haritası &#45; inceleme alanı tanımı](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Kod düzenleyicisinde imleci hareket ettirerek yeşil oku eşlemede taşıyabilirsiniz.

## <a name="understand-relationships-between-pieces-of-code"></a>Kod parçaları arasındaki ilişkileri anlama
 Artık hangi diğer kodun `history` ve `paintObjects` alanlarıyla etkileşime gireceğini bildirmek istiyorsunuz. Bu alanlara başvuran tüm yöntemleri eşlemeye ekleyebilirsiniz. Bunu haritadan veya kod düzenleyicisinden yapabilirsiniz.

 ![Kod Haritası &#45; tüm başvuruları bul](../modeling/media/codemapstoryboardpaint6.png)

 ![Kod düzenleyicisinden bir kod Haritası açın](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Birden çok uygulama genelinde paylaşılan bir projeden (Windows Phone veya Windows Mağazası gibi) öğe eklerseniz, bu öğeler her zaman haritada etkin olan uygulama projesiyle görüntülenir. Bu nedenle, bağlamı başka bir uygulama projesi olarak değiştirirseniz, haritadaki bağlam paylaşılan projeden yeni eklenen öğeler için de değişir. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

 İlişkilerin akışını yeniden düzenlemek ve eşlemenin okunmasını kolaylaştırmak için düzeni değiştirin. Ayrıca, öğeleri sürükleyerek de eşleme etrafında taşıyabilirsiniz.

 ![Kod Haritası &#45; değişiklik düzeni](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Varsayılan olarak, **artımlı düzen** açıktır. Yeni öğeler eklediğinizde, bu eşlemeyi mümkün olduğunca az yeniden düzenler. Her yeni öğe eklediğinizde eşlemenin tamamını yeniden düzenlemek için, **artımlı düzeni**kapatın.

 ![Kod Haritası &#45; değişiklik düzeni](../modeling/media/codemapstoryboardpaint7.png)

 Bu yöntemleri inceleyelim. Haritada **PaintCanvas yöntemine** yöntemine çift tıklayın veya bu yöntemi seçin ve **F12**tuşuna basın. Bu yöntemin `history` oluşturup `paintObjects` boş listeler olarak olduğunu öğrenirsiniz.

 ![Kod Haritası &#45; inceleme yöntemi tanımı](../modeling/media/codemapstoryboardpaint8.png)

 Şimdi `clear` yöntem tanımını incelemek için aynı adımları yineleyin. `clear` `paintObjects` ve `history`bazı görevler gerçekleştireceğini öğrenirsiniz. Daha sonra `Repaint` yöntemini çağırır.

 ![Kod Haritası &#45; inceleme yöntemi tanımı](../modeling/media/codemapstoryboardpaint9.png)

 Şimdi `addPaintObject` yöntemi tanımını inceleyin. Ayrıca `history` ve `paintObjects`bazı görevler gerçekleştirir. Ayrıca `Repaint`çağırır.

 ![Kod Haritası &#45; inceleme yöntemi tanımı](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Eşlemeyi inceleyerek sorunu bulma
 `history` ve `paintObjects` çağrı `Repaint`değiştiren tüm yöntemler. `undo` yöntemi, `undo` aynı alanları değiştirse de `Repaint`çağırmaz. Bu nedenle, `undo``Repaint` çağırarak bu sorunu giderebilirsiniz.

 ![Kod eşlemesinde &#45; eksik yöntem çağrısı bul](../modeling/media/codemapstoryboardpaint11.png)

 Size bu eksik çağrıyı gösteren bir eşlemeniz yoksa, özellikle de daha karmaşık kod söz konusu olduğunda bu sorunun bulunması daha zor olabilir.

## <a name="share-your-discovery-and-next-steps"></a>Keşfinizi ve sonraki adımları paylaşma
 Siz veya başka biri bu hatayı düzeltmeden önce, eşlemenin üzerine sorunla ve bu sorunun düzeltilmesiyle ilgili notlar ekleyebilirsiniz.

 ![İzleme için &#45; kod eşleme açıklaması ve bayrak öğeleri](../modeling/media/codemapstoryboardpaint12.png)

 Örneğin, eşlemeye açıklamalar ekleyebilir ve renkler kullanarak öğeleri işaretleyebilirsiniz.

 ![Kod Haritası &#45; açıklamalı ve bayraklı öğeler](../modeling/media/codemapstoryboardpaint12a.png)

 Microsoft Outlook yüklüyse, eşlemeyi başkalarına e-postayla gönderebilirsiniz. Eşlemeyi bir görüntü veya başka bir biçim olarak dışarı da aktarabilirsiniz.

 ![Kod Haritası &#45; paylaşma, dışarı aktarma, posta](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Sorunu giderme ve ne yaptığınızı gösterme
 Bu hatayı onarmak için `Repaint` çağrısını `undo`eklersiniz.

 ![Kod eşlemesi &#45; eksik metot çağrısını Ekle](../modeling/media/codemapstoryboardpaint14.png)

 Düzeltmenizi onaylamak için hata ayıklama oturumunu yeniden başlatır ve hatayı yeniden oluşturmaya çalışırsınız. Şimdi **son vuruşumu geri al** ' ın seçilmesi, beklediği gibi çalışarak doğru düzeltmeyi yaptığını onayladınız.

 ![Kod Haritası &#45; kod düzeltmesini onaylayın](../modeling/media/codemapstoryboardpaint15.png)

 Eşlemeyi yaptığınız düzeltmeyi gösterecek şekilde güncelleştirebilirsiniz.

 ![Kod Haritası &#45; Güncelleştirme eşlemesi eksik yöntem çağrısı](../modeling/media/codemapstoryboardpaint16.png)

 Haritanız artık **geri alma** ve yeniden **çizmeyi**arasında bir bağlantı gösterir.

 ![Kod eşlemesi &#45; , metot çağrısı ile Haritayı güncelleştirildi](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Eşlemeyi güncelleştirdiğinizde, eşlemeyi oluşturmak için kullanılan kod dizininin güncelleştirdiğini belirten bir ileti görebilirsiniz. Bu, birisinin kodu eşlemenizin geçerli kodla eşleşmemesine neden olacak şekilde değiştirdiği anlamına gelir. Bu sizi eşlemeyi güncelleştirmekten alıkoymaz, ancak kodla eşleştiğini doğrulamak için eşlemeyi yeniden oluşturmak zorunda kalabilirsiniz.

 Artık araştırmanıza göre tamamladınız. Kodu eşleştirerek sorunu başarıyla buldunuz ve giderdiniz. Ayrıca kodda gezinmeye ve öğrendiklerinizi hatırlamanıza yardımcı olan ve sorunu gidermek için attığınız adımları gösteren bir eşlemeniz de vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kodu görselleştirme](../modeling/visualize-code.md)
