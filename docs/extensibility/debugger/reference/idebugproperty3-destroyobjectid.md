---
title: IDebugÖzellik3::DestroyObjectID | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721206"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Bu özellik ile ilişkili benzersiz kimliği yok eder ve arayan kişinin artık bu özelliği diğer tüm özelliklerden benzersiz olarak tanımlamayı önemsemediğini gösterir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı nın bir özellik için benzersiz edilmiş iAh'ları desteklemesi gerekmiyorsa (çünkü bunları `E_NOTIMPL` zaten benzersiz bir şekilde içten izler), o zaman bu yöntem için geri dönebilir.

 Tekil kimlikler, arayan bu özelliğin diğer tüm özellikler arasında benzersiz bir şekilde tanımlandığınızdan emin olmak istediğinde [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) yöntemine yapılan bir çağrıyla oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
