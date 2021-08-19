---
title: DataTips veri kaynağında değişken değerlerini | Microsoft Docs
description: Hata ayıklama sırasında diziler ve yapılar dahil olmak üzere değişkenlerle ilgili bilgileri rahatça görüntülemek için DataTips'i kullanın. Değerleri de değiştirebilirsiniz.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f2e3424f7a94358895ac89d6c4da4d8a9c251b21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058233"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Kod düzenleyicisinde DataTips'te veri değerlerini görüntüleme

DataTips, hata ayıklama sırasında programda değişkenlerle ilgili bilgileri görüntülemek için kullanışlı bir yol sağlar. DataTips yalnızca kesme modunda ve yalnızca geçerli yürütme kapsamındaki değişkenlerle çalışır. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi [](../debugger/debugging-absolute-beginners.md) okumadan önce yeni [](../debugger/write-better-code-with-visual-studio.md) başlayanlar için Hata Ayıklama ve Hata ayıklama teknikleri ve araçları makaleyi okumak istiyor olabilirsiniz.

## <a name="work-with-datatips"></a>DataTips ile çalışma

DataTips yalnızca kesme modunda ve yalnızca geçerli yürütme kapsamındaki değişkenlerde görünür.

### <a name="display-a-datatip"></a>DataTip Görüntüleme

1. Kodunda bir kesme noktası ayarlayın ve **F5** tuşuna basarak veya Hata AyıklamaYı Başlat'ı seçerek  >  **hata ayıklamaya başlayabilirsiniz.**

1. Kesme noktası duraklatılırken geçerli kapsamda herhangi bir değişkenin üzerine gelin. Değişkenin adını ve geçerli değerini gösteren bir DataTip görüntülenir.

### <a name="make-a-datatip-transparent"></a>DataTip'i saydam hale toplama

DataTip'i altındaki kodu görmek için saydam hale eklemek için DataTip'te **Ctrl tuşlarına basın.** Ctrl tuşunu basılı tutarak DataTip saydam **kalır.** Bu, sabitlenmiş veya kayan DataTips için çalışmaz.
### <a name="pin-a-datatip"></a>DataTip Sabitleme

DataTip'i açık kalacak şekilde sabitlemek için Kaynakta sabitle **simgesini** seçin.

![DataTip Sabitleme](../debugger/media/dbg-tips-data-tips-pinned.png "DataTip Sabitleme")

Sabitlenmiş bir DataTip'i kod penceresinin çevresine sürükleyerek taşıyabilirsiniz. DataTip'in sabitlenmiş olduğu satırın yanındaki oluk içinde bir itme simgesi görünür.

>[!NOTE]
>DataTips her zaman geçerli imleç veya DataTip konumu değil yürütmenin askıya alınarak askıya alınarak değerlendirilir. Geçerli bağlamdaki bir değişkenle aynı adı alan başka bir işlevde bir değişkenin üzerine gelmenizi sağlarsanız, geçerli bağlamda değişkenin değeri görüntülenir.

### <a name="unpin-a-datatip-from-source"></a>Bir DataTip'i kaynaktan geri adan

Sabitlenmiş bir DataTip'i float yapmak için DataTip'in üzerine gelin ve bağlam menüsünden pushpin simgesini seçin.

Itme simgesi, açılmamış konuma değişir ve DataTip artık kayar veya tüm açık pencerelerin üzerine sürüklenebilir. Hata ayıklama oturumu sona erdiğinde Kayan DataTips kapanır.

### <a name="repin-a-datatip"></a>DataTip'i yenidenpin

Kayan bir DataTip'i kaynak olarak yeniden eklemek için kod düzenleyicisinde üzerine gelin ve itme simgesini seçin. Pushpin simgesi sabitlenmiş konuma değişir ve DataTip yeniden yalnızca kod penceresine sabitlenir.

Bir DataTip, kaynak olmayan bir kod penceresinde kayan bir durumda ise, itme simgesi kullanılamaz ve DataTip yeniden kullanılamaz. Itme simgesine erişmek için DataTip'i sürükleyerek veya kod penceresi odağı vererek kod düzenleyicisi penceresine geri dönebilirsiniz.

### <a name="close-a-datatip"></a>DataTip'i kapatma

DataTip'i kapatmak için DataTip'in üzerine gelin ve bağlam menüsünden kapat (**x**) simgesini seçin.

### <a name="close-all-datatips"></a>Tüm DataTips'i kapatma

Tüm DataTips'i kapatmak için Hata Ayıklama **menüsünde** Tüm **DataTips'i Temizle'yi seçin.**

### <a name="close-all-datatips-for-a-specific-file"></a>Belirli bir dosya için tüm DataTips'i kapatma

Belirli bir dosyaya yönelik tüm DataTips'i kapatmak için Hata Ayıklama **menüsünde,** Sabitlenen Tüm **Veri İpucularını Temizle'yi seçin. \<Filename>**

## <a name="expand-and-edit-information"></a>Bilgileri genişletme ve düzenleme
DataTips'i kullanarak bir diziyi, yapıyı veya nesneyi üyelerini görüntülemek üzere genişletebilirsiniz. Bir değişkenin değerini DataTip'den de düzenleyebilirsiniz.

### <a name="expand-a-variable"></a>Değişkeni genişletme

DataTip'te bir nesneyi öğelerini görmek için öğe adlarında önce genişletme okları üzerine gelerek öğeleri ağaç formunda görüntüleyeceksiniz. Sabitlenmiş bir DataTip için değişken **+** adının öncesini seçin ve ağacı genişletin.

![DataTip'i genişletme](../debugger/media/dbg-tour-data-tips.png "DataTip'i genişletme")

Genişletilmiş görünümde yukarı ve aşağı hareket etmek için klavyede fareyi veya ok tuşlarını kullanabilirsiniz.

Ayrıca, üzerine gelerek ve bunların pushpin simgelerini seçerek, genişletilmiş öğeleri sabitlenmiş DataTip'e sabitlersiniz. Öğeler daha sonra ağaç daraltıldıktan sonra sabitlenmiş DataTip içinde görünür.

### <a name="edit-the-value-of-a-variable"></a>Değişkenin değerini düzenleme

DataTip'te bir değişkenin veya öğenin değerini düzenlemek için değeri seçin, yeni bir değer yazın ve Enter tuşuna **basın.** Salt okunur değerler için seçim devre dışı bırakıldı.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>DataTips'te Özellikleri Sabitleme

> [!NOTE]
> Bu özellik .NET Core 3.0 veya daha yenisi için de kullanılabilir.

Sabitlenebilir Özellikler aracıyla DataTips'te nesneleri **özelliklerine göre hızla inceebilirsiniz.**  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme  simgesini seçin veya sağ tıklayın ve sonuçta elde edilen bağlam menüsünde Üyeyi Sık Kullanılan Olarak Sabitle seçeneğini belirleyin.  Bu, bu özelliği nesnenin özellik listesinin en üstüne kadar gösterir ve özellik adı ve değeri DataTip'in sağ sütununda görüntülenir.  Bir özelliğin sabitlemesini geri eklemek için  sabitleme simgesini yeniden seçin veya bağlam menüsünde Üyeyi Sık Kullanılan olarak Kaldır seçeneğini belirleyin.

![Özelliği DataTip'e sabitleme](../debugger/media/basic-pin-datatip.gif "Özelliği DataTip'e sabitleme")

Ayrıca, bir veri ipucunda nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmiş olmayan özellikleri filtreleebilirsiniz.  Bağlam menüsünde özellik içeren bir satıra sağ tıklar  ve Yalnızca sabitlenmiş üyeleri göster veya Değerlerde sabitlenmiş üye adlarını gizle seçeneklerini seçerek iki seçenen de erişebilirsiniz. 

::: moniker-end

## <a name="visualize-complex-data-types"></a>Karmaşık veri türlerini görselleştirme

DataTip'te bir değişkenin veya öğenin yanındaki büyüteç [](../debugger/create-custom-visualizers-of-data.md)simgesi, değişken için [](../debugger/string-visualizer-dialog-box.md)Metin Görselleştiricisi gibi bir veya daha fazla görselleştiricinin kullanılabilir olduğu anlamına gelir. Görselleştiriciler bilgileri daha anlamlı, bazen grafiksel bir şekilde görüntüler.

Öğeyi veri türü için varsayılan görselleştiriciyi kullanarak görüntülemek için büyüteç simgesini Görselleştirici ![simgesi seçin.](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi") Veri türüne göre görselleştiriciler listesinden seçmek için büyüteç simgesinin yanındaki oku seçin.

## <a name="add-a-variable-to-a-watch-window"></a>Bir değişkene değişken izleme penceresi

Bir değişkeni izlemeye devam etmek için DataTip'inden bir **İzleme** penceresine ebilirsiniz. DataTip'te değişkenine sağ tıklayın ve İzleme **Ekle'yi seçin.**

değişkeni İzleme **penceresinde** görünür. Visual Studio sürümünüz birden fazla İzleme penceresini **destekliyorsa,** değişkeni İzleme **1'de görünür.**

## <a name="import-and-export-datatips"></a>DataTips'i içeri ve dışarı aktarma

DataTips'i bir XML dosyasına aktarabilirsiniz. Bu dosyayı bir metin düzenleyicisi kullanarak paylaşabilir veya düzenleyebilirsiniz. Ayrıca, almış veya düzenlemış bir DataTip XML dosyasını da içeri aktarabilirsiniz.

**DataTips'i dışarı aktarma:**

1. Veri **dışarı aktarmada**  >  **hata ayıklaTipler'i seçin.**

1. Veri **İpucu Dışarı Aktar iletişim** kutusunda, XML dosyasını kaydetmek için konuma gidin, dosya için bir ad yazın ve Kaydet'i **seçin.**

**DataTips'i içeri aktarma:**

1. Veri **İçeri Aktarmada**  >  **Hata AyıklaTipler'i seçin.**

1. Veri İpucu **İçeri Aktar iletişim** kutusunda açmak istediğiniz DataTips XML dosyasını ve ardından Aç'ı **seçin.**

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
