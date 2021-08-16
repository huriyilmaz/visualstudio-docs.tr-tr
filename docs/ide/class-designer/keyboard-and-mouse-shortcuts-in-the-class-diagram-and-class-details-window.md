---
title: Klavye ve Fare Kısayolları Sınıf Tasarımcısı
description: Klavyenin yanı sıra fareyle birlikte sınıf ve sınıf ayrıntıları penceresinde gezinti Sınıf Tasarımcısı gerçekleştirmeyi öğrenin.
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
ms.openlocfilehash: dd0d8d753d1ac3bfc338ee551bbbadd51923d9957faa7abc1246a0eb0283eb1a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358421"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Sınıf Diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları

Klavyeyi fareye ek olarak kullanarak hem Sınıf Tasarımcısı'de hem de Sınıf Ayrıntıları penceresinde **gezinti eylemleri gerçekleştirebilirsiniz.** 

## <a name="use-the-mouse-in-class-designer"></a>Fareyle birlikte Sınıf Tasarımcısı

Aşağıdaki fare eylemleri sınıf diyagramlarında de destekler:

|Fare Birleşimi|Bağlam|Açıklama|
| - |-------------|-----------------|
|Çift tıklatın|Şekil öğeleri|Kod düzenleyicisini açar.|
|Çift tıklatın|Lollipop bağlayıcısı|Lollipop'ları genişletin/daralt.|
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

## <a name="use-the-keyboard-in-class-designer"></a>Klavyeyi klavyeyle Sınıf Tasarımcısı

Sınıf diyagramlarında aşağıdaki klavye eylemleri de destekler:

|Anahtar|Bağlam|Açıklama|
|---------|-------------|-----------------|
|**Ok tuşları**|Tür şekilleri içinde|Şekil içeriğinde ağaç stili gezinti (şekli sarmalama de desteklemiştir). Genişletilebilirse sol ve sağ anahtarlar geçerli öğeyi genişletebilir/daraltabilir ve genişletilemezse üst öğeye gidilebilir (ayrıntılı davranış için bkz. ağaç görünümü gezintisi).|
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
|**Silme**|Diğer her şey için.|Koddan **Sil komutunu çağırır** (üyeler, parametreler, ilişkilendirmeler, devralma, lollipop etiketleri).|
|**Ctrl tuşunu basılı tutarak** + **Sil**|Tüm bağlamlar|Seçimde **Koddan Sil** komutunu çağırır.|
|**Sekme**|Tüm bağlamlar|Aynı üst öğe içinde sonraki alt öğeye gidin (sarmalamayı destekler).|
|**Shift ile kaydırma** + **Sekme**|Tüm bağlamlar|Aynı üst öğe içinde önceki alt öğeye gidin (sarmalamayı destekler).|
|**Boşluk çubuğu**|Tüm bağlamlar|Geçerli öğede seçimi iki durumlu olarak değiştir.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde klavyeyi kullanma

> [!NOTE]
> Aşağıdaki anahtar bağlamaları özellikle kod yazma deneyimini taklit etmek için seçilmiştir.

Sınıf Ayrıntıları penceresinde gezinmek için **aşağıdaki anahtarları** kullanın:

|Anahtar|Sonuç|
|-|-|
|**,** (virgül)|İmleç bir parametre satırı içinde ise, virgül yazarak imleci sonraki parametrenin Ad alanına taşır. İmleç bir yöntemin son parametre satırına ise imleci alana taşır ve bunu kullanarak yeni \<add parameter> bir parametre oluşturabilirsiniz.<br /><br /> İmleç Sınıf Ayrıntıları penceresinin başka **bir yerinde** ise, virgül yazarak geçerli alana bir virgül ekler.|
|**;** (noktalı virgül) veya **)** (kapatma parantezi)|İmleci Sınıf Ayrıntıları pencere kılavuzunda sonraki üye satırın **Ad alanına** sürükleyin.|
|**Sekme**|İmleci bir sonraki alana taşır, önce soldan sağa ve sonra üstten aşağıya doğru hareket eder. İmleç, metin yazma işleminin olduğu bir alandan taşınıyorsa, **Sınıf** Ayrıntıları bu metni işler ve hata üretmezse depolar.<br /><br /> İmleç gibi boş bir alanda ise \<add parameter> Tab bunu sonraki satırın ilk alanına taşır.|
|**Boşluk çubuğu**|İmleci bir sonraki alana taşır, önce soldan sağa ve sonra üstten aşağıya doğru hareket eder. İmleç gibi boş bir alanda \<add parameter> ise, sonraki satırın ilk alanına taşınır. Virgülden \<space> hemen sonra yazılmalıdır.<br /><br /> İmleç Özet alanında ise boşluk yazmak bir boşluk karakteri ekler.<br /><br /> İmleç, verili bir satırın Gizle sütununda yer alırsa, boşluk yazarak Gizle onay kutusunun değerini değiştirebilirsiniz.|
|**Ctrl tuşunu basılı tutarak** + **Sekme**|Başka bir belge penceresine geçiş. Örneğin, Sınıf Ayrıntıları **penceresinden açık** bir kod dosyasına geçin.|
|**Esc**|Bir alana metin yazmaya başladıysanız ESC tuşuna basmak geri alma anahtarı gibi davranır ve alanın içeriğini önceki değerine geri döndürerek. Uygulamanın Sınıf Detayları Penceresi ama belirli bir hücre odağı yoksa ESC tuşuna basmak odağı Sınıf Ayrıntıları **penceresinden uzağa** taşır.|
|**Yukarı ok** ve **aşağı ok**|Bu anahtarlar, sınıf ayrıntıları pencere kılavuzunda imleci satırdan **satıra** dikey olarak hareket ettirin.|
|**Sol ok**|İmleç Ad sütununda ise, sol oka basılarak hiyerarşideki geçerli düğüm daraltılmış olur (açıksa).|
|**Sağ ok**|İmleç Ad sütununda ise, sağ oka basılarak hiyerarşideki geçerli düğüm genişlet (daraltılmışsa).|

## <a name="see-also"></a>Ayrıca bkz.

- [Tür üyeleri oluşturma ve yapılandırma](creating-and-configuring-type-members.md)
- [Klavyeyi özel olarak kullanma](../reference/how-to-use-the-keyboard-exclusively.md)
- [Visual Studio'de varsayılan klavye kısayolları](../default-keyboard-shortcuts-in-visual-studio.md)
- [Blend’de klavye kısayolları](../../xaml-tools/keyboard-shortcuts-in-blend.md)
