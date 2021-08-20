---
title: Komut Satırı Komut Satırı | Microsoft Docs
description: Raporlamayı VSPerfReport.exe belirli bir zaman dönemiyle veya seçilen işlemler ve iş parçacıklarıyla sınırlamak için bu ayarları kullanın. Bu makalede seçenekler ve açıklamalar listelanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 39471e7006cfe49a8c03c0d4d0f34bb3b149aad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061005"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: Komut satırından raporları filtreleme
**VSPerfReport** komutuna yönelik seçenekleri kullanarak, raporları profil oluşturma veri dosyasının belirli bir zaman segmentine filtre oluşturabilir veya verileri bir veya daha fazla işlem ya da iş parçacığıyla kısıtabilirsiniz. Bu komut hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Seçenekler|Açıklama|
|-------------|-----------------|
|**StartTime:**[*Değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden).)|
|**EndTime:**[*Değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden).)|
|**FilterFile:**`VSPFFile`|Performans Raporu penceresinden oluşturulan filtre dosyasının **Visual Studio belirtir.**|
|**MsFilter:**[*StartTime,Duration*]|Yalnızca uzunluğuna `StartTime` kadar olan verileri göster `Duration` (milisaniye cinsinden).)|
|**İşlem:**[*Pid*]|Yalnızca belirtilen işlemden gelen verileri göster.|
|**İş Parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri gösterir.|
|**İş Parçacığı:**[*ThreadID,ProcessID*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığından verileri gösterir.|
