---
title: DataTips değişken değerlerini görüntüleme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5eda8205dbe0629d0b2801473de83c2f91257e
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404275"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Kod Düzenleyicisi'nde veri değerlerini görüntüleme datatips

DataTips, hata ayıklama sırasında programınızdaki değişkenleri hakkında daha fazla bilgi görüntülemek için kullanışlı bir yol sağlar. DataTips, sadece kesme modunda ve yalnızca yürütme geçerli kapsamdaki değişkenler çalışın. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="work-with-datatips"></a>DataTips ile çalışma

Veri ipuçlarını ve yalnızca yürütme geçerli kapsamdaki değişkenler yalnızca kesme modunda görüntülenir.

### <a name="display-a-datatip"></a>Bir DataTip görüntüleme

1. Kodunuzda bir kesme noktası ayarlayın ve tuşuna basarak hata ayıklamayı Başlat **F5** veya seçerek **hata ayıklama** > **hata ayıklamayı Başlat**.

1. Kesme noktasında durdurulduğu zaman geçerli kapsamdaki herhangi bir değişken üzerine gelin. Adı ve geçerli bir değişkenin değerini gösteren bir DataTip görünür.

### <a name="make-a-datatip-transparent"></a>Bir DataTip saydam hale getirme

Bir DataTip sırada DataTip içinde bunun altındaki kodu görmek için saydam hale getirmek için basın **Ctrl**. Basılı sürece DataTip saydam kalır **Ctrl** anahtarı. Bu sabitlenmiş veya kayan DataTips için çalışmaz.
### <a name="pin-a-datatip"></a>PIN bir DataTip

Açık kalması bir DataTip sabitlemek için Raptiye seçin **kaynağına PIN** simgesi.

![Veri Ipucunu sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "PIN bir DataTip")

Sabitlenmiş bir DataTip kod penceresi sürükleyerek taşıyabilirsiniz. Cilt payını DataTip sabitlenmiş satırın yanındaki Raptiye simgesi görünür.

>[!NOTE]
>DataTips, burada yürütmesi askıya alınır bağlamı, değil geçerli imleç veya DataTip konumu her zaman değerlendirilir. Geçerli bağlam değişkeninin değerini, geçerli bağlamda bir değişken olarak aynı ada sahip başka bir işlev bir değişkende üzerine gelin, görüntülenir.

### <a name="unpin-a-datatip-from-source"></a>Bir DataTip kaynaktan Ayır

Sabitlenmiş bir DataTip kaydırmak için DataTip getirin ve bağlam menüsünden Raptiye simgesini seçin.

Sabitlenmemiş konuma Raptiye simgesi değiştirir ve DataTip artık gezinen veya tüm açık pencereleri sürüklenerek değiştirilebilir. Kayan DataTips, hata ayıklama oturumu bittiğinde kapatın.

### <a name="repin-a-datatip"></a>Bir DataTip Görselden

Kayan bir DataTip kaynağına Görselden için Kod Düzenleyicisi'nde üzerine gelin ve Raptiye simgesini seçin. Raptiye simgesi sabitlenmiş konumuna değiştirir ve DataTip yalnızca kod penceresine yeniden sabitlenir.

Bir kaynak kodu olmayan pencere üzerinde bir DataTip kayan noktalı Raptiye simgesi kullanılamıyor ve DataTip repinned. Raptiye simgesi erişmek için sürükleyerek veya kod Pencere odağı vermek için kod düzenleyicisi penceresi DataTip döndürür.

### <a name="close-a-datatip"></a>Bir DataTip kapatın

Bir DataTip kapatmak için DataTip gelin ve kapatma seçin (**x**) bağlam menüsünden simgesi.

### <a name="close-all-datatips"></a>Tüm veri ipuçlarını Kapat

Tüm veri ipuçlarını üzerinde kapatmak için **hata ayıklama** menüsünde **Temizle tüm veri ipuçlarını**.

### <a name="close-all-datatips-for-a-specific-file"></a>Belirli bir dosya için tüm veri ipuçlarını Kapat

Tüm veri ipuçlarını için belirli bir dosya çubuğunda kapatmak için **hata ayıklama** menüsünde **Temizle tüm veri ipuçlarını sabitlenmiş için \<Filename >** .

## <a name="expand-and-edit-information"></a>Genişletin ve bilgilerini Düzenle
DataTips, bir dizi, yapı veya üyelerini görüntülemek için bir nesne genişletmek için kullanabilirsiniz. Bir DataTip değişkeninden değerini de düzenleyebilirsiniz.

### <a name="expand-a-variable"></a>Bir değişkeni genişletin

Bir nesne öğeleri görmek için bir DataTip içinde genişletmek için Genişlet oklar öğeleri ağaç formunda görüntülenecek öğe adları önce üzerine gelin. Sabitlenmiş bir DataTip için seçin **+** değişkeni önce adlandırın ve ardından ağacı genişletin.

![Bir veri Ipucunu Genişlet](../debugger/media/dbg-tour-data-tips.png "Bir veri Ipucunu Genişlet")

Genişletilmiş görünümde yukarı ve aşağı taşımak için klavye üzerinde fareyi veya ok tuşlarını kullanabilirsiniz.

Ayrıca, üzerine gelip Raptiye simgelerine seçerek sabitlenmiş DataTip genişletilmiş olan öğelerle sabitleyebilirsiniz. Ağaç daraltılmış sonra öğeleri daha sonra sabitlenmiş DataTip içinde görünür.

### <a name="edit-the-value-of-a-variable"></a>Bir değişkenin değerini Düzenle

Bir değişken veya DataTip öğesinde değerini düzenlemek için değer, yeni bir değer yazın ve ENTER tuşuna seçin **Enter**. Seçimi için salt okunur değerleri devre dışı bırakıldı.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Veri Ipuçlarında PIN özellikleri

> [!NOTE]
> Bu özellik .NET Core 3,0 veya üzeri sürümlerde desteklenir.

Veri Ipuçları **bölümünde, bu nesneleri özelliklerine göre** hızlıca inceleyebilirsiniz.  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme simgesini seçin ya da sağ tıklayın ve ortaya çıkan bağlam menüsünde **üyeyi sık kullanılanlara sabitle** seçeneğini belirleyin.  Bu özelliği nesnenin özellik listesinin en üstüne, özellik adı ve değeri ise veri Ipucunun sağ sütununda görüntülenir.  Bir özelliği kaldırmak için, PIN simgesini yeniden seçin veya bağlam menüsünde **üyeyi sık kullanılanlara ayır** seçeneğini belirleyin.

![Bir veri Ipucunda bir özelliği sabitleme](../debugger/media/basic-pin-datatip.gif "Bir veri Ipucunda bir özelliği sabitleme")

Ayrıca, bir veri ipucunda nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmemiş özellikleri filtreleyebilirsiniz.  Özellik içeren bir satıra sağ tıklayıp, **yalnızca sabitlenmiş üyeleri göster** ' i seçerek ya da bağlam menüsündeki **değerler seçeneklerinde sabitlenmiş üye adlarını gizleyerek** her iki seçeneğe erişebilirsiniz.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Karmaşık veri türleri görselleştirin

Bir veya daha fazla yanında bir değişken veya öğesi bir DataTip içinde bir Büyüteç simgesi anlamına gelir [görselleştiriciler](../debugger/create-custom-visualizers-of-data.md), gibi [metin görselleştiricisi](../debugger/string-visualizer-dialog-box.md), değişken için kullanılabilir. Görselleştiriciler, bazen grafik daha anlamlı bir şekilde bilgi görüntüler.

Veri türü için varsayılan görselleştiricisi kullanarak öğeyi görüntülemek için büyüteç simgesini ![görselleştirme simgesini](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")seçin. Görselleştiriciler veri türü için bir listesinden seçmek için Büyüteç simgesinin yanındaki oku seçin.

## <a name="add-a-variable-to-a-watch-window"></a>Bir Gözcü penceresi için bir değişken Ekle

Bir değişken izlemek devam etmek istiyorsanız, bunu ekleyebilirsiniz bir **Watch** bir DataTip penceresinde. DataTip içinde değişkeni sağ tıklatın ve seçin **Gözcü Ekle**.

Değişken görünür **Watch** penceresi. Birden fazla Visual Studio sürümünüzü destekleyip desteklemediğini **Watch** değişken penceresinde görünür **Watch 1**.

## <a name="import-and-export-datatips"></a>İçeri aktarma ve veri ipuçlarını Dışarı Aktar

DataTips paylaşabilir veya bir metin düzenleyicisi kullanarak Düzenle bir XML dosyasına dışarı aktarabilirsiniz. Ayrıca, alınan veya düzenlediğiniz bir DataTip XML dosyasını içeri aktarabilirsiniz.

**Veri ipuçlarını dışarı aktarmak için:**

1. Seçin **hata ayıklama** > **veri ipuçlarını dışarı aktar**.

1. İçinde **veri ipuçlarını dışarı aktar** iletişim kutusunda, XML dosyasını, dosya için bir ad yazın konumuna gidin ve ardından **Kaydet**.

**Veri ipuçlarını içeri aktarmak için:**

1. Seçin **hata ayıklama** > **veri ipuçlarını içeri aktar**.

1. İçinde **alma DataTips** iletişim kutusunda, açın ve ardından istediğiniz DataTips XML dosyasını seçin **açın**.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklıyor?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
