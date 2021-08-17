---
description: Bir programın hata ayıklaması için kullanılamaz hale getirir.
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e51d327f8b5a6963a87c13aa7c19b2d6ab297b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071359"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Bir programın hata ayıklaması için kullanılamaz hale getirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametreler
`pDebuggeeInterface`\
[in] Programın `IUnknown` arabirimi. Bu, [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) yöntemine sağlanan değerle aynıdır ve kaldırılan programı benzersiz olarak tanımlar (yani tanımlama bilgisi olarak kullanılır).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir programı hata ayıklama altyapıları ve oturum hata ayıklama yöneticisi için kullanılabilir yapmak için [PublishProgram yöntemini](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
