---
description: Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir kimlik oluşturur.
title: IDebugProperty3::CreateObjectID | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8072bc2d7689677b27ccc3ef63f6d9176927603c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063986"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Diğer tüm özellikler arasında benzersiz olduğundan emin olmak için bu özellik için benzersiz bir kimlik oluşturur.

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
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi bu özelliğin diğer tüm özellikler arasında benzersiz olarak tanım olduğundan emin olmak istiyorsa bu yöntem çağrılır. Hata ayıklama altyapısı (DE), ilgili özellikler önceden benzersiz olarak tanımlandı değilse bu yöntemi destekler. DE bu yöntemi desteklemezse `E_NOTIMPL` döndürür.

 destroyObjectID yöntemi çağrıldıktan sonra ile oluşturulan tüm benzersiz kimlikler yok edilir; bu özellik benzersiz olarak tanımlama `CreateObjectID` ihtiyacının sonuna da işaret eder. [](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

> [!NOTE]
> Bu benzersiz kimliği almak için bir yöntem yoktur, bu nedenle de yöntem çağrıldıken benzersiz kimlikler için `CreateObjectID` istediği her şeyi yapar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
