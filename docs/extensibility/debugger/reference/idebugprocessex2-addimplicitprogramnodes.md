---
title: 'IDebugProcessEx2:: Admplicitprogramnodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ef9379edc9e02e8bed6761abf0aa4a2830fc415
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861094"
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
'ndaki `GUID` Programları başlatmak için kullanılacak olan BIR de (ve kendi program düğümlerini eklemek için varsayılır).

`rgguidSpecificEngines`\
'ndaki `GUID`Program düğümlerinin ekleneceği des dizisi.

`celtSpecificEngines`\
'ndaki `GUID`Dizideki s sayısı `rgguidSpecificEngines` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- Program [düğümleri](../../../extensibility/debugger/program-nodes.md) `rgguidSpecificEngines` `guidLaunchingEngine` , bir program başlattığında kendi program düğümünü eklemek için belirtilen başlatma altyapısı hariç olmak üzere, ' da listelenen her bir ve ' de listelenirler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Program Düğümleri](../../../extensibility/debugger/program-nodes.md)
