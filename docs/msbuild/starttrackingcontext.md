---
title: StartTrackingContext | Microsoft Docs
description: İzleme bağlamını başlatan StartTrackingContext MSBuild parametreleri, gereksinimleri ve dönüş değerini öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: afd46ac5ed538f4773e35c7c727f1cf5fdbcc69a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625502"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

İzleme bağlamı başlatma.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametreler

[in] `intermediateDirectory`

 İzleme günlüğünün depolan olduğu dizin.

[in] `taskName`

 İzleme bağlamını tanımlar. Bu ad, günlük dosyası adını oluşturmak için kullanılır.

## <a name="return-value"></a>Döndürülen değer

 İzleme bağlamı oluşturulduktan sonra **SUCCEEDED** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

 **Üst bilgi:** *FileTracker.h*
