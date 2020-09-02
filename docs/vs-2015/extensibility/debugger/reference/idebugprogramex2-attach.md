---
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fe729f2fc196380a3db1a60d1c32f62bbd70998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817807"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir programa oturum iliştirme.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCallback`  
 'ndaki Ekli hata ayıklama altyapısının olayları gönderdiği geri çağırma işlevini temsil eden bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.  
  
 `dwReason`  
 'ndaki [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırmasından iliştirme işleminin nedenini açıklayan bir değer.  
  
 `pSession`  
 'ndaki Programa bağlanan oturumu benzersiz bir şekilde tanımlayan bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. Program zaten ekli ise, bu yöntem döndürmelidir `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` .  
  
## <a name="remarks"></a>Açıklamalar  
 Programı içeren bağlantı noktası, `pSession` hangi oturumun programa iliştirilmeye çalışacağını öğrenmek için içindeki değerini kullanabilir. Örneğin, bir bağlantı noktası tek seferde bir işleme yalnızca bir hata ayıklama oturumunun iliştirmeye izin veriyorsa, bağlantı noktası aynı oturumun işlemdeki diğer programlara zaten eklenmiş olup olmadığını belirleyebilir.  
  
> [!NOTE]
> Geçirilen arabirim, `pSession` Bu programa eklenen oturum hata ayıklama yöneticisini benzersiz bir şekilde tanımlayan bir değer olan tanımlama bilgisi olarak değerlendirilir. sağlanan arabirimdeki yöntemlerin hiçbiri işlevsel değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
