---
title: 'IDebugProgram2:: Enumcodebağlamları | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723044"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Kaynak dosyadaki belirli bir konum için kod bağlamlarının bir listesini alır.

## <a name="syntax"></a>Söz dizimi

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
'ndaki IDE tarafından bilinen bir kaynak dosyasındaki soyut konumu temsil eden bir [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) nesnesi.

`ppEnum` dışı Kod bağlamlarının bir listesini içeren bir [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, oturum hata ayıklama Yöneticisi 'nin (SDM) veya IDE 'nin bir kaynak dosya konumunu kod konumuyla eşlemesine olanak sağlar. Kaynak birden fazla kod bloğu oluşturursa birden fazla kod bağlamı döndürülür (örneğin, C++ şablonları).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
