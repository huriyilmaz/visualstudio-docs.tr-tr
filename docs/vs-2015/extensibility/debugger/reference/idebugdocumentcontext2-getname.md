---
title: 'IDebugDocumentContext2:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1186b3b7d821be6861b992dfc6f2b744e8f722e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144939"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu belge bağlamını içeren belgenin görüntülenebilen adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `gnType`  
 'ndaki [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) numaralandırmasından döndürülecek ad türünü belirten bir değer.  
  
 `pbstrFileName`  
 dışı Dosyanın adını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem genellikle, belge adı belge adının kendisini depolamak üzere yazılmadığı sürece (örneğin gösterildiği gibi), çağrı [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) yöntemine iletilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `CDebugContext` [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimini kullanıma sunan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.  
  
```cpp#  
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)    
{    
   HRESULT hr;    
  
   // Check for a valid file name argument.    
   if (pbstrFileName)    
   {    
      *pbstrFileName = NULL;    
  
      switch (gnType)    
      {    
         case GN_NAME:    
         case GN_FILENAME:    
         {    
            // Copy the member file name into the local file name.    
            *pbstrFileName = SysAllocString(m_sbstrFileName);    
            // Check for successful copy.    
            hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;    
            break;    
         }    
         default:    
         {    
            hr = E_FAIL;    
            break;    
         }    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
