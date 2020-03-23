---
title: R ile verileri görselleştirme
description: Visual Studio'daki R programlarından gelen verileri çizim pencerelerini kullanarak nasıl çizilir?
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a48ad7800f8ea2b992e848cfbf6b4fdac99b2062
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62811186"
---
# <a name="create-visual-data-plots-with-r"></a>R ile görsel veri çizimleri oluşturma

Çizim, bir veri bilimcinin iş akışının önemli bir parçasıdır. R Tools for Visual Studio 'da (RTVS), bu anahtar etkinlikle üretkenliğinizi artırmak için tasarlanmış bir veya daha fazla çizim penceresi etrafında ki tüm çizim etkinlik merkezleri.

![Kahraman İmajı Çizme](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | R (2m 02s) ile çizim yaparken [bir video (youtube.com) izleyin.](https://www.youtube.com/watch?v=ZTbKmz5RSgY) |

## <a name="the-plot-window"></a>Çizim penceresi

Çizim penceresi, her çizimin bir `plot` komut tarafından oluşturulduğu bir dizi çizim tutar. Örneğin, kullanmak `plot(1:100)` zaten kullanılamıyorsa yeni bir çizim penceresi oluşturur:

![1 - 100 Doğrusal çizim](media/plotting-1-to-100.png)

Teknik olarak konuşursak, R `plot` komutları çıktılarını bir R grafik aygıtına işleter; çizim penceresi, bir R grafik aygıtının içeriğini işler, bu nedenle her çizim penceresine bir aygıt numarası verilir.

Çizim pencereleri Visual Studio projelerinden bağımsızdır ve projeleri yükledikçe ve kapattıkça açık kalır.

Bir çizim oluşturma "etkin" çizim penceresi kullanır, herhangi bir önceki arsa o arsa geçmişi kaydederek [(Çizim geçmişi](#plot-history)bakınız). Örneğin, girin `plot(100:1)` ve ilk çizim aşağı doğru bir çizgi ile değiştirilir.

Diğer tüm Visual Studio pencereleri gibi. çizim penceresi özelleştirilmiş düzenleri destekler [(Bkz. Visual Studio'da pencere düzenlerini özelleştir.](../ide/customizing-window-layouts-in-visual-studio.md) Çizim pencereleri Visual Studio çerçevesi içinde farklı konumlara sabitlenebilir, bu çerçeve içinde yeniden boyutlandırılabilir veya tamamen bağımsız yeniden boyutlandırma için çerçeveden çıkarılabilir.

Çizim penceresini yeniden boyutlandırma, en iyi kalitede görüntü sağlamak için çizimi her zaman yeniden işler. Genellikle, bir sonraki bölümde açıklanan komutları kullanarak çizimi bir dosyaya veya panoya dışa aktarmadan önce çizimi yeniden boyutlandırmak istersiniz.

## <a name="plot-window-commands"></a>Çizim penceresi komutları

Çizim penceresinin araç çubuğu, çoğu **R Tools** > **Plots** menüsünden de kullanılabilen geçerli komutları tutar.

| Düğme | Komut | Açıklama |
| --- | --- | --- |
| ![Yeni çizim penceresi düğmesi](media/plotting-toolbar-01-new-plot-window.png) | Yeni çizim penceresi | Kendi geçmişi olan ayrı bir çizim penceresi oluşturur. Bkz. [Birden çok çizim penceresi.](#multiple-plot-windows) |
| ![Çizim penceresi düğmesini etkinleştirme](media/plotting-toolbar-02-activate-plot-window.png) | Çizim pencereni etkinleştirme | Geçerli çizim penceresini etkin pencere olarak `plot` ayarlar, böylece sonraki komutlar bu pencereye işlenir. Bkz. [Birden çok çizim penceresi.](#multiple-plot-windows) Bkz. [Birden çok çizim penceresi.](#multiple-plot-windows) |
| ![Geçmiş penceresi düğmesini çiz](media/plotting-toolbar-03-plot-history.png) | Çizim geçmişi penceresi | Küçük resim olarak gösterilen tarihteki tüm çizimleri içeren bir pencere açar. Bkz. [Arsa geçmişi.](#plot-history) |
| ![Geçmiş düğmelerini çiz](media/plotting-toolbar-04-plot-history-arrows.png) | Önceki/Sonraki Çizim |  Tarihteki önceki veya sonraki çizime doğru ilerlerken. Ctrl+Alt+F11 (Önceki) ve Ctrl+Alt+F12 (İleri) ile de geçmişi gezinebilirsiniz. Bkz. [Arsa geçmişi.](#plot-history) |
| ![Görüntü olarak kaydet düğmesi](media/plotting-toolbar-05-save-as-image.png)| Görüntü Olarak Kaydet | Dosya adı ister ve geçerli çizimi (pencere içeriği, pencere boyutunda) bir resim dosyasına kaydeder. Kullanılabilir biçimler `.png` `.jpg`, `.bmp`, `.tif`, ve . |
| ![PDF olarak kaydet düğmesi](media/plotting-toolbar-06-save-as-pdf.png)| PDF Olarak Kaydet | Geçerli pencere boyutunu kullanarak geçerli çizimi PDF dosyasına kaydeder. PDF ölçeklendirilirse çizim yeniden işlenir. |
| ![Bitmap düğmesi olarak kopyala](media/plotting-toolbar-07-copy-as-bitmap.png)| BitMap Olarak Kopyala | Geçerli pencere boyutunu kullanarak çizimi panoya bir raster bit eşlemi olarak kopyalar. |
| ![Metadosya düğmesi olarak kopyala](media/plotting-toolbar-08-copy-as-metafile.png)| Metadosya Olarak Kopyala | Çizimi panoya [Windows metadosyası](https://en.wikipedia.org/wiki/Windows_Metafile) (Vikipedi) olarak kopyalar. |
| ![Çizim düğmesini kaldırma](media/plotting-toolbar-09-remove-plot.png)| Çizimi Kaldır | Geçerli çizimi tarihten kaldırır. |
| ![Tüm çizimler düğmesini temizle](media/plotting-toolbar-10-clear-all-plots.png) | Tüm Çizimleri Temizle | Tüm çizimleri geçmişten kaldırır (onay istemi). |

## <a name="multiple-plot-windows"></a>Birden çok çizim penceresi

Veri bilim adamları genellikle birçok farklı veri kümelerinden birçok arsaile çalıştıklarıiçin, RTVS birçok bağımsız çizim penceresi oluşturmanıza olanak tanır. Daha sonra bu pencereleri Visual Studio çerçevesi içinde veya bu çerçevenin dışında istediğiniz gibi düzenleyebilirsiniz. (Pencereleri yerleştirme ve yeniden boyutlandırma hakkında genel bilgi için [Visual Studio'daki pencere düzenlerini özelleştir'e](../ide/customizing-window-layouts-in-visual-studio.md) bakın.)

Araç çubuğu düğmesini veya **R Tools** > **Plots New Plot Window'u**kullanarak yeni bir çizim penceresi**oluşturursunuz.** >  Yeni çizim penceresi, yeni *çizimlerin* işlendiği etkin pencere olur. Etkin pencereyi değiştirmek için, ona geçin ve **Çizim Penceresi** araç çubuğunu etkinleştir düğmesini veya **R Araçları** > **Çizimlerini** > **Etkinleştir Çizim Penceresi'ni**seçin.

Çizimler de bağımsız nesnelerdir, bu da fareyle sürükle ve bırak'ı kullanarak veya sağ tıklatma bağlamında **Copy**kopyala, **kes**ve **yapıştır** komutlarını kullanarak ve menüleri **edin** komutlarını kullanarak bunları kopyalayıp çizim pencereleri arasında taşıyabileceğiniz anlamına gelir.

Sürükle ve bırak için varsayılan davranış kopyadır; **Shift** tuşunu basılı tutarken hareket etmek, sürükle ve bırak.

## <a name="plot-history"></a>Arsa geçmişi

Çizim komutları, her pencere için bir çizim geçmişinde korunur ve oturumdaki tüm çizimlerinizin korunmasını sağlar. Geçmişi gezinmek için, çizim penceresi araç çubuğundaki ok düğmelerini veya **Ctrl**+Alt**F11** ve **Ctrl**+**Alt**+**Alt**+**F12'yi**kullanın. Ayrıca, araç çubuğu düğmelerini veya **R Tools** > **Plots** menü komutlarını kullanarak tek çizimleri kaldırabilir veya pencereden tüm çizimleri yeniden temizleyebilirsiniz.

Çizimlerin tüm koleksiyonunu görmek için, araç çubuğu düğmesini veya **R Tools** > **Plots** > **Plot History Window'u**kullanarak çizim geçmişi penceresini açın.
Geçmiş, bu pencerede görüntülenen ve farklı çizim pencerelerine (veya aygıtlara) göre gruplanmış çizimlerin küçük resimlerinin bir listesini verir. Araç çubuğundaki yakınlaştırma düğmelerini kullanmak küçük resimlerin boyutunu değiştirir.

![Çizim geçmişi penceresi](media/plotting-plot-history-window.png)

İlişkili penceresinde bir çizimi açmak için, bu çizimi çift tıklatın, seçin ve ardından **Çizimi Göster** araç çubuğunu seçin veya Çizimi Göster'i sağ tıklatın ve **Çizimi Göster'i**seçin. Ayrıca tek bir çizim seçebilir ve sağ tıklatma bağlamından veya **Menüleri Düzenle** menülerinden kopyalayabilir, kesebilir veya silebilirsiniz.

Tüm pencerelerdeki çizim geçmişinizin ömrü etkileşimli R oturumunuzun ömrüne bağlıdır. R oturumunuzu sıfırlarsanız veya Visual Studio'dan çıkıp yeniden başlatın, çizim geçmişiniz sıfırlanır.

## <a name="programmatically-manipulate-plot-windows"></a>Çizim pencerelerini programlı olarak manipüle etmek

Belirli çizim pencerelerini tanımlamak için aygıt numaralarını kullanarak R kodundan çizim pencerelerini programlı bir şekilde işleyebilirsiniz.

- `dev.list()`: Geçerli R oturumundaki tüm grafik aygıtlarını listele.
- `dev.new()`: Yeni bir grafik aygıtı (yeni bir çizim penceresi) oluşturun.
- `dev.set(<device number>)`: Etkin grafik aygıtını ayarlayın.
- `dev.off()`: Etkin aygıtı silin.
