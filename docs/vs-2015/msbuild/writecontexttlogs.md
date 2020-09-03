---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteContextTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bba9c5b46aa01cddca4de5c8e1347b540999289
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156456"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçerli bağlam için günlük dosyalarını yazar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametreler  
 'ndaki `intermediateDirectory`  
 İzleme günlüğünün depolayabileceği dizin.  
  
 'ndaki `tlogRootName`  
 Günlük dosyası adının kök adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 A [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) ile [başarılı] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) izleme bağlamı oluşturulduysa bit ayarlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** FileTracker. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WriteAllTLogs](../msbuild/writealltlogs.md)
