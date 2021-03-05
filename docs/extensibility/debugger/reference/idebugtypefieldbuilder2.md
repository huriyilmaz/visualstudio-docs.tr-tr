---
description: Dizi türleri oluşturabilmeniz için ıdebugtypefieldbuilder 'ı genişletir.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73642024cb379e804559ba8dd55eb44722cf580
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223010"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Dizi türleri oluşturabilmeniz için **ıdebugtypefieldbuilder** 'ı genişletir.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, sembol sağlayıcısından elde edilebilir.

## <a name="methods"></a>Yöntemler
 Bu arabirim, [ıdebugtypefieldbuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Belirtilen türde ve boyutta bir dizi oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
