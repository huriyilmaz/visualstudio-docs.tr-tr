---
title: 'İzlenecek yol: grafik bilgilerini yakalama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebd0453347084d1662c6bc7837fc1e96f498fbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151465"
---
# <a name="walkthrough-capturing-graphics-information"></a>İzlenecek yol: Grafik Bilgilerini Yakalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] grafik bilgilerini Direct3D uygulamasından el ile yakalamak için grafik tanılama nasıl kullanacağınızı gösterir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Uygulamanıza Grafik Tanılama birleştirme  
  
- Graf bilgilerini yakalama  
  
## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Grafik Tanılama araçlarını kullanmak için önce temel aldığı grafik bilgilerini yakalamanız gerekir. Yakalamayı etkinleştirmek için, başlatıldığında Grafik Tanılama uygulamanıza bağlamak için **Tanılamayı Başlat** komutunu kullanın.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Bir proje veya çözüm yüklendikten sonra grafik bilgilerinin yakalanmasını etkinleştirmek için  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , grafik bilgilerini yakalamak istediğiniz uygulama için bir proje veya çözüm dosyası yükleyin.  
  
2. Grafik Tanılama araç çubuğunda **Tanılamayı Başlat**' ı seçin.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Bir proje veya çözüm yüklemeden grafik bilgilerinin yakalanmasını etkinleştirmek için  
  
1. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin. **Proje Aç** iletişim kutusu görüntülenir.  
  
2. Proje veya çözüm dosyası yerine, grafik bilgilerini yakalamak istediğiniz uygulamanın yürütülebilir dosyasını belirtin ve **Aç**' ı seçin.  
  
3. Menü çubuğunda **Hata Ayıkla**, **grafikler**, **Tanılamayı Başlat**' ı seçin.  
  
   Uygulamayı başlattıktan ve çerçeveleri işleme aldıktan sonra grafik bilgilerini yakalayabilirsiniz.  
  
#### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için  
  
- Grafik Tanılama araç çubuğunda **yakala** düğmesini seçin. ![Grafik yakalama düğmesi simgesi](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   -veya-  
  
   Uygulamadaki uygulamayla birlikte **PRINT Screen**tuşuna basın.  
  
  Bir çerçeve hakkındaki bilgileri her yakaladığınızda, Grafik Tanılama Direct3D olaylarını ve ilişkili durumunu kaydeder ve bu verileri bir grafik günlüğüne ekler. Her bir Grafik Tanılama oturumu için yeni bir grafik günlüğü oluşturulur. Grafik günlükleri hakkında daha fazla bilgi için bkz. [genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzda grafik bilgilerinin el ile nasıl yakalanacağı gösterilmiştir. Sonraki adım olarak bu seçeneği göz önünde bulundurun:  
  
- Grafik Tanılama araçlarını kullanarak yakalanan grafik bilgilerini çözümlemeyi öğrenin. Bkz. [genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Bilgilerini Yakalama](../debugger/capturing-graphics-information.md)
