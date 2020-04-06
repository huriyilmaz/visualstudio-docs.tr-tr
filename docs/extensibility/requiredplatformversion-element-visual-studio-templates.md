---
title: GerekliPlatformVersion Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701491"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>GerekliPlatformVersion öğesi (Visual Studio şablonları)
Proje şablonunun doğru çalışmasını gerektiren işletim sisteminin minimum sürümünü belirtir. Bu öğe, uygulama oluşturan [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] proje şablonları için kullanılır.

 Değer `RequiredPlatformVersion` doğrudan işletim sisteminin sürümü ile karşılaştırılır. İşletim `RequiredPlatformVersion` sistemi sürümünden daha yüksekse, şablon **Yeni Proje** iletişim kutusunda görünmez. 6.2.0 [!INCLUDE[win8](../debugger/includes/win8_md.md)] olarak ayarlayın, `RequiredPlatformVersion` için veya daha yüksek bir şablon belirtmek için. 6.3.0 [!INCLUDE[win81](../debugger/includes/win81_md.md)] olarak ayarlayın, `RequiredPlatformVersion` için veya daha yüksek bir şablon belirtmek için.

 =8 belirten `RequiredPlatformVersion`şablonlar önceki müşteri [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] şablonlarıyla uyumludur.

 VSTemplate ŞablonVerileri ..... TargetPlatformName GerekliPlatformVersion

## <a name="syntax"></a>Sözdizimi

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Yok.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Proje şablonunun hedeflenebilen platformu belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar
 Bu metin, şablon tarafından gerekli minimum işletim sistemi sürümünü belirtir.

## <a name="example"></a>Örnek
 Bu örnek, proje şablonu [!INCLUDE[win8](../debugger/includes/win8_md.md)] veya daha sonra hedefleri belirtir.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [TargetPlatformName öğesi (Visual Studio şablonları)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
