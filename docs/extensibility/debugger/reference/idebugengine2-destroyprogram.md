---
title: IDebugEngine2::DestroyProgram | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce139dd22361d9914693cbe8ad723656ab7d4f26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731101"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Bir hata ayıklama altyapısına (DE) belirtilen programın genel olarak sonlandırıldığını ve DE'nin programa yapılan tüm başvuruları temizlemesi ve bir program yok etme olayı göndermesi gerektiğini bildirir.

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
[içinde] Atipik olarak sonlandırılan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, DE daha sonra oturum hata ayıklama yöneticisine (SDM) bir [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) olayını geri gönderir.

 Debugged program olarak `E_NOTIMPL`aynı işlemde çalışıyorsa, bu yöntem uygulanmaz (döndürür). Bu yöntem yalnızca DE SDM ile aynı işlemde çalıştığında uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
