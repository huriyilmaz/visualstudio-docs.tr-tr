---
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485875f2ca4cd54c41d959ffaf769368db265243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879052"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Belirtilen programın genellikle sonlandırıldığı ve aynı programın tüm başvurularını temizlemesi ve program yok etme olayı göndermesini gerektiren bir hata ayıklama altyapısına (DE) bildirir.

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
'ndaki Atipik olarak sonlandırılan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, daha sonra oturum hata ayıklama Yöneticisi 'ne (SDM) geri bir [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) olayı gönderir.

 Bu yöntem, `E_NOTIMPL` hata ayıklamakta olan programla aynı işlemde çalışıyorsa, uygulanmaz (döndürür). Bu yöntem yalnızca, SDM ile aynı işlemde çalıştırılıyorsa uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
