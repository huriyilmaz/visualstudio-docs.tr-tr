---
title: 'IDebugProperty2:: Gebir Deınfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164983"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Özelliği için genişletilmiş bilgileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidExtendedInfo`  
 'ndaki Alınacak genişletilmiş bilgilerin türünü belirleyen GUID. Ayrıntılar için bkz. açıklamalar.  
  
 `pExtendedInfo`  
 dışı `VARIANT` Genişletilmiş özellik bilgilerini almak için kullanılabilecek bir (C++) veya nesne (C#) döndürür. Örneğin, bu parametre `IUnknown` bir [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi için sorgulanabilen bir arabirim döndürebilir. Ayrıntılar için bkz. açıklamalar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. `S_GETEXTENDEDINFO_NO_EXTENDEDINFO`Alınacak genişletilmiş bilgi yoksa döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemini çağırarak, kendisini alma amacını taşıyan bilgileri alma amacıyla mevcuttur.  
  
 Aşağıdaki GUID 'Ler genellikle bu yöntem tarafından tanınır (ad hiçbir derlemede kullanılamadığından, C# için GUID değerleri belirtilir). İç kullanım için ek GUID 'Ler oluşturulabilir.  
  
|Name|GUID|Açıklama|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11D0-b47f-00a0244a1dd2}|Belgeye bir `IUnknown` arabirim döndürür. Genellikle, [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi Bu arabirimden elde edilebilir `IUnknown` .|  
|guidCodeContext|{e2fc65e-56ce-11D1-b528-00aax004a8797}|`IUnknown`Belge bağlamına bir arabirim döndürür. Genellikle, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi Bu arabirimden elde edilebilir `IUnknown` .|  
|Guidcustomviewerdestekleniyor|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Genellikle bir ifade değerlendirici tarafından uygulanan özel bir görüntüleyicinin CLSID 'sini içeren bir dize döndürür.|  
|Kılavuzu Xtendedinfoslot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Bu özellik yönetilen bir kod yerel adresini temsil ediyorsa, istenen yuva numarasını temsil eden 32 bitlik bir sayı döndürür.|  
|Kılavuzu Xtendedinfosignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Property nesnesiyle ilişkili değişkenin imzasını içeren bir dize döndürür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
