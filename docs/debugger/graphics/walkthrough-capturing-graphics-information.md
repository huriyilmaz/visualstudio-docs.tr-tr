---
title: 'İzlenecek yol: grafik bilgilerini yakalama | Microsoft Docs'
description: Grafik bilgilerini Direct3D uygulamasından el ile yakalamak için bkz. Visual Studio Grafik Tanılama nasıl kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3acd9df9dbb5a430171ae7a283bbf4292e07e26a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994985"
---
# <a name="walkthrough-capturing-graphics-information"></a>İzlenecek yol: Grafik Bilgilerini Yakalama
Bu izlenecek yol, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] grafik bilgilerini Direct3D uygulamasından el ile yakalamak için grafik tanılama nasıl kullanacağınızı gösterir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Uygulamanıza Grafik Tanılama birleştirme

- Graf bilgilerini yakalama

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Grafik Tanılama araçlarını kullanmak için önce temel aldığı grafik bilgilerini yakalamanız gerekir. Yakalamayı etkinleştirmek için, başlatıldığında Grafik Tanılama uygulamanıza bağlamak için **Tanılamayı Başlat** komutunu kullanın.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Bir proje veya çözüm yüklendikten sonra grafik bilgilerinin yakalanmasını etkinleştirmek için

1. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , grafik bilgilerini yakalamak istediğiniz uygulama için bir proje veya çözüm dosyası yükleyin.

2. Grafik Tanılama araç çubuğunda **Tanılamayı Başlat**' ı seçin.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Bir proje veya çözüm yüklemeden grafik bilgilerinin yakalanmasını etkinleştirmek için

1. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin. **Proje Aç** iletişim kutusu görüntülenir.

2. Proje veya çözüm dosyası yerine, grafik bilgilerini yakalamak istediğiniz uygulamanın yürütülebilir dosyasını belirtin ve **Aç**' ı seçin.

3. Menü çubuğunda **Hata Ayıkla**, **grafikler**, **Tanılamayı Başlat**' ı seçin.

   Uygulamayı başlattıktan ve çerçeveleri işleme aldıktan sonra grafik bilgilerini yakalayabilirsiniz.

#### <a name="to-capture-graphics-information"></a>Grafik bilgilerini yakalamak için

- Grafik Tanılama araç çubuğunda **yakala** düğmesini seçin. ![Grafik yakalama düğmesi simgesi](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   -veya-

   Uygulamadaki uygulamayla birlikte **PRINT Screen** tuşuna basın.

  Bir çerçeve hakkındaki bilgileri her yakaladığınızda, Grafik Tanılama Direct3D olaylarını ve ilişkili durumunu kaydeder ve bu verileri bir grafik günlüğüne ekler. Her bir Grafik Tanılama oturumu için yeni bir grafik günlüğü oluşturulur. Grafik günlükleri hakkında daha fazla bilgi için bkz. [genel bakış](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Sonraki Adımlar
 Bu kılavuzda grafik bilgilerinin el ile nasıl yakalanacağı gösterilmiştir. Sonraki adım olarak bu seçeneği göz önünde bulundurun:

- Grafik Tanılama araçlarını kullanarak yakalanan grafik bilgilerini çözümlemeyi öğrenin. Bkz. [genel bakış](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Bilgilerini Yakalama](capturing-graphics-information.md)