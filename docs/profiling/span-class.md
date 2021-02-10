---
title: Span sınıfı | Microsoft Docs
description: Span sınıfı ve uygulamanın bir aşamasını nasıl tanımladığını öğrenin. Ayrıca, span class public oluşturucular ve devralma hiyerarşisi hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fff7f91326cac47100f5b2b1b42e22b9c0fc1d9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949967"
---
# <a name="span-class"></a>span sınıfı
Uygulamanın aşamasını tanımlar.

## <a name="syntax"></a>Syntax

```cpp
class span;
```

## <a name="members"></a>Üyeler

### <a name="public-constructors"></a>Ortak oluşturucular

|Ad|Açıklama|
|----------|-----------------|
|[span::span Oluşturucusu](../profiling/span-span-constructor.md)|`span` sınıfının yeni bir örneğini başlatır.|
|[span::~span Yok Edicisi](../profiling/span-tilde-span-destructor.md)|Nesneyi yok eder `span` ve kaynaklarını serbest bırakır.|

## <a name="inheritance-hierarchy"></a>Devralma Hiyerarşisi
 `span`

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.
- [Tanılama ad alanı](../profiling/diagnostic-namespace.md)