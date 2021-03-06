---
description: PerfView, Visual Studio ile ilgili bazı sorunların giderilmesi için yararlı olabilecek, Windows için olay Izleme 'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır.
title: PerfView ile ETL izlemesi toplama
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 81cf6469a14fb3559d37056ba5193d9018ccc1c8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221073"
---
# <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

PerfView, Visual Studio ile ilgili bazı sorunların giderilmesi için yararlı olabilecek, [Windows Için olay izleme](/windows/desktop/ETW/event-tracing-portal) 'ye dayalı ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır. Bazen bir sorun rapor ettiğinizde, ürün ekibi ek bilgi toplamak için PerfView çalıştırmanızı isteyebilir.

## <a name="install-perfview"></a>PerfView 'ı yükler

PerfView öğesini [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)'dan indirin.

## <a name="run-perfview"></a>PerfView çalıştırma

1. Windows Gezgini 'nde **PerfView.exe** sağ tıklayın ve **yönetici olarak yönetici olarak çalıştır** ' ı seçin.
1. Topla menüsünde **topla** ' yı seçin.
1. **Zip**, **birleştirme** ve **threadtime**'ı denetleyin.
1. **DAIRESEL MB** ile 1000 arasında bir artış yapın.
1. Birden çok kez toplanmanız durumunda ETL izlemelerini belirtilen bir klasöre ve veri dosyasına kaydetmek için **geçerli dizini** değiştirin.
1. Veri kaydetmeye başlamak için **koleksiyonu Başlat** düğmesini seçin.
1. Verileri kaydetmeyi durdurmak için **koleksiyonu durdur** düğmesini seçin. PrefView.etl.zip dosya belirtilen dizine kaydedilir.

PerfView yalnızca kendi arabelleğine sığan en son verileri saklayabilir. Bu nedenle, Visual Studio Donmadan veya yavaşlamaya başladıktan sonra toplamayı en kısa sürede durdurmayı deneyin. Bir sorunla karşılaşmadan 30 saniyeden uzun süre toplanmayın.

Daha fazla bilgi için bkz. [Channel9 üzerinde PerfView öğreticisi](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
