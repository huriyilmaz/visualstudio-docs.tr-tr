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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a36599259a38d0b9b8eb814a457b3625d593b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934604"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Yönetilen bir VSTO eklentisi kaldırılmadan hemen önce çağırılır.

## <a name="syntax"></a>Sözdizimi

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
