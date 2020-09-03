---
title: '&lt;Assembly &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155730"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly &gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dağıtım bildirimi için en üst düzey öğe.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `assembly`Öğesi kök öğesidir ve gereklidir. İlk kapsanan öğesi bir `assemblyIdentity` öğesi olmalıdır. Bildirim öğeleri şu ad alanlarında olmalıdır: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` , ve `http://www.w3.org/2000/09/xmldsig#` . Derlemenin alt öğeleri de bu ad alanlarında, devralmayla veya etiketlemeyle olmalıdır.  
  
 `assembly`Öğesi aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`manifestVersion`|Gereklidir. Bu özniteliğin olarak ayarlanması gerekir `1.0` .|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `assembly` kullanılarak dağıtılan bir uygulama için dağıtım bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu kod örneği, [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> Dosyalarında](../deployment/assembly-element-clickonce-application.md)
