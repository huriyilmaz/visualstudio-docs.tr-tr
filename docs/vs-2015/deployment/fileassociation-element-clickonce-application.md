---
title: '&lt;fileAssociation &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150837"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation &gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamayla ilişkilendirilecek dosya uzantısını tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `fileAssociation`Öğesi isteğe bağlıdır. Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`extension`|Gereklidir. Uygulamayla ilişkilendirilecek dosya uzantısı.|  
|`description`|Gereklidir. Kabuğun kullanması için dosya türünün açıklaması.|  
|`progid`|Gereklidir. Dosya türünü benzersiz bir şekilde tanımlayan ad.|  
|`defaultIcon`|Gereklidir. Bu uzantıya sahip dosyalar için kullanılacak simgeyi belirtir. Simge dosyası, bu öğeyi içeren [ \<assembly> öğe](../deployment/assembly-element-clickonce-application.md) içinde [ \<file> öğesi](../deployment/file-element-clickonce-application.md) kullanılarak belirtilmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, "urn: schemas-microsoft-com: ClickOnce. v1" öğesine bir XML ad alanı başvurusu içermelidir. `<fileAssociation>`Öğesi kullanılırsa, `<application>` onun üst [ \<assembly> öğesinde](../deployment/assembly-element-clickonce-application.md)öğesinden sonra gelmesi gerekir.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] var olan dosya ilişkilendirmelerinin üzerine yazılmayacak. Ancak, bir ClickOnce uygulaması yalnızca geçerli kullanıcı için dosya uzantısını geçersiz kılabilir. ClickOnce uygulaması kaldırıldıktan sonra, ClickOnce kullanıcının dosya ilişkilendirmesini siler ve makine başına ilişki yeniden etkin olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `fileAssociation` kullanılarak dağıtılan bir metin düzenleyici uygulaması için bir uygulama bildirimindeki öğeleri gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu kod örneği, özniteliği için gereken [ \<file> öğesini](../deployment/file-element-clickonce-application.md) de içerir `defaultIcon` .  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
