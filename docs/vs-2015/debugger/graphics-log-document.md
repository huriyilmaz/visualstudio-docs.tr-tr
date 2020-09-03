---
title: Grafik günlük belgesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 430c321c14226228b46bfb0e43f372851fb2a232
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161230"
---
# <a name="graphics-log-document"></a>Grafik Günlük Belgesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik günlüğü belgesi, uygulamanız bir grafik Tanılama oturumu altında çalışırken gerçekleşen grafik olaylarının kaydıdır. Kaydedildikten sonra, işleme ve performans sorunlarını tanılamak için Visual Studio Grafik Çözümleyicisi oturum açma durumunu inceleyebilirsiniz.  
  
 Grafik Çözümleyicisi 'nde grafik günlüğü belgesi şöyle görünür:  
  
 ![Yakalanan iki kare içeren grafik günlüğü.](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Grafik günlüğü belgelerini anlama  
 Grafik bir günlük belgesini incelemek için grafik Çözümleyicisi 'ni kullanarak, yakalama sırasında oluşan işleme hedefinde Direct3D olaylarının etkilerini görselleştirebilirsiniz. İşlem hedefinin, beklenmeyen bir çıkış içeren bölgelerini işleyebilirsiniz. Etkilenen bölgede bir piksel seçtiğinizde, bunu incelemek için Grafik Tanılama, gölgelendiriciler, etkilenen Direct3D olayları, bu olaylara işaret eden uygulama çağrı yığını ve bu olayları destekleyen DirectX nesneleri için kullanabilirsiniz. Bu bilgileri, oyununuzda veya uygulamanızda işleme sorunlarını tanılamak için kullanabilirsiniz.  
  
 Pencerenin üst bölümü (**Graphics denemeler. vsglog**) seçili çerçevenin geçerli işleme hedefi çıkışını görüntüler ve alt bölüm yakalanan çerçevelerin küçük resimlerini Içeren bir **Çerçeve listesi** görüntüler.  
  
#### <a name="to-inspect-a-frame"></a>Bir çerçeveyi incelemek için  
  
- **Çerçeve listesinde**, incelemek istediğiniz çerçeveyi seçin. Grafik günlüğü belgesinin en üst kısmındaki işleme hedefi çıktısı seçili çerçeveyi görüntüleyecek şekilde güncelleştirilir.  
  
#### <a name="to-inspect-a-pixel"></a>Bir pikseli denetlemek için  
  
- Grafik günlüğü belgesinin en üst kısmında, işleme hedefi çıktısından istediğiniz pikseli seçin. Bir piksel seçildiğinde, seçilen pikselle ilgili ayrıntılı bilgileri görüntülemek için **Grafik piksel geçmişi** penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [piksel geçmişi](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Kayıttan yürütme makinesi  
 **Çerçeve listesinin** sağ üst köşesinde da bir **oynatma makinesi**de görüntülenir. Kayıttan yürütme makinesi, daha sonraki bir grafik tanılama oturumunda grafik olaylarını bir grafik günlük dosyasından çalmak için kullanılan bir makine veya cihazdır. Yakalanan olayları çalmak için geliştirme makineniz yerine farklı bir cihaz kullanarak, sorunun gerçekleştiği yürütme ortamını daha doğru şekilde yeniden oluşturabilirsiniz — örneğin, geliştirme makinenizin kullandığı farklı grafik donanımına veya sürücülerine sahip olan bir makineyi veya ARM tabanlı Windows RT tablet veya Windows Phone cihazı gibi diğer cihaz türlerini kullanabilirsiniz.  
  
 Kayıttan yürütme makinesi belirtme hakkında daha fazla bilgi için bkz. [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Grafik günlüğü Özet bilgileri  
 Grafik günlük dosyası etkin belge olduğunda, **Özellikler** penceresi Grafik tanılama yakalama oturumunu barındıran ortamla ilgili bilgileri görüntüler. Birkaç bilgi kategorisi görüntülenir.  
  
 **Direct3D bilgileri**  
 Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısının donanım ve sürücü özellikleriyle ilgili bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**10 bit XR yüksek renk biçimi**|10 bit XR yüksek renk biçimi destekleniyorsa **true** ; Aksi takdirde, **false**.|  
|**DirectCompute CS 4. x**|Işlem gölgelendirici 4,0 destekleniyorsa, **doğru** ; Aksi takdirde, **false**.|  
|**Çift duyarlık gölgelendiricileri**|Görüntüleme bağdaştırıcısı çift duyarlıklı (64-bit) kayan nokta değerlerini destekliyorsa **doğru** . Aksi takdirde, **false**.|  
|**Sürücü komut listeleri**|Sürücü komut listelerini destekliyorsa, **doğru** . Aksi takdirde, **false**.|  
|**Sürücü eşzamanlı oluşturur**|Sürücü eşzamanlı (zaman uyumsuz) oluşturmayı destekliyorsa **doğru** . Aksi takdirde, **false**.|  
|**Genişletilmiş biçimler (BGRA, vb.)**|BGRA gibi genişletilmiş biçimler destekleniyorsa **doğru** ; Aksi takdirde, **false**.|  
|**En fazla HW Feature düzeyi**|Görüntü bağdaştırıcısının desteklediği en yüksek özellik düzeyini görüntüler.|  
  
 **Görüntüleme bilgileri**  
 Yakalama oturumu sırasında kullanılan görüntü bağdaştırıcısı hakkındaki bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Açıklama**|Görüntü bağdaştırıcısı açıklama dizesi.|  
|**Görüntüleme belleği**|Grafik bağdaştırıcısında yüklü bellek miktarı.|  
|**Sürücü Adı**|Grafik bağdaştırıcı sürücüsünün adı.|  
|**Sürücü Sürümü**|Grafik bağdaştırıcı sürücüsünün sürümü.|  
|**Ad**|Grafik bağdaştırıcısının adı.|  
  
 **Deneme dosyası**  
 Yakalama oturumuyla ilişkili olan deneme dosyası hakkındaki bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Yol**|. Vsglog dosyasının yolu. **Note:**  Eski yakalama altında bu özellik kullanılmaz.|  
  
 **Modül bilgileri**  
 Yakalama oturumu sırasında uygulama tarafından yüklenen dinamik bağlantı kitaplıklarının (dll 'Ler) adını ve sürümünü listeler.  
  
 **Sistem bilgileri**  
 Yakalama oturumu sırasında uygulamayı barındıran donanım ve işletim sistemiyle ilgili bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Bellek**|Bilgisayarda yüklü olan bellek miktarı.|  
|**İşletim sistemi mimarisi**|İşletim sisteminin hedef CPU mimarisi.|  
|**İşletim Sistemi Sürümü**|İşletim sistemi sürümü.|  
|**İşlemci**|Bilgisayarda yüklü olan işlemci.|  
|**Hedef uygulama mimarisi**|Uygulamanın hedef CPU mimarisi. Bu, **Işletim sistemi mimarisinden**farklı olabilir.|  
  
 **Hedef uygulama**  
 Yakalama oturumunun konusu olan uygulamayla ilgili bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Son değiştirilme tarihi/saati**|Uygulamanın oluşturulduğu tarih ve saat.|  
|**Yol**|Uygulamanın yolu.|  
|**İşlem Kimliği**|Uygulamaya verilen işlem KIMLIĞI.|  
|**Sürüm**|Uygulama sürümü.|  
  
 **VSG günlük dosyası**  
 Grafik günlüğü belgesi hakkındaki bilgileri listeler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Oluşturan:**|Grafik günlüğü belgesini oluşturan uygulamanın adı. Örneğin, yakalama oturumunun başlatıldığı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (el ile yakalama), bu özelliğin değeri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|**Oturum başlangıç saati**|Yakalama oturumunun başladığı tarih ve saat.|  
|**Boyut**|Grafik günlüğü belgesinin boyutu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: köşe gölgelendirmesi nedeniyle nesneler eksik](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)
