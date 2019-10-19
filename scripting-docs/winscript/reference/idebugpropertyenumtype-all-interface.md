---
title: IDebugPropertyEnumType_All arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574310"
---
# <a name="idebugpropertyenumtype_all-interface"></a>IDebugPropertyEnumType_All Arabirimi
@No__t_0 arabirimleri, her bir IIDS, uygun Numaralandırıcı istenirken `IDebugProperty::EnumMembers` bir filtre olarak geçirilebilmesi için tanımlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Adı açıklayan bir metin dizesi döndürür|  
  
 Aşağıdaki arabirimler `IDebugPropertyEnumType_All` devralınır ve ek yöntemlere sahip olmaz.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)