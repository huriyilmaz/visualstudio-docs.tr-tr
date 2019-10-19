---
title: Icriptnode arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577512"
---
# <a name="iscriptnode-interface"></a>IScriptNode Arabirimi
@No__t_0 arabirimini uygulayan bir nesne bir Web sayfasını temsil eder.  
  
 @No__t_0 devralınan yöntemlere ek olarak, `IScriptNode` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Bir nesnenin hala etkin olup olmadığını gösterir.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Bir `IScriptEntry` alt örneği ekler.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Bir `IScriptNode` alt örneği olarak bir kod oluşturma yöntemi ekler.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Nesne ağacını siler.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Düğümde belirtilen dizinde olan alt öğesini döndürür.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Bir kod oluşturma yöntemi konak nesnesiyle ilişkilendirmek için kullanılan uygulama tanımlı bir değer döndürür.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Üst öğenin alt öğe listesindeki bir nesnenin dizinini döndürür.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Geçerli betik düğümü tarafından kullanılan komut dosyası dilini döndürür.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|@No__t_0 nesnesinin alt düğümlerinin sayısını döndürür.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Nesnenin üst öğesi olan `IScriptNode` nesnesini döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Yazma Arabirimleri](../../winscript/reference/active-script-authoring-interfaces.md)