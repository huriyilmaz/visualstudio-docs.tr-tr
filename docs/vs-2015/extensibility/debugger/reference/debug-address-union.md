---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b500bcb49e9072c3d31ea5ac3f77bda606c23b78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179183"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Farklı adres türlerini açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Terimler  
 dwKind  
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından, birleşimin nasıl yorumlanacağını belirten bir değer.  
  
 addr. addrNative  
 [Yalnızca C++] = ADDRESS_KIND_NATIVE ise [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) yapısını içerir `dwKind` .  
  
 addr. addrThisRel  
 [Yalnızca C++] = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE ise[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) yapısını içerir `dwKind` .  
  
 addr. addUPhysical  
 [Yalnızca C++] = ADDRESS_KIND_UNMANAGED_PHYSICAL ise[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) yapısını içerir `dwKind` .  
  
 addr. addrMethod  
 [Yalnızca C++] = ADDRESS_KIND_METHOD ise[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) yapısını içerir `dwKind` .  
  
 addr. addrField  
 [Yalnızca C++] = ADDRESS_KIND_FIELD ise[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) yapısını içerir `dwKind` .  
  
 addr. addrLocal  
 [Yalnızca C++] = ADDRESS_KIND_LOCAL ise[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) yapısını içerir `dwKind` .  
  
 addr. addrParam  
 [Yalnızca C++] = ADDRESS_KIND_PARAM ise[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) yapısını içerir `dwKind` .  
  
 addr. Addrarrayeled  
 [Yalnızca C++] = ADDRESS_KIND_ARRAYELEM ise[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) yapısını içerir `dwKind` .  
  
 addr. addrRetVal  
 [Yalnızca C++] = ADDRESS_KIND_RETVAL ise[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) yapısını içerir `dwKind` .  
  
 addr. kullanılmıyor  
 [Yalnızca C++] doldurma.  
  
 addr  
 [Yalnızca C++] Birleşimin adı.  
  
 unionmember  
 [Yalnızca C#] Bu değerin, temel alınarak uygun yapı türüne sıralanması gerekir `dwKind` . Birleşim arasındaki ilişkilendirmeyi ve yorumu görmek için bkz `dwKind` . açıklamalar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısının bir parçasıdır ve farklı türde adreslerden birini temsil eder ( `DEBUG_ADDRESS` Yapı, [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine yapılan bir çağrı ile doldurulur).  
  
 [Yalnızca C#] Aşağıdaki tabloda `unionmember` her bir adres türü için üyenin nasıl yorumlanacağı gösterilmektedir. Örnek, bunun bir tür adres için nasıl yapıldığını gösterir.  
  
|`dwKind`|`unionmember` yorumlanan|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek `METADATA_ADDRESS_ARRAYELEM` , `DEBUG_ADDRESS_UNION` C# ' deki yapının bir tür adresini () nasıl yorumlayacağını gösterir. Kalan öğeler tam olarak aynı şekilde yorumlanabilir.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
