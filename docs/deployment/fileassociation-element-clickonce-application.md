---
title: '&lt;fileassociation &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
description: FileAssociation öğesi uygulamayla ilişkilendirilecek bir dosya uzantısını tanımlar. FileAssociation öğesi isteğe bağlıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a17f239b7abaf981416b86ec785cb7a4d7e95e8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160822"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileassociation &gt; öğesi (ClickOnce uygulaması)
Uygulamayla ilişkilendirilecek dosya uzantısını tanımlar.

## <a name="syntax"></a>Syntax

```xml
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

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] var olan dosya ilişkilendirmelerinin üzerine yazılmayacak. ancak, bir ClickOnce uygulaması yalnızca geçerli kullanıcının dosya uzantısını geçersiz kılabilir. ClickOnce uygulama kaldırıldıktan sonra, ClickOnce kullanıcının dosya ilişkilendirmesini siler ve makine başına ilişki yeniden etkin olur.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `fileAssociation` kullanılarak dağıtılan bir metin düzenleyici uygulaması için bir uygulama bildirimindeki öğeleri gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, özniteliği için gereken [ \<file> öğesini](../deployment/file-element-clickonce-application.md) de içerir `defaultIcon` .

```xml
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

## <a name="see-also"></a>Ayrıca bkz.
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)