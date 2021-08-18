---
description: Bir hata ayıklama altyapısına (DE) belirtilen programın zaman içinde sonlandırılma durumu olduğunu ve DE'nin programa yapılan tüm başvuruları temizlemesi ve bir program yok etme olayı göndermesi gerektiğini bilgi verir.
title: IDebugEngine2::D estprogram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49256244f5839341c66f5a308505c18c0737eace
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119145"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Bir hata ayıklama altyapısına (DE) belirtilen programın zaman içinde sonlandırılma durumu olduğunu ve DE'nin programa yapılan tüm başvuruları temizlemesi ve bir program yok etme olayı göndermesi gerektiğini bilgi verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parametreler
`pProgram`\
[in] Atipik olarak sonlandırılan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, DE daha sonra oturum hata ayıklama yöneticisine (SDM) [bir IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) olayı gönderir.

 DE, hata ayıklama yapılan programla aynı işlemde çalıştırıldısa bu yöntem uygulanmaz `E_NOTIMPL` (döndürür). Bu yöntem yalnızca DE SDM ile aynı işlemde çalıştırıldısa uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
