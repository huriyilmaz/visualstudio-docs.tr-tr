---
description: Bir türü temsil eden bir alan oluşturma yeteneğini temsil eder.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fec9ec87f1cc6bfd97a4acd2d83100919505f47e797d7cb82f86fbe57879e971
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121291902"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Bir türü temsil eden bir alan oluşturma yeteneğini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, sembol sağlayıcısından edinilebilir.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|İlkel türü temsil eden bir nesne oluşturur.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Belirtilen türe bir işaretçi oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
