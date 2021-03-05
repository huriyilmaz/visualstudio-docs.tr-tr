---
description: Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir KIMLIK oluşturur.
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e82e11d83c77131e47d815529813484d2869cdc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171445"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir KIMLIK oluşturur.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, oturum hata ayıklama Yöneticisi, bu özelliğin diğer tüm özellikler arasında benzersiz şekilde tanımlanmasını sağlamak istediğinde çağrılır. Hata ayıklama altyapısı (DE), ile ilgilenen özellikler zaten benzersiz olarak tanımlanmamışsa, bu yöntemi destekler. DE bu yöntemi desteklemiyorsa, döndürür `E_NOTIMPL` .

 `CreateObjectID` [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) yöntemi çağrıldığında ile oluşturulan HERHANGI bir benzersiz kimlik yok edilir; bu da bu özelliği benzersiz bir şekilde tanımlamak için gerekin sonuna işaret eder.

> [!NOTE]
> Bu benzersiz KIMLIĞI almak için herhangi bir yöntem yoktur; bu nedenle, yöntemi çağrıldığında DE benzersiz kimlikler için istediği her şeyi yapabilir `CreateObjectID` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
