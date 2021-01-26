---
title: Raporları komut satırından filtrele | Microsoft Docs
description: Raporlamayı belirli bir zaman dönemine veya seçili işlemlere ve iş parçacıklarıyla kısıtlamak için VSPerfReport.exe kullanın. Bu makalede, açıklamalar ile birlikte seçenekler listelenmektedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 968b02569c123326710482705146844ef393dfa6
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801196"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: Komut satırından raporları filtreleme
**VSPerfReport** komutu seçeneklerini kullanarak, profil oluşturma veri dosyasının belirli bir zaman segmentine rapor filtreleyebilir veya verileri bir veya daha fazla işlem ya da iş parçacığı ile kısıtlayabilirsiniz. Bu komut hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Seçenekler|Description|
|-------------|-----------------|
|**StartTime:**[*değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden)|
|**Bitişsaati:**[*değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden)|
|**Filtredosyası:**`VSPFFile`|**Visual Studio performans raporu** penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|
|**Msfilter:**[*başlangıçsaati, süre*]|Yalnızca `StartTime` uzunluğu `Duration` (milisaniye cinsinden) kadar olan verileri göster|
|**İşlem:**[*pid*]|Yalnızca belirtilen işlemden verileri göster.|
|**Iş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri göster.|
|**Iş parçacığı:**[*ThreadID, ProcessId*]|Belirtilen işlemle ilişkili iş parçacığından yalnızca verileri göster.|
