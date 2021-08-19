---
description: Kaynak dosyada verilen bir konum için kod bağlamlarının listesini alın.
title: IDebugProgram2::EnumCodeContexts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 669c513b07e91299be7c3b9d600995eca886b9ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132788"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Kaynak dosyada verilen bir konum için kod bağlamlarının listesini alın.

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
[in] IDE tarafından bilinen bir kaynak dosyada soyut konumu temsil eden bir [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) nesnesi.

`ppEnum` [out] Kod [bağlamlarının listesini içeren bir IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bir kaynak dosya konumunu kod konumunda eşlemek için oturum hata ayıklama yöneticisi (SDM) veya IDE sağlar. Kaynak birden çok kod bloğu (örneğin, C++ şablonları) oluşturursa birden fazla kod bağlamı döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
