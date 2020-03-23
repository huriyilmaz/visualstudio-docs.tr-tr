---
title: PerfView ile ETL izlemesi toplama
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 24d72e9630506ecc3d25fcc75e51eeb84f619e53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271157"
---
# <a name="collect-an-etl-trace-with-perfview"></a>PerfView ile ETL izlemesi toplama

PerfView, Visual Studio ile ilgili bazı sorunları gidermede yararlı olabilecek [Windows için Olay İzleme'ye](/windows/desktop/ETW/event-tracing-portal) dayalı ETL (olay izleme günlüğü) dosyaları oluşturan bir araçtır. Bazen bir sorunu rapor ettiğinizde, ürün ekibi ek bilgi toplamak için PerfView'i çalıştırmanızı isteyebilir.

## <a name="install-perfview"></a>PerfView'i Yükleyin

PerfView'i [GitHub'dan indirin.](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)

## <a name="run-perfview"></a>PerfView çalıştırın

1. Windows Gezgini'nde **PerfView.exe'ye** sağ tıklayın ve **yönetici olarak Çalıştır'ı** seçin
1. Topla menüsünde **Topla'yı** seçin
1. **Zip,** **Birleştirme**ve **ThreadTime'ı**denetleyin.
1. **Dairesel MB'yi** 1000'e yükseltin.
1. Birden fazla kez toplayacaksanız, ETL izlerini belirli bir klasöre ve Veri Dosyasına kaydetmek için **Geçerli Dir'i** değiştirin.
1. Veri kaydetmeye başlamak için **Koleksiyonu Başlat** düğmesini seçin.
1. Veri kaydını durdurmak için **Koleksiyonu Durdur** düğmesini seçin. PrefView.etl.zip dosyası belirtilen dizine kaydedilir.

PerfView yalnızca arabelleği sığan en son verileri depolayabilir. Bu nedenle, Visual Studio donmaya veya yavaşlamaya başladıktan sonra koleksiyonu mümkün olan en kısa sürede durdurmaya çalışın. Bir soruna ulaştıktan sonra 30 saniyeden fazla para toplamayın.

Daha fazla bilgi için [Kanal9'daki PerfView Tutorial bölümüne](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)bakın.
