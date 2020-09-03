---
title: IDebugProperty3::D Estroyobjectıd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721206"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Bu özellik ile ilişkili benzersiz KIMLIĞI yok eder ve çağıranın artık bu özelliği diğer tüm özelliklerden benzersiz bir şekilde belirlemesine işaret eder.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının bir özelliğin benzersiz kimliklerini desteklemesi gerekmiyorsa (bunları benzersiz bir şekilde takip ettiğinden), bu yöntem için yalnızca geri dönüş yapılabilir `E_NOTIMPL` .

 Çağıran, bu özelliğin diğer tüm özellikler arasında benzersiz bir şekilde tanımlandığını doğrulamak istediğinde [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) yöntemine yapılan bir çağrıyla benzersiz kimlikler oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
