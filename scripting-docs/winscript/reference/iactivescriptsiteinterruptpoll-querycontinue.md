---
title: 'Iactivescriptsiteınterruptpoll:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572229"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Bir ana bilgisayarın bir betiğin sonlandırılması gerektiğini belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Çağrı başarılı ve ana bilgisayar betiğin çalışmaya devam etmesine izin veriyor.|  
|`S_FALSE`|Çağrı başarılı ve ana bilgisayar, betiğin sonlanmasına istek.|  
  
## <a name="remarks"></a>Açıklamalar  
 `QueryContinue` yönteminin dönüş değeri `S_OK`olmadığı müddetçe barındırılan betiğin sonlandırılması gerekir. `S_FALSE` dönüş değeri konağın, betiğin sonlandırdığını açıkça istemesi gerektiğini gösterir.  
  
 Çok iş parçacıklı bir konak, bir betiği sonlandırmak için `IActiveScript::InterruptScriptThread` yöntemini kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptsiteınterruptpoll arabirimi](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)