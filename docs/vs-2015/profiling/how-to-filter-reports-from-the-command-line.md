---
title: 'Nasıl yapılır: komut satırından raporları filtreleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146010"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Nasıl yapılır: Komut Satırından Raporları Filtreleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
