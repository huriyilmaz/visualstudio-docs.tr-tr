---
description: Bir IDebugProperty2 veya IDebugReference2 arabirimi için çeşitli öznitelikleri açıklar.
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f467c9ac66bc249974f919a48a1527bebb26f361
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170724"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) veya [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi için çeşitli öznitelikleri açıklar. [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısının üyesi.

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
 Başvurunun veya özelliğin alt öğe olduğunu gösterir.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Bu nesne için bir KIMLIK oluşturulduğunu gösterir.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Bu nesne için bir KIMLIK oluşturulup oluşturuamayacağını gösterir.

 `DBG_ATTRIB_VALUE_READONLY`\
 Değerin salt okunurdur olduğunu gösterir.

 `DBG_ATTRIB_VALUE_ERROR`\
 Değerin bir hata olduğunu gösterir.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Değerlendirmenin bir yan etkiye sahip olduğunu gösterir.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Bu özelliğin gerçekten aşırı yükleme kapsayıcısı olduğunu gösterir.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 İçindeki değerin Boole olduğunu gösterir `DEBUG_PROPERTY_INFO::bstrValue` .

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 İçindeki değerinin `DEBUG_PROPERTY_INFO::bstrValue` Boolean ve olduğunu gösterir `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 İçindeki değerin geçerli olmadığını gösterir `DEBUG_PROPERTY_INFO::bstrValue` .

 `DBG_ATTRIB_VALUE_NAT`\
 İçindeki değerin `DEBUG_PROPERTY_INFO::bstrValue` "*bir şey değil*" (NAT) olduğunu gösterir. NAT, ertelenmiş öngörülebilir özel durumları belirten Intel 64-bit işlemcilerde bir kayıt bayrağını açıklar.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 İçindeki değerin, `DEBUG_PROPERTY_INFO::bstrValue` büyük olasılıkla otomatik olarak genişletildiğini gösterir.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Bir değerlendirmenin zaman aşımına uğradığını gösterir.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 İçindeki değerin `DEBUG_PROPERTY_INFO::bstrValue` bir ham dizeyle temsil edilebilir olduğunu gösterir.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Bu özelliğe ilişkili en az bir özel Görüntüleyici olduğunu gösterir.

 `DBG_ATTRIB_ACCESS_NONE`\
 Değil `public` , `private` , veya erişimi olmayan bir nesneyi gösterir `protected` .

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Ortak erişime sahip bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Özel erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Korumalı erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Son erişimi olan bir nesneyi gösterir.

 `DBG_ATTRIB_ACCESS_ALL`\
 Erişim özniteliklerini Ayıklanacak maske `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Hiçbir depolama türü belirtilmemiş olduğunu gösterir.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Genel depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Statik depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Kayıttaki depolamayı gösterir.

 `DBG_ATTRIB_STORAGE_ALL`\
 Depolama özniteliklerini Ayıklanacak maske `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_TYPE_NONE`\
 Tür değiştiricisi olmadığını gösterir.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Nesne türünün sanal olduğunu gösterir.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Nesne türünün sabit olduğunu gösterir.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Nesne türünün eşitlendiğini gösterir.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Nesne türünün geçici olduğunu gösterir.

 `DBG_ATTRIB_TYPE_ALL`\
 Tür özniteliklerinin ayıklanacağı maske `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Bu nesnenin bir veri alanı olduğunu gösterir.

 `DBG_ATTRIB_METHOD`\
 Bu nesnenin bir yöntem olduğunu gösterir.

 `DBG_ATTRIB_PROPERTY`\
 Bu nesnenin bir özellik olduğunu gösterir.

 `DBG_ATTRIB_CLASS`\
 Bu nesnenin bir sınıf olduğunu belirtir.

 `DBG_ATTRIB_BASECLASS`\
 Bu nesnenin bir temel sınıf olduğunu gösterir.

 `DBG_ATTRIB_INTERFACE`\
 Bu nesnenin bir arabirim olduğunu gösterir.

 `DBG_ATTRIB_INNERCLASS`\
 Bu nesnenin bir iç sınıf olduğunu gösterir.

 `DBG_ATTRIB_MOSTDERIVED`\
 Bu nesnenin '*en-türetilmiş*' olduğunu gösterir. "*En-türetilmiş*" terimi, başvurusunun türü değil, nesnenin gerçek türü anlamına gelir.

 `DBG_ATTRIB_CHILD_ALL`\
 İle maskesini belirtir `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Nesnenin kendisiyle ilişkili birden çok özel görüntüleyiciyle olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu Numaralandırmadaki değerler gerçekte C# derlemesinde tanımlanmamıştır. Bunun yerine, tanımları kaynak dosyanıza kopyalamanız gerekir.

 Bu bayraklar Ayrıca bir nesnenin alt öğelerini filtrelemek için kullanılır, örneğin, [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)'a bağımsız değişken olarak geçirildiğinde. Değerler bit düzeyinde birleştirilebilir `OR` .

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`Bayrak, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabiriminden [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimini elde etmek ve özel görüntüleyicilerin listesi için [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) öğesini çağırmak için bir belirtidir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
