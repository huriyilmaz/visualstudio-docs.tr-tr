---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ec01ebc32472e315fe2c905ecfd2cfef0f4bbe1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541017"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Yönetilen bir VSTO eklentisi kaldırılmadan hemen önce çağırılır.

## <a name="syntax"></a>Syntax

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Döndürülen değer
 Metodun başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, geçerli Microsoft Office sürümleri tarafından çağrılmıyor. Bu yöntem gelecekte kullanılmak üzere ayrılmıştır.

## <a name="see-also"></a>Ayrıca bkz.
- [IManagedAddin arabirimi](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
