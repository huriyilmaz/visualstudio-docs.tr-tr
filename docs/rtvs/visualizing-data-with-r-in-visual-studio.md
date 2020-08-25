---
title: R ile verileri görselleştirme
description: Visual Studio 'da R programlarından verileri, çizim pencerelerini kullanarak çizdirme.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: dbb3984385e0042c669f8aad1d5bb4a2f64de917
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801626"
---
# <a name="create-visual-data-plots-with-r"></a>R ile görsel veri çizimleri oluşturma

Çizim, veri bilimi 'nin iş akışının önemli bir parçasıdır. Visual Studio için R Araçları (RTVS) ' de, tüm çizim etkinlikleri, bu anahtar etkinliğiyle üretkenliğinizi artırmak için tasarlanan bir veya daha fazla çizim penceresi etrafında ortalar.

![Hero görüntüsünü çizme](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için")
    :::column-end:::
    :::column:::
        R (2m 02S) ile çizim yaparken [bir videoyu (YouTube.com) izleyin](https://www.youtube.com/watch?v=ZTbKmz5RSgY) .
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>Çizim penceresi

Çizim penceresi, her çizimin bir komut tarafından oluşturulduğu bir dizi çizim içerir `plot` . Örneğin, kullanma, `plot(1:100)` zaten mevcut değilse yeni bir çizim penceresi oluşturur:

![1-100 Doğrusal çizim](media/plotting-1-to-100.png)

Teknik olarak, R `plot` komutları çıktılarını bir r grafik cihazında işleyebilir; bir çizim penceresi, her çizim penceresine bir cihaz numarası verilmesinin neden olduğu bir r grafik cihazının içeriğini işler.

Çizim pencereleri Visual Studio projelerinden bağımsızdır ve projeleri yüklerken ve kapatırken açık kalır.

Bir çizim oluşturmak, yukarıdaki çizim geçmişini (bkz. [Çizim geçmişi](#plot-history)) kaydederek "etkin" çizim penceresini kullanır. Örneğin, girin `plot(100:1)` ve ilk çizim, aşağı doğru bir satırla değiştirilmiştir.

Diğer tüm Visual Studio pencereleri gibi. çizim penceresi özelleştirilmiş düzenleri destekler (bkz. [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md). Çizim pencereleri, Visual Studio çerçevesindeki farklı konumlara yerleştirilebilir, bu çerçeve içinde yeniden boyutlandırılabilir veya tamamen bağımsız yeniden boyutlandırma için çerçevenin dışına çıkarılabilir.

Bir çizim penceresinin yeniden boyutlandırılması, en iyi kalite görüntüsünü sağlamak için her zaman çizimi yeniden oluşturur. Genellikle bir çizimi bir dosyaya veya panoya vermeden önce, sonraki bölümde açıklanan komutları kullanarak yeniden boyutlandırmak istersiniz.

## <a name="plot-window-commands"></a>Çizim penceresi komutları

Çizim penceresi araç çubuğu, büyük bir bölümünü **R araçları**  >  **çizimleri** menüsünde de bulunan uygun komutları barındırır.

| Düğme | Komut | Açıklama |
| --- | --- | --- |
| ![Yeni çizim penceresi düğmesi](media/plotting-toolbar-01-new-plot-window.png) | Yeni çizim penceresi | Kendi geçmişiyle ayrı bir çizim penceresi oluşturur. Bkz. [birden çok çizim pencereleri](#multiple-plot-windows). |
| ![Çizim penceresini etkinleştir düğmesi](media/plotting-toolbar-02-activate-plot-window.png) | Çizim penceresini etkinleştir | Sonraki `plot` komutların Bu pencerede işlenmesi için geçerli çizim penceresini etkin pencere olarak ayarlar. Bkz. [birden çok çizim pencereleri](#multiple-plot-windows). Bkz. [birden çok çizim pencereleri](#multiple-plot-windows). |
| ![Çizim geçmişi penceresi düğmesi](media/plotting-toolbar-03-plot-history.png) | Çizim geçmişi penceresi | Küçük resim olarak gösterilen geçmişe ait tüm çizimleri içeren bir pencere açar. Bkz. [Çizim geçmişi](#plot-history). |
| ![Çizim geçmişi düğmeleri](media/plotting-toolbar-04-plot-history-arrows.png) | Önceki/sonraki çizim |  Geçmişin önceki veya sonraki çizime gider. Ayrıca, CTRL + ALT + F11 (önceki) ve Ctrl + Alt + F12 (Ileri) ile geçmişe gidebilirsiniz. Bkz. [Çizim geçmişi](#plot-history). |
| ![Görüntü olarak Kaydet düğmesi](media/plotting-toolbar-05-save-as-image.png)| Görüntü olarak kaydet | Bir dosya adı ister ve geçerli çizimi (pencere boyutundaki pencere içeriği) bir görüntü dosyasına kaydeder. Kullanılabilir biçimler `.png` ,, `.jpg` `.bmp` ve `.tif` . |
| ![PDF olarak Kaydet düğmesi](media/plotting-toolbar-06-save-as-pdf.png)| PDF olarak kaydet | Geçerli pencere boyutunu kullanarak geçerli çizimi bir PDF dosyasına kaydeder. PDF ölçeklendirilirse çizim yeniden işlenir. |
| ![Bit eşlem olarak Kopyala düğmesi](media/plotting-toolbar-07-copy-as-bitmap.png)| Bit eşlem olarak Kopyala | Çizimi panoya, geçerli pencere boyutunu kullanarak raster bit eşlem olarak kopyalar. |
| ![Meta dosyası olarak Kopyala düğmesi](media/plotting-toolbar-08-copy-as-metafile.png)| Meta dosyası olarak Kopyala | Çizimi panoya [Windows meta dosyası](https://en.wikipedia.org/wiki/Windows_Metafile) (Vikipedi) olarak kopyalar. |
| ![Çizim düğmesini kaldır](media/plotting-toolbar-09-remove-plot.png)| Çizimi Kaldır | Geçerli çizimi geçmişten kaldırır. |
| ![Tüm çizimleri temizle düğmesi](media/plotting-toolbar-10-clear-all-plots.png) | Tüm çizimleri temizle | Geçmişten tüm çizimleri kaldırır (onay ister). |

## <a name="multiple-plot-windows"></a>Birden çok çizim penceresi

Veri bilimcileri birçok farklı veri kümesinden çok sayıda çizim ile çalıştığı için RTVS, çok sayıda bağımsız çizim penceresi oluşturmanızı sağlar. Daha sonra bu pencereleri, Visual Studio çerçevesinde veya bu çerçevenin dışında istediğiniz şekilde düzenleyebilirsiniz. (Windows 'u yerleştirme ve yeniden boyutlandırma hakkında genel bilgi için bkz. [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) .)

Araç çubuğu düğmesini veya **R araçları**  >  **Çizim**  >  **penceresi ' ni**kullanarak yeni bir çizim penceresi oluşturursunuz. Yeni çizim penceresi, yeni çizilmez oluşturulan *etkin* pencere olur. Etkin pencereyi değiştirmek için, ona geçin ve **çizim penceresi** araç çubuğu düğmesini veya **R araçları**' nı Etkinleştir  >  **Plots**  >  **Çiz penceresini**seçin.

Çizim, çok bağımsız nesnelerdir, fare ile sürükle ve bırak ile veya sağ tıklama bağlam ve **düzenleme** menülerinde **Kopyala**, **Kes**ve **Yapıştır** komutlarını kullanarak bunları kopyalayabilir veya taşıyabilirsiniz.

Sürükle ve bırak için varsayılan davranış kopyalama ' dır; **kaydırma** tuşuna basarak taşımak için sürükle ve bırak.

## <a name="plot-history"></a>Geçmişi çiz

Çizim komutları her pencere için bir çizim geçmişinde saklanır, bu da bir oturumdaki tüm çizinizin korunmasını sağlar. Geçmişi gezinmek için, çizim penceresi araç çubuğundaki ok düğmelerini veya **CTRL** + **alt** + **F11** ve **CTRL** + **alt** + **F12**tuşlarını kullanın. Ayrıca, araç çubuğu düğmelerini veya **R araçları**  >  **çizimleri** menü komutlarını kullanarak penceredeki tüm çizimleri kaldırabilir veya tek çizimleri temizleyebilir.

Tüm çizim topluluğunu görmek için, araç çubuğu düğmesini veya **R araçları**  >  **Çizim**  >  **geçmişi penceresi**' ni kullanarak çizim Geçmişi penceresini açın.
Bu geçmiş, bu pencerede görüntülenen, farklı çizim pencereleri (veya cihazlara) göre gruplanmış olarak çizimler için küçük resimlerin bir listesini sağlar. Araç çubuğundaki yakınlaştırma düğmelerini kullanmak küçük resimlerin boyutunu değiştirir.

![Çizim geçmişi penceresi](media/plotting-plot-history-window.png)

İlişkili penceresinde bir çizim açmak için, bu çizimi çift tıklatın, seçin ve ardından Çizim araç çubuğunu **göster** düğmesini seçin. Alternatif olarak, çizimi sağ tıklayıp **çizimi göster**' i seçin. Ayrıca, tek bir çizim seçebilir ve bağlam ya da **düzenleme** menülerinden kopyalayabilir, kesebilir veya silebilirsiniz.

Çizim geçmişinizin tüm pencereler genelinde ömrü, etkileşimli R oturumunuzun ömrüne bağlanır. R oturumunuzu sıfırlayabilir veya çıkıp Visual Studio 'Yu yeniden başlatırsanız, çizim geçmişiniz sıfırlanır.

## <a name="programmatically-manipulate-plot-windows"></a>Çizim pencerelerini programlı olarak değiştirme

Belirli çizim pencerelerini belirlemek için cihaz numaralarını kullanarak R kodundan çizim pencerelerini program aracılığıyla değiştirebilirsiniz.

- `dev.list()`: Geçerli R oturumunda tüm grafik cihazlarını listeleyin.
- `dev.new()`: Yeni bir grafik aygıtı (yeni bir çizim penceresi) oluşturun.
- `dev.set(<device number>)`: Etkin grafik cihazını ayarlayın.
- `dev.off()`: Etkin cihazı silin.
