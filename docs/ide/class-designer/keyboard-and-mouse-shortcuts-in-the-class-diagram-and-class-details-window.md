---
title: Klavye ve Fare Kısayolları Sınıf Tasarımcısı
description: Farenin yanı sıra klavyeyi kullanarak gezinti eylemlerini Sınıf Tasarımcısı Sınıf Ayrıntıları penceresinde gerçekleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 497dca2db5aff11af54a81d549c23c35721a48f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102018"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Sınıf Diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları

Klavyeyi fareye ek olarak kullanarak hem Sınıf Tasarımcısı'de hem de Sınıf Ayrıntıları penceresinde **gezinti eylemleri gerçekleştirebilirsiniz.** 

## <a name="use-the-mouse-in-class-designer"></a>Fareyle birlikte Sınıf Tasarımcısı

Aşağıdaki fare eylemleri sınıf diyagramlarında de destekler:

|Fare Birleşimi|Bağlam|Açıklama|
| - |-------------|-----------------|
|Çift tıklatın|Şekil öğeleri|Kod düzenleyicisini açar.|
|Çift tıklatın|Lollipop bağlayıcısı|Lollipop'i genişletin/daralt.|
|Çift tıklatın|Lollipop bağlayıcı etiketi|Arabirimi **Göster komutunu** çağırır.|
|Fare Tekerleği|Sınıf diyagramı|Dikey olarak kaydırın.|
|**Shift** + Fare Tekerleği|Sınıf diyagramı|Yatay olarak kaydırın.|
|**Ctrl** + Fare Tekerleği|Sınıf diyagramı|Zoom.|
|**Ctrl tuşunu basılı tutarak** + **Shift +** tıklama|Sınıf diyagramı|Zoom.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde fareyi kullanma

Fare kullanarak Sınıf Ayrıntıları penceresinin **görünümünü** ve görüntüle ilgili verileri aşağıdaki yollarla değiştirebilirsiniz:

- Düzenlenebilir herhangi bir hücreye tıklamak, hücrenin içeriğini düzenlemenizi sağlar. Değişiklikleriniz, Özellikler penceresi ve kaynak kodu dahil olmak üzere verilerin depolandığı veya **görüntülandığı** tüm yerlerde yansıtıldı.

- Bir satırın herhangi bir hücresine **tıklarsınız, Özellikler** penceresinin bu satır tarafından temsil edilen öğenin özelliklerini görüntülemesine neden olur.

- Bir sütunun genişliğini değiştirmek için, sınırı sütun başlığının sağ tarafındaki sütunu istediğiniz genişlik olana kadar sürükleyin.

- Satırın sol yanındaki ok simgelerine tıklayarak bölme veya özellik düğümlerini genişleterek veya daraltabilirsiniz.

- Sınıf **Ayrıntıları penceresi,** geçerli sınıfta yeni üye oluşturmak ve Sınıf Ayrıntıları pencere kılavuzundaki üyelerin bölmeleri arasında gezinmek için **çeşitli** düğmeler sunar.

## <a name="use-the-keyboard-in-class-designer"></a>Klavyeyi Sınıf Tasarımcısı

Sınıf diyagramlarında aşağıdaki klavye eylemleri de destekler:

|Anahtar|Bağlam|Açıklama|
|---------|-------------|-----------------|
|**Ok tuşları**|Tür şekilleri içinde|Şekil içeriğinde ağaç stili gezinti (şekli sarmalama de desteklemiştir). Genişletilebilirse sol ve sağ anahtarlar geçerli öğeyi genişletebilir/daraltabilir ve genişletilemezse üst öğeye gidin (ayrıntılı davranış için bkz. ağaç görünümü gezintisi).|
|**Ok tuşları**|Üst düzey şekiller|Diyagramda şekilleri taşıma.|
|**Shift ile kaydırma** + **ok tuşları**|Tür şekilleri içinde|Üyeler, iç içe geçmiş türler veya bölmeler gibi şekil öğelerinden oluşan sürekli seçim geliştirme. Bu kısayollar sarmalamayı desteklemez.|
|**Giriş Ekranı**|Tür şekilleri içinde|Üst düzey şekil başlığına gidin.|
|**Giriş Ekranı**|Üst düzey şekiller|Diyagramda ilk şekle gidin.|
|**End**|Tür şekilleri içinde|Şeklin içindeki son görünür öğeye gidin.|
|**End**|Üst düzey şekiller|Diyagramda son şekle gidin.|
|**Shift ile kaydırma** + **Giriş**|Tür şekli içinde|Şekil içindeki öğeleri geçerli öğeyle başlayarak ve aynı şekilde en üst öğeyle biten öğeleri seçer.|
|**Shift ile kaydırma** + **Bitiş**|Tür şekli içinde|Shift Home + **ile aynı** ama aşağı yönlü.|
|**Enter**|Tüm bağlamlar|Çift tıklama yoluyla da kullanılabilen şekilde varsayılan eylemi çağırır. Çoğu durumda bu Görünüm Kodudur ancak bazı öğeler farklı tanımlar (lollipops, bölme üst bilgileri, lollipop etiketleri).|
|**+** Ve **-**|Tüm bağlamlar|Şu anda odaklanmış öğe genişletilebilir ise, bu anahtarlar öğeyi genişletebilir veya daraltabilir.|
|**>**|Tüm bağlamlar|Alt öğeye sahip öğelerde bu, daraltılmışsa öğeyi genişletecek ve ilk alt öğeye gidecek.|
|**<**|Tüm bağlamlar|Üst öğeye gidin.|
|**Alt** + **Shift ile kaydırma** + **L**|Tür şekilleri içinde + tür şekilleri üzerinde.|Mevcutsa seçili olan şeklin lolipopuna gidin.|
|**Alt** + **Shift ile kaydırma** + **B**|Tür şekilleri içinde + tür şekilleri üzerinde.|Temel tür listesi, tür şekli üzerinde gösteriliyorsa ve birden fazla öğeye sahipse bu, listenin genişletme durumunu (daralt/genişlet) gösterir.|
|**Silme**|Tür ve açıklama şekilleri üzerinde|Diyagramdan **Kaldır komutunu** çağırır.|
|**Silme**|Diğer her şey için.|Koddan **Sil komutunu** çağırır (üyeler, parametreler, ilişkilendirmeler, devralma, lollipop etiketleri).|
|**Ctrl tuşunu basılı tutarak** + **Sil**|Tüm bağlamlar|Seçimde **Koddan Sil** komutunu çağırır.|
|**Sekme**|Tüm bağlamlar|Aynı üst öğe içindeki sonraki alt öğeye gider (kaydırmayı destekler).|
|**SHIFT** + **Sekme**|Tüm bağlamlar|Aynı üst öğe içinde önceki alt öğeye gider (kaydırmayı destekler).|
|**Boşluk çubuğu**|Tüm bağlamlar|Geçerli öğedeki seçime geçiş yapar.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresindeki klavyeyi kullanın

> [!NOTE]
> Kod yazma deneyimini taklit etmek için aşağıdaki anahtar bağlamaları seçildi.

**Sınıf Ayrıntıları** penceresinde gezinmek için aşağıdaki anahtarları kullanın:

|Anahtar|Sonuç|
|-|-|
|**,** (virgül)|İmleç bir parametre satırdaysa, bir virgül yazıldığında, imleç sonraki parametrenin ad alanına getirilir. İmleç bir yöntemin son parametre satırdaysa, imleci \<add parameter> alana, yeni bir parametre oluşturmak için kullanabileceğiniz şekilde taşıyabilirsiniz.<br /><br /> İmleç, **Sınıf Ayrıntıları** penceresinde başka bir yerse, bir virgül yazıldığında geçerli alana bir virgül eklenir.|
|**;** (noktalı virgül) veya **)** (parantez kapatma)|İmleci, **Sınıf Ayrıntıları** penceresi kılavuzundaki sonraki üye satırının ad alanına taşıyın.|
|**Sekme**|İmleci bir sonraki alana taşır, önce sola ve sonra yukarıdan aşağıya doğru hareket eder. İmleç metin yazdığınız bir alandan taşıyor ise, **Sınıf Ayrıntıları** bu metni işler ve bir hata oluşturmuyorsa onu depolar.<br /><br /> İmleç gibi boş bir alanda ise \<add parameter> Tab, sonraki satırın ilk alanına gider.|
|**Boşluk çubuğu**|İmleci bir sonraki alana taşır, önce sola ve sonra yukarıdan aşağıya doğru hareket eder. İmleç gibi boş bir alanda yer alıyorsa \<add parameter> , sonraki satırın ilk alanına gider. \<space>Virgül yoksayıldıktan hemen sonra yazılan unutmayın.<br /><br /> İmleç Özet alanında ise, boşluk yazıldığında boşluk karakteri eklenir.<br /><br /> İmleç belirli bir satırın gizleme sütunundayken, bir boşluk yazıldığında gizleme onay kutusunun değeri geçer.|
|**CTRL** + **Sekme**|Başka bir belge penceresine geç. Örneğin, **Sınıf Ayrıntıları** penceresinden açık bir kod dosyasına geçiş yapın.|
|**Esc**|Bir alana metin yazmaya başladıysanız ESC tuşuna basmak geri alma anahtarı olarak davranır ve alanın içeriğini önceki değerine geri alır. Sınıf Detayları Penceresi genel odağa sahipse ancak belirli bir hücre odağa sahip değilse, ESC tuşuna basmak, **Sınıf Ayrıntıları** penceresinden odağı uzağa kaydırır.|
|**Yukarı ok** ve **aşağı ok**|Bu anahtarlar, **Sınıf Ayrıntıları** penceresi kılavuzunda imleci satırdan satıra taşır.|
|**Sol ok**|İmleç ad sütunundayken, sol ok tuşuna basıldığında hiyerarşideki geçerli düğüm (açıksa) daraltılır.|
|**Sağ ok**|İmleç ad sütunundayken, sağ ok tuşuna basıldığında hiyerarşideki geçerli düğüm (daraltılmış durumdaysa) genişletilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Tür üyeleri oluşturma ve yapılandırma](creating-and-configuring-type-members.md)
- [Klavye kullanımı özel](../reference/how-to-use-the-keyboard-exclusively.md)
- [Visual Studio varsayılan klavye kısayolları](../default-keyboard-shortcuts-in-visual-studio.md)
- [Blend’de klavye kısayolları](../../xaml-tools/keyboard-shortcuts-in-blend.md)
