---
description: Bu işlemde hata ayıklayıcı olan oturumun adını alır.
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b391738f9e43f9d26c3bec07f801a15c74490e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050812"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Bu işlemde hata ayıklayıcı olan oturumun adını alır. IDE, bu bilgileri belirli bir makinede belirli bir işlemde hata ayıklayıcı olan bir kullanıcıya gösterebilirsiniz.

> [!NOTE]
> Bu yöntem kullanım dışıdır ve uygulaması her zaman `E_NOTIMPL` dönüşletir.

## <a name="syntax"></a>Sözdizimi

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametreler
`pbstrSessionName`\

## <a name="return-value"></a>Dönüş Değeri
 Bu yöntem her zaman `E_NOTIMPL` dönüşletir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
