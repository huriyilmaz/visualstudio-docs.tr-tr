---
title: R ile verileri görselleştirme
description: Çizim pencerelerini kullanarak R programlarından Visual Studio çizim.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 150bc0a1fb78c58ecc9e086cf20a25e32243215b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060511"
---
# <a name="create-visual-data-plots-with-r"></a>R ile görsel veri çizimleri oluşturma

Çizim, veri bilimcisi iş akışının önemli bir bölümü. Bu Visual Studio için R Araçları (RTVS) tüm çizim etkinliği, bu önemli etkinlikle üretkenliğinizi artırmak için tasarlanmış bir veya daha fazla çizim pencereleri çevresinde yer alıyor.

![Hero Görüntüsünü Çizerek](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için")
    :::column-end:::
    :::column:::
        [R (2m 02s)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) ile çizim youtube.com bir video (video) izleyin.
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>Çizim penceresi

Çizim penceresi, her çizimin bir komut tarafından oluşturularak oluşturulacak bir çizim `plot` serisini tutar. Örneğin, kullanmak `plot(1:100)` henüz kullanılamıyorsa yeni bir çizim penceresi oluşturur:

![1-100 Doğrusal çizim](media/plotting-1-to-100.png)

Teknik olarak, R komutları çıkışlarını bir R grafik cihazına işler; çizim penceresi R grafik cihazı içeriğini işler ve bu nedenle her çizim penceresine `plot` bir cihaz numarası verilir.

Çizim pencereleri, Visual Studio projelerden bağımsızdır ve siz projeleri yük açıp kapatırken açık kalır.

Çizim oluşturmak için "etkin" çizim penceresini kullanır ve önceki çizimleri çizim geçmişine kaydederek (bkz. [Çizim geçmişi).](#plot-history) Örneğin, girin `plot(100:1)` ve ilk çizim bir aşağı doğruyla değiştirilir.

Diğer tüm pencerelerde olduğu Visual Studio. çizim penceresi özelleştirilmiş düzenleri destekler [(bkz. Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md). Çizim pencereleri, bağımsız yeniden boyutlandırma için Visual Studio çerçeve içinde farklı konumlara yerleştirılabilir, bu çerçeve içinde yeniden boyutlandırılabilir veya tamamen çerçeveden çekılabilir.

Çizim penceresini yeniden boyutlandırmak, en iyi kaliteli görüntüyü sağlamak için çizimi her zaman yeniden işler. Genellikle sonraki bölümde açıklanan komutları kullanarak çizimi bir dosyaya veya panoya aktarmadan önce çizimi yeniden boyutlandırmak istersiniz.

## <a name="plot-window-commands"></a>Pencere komutlarını çiz

Çizim penceresinin araç çubuğunda geçerli komutlar yer almaktadır ve bunların çoğu **R** Araçları Çizimleri  >  **menüsünden de** kullanılabilir.

| Düğme | Komut | Açıklama |
| --- | --- | --- |
| ![Yeni çizim penceresi düğmesi](media/plotting-toolbar-01-new-plot-window.png) | Yeni çizim penceresi | Kendi geçmişine sahip ayrı bir çizim penceresi oluşturur. Bkz. [Çoklu çizim pencereleri.](#multiple-plot-windows) |
| ![Çizim penceresini etkinleştir düğmesi](media/plotting-toolbar-02-activate-plot-window.png) | Çizim penceresini etkinleştirme | Sonraki komutların bu pencereye işlenecek şekilde geçerli çizim `plot` penceresini etkin pencere olarak ayarlar. Bkz. [Çoklu çizim pencereleri.](#multiple-plot-windows) Bkz. [Çoklu çizim pencereleri.](#multiple-plot-windows) |
| ![Çizim geçmişi penceresi düğmesi](media/plotting-toolbar-03-plot-history.png) | Çizim geçmişi penceresi | Tarihteki tüm çizimlerin küçük resim olarak gösterildiği bir pencere açar. Bkz. [Çizim geçmişi.](#plot-history) |
| ![Çizim geçmişi düğmeleri](media/plotting-toolbar-04-plot-history-arrows.png) | Önceki/Sonraki Çizim |  Geçmişte önceki veya sonraki çizime gidin. Ayrıca Ctrl+Alt+F11 (Önceki) ve Ctrl+Alt+F12 (Sonraki) tuşlarıyla da geçmişte gezinsiniz. Bkz. [Çizim geçmişi.](#plot-history) |
| ![Görüntü olarak kaydet düğmesi](media/plotting-toolbar-05-save-as-image.png)| Farklı Kaydet Resmi | Bir dosya adı istenir ve geçerli çizimi (pencere içeriği, pencere boyutunda) bir görüntü dosyasına kaydeder. Kullanılabilir biçimler `.png` : , , ve `.jpg` `.bmp` `.tif` . |
| ![PDF olarak kaydet düğmesi](media/plotting-toolbar-06-save-as-pdf.png)| PDF Olarak Kaydet | Geçerli pencere boyutunu kullanarak geçerli çizimi bir PDF dosyasına kaydeder. PDF ölçeklendirildi ise çizim yeniden işleyici hale gelecektir. |
| ![Bit eşlem olarak kopyala düğmesi](media/plotting-toolbar-07-copy-as-bitmap.png)| Bit Eşlem Olarak Kopyala | Çizimi panoya, geçerli pencere boyutunu kullanarak bir tarama bit eşlemi olarak kopyalar. |
| ![Meta dosya olarak kopyala düğmesi](media/plotting-toolbar-08-copy-as-metafile.png)| Meta Dosya Olarak Kopyala | Çizimi panoya bir meta dosya (Wikipedia Windows [olarak](https://en.wikipedia.org/wiki/Windows_Metafile) kopyalar. |
| ![Çizimi kaldır düğmesi](media/plotting-toolbar-09-remove-plot.png)| Çizimi Kaldır | Geçerli çizimi tarihten kaldırır. |
| ![Tüm çizimleri temizle düğmesi](media/plotting-toolbar-10-clear-all-plots.png) | Tüm Çizimleri Temizle | Geçmişin tüm çizimlerini kaldırır (onay istemleri). |

## <a name="multiple-plot-windows"></a>Birden çok çizim pencereleri

Veri bilimcileri genellikle birçok farklı veri kümesinden çok sayıda çizimle birlikte çalışmalarından dolayı RTVS, çok sayıda bağımsız çizim pencereleri oluşturmanıza olanak sağlar. Daha sonra bu pencereleri, bu çerçevenin içinde veya Visual Studio tamamen aynı şekilde ayarlayabilirsiniz. (Pencereleri [yerleştirme ve yeniden boyutlandırma hakkında Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) için bkz. Visual Studio pencere düzenlerini özelleştirme.)

Araç çubuğu düğmesini veya **R** Araçları Çizimleri Yeni Çizim Penceresi'yi  >  **kullanarak yeni bir** çizim penceresi  >  **oluşturabilirsiniz.** Yeni çizim penceresi, yeni *çizimlerin* işlenecek olduğu etkin pencere olur. Etkin pencereyi değiştirmek için bu pencereye geçişin ve Çizim **Penceresini** Etkinleştir araç çubuğu düğmesini veya **R Araçları** ÇizimLeri Çizimi Etkinleştir  >    >  **Penceresini seçin.**

Çizimler de bağımsız nesnelerdir. Başka bir ifadeyle fareyle sürükleyip bırakarak veya sağ tıklama bağlamındaki **Kopyala,** Kes  ve Yapıştır komutlarını kullanarak bunları çizim pencereleri arasında kopyalayıp hareket **ettirebilirsiniz.** 

Sürükle ve bırak için varsayılan davranış kopyalamadır; Shift tuşuna basarak hareket etmek için **sürükleyip** bırakın.

## <a name="plot-history"></a>Çizim geçmişi

Çizim komutları her pencere için çizim geçmişinde tutularak oturum içindeki tüm çizimlerin korunmasını sağlar. Geçmiş'te gezinmek için çizim penceresi araç çubuğundaki ok düğmelerini veya **Ctrl** + **Alt** + **F11** ve **Ctrl** + **Alt** + **F12 tuşlarını kullanın.** Ayrıca, araç çubuğu düğmelerini veya **R** Araçları Çizimleri menü komutlarını kullanarak tek çizimleri kaldırabilir veya tüm  >  **çizimleri pencerede yeniden** temizleyebilirsiniz.

Çizim koleksiyonunun tamamını görmek için, araç çubuğu düğmesini veya **R** Araçları ÇizimLeri Çizim Geçmişi  >  **Penceresi'yi** kullanarak çizim  >  **geçmişi penceresini açın.**
Geçmiş, bu pencerede görüntülenen çizimlerin küçük resimlerin listesini, farklı çizim pencereleri (veya cihazlar) ile gruplara göre verir. Araç çubuğundaki yakınlaştırma düğmelerinin kullanımı küçük resimlerin boyutunu değiştirir.

![Çizim geçmişi penceresi](media/plotting-plot-history-window.png)

Bir çizimi ilişkili penceresinde açmak için bu çizime çift tıklayın, seçin ve ardından Çizimi Göster **araç çubuğu** düğmesini seçin. Alternatif olarak, çizime sağ tıklayın ve Çizimi **Göster'i seçin.** Ayrıca tek bir çizim seçerek bağlam veya Düzenleme menülerinden kopyalayıp kesebilirsiniz veya **silebilirsiniz.**

Çizim geçmişinizin tüm pencerelerde yaşam süresi, etkileşimli R oturum sürenizin ömrüne bağlı olur. R oturumlarınızı sıfırlarsanız veya oturumdan çıkar ve Visual Studio yeniden başlattıktan sonra çizim geçmişiniz sıfırlanır.

## <a name="programmatically-manipulate-plot-windows"></a>Çizim pencerelerini program aracılığıyla işleme

Belirli çizim pencerelerini tanımlamak için cihaz numaralarını kullanarak R kodundan çizim pencerelerini program aracılığıyla işebilirsiniz.

- `dev.list()`: Geçerli R oturumundaki tüm grafik cihazlarını listele.
- `dev.new()`: Yeni bir grafik cihazı (yeni bir çizim penceresi) oluşturun.
- `dev.set(<device number>)`: Etkin grafik cihazı ayarlayın.
- `dev.off()`: Etkin cihazı silin.
