---
title: IActiveScriptSiteDebug32 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835270"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Arabirimi
Akıllı Konaklar `IActiveScriptSiteDebug32` belge yönetimi gerçekleştirmek ve hata ayıklamaya katılmak için arabirimi uygular. `IActiveScriptSite`Nesnesi genellikle arabirimin bir uygulamasını sağlar `IActiveScriptSiteDebug32` . Bu işlem yapıldıktan sonra, `IActiveScriptSite::QueryInterface` arabirimini almak için yöntemini çağırın `IActiveScriptSiteDebug32` .  
  
 Kaynağından devralınan yöntemlere ek olarak `IUnknown` , `IActiveScriptSiteDebug32` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Bu betik sitesiyle ilişkili hata ayıklama uygulama nesnesini döndürür.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Temsilci seçmek için dil motoru tarafından kullanılır `IDebugCodeContext::GetSourceContext` .|