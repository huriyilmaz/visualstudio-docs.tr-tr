---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "64837091"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yapı, bir alanın türü hakkında çeşitli bilgi türlerini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 dwKind  
 [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından, birleşimin nasıl yorumlanacağını belirleyen bir değer.  
  
 Type. typeMeta  
 [Yalnızca C++] İse [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) yapısını içerir `dwKind` `TYPE_KIND_METADATA` .  
  
 Type. typePdb  
 [Yalnızca C++] İse [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) yapısını içerir `dwKind` `TYPE_KIND_PDB` .  
  
 Type. Typeüretildi  
 [Yalnızca C++] İse [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) yapısını içerir `dwKind` `TYPE_KIND_BUILT` .  
  
 tür. kullanılmıyor  
 Kullanılmayan doldurma.  
  
 tür  
 Birleşimin adı.  
  
 unionmember  
 [Yalnızca C#] Bunu temel alarak uygun yapı türüne göre sıralama `dwKind` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, doldurulduğu [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemine geçirilir. Yapının içeriğinin yorumlanması alanı temel alır `dwKind` .  
  
> [!NOTE]
> [Yalnızca C++] `dwKind` Eşitse `TYPE_KIND_BUILT` , yapıyı yok edilirken temeldeki [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesini serbest bırakmak gereklidir `TYPE_INFO` . Bu, çağırarak yapılır `typeInfo.type.typeBuilt.pUnderlyingField->Release()` .  
  
 [Yalnızca C#] Aşağıdaki tabloda `unionmember` her tür türü için üyenin nasıl yorumlanacağı gösterilmektedir. Örnek, bir tür türü için bunun nasıl yapıldığını gösterir.  
  
|`dwKind`|`unionmember` yorumlanan|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Örnek  
 Bu örnek, `unionmember` `TYPE_INFO` C# ' deki yapının üyesini nasıl yorumlayacağını gösterir. Bu örnek yalnızca bir türün () yorumlandığını gösterir `TYPE_KIND_METADATA` , ancak diğerleri tamamen aynı şekilde yorumlanır.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
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
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
