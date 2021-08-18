---
description: Özel bir hata ayıklama altyapısı (DE) arabirimini alır.
title: 'IDebugQueryEngine2:: Getengineınterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5458ec92e121fcfe954e03a660370ec207d3ba55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118638"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Özel bir hata ayıklama altyapısı (DE) arabirimini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parametreler
`ppUnk`\
dışı Bir nesnesi döndürür; `IUnknown` hata ayıklama altyapısını (de) temsil eder ve bır de (örneğin [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) veya [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)) ile ilişkili başka bir geçerli arabirim için sorgulanabilecek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemden alınan arabirimlerin çağrılması, oturum hata ayıklama yöneticisinin işlenmesini atladığından ve hata ayıklama sırasında SDM 'nin hatalı duruma alınmasına veya hata üretmesine neden olabileceği için, elde edilen arabirim dikkatli kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
