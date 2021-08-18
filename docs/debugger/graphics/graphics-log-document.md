---
title: Grafik Günlüğü Belge | Microsoft Docs
description: Bir uygulama bir grafik tanılama Visual Studio çalışırken meydana gelen grafik olaylarını kaydeden Grafik Günlüğü belgesini anlama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f713687e1b4b045fc6d48d9c6a237a11a8f3091e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058582"
---
# <a name="graphics-log-document"></a>Grafik Günlük Belgesi
Grafik Günlüğü belgesi, uygulama bir grafik tanılama oturumu altında çalışırken meydana gelen grafik olaylarının kaydıdır. Kaydedildikten sonra, işleme ve performans sorunlarını tanılamak için Visual Studio Grafik Çözümleyicisi'nin günlüğünü incelersiniz.

 Grafik günlüğü belgesi, Grafik Çözümleyicisi'ne şu şekilde görünür:

 ![Yakalanan iki kare içeren bir grafik günlüğü.](media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")

## <a name="understanding-graphics-log-documents"></a>Grafik günlüğü belgelerini anlama
 Grafik günlüğü belgesini incelemek için Grafik Çözümleyicisi'yi kullanarak, Direct3D olaylarının yakalama sırasında meydana gelen işleme hedefi üzerindeki etkilerini görselleştirebilirsiniz. İşleme hedefinin beklenmeyen çıkış içeren bölgelerini tespit ediyor olabilir. Etkilenen bölgede bir pikseli seçerek Grafik Tanılama'i kullanarak onu, gölgelendiricilerini, onu etkileyen Direct3D olaylarını, bu olaylara yol alan uygulama çağrı yığınını ve bu olayları destekleyen DirectX nesnelerini inceebilirsiniz. Oyun veya uygulamanıza işleme sorunlarını tanılamak için bu bilgileri kullanabilirsiniz.

 Pencerenin üst kısmı **(Grafik Denemesi.vsglog),** seçilen çerçevenin geçerli işleme hedefi çıkışını,  alt kısım ise yakalanan karelerin küçük resim görüntülerini içeren Bir Çerçeve Listesi görüntüler.

#### <a name="to-inspect-a-frame"></a>Çerçeveyi incelemek için

- Çerçeve **Listesi'nin** içinde, incelemek istediğiniz çerçeveyi seçin. Grafik günlüğü belgesinin üst kısmında yer alan işleme hedefi çıkışı, seçilen çerçeveyi görüntülenecek şekilde güncelleştirilir.

#### <a name="to-inspect-a-pixel"></a>Pikseli incelemek için

- Grafik günlüğü belgesinin üst kısmında, işleme hedefi çıkışından istediğiniz pikseli seçin. Piksel seçildiğinde Grafik Piksel Geçmişi penceresini **kullanarak** seçili pikselle ilgili ayrıntılı bilgileri görüntüebilirsiniz. Daha fazla bilgi için [bkz. Piksel Geçmişi.](graphics-pixel-history.md)

## <a name="playback-machine"></a>Kayıttan yürütme makinesi
 Çerçeve Listesi'nin sağ üst köşesinde de **Kayıttan Yürütme** Makinesi **görüntülenir.** Kayıttan yürütme makinesi, sonraki grafik tanılama oturumu sırasında grafik günlük dosyasından grafik olaylarını oynatmak için kullanılan bir makine veya cihazdır. Yakalanan olayları geri oynatmak için geliştirme makineniz yerine farklı bir cihaz kullanarak, sorunun oluştuğu yürütme ortamını daha doğru bir şekilde yeniden üretebilirsiniz; örneğin, geliştirme makinenizin kullandığından farklı grafik donanımına veya sürücülerine sahip bir makine veya ARM tabanlı Windows RT tablet veya Windows Phone cihazı gibi diğer cihaz türleri kullanabilirsiniz.

 Kayıttan yürütme makinesi belirtme hakkında bilgi için [bkz. Nasıl: Kayıttan Yürütme Grafik Tanılama Değiştirme.](how-to-change-the-graphics-diagnostics-playback-machine.md)

## <a name="graphics-log-summary-information"></a>Grafik günlüğü özet bilgileri
 Bir grafik günlüğü dosyası etkin belge olduğunda Özellikler **penceresi,** yakalama oturumunun barındır olduğu ortamla ilgili Grafik Tanılama görüntüler. Çeşitli bilgi kategorileri görüntülenir.

 **Direct3D Bilgileri** Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısının donanım ve sürücü özellikleriyle ilgili bilgileri listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|**10 bit XR Yüksek Renk Biçimi**|**10** bit XR yüksek renk biçimi desteklense true; aksi takdirde **False olur.**|
|**DirectCompute CS 4.x**|**İşlem** Gölgelendiricisi 4.0 desteklense True; aksi takdirde **False olur.**|
|**Çift Duyarlık Gölgelendiricileri**|**Görüntü** bağdaştırıcısı çift duyarlık (64 bit) kayan nokta değerlerini destekliyorsa true; aksi takdirde **False olur.**|
|**Sürücü Komut Listeleri**|**Sürücü** komut listelerini destekliyorsa True; aksi takdirde **False olur.**|
|**Sürücü Eşzamanlı Oluşturur**|**Sürücü** eşzamanlı (zaman uyumsuz) oluşturmayı destekliyorsa true; aksi takdirde **False olur.**|
|**Genişletilmiş Biçimler (BGRA vb.)**| BGRA gibi genişletilmiş biçimler desteklense true olur; aksi takdirde **False olur.**|
|**Maksimum HW Özellik Düzeyi**|Görüntü bağdaştırıcısı tarafından desteklenen en yüksek özellik düzeyini görüntüler.|

 **Bilgileri Görüntüleme** Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısıyla ilgili bilgileri listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|**Açıklama**|Görüntü bağdaştırıcısı açıklama dizesi.|
|**Belleği Görüntüle**|Grafik bağdaştırıcısında yüklü bellek miktarı.|
|**Sürücü Adı**|Grafik bağdaştırıcısı sürücüsünün adı.|
|**Sürücü Sürümü**|Grafik bağdaştırıcısı sürücüsünün sürümü.|
|**Ad**|Grafik bağdaştırıcısının adı.|

 **Deneme Dosyası** Yakalama oturumuyla ilişkili deneme dosyasıyla ilgili bilgileri listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|**Yol**|.vsglog dosyasının yolu. **Not:**  Eski yakalama altında bu özellik kullanılmaz.|

 **Modül Bilgileri** Yakalama oturumu sırasında uygulama tarafından yüklenen dinamik bağlantı kitaplıklarının (DLL) adını ve sürümünü listeler.

 **Sistem Bilgileri** Yakalama oturumu sırasında uygulamayı barındıran donanım ve işletim sistemiyle ilgili bilgileri listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|**Bellek**|Bilgisayarda yüklü bellek miktarı.|
|**Işletim Sistemi Mimarisi**|İşletim sisteminin hedef CPU mimarisi.|
|**Işletim Sistemi Sürümü**|İşletim sistemi sürümü.|
|**İşlemci**|Bilgisayarda yüklü olan işlemci.|
|**Hedef Uygulama Mimarisi**|Uygulamanın hedef CPU mimarisi. Bu, işletim sistemi **mimarisinden farklı olabilir.**|

 **Hedef Uygulama** Yakalama oturumunun konusu olan uygulamayla ilgili bilgileri listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|**Son Değiştirme Tarihi/Saati**|Uygulamanın inşa tarihi ve saati.|
|**Yol**|Uygulamanın yolu.|
|**İşlem Kimliği**|Uygulamaya verilen işlem kimliği.|
|**Sürüm**|Uygulama sürümü.|

 **VSG Günlük Dosyası** Grafik günlüğü belgesiyle ilgili bilgileri listeler.

| Özellik | Açıklama |
|------------------------| - |
| **Oluşturan:** | Grafik günlüğü belgesini oluşturan uygulamanın adı. Örneğin, yakalama oturumu (el ile yakalama) ile başlatıldı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ise bu özelliğin değeri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olur. |
| **Oturum Başlangıç Zamanı** | Yakalama oturumunun başladığı tarih ve saat. |
| **Boyut** | Grafik günlüğü belgesinin boyutu. |

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)