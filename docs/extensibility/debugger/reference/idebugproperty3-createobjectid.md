---
title: IDebugÖzellik3::CreateObjectID | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721182"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir kimlik oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, oturum hata ayıklama yöneticisi bu özelliğin diğer tüm özellikleri arasında benzersiz olarak tanımlandığınızdan emin olmak istediğinde çağrılır. Hata ayıklama altyapısı (DE), ilgilendiği özellikler zaten benzersiz olarak tanımlanmamışsa bu yöntemi destekler. DE bu yöntemi desteklemiyorsa, `E_NOTIMPL`döndürür.

 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) yöntemi `CreateObjectID` çağrıldığında oluşturulan benzersiz kimlik yok edilir; bu aynı zamanda bu özelliği benzersiz bir şekilde tanımlama ihtiyacının da sona erdirilme sinyali vetir.

> [!NOTE]
> Bu benzersiz kimliği almak için bir yöntem yoktur, bu nedenle DE `CreateObjectID` yöntem çağrıldığında benzersiz kimlikler için ne isterse yapabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
