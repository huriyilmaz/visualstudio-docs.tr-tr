---
title: Grafik API'si ve Bellek İstatistikleri | Microsoft Docs
description: Çeşitli kaynakların Direct3D API kullanımı ve GPU bellek tüketimiyle ilgili bilgileri göstermek için Grafik API İstatistikleri ve Bellek İstatistikleri araçlarını gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7cdd9def44588dacb6995dee966e8f23266aff51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121043"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik API'si ve Bellek İstatistikleri
<!-- VERSIONLESS -->
Visual Studio 2017 ve daha yenisi Grafik API'si İstatistikleri ve Bellek İstatistikleri araçlarını destekler.  Bu iki araç, Direct3D API kullanımıyla ve çeşitli kaynakların GPU bellek tüketimiyle ilgili çeşitli bilgileri görüntülemeye izin verir.

## <a name="graphics-api-statistics"></a>Grafik API'si İstatistikleri
Visual Studio Grafik Tanılama Grafik API'si İstatistikleri, yapılan tüm Direct3D çağrılarını ve her çağrının sayısını görüntülemenizi sağlar.  Pencereyi görüntülemek için Api **İstatistiklerini > öğesini** seçin.

![API İstatistikleri](media/gfx_diag_api_statistics.png)

Bu araç, sık sık veya çok sık çağrılar yaptığını fark ediyor olmadığınız DirectX çağrılarını bulmada kullanışlı olabilir.

Pencerede sağ tıklayıp Tüm verileri CSV Olarak Kopyala'ya tıklayıp daha fazla analiz için Excel yapıştırabilirsiniz.

## <a name="memory-statistics"></a>Bellek İstatistikleri
Bu araç, grafik sürücüsünün çerçevede oluştur kaynaklarının ne kadar bellek olduğunu görüntüler.  Bu pencereyi görüntülemek için Bellek **İstatistikleri > görüntüle menü** öğesini seçin.

![Bellek İstatistikleri](media/gfx_diag_memory_statistics.png)

**GPU Ayırma** sütunu, Olay sütununda görüntülenen olay tarafından kullanılan bellek **miktarını** görüntüler.  Ayrıca, seçilen etkinliğin Kaynak ![ Geçmişini görüntülemek için saat simgesini ](media/gfx_watch.png) [izleme](graphics-event-list.md#resource-history) simgesini de seçin.

API İstatistikleri aracında olduğu gibi pencereye sağ tıklayıp Tüm verileri CSV olarak kopyala'ya tıklayıp daha fazla analiz için Excel yapıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Tanılama (DirectX Grafiklerinde Hata Ayıklama)](visual-studio-graphics-diagnostics.md)
- [Kaynak Geçmişi](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->