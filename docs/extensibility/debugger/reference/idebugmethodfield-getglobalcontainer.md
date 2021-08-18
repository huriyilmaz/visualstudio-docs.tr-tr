---
description: Metodun genel kapsayıcısını alır.
title: 'IDebugMethodField:: GetGlobalContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5cc417422b16b47ae989e86032efb43bd5d9fef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118651"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Metodun genel kapsayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametreler
`ppClass`\
dışı Bu yöntemin tanımlandığı modülü temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi Modülün tamamını temsil eder ve yapay bir nesnedir, diğer bir deyişle, modülün kendisi gerçek bir sınıfa sahip değildir ancak bir nesne tarafından temsil edilebilir, bu da `IDebugClassField` modülün çeşitli öğelerinin numaralandırılmasına ve keşfedilmesini sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
