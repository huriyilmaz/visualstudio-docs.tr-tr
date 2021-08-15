---
description: perfview, Visual Studio bazı tür sorunları gidermede yararlı olabilecek, Windows için olay izlemeyi temel alan ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır.
title: PerfView ile ETL izlemesi toplama
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 7c602162fccacc5036404f03621ede8c6e8dd4b077d154a6b0fc608b52f1b0f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232217"
---
# <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

perfview, Visual Studio bazı sorun sorunlarını gidermede faydalı olabilecek [Windows için olay izleme](/windows/desktop/ETW/event-tracing-portal) tabanlı ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır. Bazen bir sorun rapor ettiğinizde, ürün ekibi ek bilgi toplamak için PerfView çalıştırmanızı isteyebilir.

## <a name="install-perfview"></a>PerfView 'ı yükler

[GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)PerfView öğesini indirin.

## <a name="run-perfview"></a>PerfView çalıştırma

1. Windows gezgininde **PerfView.exe** sağ tıklayıp **yönetici olarak çalıştır** ' ı seçin.
1. Topla menüsünde **topla** ' yı seçin.
1. **Zip**, **birleştirme** ve **threadtime**'ı denetleyin.
1. **DAIRESEL MB** ile 1000 arasında bir artış yapın.
1. Birden çok kez toplanmanız durumunda ETL izlemelerini belirtilen bir klasöre ve veri dosyasına kaydetmek için **geçerli dizini** değiştirin.
1. Veri kaydetmeye başlamak için **koleksiyonu Başlat** düğmesini seçin.
1. Verileri kaydetmeyi durdurmak için **koleksiyonu durdur** düğmesini seçin. PrefView.etl.zip dosya belirtilen dizine kaydedilir.

PerfView yalnızca kendi arabelleğine sığan en son verileri saklayabilir. bu nedenle, Visual Studio dondurma veya yavaşlamaya başladıktan sonra toplamayı en kısa sürede durdurmayı deneyin. Bir sorunla karşılaşmadan 30 saniyeden uzun süre toplanmayın.

Daha fazla bilgi için bkz. [Channel9 üzerinde PerfView öğreticisi](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
