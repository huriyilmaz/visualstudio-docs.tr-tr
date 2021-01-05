---
title: Grafik API 'SI ve bellek Istatistikleri | Microsoft Docs
description: Direct3D API 'SI kullanımı ve çeşitli kaynakların GPU bellek tüketimi hakkındaki bilgileri gösteren grafik API 'SI Istatistiklerini ve bellek Istatistikleri araçlarını gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e0ad2bc48e1e15e1b061cdb600ce65773523e70
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727896"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik API 'SI ve bellek Istatistikleri
<!-- VERSIONLESS -->
Visual Studio 2017 ve üzeri grafik API Istatistiklerini ve bellek Istatistikleri araçlarını destekler.  Bu iki araç, Direct3D API kullanımıyla ilgili çeşitli bilgileri ve çeşitli kaynakların GPU bellek tüketimini görüntülemenize olanak sağlar.

## <a name="graphics-api-statistics"></a>Grafik API Istatistikleri
Visual Studio 'daki grafik API Istatistikleri Grafik Tanılama, yapılan tüm Direct3D çağrılarını ve her çağrının sayısını görüntülemenizi sağlar.  Pencereyi görüntülemek için **> API istatistikleri** menü öğesini görüntüle ' yi seçin.

![API Istatistikleri](media/gfx_diag_api_statistics.png)

Bu araç, yaptığınız fark etmeyebilirsiniz ya da çok sık yaptığınız çağrılar için DirectX çağrılarını keşfetmekle kullanışlı olabilir.

Tüm verileri, daha fazla analiz için Excel gibi bir şeye yapıştırılabilecek CSV olarak kopyalamak için pencereye sağ tıklayabilirsiniz.

## <a name="memory-statistics"></a>Bellek Istatistikleri
Bu araç, grafik sürücüsünün bir çerçevede oluşturduğunuz kaynaklar için ne kadar bellek ayırıyor olduğunu gösterir.  Bu pencereyi görüntülemek için **> bellek Istatistiklerini görüntüle** menü öğesini seçin.

![Bellek Istatistikleri](media/gfx_diag_memory_statistics.png)

**GPU ayırma** sütunu **olay sütununda görüntülenen olay tarafından** kullanılan bellek miktarını görüntüler.  Ayrıca, ![ ](media/gfx_watch.png) Seçilen olaya ait [kaynak geçmişini](graphics-event-list.md#resource-history) görüntülemek için izleme simgesi izle simgesini de seçebilirsiniz.

API Istatistikleri aracında olduğu gibi, tüm verileri daha fazla analiz için Excel gibi bir tabloya yapıştırılabilecek CSV olarak kopyalamak için pencereye sağ tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Tanılama (DirectX Grafiklerinde Hata Ayıklama)](visual-studio-graphics-diagnostics.md)
- [Kaynak geçmişi](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->