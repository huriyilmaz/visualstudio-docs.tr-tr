---
title: Veri Ipuçlarında değişken değerlerini görüntüle | Microsoft Docs
description: Hata ayıklama sırasında diziler ve yapılar dahil olmak üzere değişkenler hakkındaki bilgileri rahat bir şekilde görüntülemek için DataTips kullanın. Değerleri de değiştirebilirsiniz.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a560d97bd96124e71ec84f5011fcd2abd986ff9c
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970210"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Kod düzenleyicisinde DataTips 'daki veri değerlerini görüntüleme

DataTips, hata ayıklama sırasında programınızdaki değişkenlerle ilgili bilgileri görüntülemek için kullanışlı bir yol sağlar. DataTips yalnızca kesme modunda ve yalnızca geçerli yürütme kapsamındaki değişkenlerle çalışır. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="work-with-datatips"></a>DataTips ile çalışma

DataTips yalnızca kesme modunda ve yalnızca geçerli yürütme kapsamındaki değişkenlerde görünür.

### <a name="display-a-datatip"></a>Bir veri Ipucu görüntüleme

1. Kodunuzda bir kesme noktası ayarlayın ve **F5** tuşuna basarak **veya hata ayıklama**  >  **Başlat hata ayıklamayı** seçerek hata ayıklamayı başlatın.

1. Kesme noktasında duraklatıldığında, geçerli kapsamdaki herhangi bir değişkenin üzerine gelin. Değişkenin adını ve geçerli değerini gösteren bir veri Ipucu görünür.

### <a name="make-a-datatip-transparent"></a>DataTip saydam yapma

Veri ipucundaki kodun altında bulunan kodu görmek üzere saydam hale getirmek için **CTRL** tuşuna basın. **CTRL** tuşunu basılı tuttuğunuz sürece datatıp saydam kalır. Bu, sabitlenmiş veya kayan veri Ipuçları için çalışmaz.
### <a name="pin-a-datatip"></a>Veri Ipucunu sabitleme

Bir veri Ipucunu açık kalacak şekilde sabitlemek için raptiye 'yi **kaynağa sabitle** simgesine tıklayın.

![Veri Ipucunu sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "Veri Ipucunu sabitleme")

Sabitlenmiş bir veri Ipucunu kod penceresi etrafında sürükleyerek taşıyabilirsiniz. Veri ucunun sabitlendiği satırın yanındaki cilt alanında raptiye simgesi görüntülenir.

>[!NOTE]
>DataTips her zaman, geçerli imleç veya DataTip konumu değil, yürütmenin askıya alındığı bağlamda değerlendirilir. Geçerli bağlamdaki bir değişkenle aynı ada sahip başka bir işlevde bulunan bir değişkenin üzerine geldiğinizde, geçerli bağlamdaki değişkenin değeri görüntülenir.

### <a name="unpin-a-datatip-from-source"></a>Bir veri Ipucunu kaynaktan kaldır

Sabitlenmiş bir veri Ipucunu kaydırmak için, veri Ipucunun üzerine gelin ve bağlam menüsünden raptiye simgesini seçin.

Raptiye simgesi sabitlenmemiş konuma değişir ve Datatıp artık tüm açık pencerelerin üzerine kayarak veya sürüklenebilir. Hata ayıklama oturumu sona erdiğinde kayan veri Ipuçları kapanır.

### <a name="repin-a-datatip"></a>Veri Ipucunda repın

Kayan bir veri Ipucunu kaynağa eklemek için, kod düzenleyicisinde üzerine gelin ve raptiye simgesini seçin. Raptiye simgesi sabitlenmiş konuma değişir ve DataTip yalnızca kod penceresine sabitlenmiştir.

Bir DataTip, kaynak olmayan bir kod penceresinde dalgalanma gelirse, raptiye simgesi kullanılamaz ve Datatıp, veri Ipucu kullanılamaz. Raptiye simgesine erişmek için, verileri sürükleyerek veya kod penceresi odaklı odağa ekleyerek veri Ipucunu kod Düzenleyicisi penceresine döndürün.

### <a name="close-a-datatip"></a>Veri Ipucunu kapatma

Bir veri Ipucunu kapatmak için, veri Ipucunun üzerine gelin ve bağlam menüsünden Kapat (**x**) simgesini seçin.

### <a name="close-all-datatips"></a>Tüm veri Ipuçlarını kapat

Tüm veri Ipuçlarını kapatmak için, **Hata Ayıkla** menüsünde **tüm veri ipuçlarını temizle**' yi seçin.

### <a name="close-all-datatips-for-a-specific-file"></a>Belirli bir dosya için tüm veri Ipuçlarını kapat

Belirli bir dosyanın tüm veri Ipuçlarını kapatmak için, **Hata Ayıkla** menüsünde, **üzerine \<Filename> sabitlenmiş tüm veri ipuçlarını temizle**' yi seçin.

## <a name="expand-and-edit-information"></a>Bilgileri Genişlet ve Düzenle
Üyelerini görüntülemek için bir diziyi, yapıyı veya nesneyi genişletmek üzere DataTips kullanabilirsiniz. Bir değişkenin değerini bir veri Ipucundan de düzenleyebilirsiniz.

### <a name="expand-a-variable"></a>Bir değişkeni Genişlet

Öğeleri görmek üzere bir veri Ipucunda bir nesneyi genişletmek için, öğeleri ağaç formunda görüntülemek için öğe adlarından önce genişletme oklarının üzerine gelin. Sabitlenmiş bir veri Ipucu için, **+** değişken adından önce öğesini seçin ve ardından ağacı genişletin.

![Bir veri Ipucunu Genişlet](../debugger/media/dbg-tour-data-tips.png "Bir veri Ipucunu Genişlet")

Genişletilmiş görünümde yukarı ve aşağı taşımak için klavyede fare veya ok tuşlarını kullanabilirsiniz.

Ayrıca, genişletilmiş öğeleri, üzerine gelip raptiye simgesini seçerek sabitlenmiş veri Ipucuna sabitleyebilirsiniz. Daha sonra öğeler, ağaç daraltıldıktan sonra sabitlenmiş Datatıp içinde görüntülenir.

### <a name="edit-the-value-of-a-variable"></a>Bir değişkenin değerini düzenleme

Bir veri Ipucunda bir değişkenin veya öğenin değerini düzenlemek için, değeri seçin, yeni bir değer yazın ve **ENTER** tuşuna basın. Seçim salt okuma değerleri için devre dışı bırakıldı.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Veri Ipuçlarında PIN özellikleri

> [!NOTE]
> Bu özellik .NET Core 3,0 veya üzeri sürümlerde desteklenir.

Veri Ipuçları **bölümünde, bu nesneleri özelliklerine göre** hızlıca inceleyebilirsiniz.  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme simgesini seçin ya da sağ tıklayın ve ortaya çıkan bağlam menüsünde **üyeyi sık kullanılanlara sabitle** seçeneğini belirleyin.  Bu özelliği nesnenin özellik listesinin en üstüne, özellik adı ve değeri ise veri Ipucunun sağ sütununda görüntülenir.  Bir özelliği kaldırmak için, PIN simgesini yeniden seçin veya bağlam menüsünde **üyeyi sık kullanılanlara ayır** seçeneğini belirleyin.

![Bir veri Ipucunda bir özelliği sabitleme](../debugger/media/basic-pin-datatip.gif "Bir veri Ipucunda bir özelliği sabitleme")

Ayrıca, bir veri ipucunda nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmemiş özellikleri filtreleyebilirsiniz.  Özellik içeren bir satıra sağ tıklayıp, **yalnızca sabitlenmiş üyeleri göster** ' i seçerek ya da bağlam menüsündeki **değerler seçeneklerinde sabitlenmiş üye adlarını gizleyerek** her iki seçeneğe erişebilirsiniz.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Karmaşık veri türlerini görselleştirin

Bir veri Ipucunda bir değişkenin veya öğenin yanındaki büyüteç simgesi, [metin görselleştiricisi](../debugger/string-visualizer-dialog-box.md)gibi bir veya daha fazla [görselleştiricinin](../debugger/create-custom-visualizers-of-data.md)değişken için kullanılabilir olduğu anlamına gelir. Görselleştiriciler bilgileri daha anlamlı, bazen grafik, şekilde görüntüler.

Veri türü için varsayılan görselleştiricisi kullanarak öğeyi görüntülemek için büyüteç simgesini ![görselleştirme simgesini](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")seçin. Veri türü için Görselleştiriciler listesinden seçim yapmak için büyüteç simgesinin yanındaki oku seçin.

## <a name="add-a-variable-to-a-watch-window"></a>izleme penceresi bir değişken ekleme

Bir değişkeni izlemeye devam etmek istiyorsanız, bir veri Ipucundan bir **izleme** penceresine ekleyebilirsiniz. Veri Ipucunda değişkenine sağ tıklayın ve **Gözcü Ekle**' yi seçin.

Değişken, **Gözcü** penceresinde görünür. Visual Studio sürümünüz birden fazla **izleme** penceresini destekliyorsa, değişken **1. gözcü**' de görünür.

## <a name="import-and-export-datatips"></a>Veri Ipuçlarını içeri ve dışarı aktarma

Bir metin düzenleyicisi kullanarak paylaşabileceğiniz veya düzenleyebileceğiniz bir XML dosyasına DataTips aktarabilirsiniz. Aldığınız veya düzenlediğiniz bir Datatıp XML dosyasını da içeri aktarabilirsiniz.

**Veri Ipuçlarını dışarı aktarmak için:**

1.   >  **Dışarı aktarma veri ipuçlarını** Hata Ayıkla ' yı seçin.

1. **Veri Ipuçlarını dışarı aktar** iletişim kutusunda, XML dosyasını kaydetmek için konuma gidin, dosya için bir ad yazın ve ardından **Kaydet**' i seçin.

**Veri Ipuçlarını içeri aktarmak için:**

1. **Hata ayıklama**  >  **veri ipuçlarını** seçin.

1. **Veri Ipuçlarını Içeri aktar** iletişim kutusunda, açmak Istediğiniz DATATIPS XML dosyasını seçin ve **Aç**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
