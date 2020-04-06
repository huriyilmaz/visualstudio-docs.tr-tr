---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70fd48adacdbbf936c6997fc373ad4a8d7e696b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724075"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Bu işlemi hata ayıklayan oturumun adını alır. Bir IDE, bu bilgileri belirli bir makinede belirli bir işlemi hata ayıklayan bir kullanıcıya görüntüleyebilir.

> [!NOTE]
> Bu yöntem amortismana sokuldu ve uygulanması `E_NOTIMPL`her zaman geri dönmelidir.

## <a name="syntax"></a>Sözdizimi

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametreler
`pbstrSessionName`\

## <a name="return-value"></a>Dönüş Değeri
 Bu yöntem her `E_NOTIMPL`zaman dönmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
