---
title: 'Nasıl yapılır: komut satırından raporları filtreleme | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778940"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: komut satırından raporları filtreleme
**VSPerfReport** komutu seçeneklerini kullanarak, profil oluşturma veri dosyasının belirli bir zaman segmentine rapor filtreleyebilir veya verileri bir veya daha fazla işlem ya da iş parçacığı ile kısıtlayabilirsiniz. Bu komut hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Seçenekler|Açıklama|
|-------------|-----------------|
|**StartTime:** [*değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden)|
|**Bitişsaati:** [*değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden)|
|**Filtredosyası:** `VSPFFile`|**Visual Studio performans raporu** penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|
|**Msfilter:** [*başlangıçsaati, süre*]|Yalnızca `Duration` uzunluğu kadar `StartTime` verileri göster (milisaniye cinsinden)|
|**İşlem:** [*pid*]|Yalnızca belirtilen işlemden verileri göster.|
|**Iş parçacığı:** [*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri göster.|
|**Iş parçacığı:** [*ThreadID, ProcessId*]|Belirtilen işlemle ilişkili iş parçacığından yalnızca verileri göster.|
