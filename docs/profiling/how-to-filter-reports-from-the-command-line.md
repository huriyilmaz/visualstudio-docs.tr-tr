---
title: Raporları komut satırından filtrele | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b6408975e8a3d7189db26913f3de75ad1c7c595
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851144"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: Komut satırından raporları filtreleme
**VSPerfReport** komutu seçeneklerini kullanarak, profil oluşturma veri dosyasının belirli bir zaman segmentine rapor filtreleyebilir veya verileri bir veya daha fazla işlem ya da iş parçacığı ile kısıtlayabilirsiniz. Bu komut hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Seçenekler|Açıklama|
|-------------|-----------------|
|**StartTime:**[*değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden)|
|**Bitişsaati:**[*değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden)|
|**Filtredosyası:**`VSPFFile`|**Visual Studio performans raporu** penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|
|**Msfilter:**[*başlangıçsaati, süre*]|Yalnızca `StartTime` uzunluğu `Duration` (milisaniye cinsinden) kadar olan verileri göster|
|**İşlem:**[*pid*]|Yalnızca belirtilen işlemden verileri göster.|
|**Iş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri göster.|
|**Iş parçacığı:**[*ThreadID, ProcessId*]|Belirtilen işlemle ilişkili iş parçacığından yalnızca verileri göster.|
