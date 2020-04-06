---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723401"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Bu yöntem, belirtilen her hata ayıklama altyapısı (DE) için bir program düğümü ekler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parametreler
`guidLaunchingEngine`\
[içinde] `GUID` Programları başlatmak için kullanılacak bir DE (ve kendi program düğümleri eklemek için kabul edilir).

`rgguidSpecificEngines`\
[içinde] `GUID`Program düğümlerinin ekleneceği DEs dizileri.

`celtSpecificEngines`\
[içinde] Dizideki `rgguidSpecificEngines` `GUID`s sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- [Program Düğümleri](../../../extensibility/debugger/program-nodes.md) listelenen her DE için `rgguidSpecificEngines`eklenecektir (fırlatma motoru hariç `guidLaunchingEngine`(verildiği gibi), hangi bir program başlattı zaman kendi program düğümü eklemek için kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Program Düğümleri](../../../extensibility/debugger/program-nodes.md)
