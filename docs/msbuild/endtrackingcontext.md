---
title: EndTrackingContext | Microsoft Docs
description: Geçerli izleme bağlamını sona ert için EndTrackingContext MSBuild söz dizimi, dönüş değeri ve gereksinimleri öğrenin.
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
ms.openlocfilehash: 4f4a0cd1b327f9be99b07e90bc7564a17ec13472
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054801"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Geçerli izleme bağlamını sona erdirin.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Döndürülen değer

İzleme bağlamı sona **ererse BAŞARILI** bit kümesine sahip **bir HRESULT.**

## <a name="requirements"></a>Gereksinimler

**Üst bilgi:** *FileTracker.h*

## <a name="see-also"></a>Ayrıca bkz.

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
