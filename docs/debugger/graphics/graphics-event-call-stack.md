---
title: Grafik olay çağrısı yığını | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c221a572264bf6a6aaed9edbec66fb3c0c3ff4b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735509"
---
# <a name="graphics-event-call-stack"></a>Grafik Olay Çağırma Yığını
Visual Studio Grafik Çözümleyicisi 'deki grafik olay çağrısı yığını, sorunlu grafik olayları ve uygulamanızın kaynak kodu arasındaki ilişkiyi eşlemenizi sağlar.

 Bu olay çağrı yığını penceresidir:

 ![Bir DrawIndexed olayından önceki çağrı yığını.](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")

## <a name="understanding-the-graphics-event-call-stack"></a>Grafik olay çağrı yığınını anlama
 Belirli bir Direct3D olayına işaret eden yürütmenin akışını anlamak için olay çağrı yığınını kullanabilirsiniz. Visual Studio çağrı yığını penceresine benzer, ancak çalışan bir uygulamada geçerli iş parçacığının geçerli çağrı yığınını görüntülemek yerine, seçilen Direct3D olayı gerçekleştiğinde çağrı yığınını görüntüler. Olay çağrı yığınında, çevreleyen kodu incelemek için seçilen Direct3D olayının çağrı sitesine atlayabilirsiniz.

 Bir sorun olayının kaynaklandığı kod yolunu tanımlamak için olay çağrı yığınını kullanarak, sorunun olası kaynaklarını belirlemek için kod tabanınızın bilgisini kullanabilir veya uygulamanın veya olay parametrelerinin durumunun hatalı davranmasına neden olduğunu incelemek üzere geleneksel hata ayıklama tekniklerini kullanabilmeniz için uygulamanızın kaynak kodunda kesme noktaları ekleyebilirsiniz. Bu İnceleme, kaynak kodda yalnızca işleme sorunları olarak bildirilen sorunları bulmanıza yardımcı olabilir.

### <a name="graphics-event-call-stack-information"></a>Grafik olay çağrı yığını bilgileri
 Olay çağrı yığını, çerçeve öncesi olayları veya Kullanıcı tanımlı olayları desteklemez. Grafik olay çağrı yığını bir tablo biçiminde görüntülenir.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Çağrı sitesini içeren işlevi benzersiz bir şekilde tanımlayan bir sembol. İşlevin hata ayıklama sembolü kullanılabilir olduğunda görüntülenir; Aksi takdirde, işlev boşluğu görüntülenir.|
|**Dosya**|Çağrı sitesini içeren kaynak kodu dosyasının veya kitaplık dosyasının dosya adı.|
|**Konum**|Çağrı sitesinin satır numarası.|

### <a name="links-to-graphics-objects"></a>Grafik nesnelerine bağlantılar
 Seçili grafik olayını anlamak için, onunla ilişkili Direct3D nesneleri hakkında bilgilere ihtiyacınız olabilir. **Grafik olay çağrı yığını** penceresi bu bilgilere bağlantılar sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)