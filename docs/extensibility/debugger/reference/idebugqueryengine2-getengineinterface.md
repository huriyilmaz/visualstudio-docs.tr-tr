---
description: Özel bir hata ayıklama altyapısı (DE) arabirimi alır.
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725165"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Özel bir hata ayıklama altyapısı (DE) arabirimi alır.

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
[out] Bir nesnesi hata ayıklama altyapısını (DE) temsil eder ve bir DE ile ilişkili diğer geçerli `IUnknown` arabirimler [(örneğin IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) veya [IDebugEngineLaunch2) için sorgulanabilirsiniz.](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sonuçta elde edilen arabirim, bu yöntemden alınan arabirimler aracılığıyla çağrılarak oturum hata ayıklama yöneticisinin işlemini atlar ve SDM'nin hatalı bir durumla karşılaşması veya hata ayıklama sırasında hata oluşturması ile sonuçlandırılana neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
