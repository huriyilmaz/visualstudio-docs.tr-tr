---
title: Sınıf Tasarımcısı için klavye ve fare kısayolları
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6df4932a1043c984509632951ba67864fefe31ce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590767"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Sınıf diyagramı ve Sınıf Ayrıntıları penceresinde klavye ve fare kısayolları

**Sınıf Tasarımcısı** ve **Sınıf Ayrıntıları** penceresinde gezinme eylemlerini gerçekleştirmek için fareye ek olarak klavyeyi kullanabilirsiniz.

## <a name="use-the-mouse-in-class-designer"></a>Sınıf Tasarımcısı fareyi kullanın

Aşağıdaki fare eylemleri sınıf diyagramlarında desteklenir:

|Fare birleşimi|Bağlam|Açıklama|
| - |-------------|-----------------|
|Çift tıklama|Şekil öğeleri|Kod düzenleyicisini açar.|
|Çift tıklama|Lolipop Bağlayıcısı|Lolipop 'i Genişlet/Daralt.|
|Çift tıklama|Lolipop bağlayıcı etiketi|**Arabirim komutunu göster** komutunu çağırır.|
|Fare tekerleği|Sınıf diyagramı|Dikey olarak kaydırın.|
|**SHIFT** + fare tekerleği|Sınıf diyagramı|Yatay olarak kaydırın.|
|**CTRL** + fare tekerleği|Sınıf diyagramı|Yakınlaştırma.|
|**Ctrl**+**SHIFT** + tıklama|Sınıf diyagramı|Yakınlaştırma.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde fareyi kullanın

Bir fare kullanarak, **Sınıf Ayrıntıları** penceresinin ve görüntülediği verilerin görünümünü aşağıdaki yollarla değiştirebilirsiniz:

- Herhangi bir düzenlenebilir hücreyi tıklatmak, bu hücrenin içeriğini düzenlemenizi sağlar. Değişiklikleriniz, **Özellikler** penceresi ve kaynak kodu dahil olmak üzere verilerin depolandığı veya görüntülendiği her yerde yansıtılır.

- Bir satırın herhangi bir hücresini tıklatmak **Özellikler** penceresinin, bu satır tarafından temsil edilen öğenin özelliklerini görüntülemesine neden olur.

- Bir sütunun genişliğini değiştirmek için sütun başlığının sağ tarafındaki sınırı sütun istediğiniz genişliğe gelinceye kadar sürükleyin.

- Satırın solundaki ok sembollerine tıklayarak bölme veya özellik düğümlerini genişletebilir veya daraltabilirsiniz.

- **Sınıf Ayrıntıları** penceresi, geçerli sınıfta yeni üyeler oluşturmak ve **Sınıf Ayrıntıları** penceresi kılavuzunda Üyeler ' bölmeleri arasında gezinmek için birkaç düğme sunar.

## <a name="use-the-keyboard-in-class-designer"></a>Sınıf Tasarımcısı klavyeyi kullanın

Aşağıdaki klavye eylemleri sınıf diyagramlarında desteklenir:

|Anahtar|Bağlam|Açıklama|
|---------|-------------|-----------------|
|**Ok tuşları**|Tür şekillerinin içinde|Şekil içeriklerinde ağaç stili gezinti (şeklin etrafında kaydırma desteklenir). Sol ve sağ tuşları, Genişletilebilir ise geçerli öğeyi genişletir/daraltır ve değilse üst öğeye gidebilir (ayrıntılı davranış için bkz. ağaç görünümü gezintisi).|
|**Ok tuşları**|Üst düzey şekiller|Diyagramda şekiller taşınıyor.|
|**Shıft**+**ok tuşları**|Tür şekillerinin içinde|Üyeler, iç içe türler veya bölmeleri gibi şekil öğelerinden oluşan sürekli seçim oluşturma. Bu kısayollar etrafında kaydırmayı desteklemez.|
|**Giriş**|Tür şekillerinin içinde|Üst düzey şekil başlığına gidin.|
|**Giriş**|Üst düzey şekiller|Diyagramdaki ilk şekle gidin.|
|**Son**|Tür şekillerinin içinde|Şeklin içindeki son görünür öğeye gidin.|
|**Son**|Üst düzey şekiller|Diyagramdaki son şekle gidin.|
|**Shıft**+**ana**|Tür şeklinin içinde|Geçerli öğeyle başlayan ve aynı şekildeki en üstteki öğeyle biten şekildeki öğeleri seçer.|
|**Shıft**+**bitişi**|Tür şeklinin içinde|**Shıft**+**Home** , ancak yukarıdan aşağı yönde olacak şekilde aynı.|
|**Girin**|Tüm bağlamlar|Şekil üzerinde, Çift tıklama ile de kullanılabilen varsayılan eylemi çağırır. Çoğu durumda bu, kod görüntüler ancak bazı öğeler bunu farklı şekilde tanımlar (Lollipop 'lar, bölme üstbilgileri, lolipop etiketleri).|
|**+** ve **-**|Tüm bağlamlar|Şu anda odaklanmış öğe Genişletilebilir ise, bu anahtarlar öğeyi genişletir veya daraltır.|
|**>**|Tüm bağlamlar|Alt öğeleri olan öğelerde, daraltılamışsa ve ilk alt öğeye gidiliyorsa, bu öğe genişletilir.|
|**<**|Tüm bağlamlar|Üst öğeye gider.|
|**Alt**+**SHIFT**+**L**|Tür şekillerinin içindeki şekil + tür şekilleri.|Varsa, seçili olan şeklin lolipop öğesine gider.|
|**Alt**+**SHIFT**+**B**|Tür şekillerinin içindeki şekil + tür şekilleri.|Tür şekli üzerinde temel tür listesi gösterilirse ve birden fazla öğe varsa, bu, listenin genişletme durumuna geçer (daraltma/genişletme).|
|**Delete**|Tür ve açıklama şekilleri üzerinde|**Diyagramdan kaldır** komutunu çağırır.|
|**Delete**|Diğer her şey.|**Koddan Sil** komutunu (Üyeler, parametreler, ilişkilendirmeler, devralma, Lollipop etiketleri) çağırır.|
|**Ctrl**+**Sil**|Tüm bağlamlar|Seçimdeki **kodu Sil** komutundan çağırır.|
|**sekmesi**|Tüm bağlamlar|Aynı üst öğe içindeki sonraki alt öğeye gider (kaydırmayı destekler).|
|**Shıft**+**sekmesi**|Tüm bağlamlar|Aynı üst öğe içinde önceki alt öğeye gider (kaydırmayı destekler).|
|**'Nu**|Tüm bağlamlar|Geçerli öğedeki seçime geçiş yapar.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresindeki klavyeyi kullanın

> [!NOTE]
> Kod yazma deneyimini taklit etmek için aşağıdaki anahtar bağlamaları seçildi.

**Sınıf Ayrıntıları** penceresinde gezinmek için aşağıdaki anahtarları kullanın:

|||
|-|-|
|Anahtar|Sonuç|
|**,** (virgül)|İmleç bir parametre satırdaysa, bir virgül yazıldığında, imleç sonraki parametrenin ad alanına getirilir. İmleç bir yöntemin son parametre satırdaysa, imleci yeni bir parametre oluşturmak için kullanabileceğiniz \<parametresi Ekle > alanına taşıyabilirsiniz.<br /><br /> İmleç, **Sınıf Ayrıntıları** penceresinde başka bir yerse, bir virgül yazıldığında geçerli alana bir virgül eklenir.|
|**;** (noktalı virgül) veya **)** (parantez kapatma)|İmleci, **Sınıf Ayrıntıları** penceresi kılavuzundaki sonraki üye satırının ad alanına taşıyın.|
|**sekmesi**|İmleci bir sonraki alana taşır, önce sola ve sonra yukarıdan aşağıya doğru hareket eder. İmleç metin yazdığınız bir alandan taşıyor ise, **Sınıf Ayrıntıları** bu metni işler ve bir hata oluşturmuyorsa onu depolar.<br /><br /> İmleç \<parametre Ekle > gibi boş bir alanda yer alıyorsa Tab, sonraki satırın ilk alanına gider.|
|**'Nu**|İmleci bir sonraki alana taşır, önce sola ve sonra yukarıdan aşağıya doğru hareket eder. İmleç \<parametre Ekle > gibi boş bir alanda yer alıyorsa, sonraki satırın ilk alanına gider. \<boşluk > virgülden hemen sonra yazılmış olduğunu unutmayın.<br /><br /> İmleç Özet alanında ise, boşluk yazıldığında boşluk karakteri eklenir.<br /><br /> İmleç belirli bir satırın gizleme sütunundayken, bir boşluk yazıldığında gizleme onay kutusunun değeri geçer.|
|**Ctrl**+**sekmesi**|Başka bir belge penceresine geç. Örneğin, **Sınıf Ayrıntıları** penceresinden açık bir kod dosyasına geçiş yapın.|
|**ESC**|Bir alana metin yazmaya başladıysanız ESC tuşuna basmak geri alma anahtarı olarak davranır ve alanın içeriğini önceki değerine geri alır. Sınıf Detayları Penceresi genel odağa sahipse ancak belirli bir hücre odağa sahip değilse, ESC tuşuna basmak, **Sınıf Ayrıntıları** penceresinden odağı uzağa kaydırır.|
|**Yukarı ok** ve **aşağı ok**|Bu anahtarlar, **Sınıf Ayrıntıları** penceresi kılavuzunda imleci satırdan satıra taşır.|
|**Sol ok**|İmleç ad sütunundayken, sol ok tuşuna basıldığında hiyerarşideki geçerli düğüm (açıksa) daraltılır.|
|**Sağ ok**|İmleç ad sütunundayken, sağ ok tuşuna basıldığında hiyerarşideki geçerli düğüm (daraltılmış durumdaysa) genişletilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Tür üyeleri oluşturma ve yapılandırma](creating-and-configuring-type-members.md)
- [Klavye kullanımı özel](../reference/how-to-use-the-keyboard-exclusively.md)
- [Visual Studio 'da varsayılan klavye kısayolları](../default-keyboard-shortcuts-in-visual-studio.md)
- [Blend’de klavye kısayolları](../../xaml-tools/keyboard-shortcuts-in-blend.md)
