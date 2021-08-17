---
title: EndTrackingContext | Microsoft Docs
description: Geçerli izleme bağlamını sona MSBuild EndTrackingContext için söz dizimi, dönüş değeri ve gereksinimleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: debfb2a287c8efe447c0c1fa299ddf15d25936f802609c4b00a55dfb91a646f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397936"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Geçerli izleme bağlamını sona erdirin.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Döndürülen değer

İzleme bağlamı sona ererse **BAŞARILI** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

**Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
