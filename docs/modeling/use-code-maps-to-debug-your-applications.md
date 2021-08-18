---
title: Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma
description: Büyük kod tabanlarında, yabancı kodlarda veya eski kodlarda kaybetmeyi önlemeye yardımcı olmak için kod haritalarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b8376b7f5fa54f7c51ae9f55841778c8cbcdbdf4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034090"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma

[Kod eşlemeleri Visual Studio](../modeling/map-dependencies-across-your-solutions.md) büyük kod tabanlarında, yabancı kodlarda veya eski kodlarda kaybedilmekten kaçınmanıza yardımcı olabilir. Örneğin, hata ayıklama sırasında birçok dosya ve proje arasında koda bakman gerekir. Kod parçaları arasında gezinmek ve aralarındaki ilişkileri anlamak için kod haritalarını kullanın. Bu şekilde, bu kodu kafanızda takip etmek veya ayrı bir diyagram çizmek zorunda değildir. Bu nedenle, çalışmanız kesintiye uğrarsa kod eşlemeleri üzerinde çalıştığınız kodla ilgili belleğinizin yenilenmesine yardımcı olur.

![Kodda &#45; eşleme ilişkileri](../modeling/media/codemapstoryboardpaint.png)

**İmlecinizin düzenleyicide nerede göründüğü yeşil okla gösterilir**

Kod eşlemeleriyle çalışırken kullanabileceğiniz komutların ve eylemlerin ayrıntıları için bkz. Kod [eşlemelerini göz atma ve yeniden düzenleme.](../modeling/browse-and-rearrange-code-maps.md)

Hata Ayıklayıcı [aracıyla Visual Studio hata ayıklama hakkında daha fazla bilgi edinebilirsiniz.](../debugger/debugger-feature-tour.md)

> [!NOTE]
> Kod eşlemeleri oluşturmak ve düzenlemek için Visual Studio Enterprise gerekir. Bu Visual Studio Community Professional sürümlerinde, Enterprise yayında oluşturulan diyagramları açabilirsiniz ancak bunları düzenleyemezsiniz.

## <a name="understand-the-problem"></a>Sorunu anlama
 Üzerinde çalıştığınız bir çizim programında bir hata olduğunu varsayın. Hatayı yeniden oluşturmak için çözümü Visual Studio **F5 tuşuna basarak** hata ayıklamaya başlayabilirsiniz.

 Bir çizgi çizin ve Son vuruşumu **geri al'ı** seçerseniz, sonraki satırı çizene kadar hiçbir şey olmaz.

 ![Yeniden &#45; kod eşlemesi hatası](../modeling/media/codemapstoryboardpaint0.png)

 Bu nedenle yöntemini arayarak araştırmaya `Undo` başlayabilirsiniz. Bunu sınıfında `PaintCanvas` bulabilirsiniz.

 ![Kod &#45; Bul](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Kodu eşleştirmeyi başlat
 Şimdi yöntemini ve `undo` ilişkilerini eşlemeye başlayabilirsiniz. Kod düzenleyicisinden yöntemini ve `undo` yeni bir kod haritasına başvuracak alanları eklersiniz. Yeni bir eşleme oluşturduğunuzda, kodun dizinini oluşturmak biraz zaman alabilir. Bu, sonraki işlemlerin daha hızlı çalışmasını sağlar.

 ![Show method &#45; ilgili alanları göstermek için kod eşlemesi](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Yeşil vurgu eşlemeye eklenen son öğeleri gösterir. Yeşil ok, imlecinizin kodda konumunu gösterir. Öğeler arasındaki oklar farklı ilişkileri temsil eder. Fareyle haritadaki öğeler hakkında daha fazla bilgi almak için fareyi bunların üzerine hareket ettirerek ve araç ipucuna bakın.

 ![Kod haritası &#45; Araç &#45; göster](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Eşlemeden koda gitme ve kodu inceleme
 Her bir alanın kod tanımını görmek için harita üzerinde alana çift tıklayın veya alanı seçin ve **F12 tuşuna basın.** Yeşil ok eşlemedeki öğeler arasında hareket eder. Ayrıca kod düzenleyicisindeki imleciniz de otomatik olarak hareket eder.

 ![Geçmiş alanı seçilmiş bir kod haritası penceresinin ve tüm geçmiş örneklerinin vurgulanmış olduğu bir kod düzenleyicisi penceresinin ekran görüntüsü.](../modeling/media/codemapstoryboardpaint5.png)

 ![PaintObjects alanı seçili olan ve tüm paintObjects örneklerinin vurgulanmış olduğu bir kod düzenleyicisi penceresinin ekran görüntüsü.](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Kod düzenleyicisinde imleci hareket ettirerek yeşil oku eşlemede taşıyabilirsiniz.

## <a name="understand-relationships-between-pieces-of-code"></a>Kod parçaları arasındaki ilişkileri anlama
 Şimdi ve alanlarıyla etkileşime geçen diğer kodu bilmek `history` `paintObjects` istiyor. Bu alanlara başvuran tüm yöntemleri eşlemeye ekleyebilirsiniz. Bunu haritadan veya kod düzenleyicisinden de yapabiliriz.

 ![Kod eşlemesi &#45; Tüm başvuruları bulma](../modeling/media/codemapstoryboardpaint6.png)

 ![Kod düzenleyicisinden kod haritası açma](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Windows Phone veya Windows Store gibi birden çok uygulama arasında paylaşılan bir projeden öğe eklersiniz, bu öğeler her zaman haritada o anda etkin olan uygulama projesiyle görünür. Bu nedenle bağlamı başka bir uygulama projesiyle değiştirirsanız, haritadaki bağlam paylaşılan projeden yeni eklenen öğeler için de değişir. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

 İlişkilerin akışını yeniden düzenlemek ve eşlemenin okunmasını kolaylaştırmak için düzeni değiştirin. Ayrıca, öğeleri sürükleyerek de eşleme etrafında taşıyabilirsiniz.

 ![Düzen menüsü açık ve Soldan Rgiht komutu seçilmiş kod haritası penceresinin ekran görüntüsü.](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Varsayılan olarak, **Artımlı** Düzen açıktır. Yeni öğeler eklediğinizde, bu eşlemeyi mümkün olduğunca az yeniden düzenler. Her yeni öğe eklerken haritanın tamamını yeniden düzenlemek için Artımlı **Düzen'i kapatın.**

 ![Alanlar arasında ilişkilerhiop oklarının soldan sağa işaret ediyor olduğu bir kod haritası penceresinin ekran görüntüsü.](../modeling/media/codemapstoryboardpaint7.png)

 Bu yöntemleri inceleyelim. Haritada **PaintCanvas** yöntemine çift tıklayın veya bu yöntemi seçin ve **F12 tuşuna basın.** Bu yöntemin boş listeler olarak `history` ve `paintObjects` oluşturduğunı öğrenirsiniz.

 ![PaintCanvas yönteminin seçili olduğu ve PainCanvas yöntem adının vurgulanmış olduğu kod parçacığı görüntüsünün yer alan kod haritası penceresinin ekran görüntüsü.](../modeling/media/codemapstoryboardpaint8.png)

 Şimdi yöntem tanımını incelemek için aynı adımları `clear` tekrarlayın. ve ile `clear` bazı görevler gerçekleştiriyor olduğunu `paintObjects` `history` öğrenirsiniz. Ardından yöntemini `Repaint` çağıran.

 ![Clear yönteminin seçili olduğu bir kod haritası penceresinin ve Clear yönteminin kodunu gösteren kod parçacığı görüntüsünün ekran görüntüsü.](../modeling/media/codemapstoryboardpaint9.png)

 Şimdi yöntem tanımını `addPaintObject` incele. Ayrıca ve ile bazı görevler `history` `paintObjects` gerçekleştirir. Ayrıca çağrısı da `Repaint` lar.

 ![addPaintObject yönteminin seçili olduğu kod haritası penceresinin ve addPaintObject yönteminin kodunu gösteren kod parçacığı görüntüsünün ekran görüntüsü.](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Eşlemeyi inceleyerek sorunu bulma
 'ı değiştiren ve çağıran tüm `history` yöntemler gibi `paintObjects` `Repaint` görünüyor. Ancak `undo` yöntemi, aynı alanları `Repaint` değiştirene `undo` rağmen yöntemini çağırmaz. Bu nedenle, 'den çağrısıyla bu sorunu `Repaint` `undo` düzeltebilirsiniz.

 ![Kod eşlemesi &#45; Eksik yöntem çağrısını bulma](../modeling/media/codemapstoryboardpaint11.png)

 Size bu eksik çağrıyı gösteren bir eşlemeniz yoksa, özellikle de daha karmaşık kod söz konusu olduğunda bu sorunun bulunması daha zor olabilir.

## <a name="share-your-discovery-and-next-steps"></a>Keşfinizi ve sonraki adımları paylaşma
 Siz veya başka biri bu hatayı düzeltmeden önce, eşlemenin üzerine sorunla ve bu sorunun düzeltilmesiyle ilgili notlar ekleyebilirsiniz.

 ![Kod eşlemesi &#45; açıklama ve bayrak öğeleri](../modeling/media/codemapstoryboardpaint12.png)

 Örneğin, eşlemeye açıklamalar ekleyebilir ve renkler kullanarak öğeleri işaretleyebilirsiniz.

 ![Kod eşlemesi &#45; ve işaretlenmiş öğeler](../modeling/media/codemapstoryboardpaint12a.png)

 Microsoft Outlook yüklüyse, eşlemeyi başkalarına e-postayla gönderebilirsiniz. Eşlemeyi bir görüntü veya başka bir biçim olarak dışarı da aktarabilirsiniz.

 ![Kod eşlemesi &#45;, dışarı aktarma, posta](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Sorunu giderme ve ne yaptığınızı gösterme
 Bu hatayı düzeltmek için için çağrısı `Repaint` `undo` eklersiniz.

 ![Kod eşlemesi &#45; Eksik yöntem çağrısı ekleme](../modeling/media/codemapstoryboardpaint14.png)

 Düzeltmenizi onaylamak için hata ayıklama oturumunu yeniden başlatır ve hatayı yeniden oluşturmaya çalışırsınız. Şimdi Son **vuruşumu geri al'ın** seçimi beklediğiniz gibi çalışıyor ve doğru düzeltmeyi yaptığınız onaylar.

 ![Kod eşlemesi &#45; düzeltmeyi onaylayın](../modeling/media/codemapstoryboardpaint15.png)

 Eşlemeyi yaptığınız düzeltmeyi gösterecek şekilde güncelleştirebilirsiniz.

 ![Kod eşlemesi &#45; eksik yöntem çağrısıyla eşlemeyi güncelleştirme](../modeling/media/codemapstoryboardpaint16.png)

 Haritanız artık geri alma ile Yeniden Boya **arasındaki** **bağlantıyı gösteriyor.**

 ![Kod eşlemesi &#45; yöntem çağrısıyla güncelleştirildi](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Eşlemeyi güncelleştirdiğinizde, eşlemeyi oluşturmak için kullanılan kod dizininin güncelleştirdiğini belirten bir ileti görebilirsiniz. Bu, birisinin kodu eşlemenizin geçerli kodla eşleşmemesine neden olacak şekilde değiştirdiği anlamına gelir. Bu sizi eşlemeyi güncelleştirmekten alıkoymaz, ancak kodla eşleştiğini doğrulamak için eşlemeyi yeniden oluşturmak zorunda kalabilirsiniz.

 Araştırmanız bitti. Kodu eşleştirerek sorunu başarıyla buldunuz ve giderdiniz. Ayrıca kodda gezinmeye ve öğrendiklerinizi hatırlamanıza yardımcı olan ve sorunu gidermek için attığınız adımları gösteren bir eşlemeniz de vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kodu görselleştirme](../modeling/visualize-code.md)
