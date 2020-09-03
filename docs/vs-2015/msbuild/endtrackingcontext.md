---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- EndTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 641c67c4830f4d882d2d81cb2f00599825ae5d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196562"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçerli izleme bağlamını sonlandırın.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 A [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) ile [başarılı] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) izleme bağlamının sonlandırılması durumunda bit ayarlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** FileTracker. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
