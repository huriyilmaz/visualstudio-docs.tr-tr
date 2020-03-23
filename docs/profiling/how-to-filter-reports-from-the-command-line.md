---
title: 'Nasıl Yapılsın: Komut Satırından Raporları Filtrele | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd6462f9159a2926c6dfa45dcadff860cce9ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778940"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: Komut satırından raporları filtreleme
**VSPerfReport** komutu için seçenekleri kullanarak, raporları profil oluşturma veri dosyasının belirli bir zaman kesimine filtreleyebilir veya verileri bir veya daha fazla işlem veya iş parçacığıyla sınırlandırabilirsiniz. Bu komut hakkında daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**Başlangıç Zamanı:**[*Değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden.)|
|**Bitiş Zamanı:**[*Değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden.)|
|**FilterFile:**`VSPFFile`|**Visual Studio Performans Raporu** penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|
|**MsFilter:**[*Başlangıç Zamanı,Süre*]|Yalnızca uzunluğa `StartTime` kadar `Duration` (milisaniye cinsinden) verileri gösterin.|
|**İşlem:**[*Pid*]|Yalnızca belirtilen işlemdeki verileri gösterin.|
|**Konu:**[*ThreadID*]|Yalnızca belirtilen iş parçacığındaki verileri gösterin.|
|**Konu:**[*ThreadID,ProcessID*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığındaki verileri gösterin.|
