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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af90f360e59e04cc5d55017c5d986e6682bab2ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064819"
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
