---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632114"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Bir izleme bağlamı başlatın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametreler

[in] `intermediateDirectory`

 İzleme günlüğünün depolayabileceği dizin.

[in] `taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

## <a name="return-value"></a>Dönüş değeri

 İzleme bağlamı oluşturulduysa, **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*
