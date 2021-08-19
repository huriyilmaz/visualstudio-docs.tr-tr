---
description: Bağlantı noktasının işlem KIMLIĞINI alır.
title: 'IDebugPortEx2:: Getportprocessıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 696ba253090bdec5c31ed814e465b2a5afca87f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088243"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Bağlantı noktasının işlem KIMLIĞINI alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parametreler
`pdwProcessId`\
dışı Bağlantı noktasının kendisinin fiziksel işlem KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, Win32 çalışma zamanında, bu yöntem genellikle `GetCurrentProcessId` fiziksel Işlem kimliği almak Için Win32 işlevini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
