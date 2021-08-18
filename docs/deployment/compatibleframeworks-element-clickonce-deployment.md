---
title: '&lt;compatibleçerçeveleri &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: compatibleçerçeveleri öğesi, bu uygulamanın yükleyebildiği ve çalışacağı .NET Framework sürümlerini tanımlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ed84d7f7ed60a95baba293a33059a05093400bbb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138945"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleçerçeveleri &gt; öğesi (ClickOnce dağıtım)
bu uygulamanın yükleyebildiği ve çalıştırılacağı .NET Framework sürümlerini tanımlar.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) , `compatibleFrameworks` [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)kullanılarak bir sertifikayla imzalanmış bir uygulama bildirimini kaydetme sırasında öğeyi desteklemez. Bunun yerine [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)kullanmanız gerekir.

## <a name="syntax"></a>Syntax

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `compatibleFrameworks`öğesi, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 4 veya üzeri tarafından belirtilen çalışma zamanını hedefleyen dağıtım bildirimleri için gereklidir. `compatibleFrameworks`öğesi, `framework` bu uygulamanın çalıştırılabileceği .NET Framework sürümlerini belirten bir veya daha fazla öğe içeriyor. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Çalışma zamanı, bu listedeki ilk kullanılabilir uygulamayı çalıştırır `framework` .

 Aşağıdaki tabloda, `compatibleFrameworks` öğesinin desteklediği özniteliği listelenmektedir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`S` `upportUrl`|İsteğe bağlı. tercih edilen uyumlu .NET Framework sürümünün indirilebileceği bir URL belirtir.|

## <a name="framework"></a>çerçeve
 Gereklidir. Aşağıdaki tablo, `framework` öğesinin desteklediği öznitelikleri listeler.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`targetVersion`|Gereklidir. Hedef .NET Framework sürüm numarasını belirtir.|
|`profile`|Gereklidir. Hedef .NET Framework profilini belirtir.|
|`supportedRuntime`|Gereklidir. Hedef .NET Framework ilişkili çalışma zamanının sürüm numarasını belirtir.|

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde bir `compatibleFrameworks` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu dağıtım üzerinde çalışabilir [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . .NET Framework 4 ' te de çalıştırılabilir çünkü bir üst kümesidir [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)