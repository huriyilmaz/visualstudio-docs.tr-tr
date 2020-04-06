---
title: IDebugProgram2::EnumCodeContexts | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22a5ce398e76ee97b2f0448900fd4e38f996615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723044"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Kaynak dosyadaki belirli bir konumun kod bağlamlarının listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`pDocPos`\
[içinde] IDE tarafından bilinen bir kaynak dosyada soyut bir konumu temsil eden bir [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) nesnesi.

`ppEnum`[çıkış] Kod bağlamlarının listesini içeren bir [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, oturum hata ayıklama yöneticisinin (SDM) veya IDE'nin bir kaynak dosya konumunu kod konumuna eşlemesine olanak tanır. Kaynak birden çok kod bloğu oluşturuyorsa (örneğin, C++ şablonları) birden fazla kod bağlamı döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
