---
description: PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve bu dosyalarla ilgili bazı sorunları gidermede yararlı Visual Studio.
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
ms.openlocfilehash: e68b8ab22ea4c045c54195381502458f915c3008
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628532"
---
# <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

PerfView, Windows için Olay İzleme'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan ve Visual Studio ile ilgili bazı sorunları gidermede yararlı Visual Studio. [](/windows/desktop/ETW/event-tracing-portal) Bazen bir sorun bildirebilirsiniz, ürün ekibi ek bilgi toplamak için PerfView'u çalıştırmanız için sizden isteyebilirsiniz.

## <a name="install-perfview"></a>PerfView'u yükleme

perfView'u [GitHub.](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)

## <a name="run-perfview"></a>PerfView Çalıştırma

1. PerfView.exe **Gezgini'nde** Windows tıklayın ve Yönetici olarak **çalıştır'ı** seçin
1. Topla menüsünde Topla'ya **tıklayın**
1. **Zip,** **Merge** ve **ThreadTime denetimlerini kullanın.**
1. Döngüsel **MB'yi** 1000'e kadar artır.
1. EtL **izlemelerini** belirtilen bir klasöre ve birden çok kez topacaksanız Veri Dosyasına kaydetmek için Geçerli Dir'i kullanın.
1. Veri kaydetmeye başlamak için Koleksiyonu **Başlat düğmesini** seçin.
1. Veri kaydını durdurmak için Koleksiyonu Durdur **düğmesini** seçin. PrefView.etl.zip dosyası belirtilen dizine kaydedilir.

PerfView yalnızca arabelleğe sığan en son verileri depolar. Bu nedenle, yeniden donmaya veya yavaşlamaya başladıktan Visual Studio mümkün olan en kısa sürede koleksiyonu durdurmayı deneyin. Bir sorun olduktan sonra 30 saniyeden uzun bir süre toplamayın.

Daha fazla bilgi için bkz. [Channel9'da PerfView Öğreticisi.](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)
