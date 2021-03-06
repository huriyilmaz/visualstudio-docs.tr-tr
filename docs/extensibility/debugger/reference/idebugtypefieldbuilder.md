---
description: Bir türü temsil eden alan oluşturma yeteneğini temsil eder.
title: Idebugtypefieldbuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223114"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Bir türü temsil eden alan oluşturma yeteneğini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, sembol sağlayıcısından alınır.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Temel bir türü temsil eden bir nesne oluşturur.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Belirtilen türe bir işaretçi oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
