---
description: Bir programa oturum iliştirme.
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4f7f6a083c37ece73be488ab0c4f6d4c25ce24c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084161"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Bir programa oturum iliştirme.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
'ndaki Ekli hata ayıklama altyapısının olayları gönderdiği geri çağırma işlevini temsil eden bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`dwReason`\
'ndaki [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırmasından iliştirme işleminin nedenini açıklayan bir değer.

`pSession`\
'ndaki Programa bağlanan oturumu benzersiz bir şekilde tanımlayan bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. Program zaten ekli ise, bu yöntem döndürmelidir `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` .

## <a name="remarks"></a>Açıklamalar
 Programı içeren bağlantı noktası, `pSession` hangi oturumun programa iliştirilmeye çalışacağını öğrenmek için içindeki değerini kullanabilir. Örneğin, bir bağlantı noktası tek seferde bir işleme yalnızca bir hata ayıklama oturumunun iliştirmeye izin veriyorsa, bağlantı noktası aynı oturumun işlemdeki diğer programlara zaten eklenmiş olup olmadığını belirleyebilir.

> [!NOTE]
> Geçirilen arabirim, `pSession` Bu programa eklenen oturum hata ayıklama yöneticisini benzersiz bir şekilde tanımlayan bir değer olan tanımlama bilgisi olarak değerlendirilir. sağlanan arabirimdeki yöntemlerin hiçbiri işlevsel değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
