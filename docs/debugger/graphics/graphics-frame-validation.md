---
title: Grafik Çerçevesi Doğrulama | Microsoft Docs
description: Visual Studio'daki grafikler için Çerçeve Doğrulama aracı hakkında Visual Studio. Bu araç, olay listesiyle ilişkili hataları ve uyarıları görüntüler.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f7c23daaa333e71f332f67fa9d34d9d3aba361139dbd3ca1fc1bc3fe623c91b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362760"
---
# <a name="graphics-frame-validation"></a>Grafik Çerçeve Doğrulaması
<!-- VERSIONLESS -->
Visual Studio 2017 ve daha yenisi Çerçeve Doğrulama **aracını** destekler.  Çerçeve Doğrulama penceresi, olay listesiyle ilişkili hataları ve uyarıları görüntüler.  Bu pencereyi görüntülemek için Çerçeve **Doğrulamasını > seçin.**

![Çerçeve Doğrulama](media/gfx_diag_frame_validation.png)

Analizi **başlatmak için** sol üst köşedeki Doğrulamayı Çalıştır düğmesine tıklayın.  Çerçevenin karmaşıklığına bağlı olarak tamamlanması birkaç dakika sürebilir.  Burada görünen veriler iki kaynağın birleşimidir: [SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) Katmanları etkinleştirildiğinde D3D'nin kendisi tarafından gönderilen iletiler ve aracın kendi iç durum izlemesinde toplanan veriler. Tamamlandıktan sonra birkaç veri sütunuyla karşınız olur:

| **Sütun** | **Açıklama** |
|------------| - |
| Olay Kimliği | Olay Listesi penceresindeki bir girişle [eşilen](graphics-event-list.md) kimlik. |
| Önem Derecesi | Bozulma, Hata, Uyarı, Bilgi veya İleti. |
| Kategori | Uygulama Tanımlı, Çeşitli, Başlatma, Temizleme, Derleme, Durum Oluşturma, Durum Ayarı, Durum Alma, Yürütme, Kaynak Düzenleme, Gölgelendirici, Yedekli ve Kullanılmayan. |
| İleti | Olayla ilişkili ileti. |
| Olay | Hata veya uyarıyla ilişkili olay. |

## <a name="see-also"></a>Ayrıca bkz.
[Grafik Tanılama (DirectX Grafiklerinde Hata Ayıklama)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->