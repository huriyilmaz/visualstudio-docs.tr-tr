---
title: IManagedAddin::Unload
description: Yönetilen bir VSTO eklentisi kaldırılmadan hemen önce çağırılır.
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
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469716"
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
