---
title: 'adım adım kılavuz: Grafik Bilgilerini | Microsoft Docs'
description: Direct3D uygulamasından Visual Studio Grafik Tanılama el ile yakalamak için nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 241ffcdb979dec0c7e39cb998479090c1e596bc18e6251ee1fe22e7b163fd0c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435874"
---
# <a name="walkthrough-capturing-graphics-information"></a>İzlenecek yol: Grafik Bilgilerini Yakalama
Bu kılavuzda, Direct3D uygulamasından Grafik Tanılama bilgileri el ile yakalamak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Grafik Tanılama'nin nasıl kullanabileceğiniz anlatıldı.

 Bu izlenecek yol şu görevleri gösterir:

- Uygulamanıza Grafik Tanılama kancalama

- Graf bilgilerini yakalama

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Bu Grafik Tanılama kullanmak için öncelikle bu araçların bağlı olduğu grafik bilgilerini yakalamamız gerekir. Yakalamayı etkinleştirmek için **Tanılamayı Başlat komutunu** kullanarak Grafik Tanılama uygulamanıza bağlanabilirsiniz.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Bir proje veya çözüm yüklendikten sonra grafik bilgilerini yakalamayı etkinleştirmek için

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]'de, grafik bilgilerini yakalamak istediğiniz uygulama için bir proje veya çözüm dosyası yükleme.

2. Yeni araç Grafik Tanılama Tanılamayı **Başlat'ı seçin.**

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Bir proje veya çözüm yüklemeden grafik bilgilerini yakalamayı etkinleştirmek için

1. Menü çubuğunda Dosya, Aç, **aç** ve **Project/Çözüm'i seçin.**  Açık **Project** iletişim kutusu görüntülenir.

2. Proje veya çözüm dosyası yerine, grafik bilgilerini yakalamak istediğiniz uygulamanın yürütülebilir dosyasını belirtin ve ardından Aç'ı **seçin.**

3. Menü çubuğunda Hata Ayıkla, **Grafikler,** **Tanılamayı** **Başlat'ı seçin.**

   Uygulamayı başlattıktan ve çerçeveleri işledikten sonra grafik bilgilerini yakalayabilirsiniz.

#### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için

- Araç çubuğunda Grafik Tanılama düğmesini **seçin.** ![Grafik yakalama düğmesi simgesi](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   -veya-

   Uygulama odakta olduğu için Print **Screen tuşuna basın.**

  Bir çerçeve hakkında her bilgi yakalay Grafik Tanılama Direct3D olaylarını ve ilişkili durumu kaydedecek ve bu verileri bir grafik günlüğüne ekler. Her oturum için yeni bir grafik Grafik Tanılama oluşturulur. Grafik günlükleri hakkında bilgi için bkz. Genel [Bakış.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="next-steps"></a>Sonraki Adımlar
 Bu kılavuzda, grafik bilgilerini el ile yakalama adımlarını gösteren bir kılavuz. Bir sonraki adım olarak şu seçeneği göz önünde önünde belirtin:

- Yakalanan grafik bilgilerini analiz etmek için Grafik Tanılama öğrenin. Bkz. [Genel Bakış.](overview-of-visual-studio-graphics-diagnostics.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Bilgilerini Yakalama](capturing-graphics-information.md)