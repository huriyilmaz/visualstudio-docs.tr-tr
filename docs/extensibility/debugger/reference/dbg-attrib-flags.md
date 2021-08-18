---
description: IDebugProperty2 veya IDebugReference2 arabirimi için çeşitli öznitelikleri açıklar.
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8137d5bad817478371fb57dcffc568db616949a1739e5d501ac4fe394d846d16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452452"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
[IDebugProperty2 veya IDebugReference2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi [için çeşitli öznitelikleri](../../../extensibility/debugger/reference/idebugreference2.md) açıklar. DEBUG_PROPERTY_INFO [üyesi.](../../../extensibility/debugger/reference/debug-property-info.md)

## <a name="syntax"></a>Syntax

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Üyeler
 `DBG_ATTRIB_NONE`\
 Öznitelik olmadığını gösterir.

 `DBG_ATTRIB_ALL`\
 Tüm öznitelikleri gösterir.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Başvuru veya özelliğin children olduğunu gösterir.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Bu nesne için bir kimliğin oluşturul olduğunu gösterir.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Bu nesne için bir kimliğin oluşturula olduğunu gösterir.

 `DBG_ATTRIB_VALUE_READONLY`\
 Değerin salt okunur olduğunu gösterir.

 `DBG_ATTRIB_VALUE_ERROR`\
 Değerin bir hata olduğunu gösterir.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Değerlendirmenin yan etkisi olduğunu gösterir.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Bu özelliğin gerçekten bir aşırı yükleme kapsayıcısı olduğunu gösterir.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 içinde değerinin `DEBUG_PROPERTY_INFO::bstrValue` Boole olduğunu gösterir.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 içinde değerinin `DEBUG_PROPERTY_INFO::bstrValue` Boole ve olduğunu `TRUE` gösterir.

 `DBG_ATTRIB_VALUE_INVALID`\
 içinde değerinin geçerli `DEBUG_PROPERTY_INFO::bstrValue` olmadığını gösterir.

 `DBG_ATTRIB_VALUE_NAT`\
 içinde değerinin `DEBUG_PROPERTY_INFO::bstrValue` " bir şey *değil*" (NAT) olduğunu gösterir. NAT, Intel 64 bit işlemcilerde ertelenen tahmine neden olan özel durumları belirten bir yazmaç bayrağını açıklar.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 içinde değerinin muhtemelen `DEBUG_PROPERTY_INFO::bstrValue` otomatik olarak genişletilir olduğunu gösterir.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Bir değerlendirmenin zaman zaman içinde olduğunu gösterir.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 içinde değerinin `DEBUG_PROPERTY_INFO::bstrValue` bir ham dize ile temsili olduğunu gösterir.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Bu özellikle ilişkilendirilmiş en az bir özel görüntüleyici olduğunu gösterir.

 `DBG_ATTRIB_ACCESS_NONE`\
 , veya türü erişimine `public` sahip `private` bir nesneyi `protected` gösterir.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Genel erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Özel erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Korumalı erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Son erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_ALL`\
 'den erişim özniteliklerini ayıklamak için `DBG_ATTRIB_FLAGS` maskeleme.

 `DBG_ATTRIB_STORAGE_NONE`\
 Belirtilen bir depolama türü olmadığını gösterir.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Genel depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Statik depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Yazmazda depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_ALL`\
 depolama özniteliklerini 'den ayıklamak için `DBG_ATTRIB_FLAGS` maskeleme.

 `DBG_ATTRIB_TYPE_NONE`\
 Tür değiştirici olmadığını gösterir.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Nesne türünün sanal olduğunu gösterir.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Nesne türünün sabit olduğunu gösterir.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Nesne türünün eşitlenmiş olduğunu gösterir.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Nesne türünün geçici olduğunu gösterir.

 `DBG_ATTRIB_TYPE_ALL`\
 'den tür özniteliklerini ayıklamak için `DBG_ATTRIB_FLAGS` maskeleme.

 `DBG_ATTRIB_DATA`\
 Bu nesnenin bir veri alanı olduğunu gösterir.

 `DBG_ATTRIB_METHOD`\
 Bu nesnenin bir yöntem olduğunu gösterir.

 `DBG_ATTRIB_PROPERTY`\
 Bu nesnenin bir özellik olduğunu gösterir.

 `DBG_ATTRIB_CLASS`\
 Bu nesnenin bir sınıf olduğunu gösterir.

 `DBG_ATTRIB_BASECLASS`\
 Bu nesnenin bir temel sınıf olduğunu gösterir.

 `DBG_ATTRIB_INTERFACE`\
 Bu nesnenin bir arabirim olduğunu gösterir.

 `DBG_ATTRIB_INNERCLASS`\
 Bu nesnenin bir iç sınıf olduğunu gösterir.

 `DBG_ATTRIB_MOSTDERIVED`\
 Bu nesnenin ' en çok türetilmiş *' olduğunu* gösterir. " en türetilmiş "*terimi,* başvuru türü değil, nesnenin gerçek türünü ifade eder.

 `DBG_ATTRIB_CHILD_ALL`\
 aracılığıyla bir `DBG_ATTRIB_DATA` maskesini `DBG_ATTRIB_MOSTDERIVED` gösterir.

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Nesnenin ilişkili birden çok özel görüntüleyicisi olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu numaralamada yer alan değerler aslında C# için derlemede tanımlanmamıştır. Bunun yerine, tanımları kaynak dosyanıza kopyalamanız gerekir.

 Bu bayraklar, bir nesnenin, örneğin [EnumChildren'a](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)bağımsız değişken olarak geçiriken filtrelemek için de kullanılır. Değerler bitwise ile birleştirilmiş `OR` olabilir.

 bayrağı, `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [IDebugProperty2 arabiriminden IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) [](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimini elde etmek ve özel görüntüleyicilerin listesi için [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) çağrısı yapmak için bir göstergedir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
