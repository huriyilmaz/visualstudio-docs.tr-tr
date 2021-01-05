---
title: Grafik çerçeve doğrulaması | Microsoft Docs
description: Visual Studio 'da grafikler için çerçeve doğrulama aracı hakkında bilgi edinin. Bu araç, olay listesiyle ilişkili hata ve uyarıları görüntüler.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe9b1ed3acbe588b342ba6550bc45558a2070d2
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727651"
---
# <a name="graphics-frame-validation"></a>Grafik çerçeve doğrulaması
<!-- VERSIONLESS -->
Visual Studio 2017 ve üzeri **çerçeve doğrulama** aracını destekler.  Çerçeve doğrulama penceresinde olay listesiyle ilişkili hatalar ve uyarılar görüntülenir.  Bu pencereyi görüntülemek için **> çerçeve doğrulama menüsünü görüntüle** ' yi seçin.

![Çerçeve Doğrulama](media/gfx_diag_frame_validation.png)

Analizi başlatmak için sol üst köşedeki **doğrulama Çalıştır** düğmesine tıklayın.  Çerçevenin karmaşıklığına bağlı olarak tamamlanması birkaç dakika sürebilir.  Burada görüntülenen veriler iki kaynaktan bir birleşimidir: Bu, D3D 'nın kendisini [SDK katmanları](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) etkinken ve aracın kendi iç durum izlemesiyle toplanan verileri yayar. İşlem tamamlandıktan sonra birkaç veri sütunu görürsünüz:

| **Sütun** | **Açıklama** |
|------------| - |
| Olay kimliği | [Olay listesi](graphics-event-list.md) penceresindeki bir GIRDIYLE eşlenen kimlik. |
| Önem derecesi | Bozulma, hata, uyarı, bilgi veya Ileti. |
| Kategori | Uygulama tanımlı, çeşitli, başlatma, Temizleme, derleme, durum oluşturma, durum ayarı, durum alma, yürütme, kaynak Işleme, gölgelendirici, yedekli ve kullanılmıyor. |
| İleti | Olayla ilişkili ileti. |
| Olay | Hata veya uyarıyla ilişkili olay. |

## <a name="see-also"></a>Ayrıca bkz.
[Grafik Tanılama (DirectX Grafiklerinde Hata Ayıklama)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->