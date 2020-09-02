---
title: '&lt;Compatibleçerçeveleri &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675424"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;Compatibleçerçeveleri &gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu uygulamanın yükleyebildiği ve çalıştırılacağı .NET Framework sürümlerini tanımlar.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) , `compatibleFrameworks` [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)kullanılarak bir sertifikayla imzalanmış bir uygulama bildirimini kaydetme sırasında öğeyi desteklemez. Bunun yerine [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)kullanmanız gerekir.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 `compatibleFrameworks`Öğesi, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] veya üzeri tarafından sağlanmış olan çalışma zamanını hedefleyen dağıtım bildirimleri için gereklidir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] . `compatibleFrameworks`Öğesi, `framework` Bu uygulamanın çalıştırılabileceği .NET Framework sürümlerini belirten bir veya daha fazla öğe içeriyor. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Çalışma zamanı, bu listedeki ilk kullanılabilir uygulamayı çalıştırır `framework` .  
  
 Aşağıdaki tabloda, `compatibleFrameworks` öğesinin desteklediği özniteliği listelenmektedir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`S` `upportUrl`|İsteğe bağlı. Tercih edilen uyumlu .NET Framework sürümünün indirilebileceği bir URL belirtir.|  
  
## <a name="framework"></a>çerçeve  
 Gereklidir. Aşağıdaki tablo, `framework` öğesinin desteklediği öznitelikleri listeler.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`targetVersion`|Gereklidir. Hedef .NET Framework sürüm numarasını belirtir.|  
|`profile`|Gereklidir. Hedef .NET Framework profilini belirtir.|  
|`supportedRuntime`|Gereklidir. Hedef .NET Framework ilişkili çalışma zamanının sürüm numarasını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir `compatibleFrameworks` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu dağıtım üzerinde çalışabilir [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Bir üst kümesi olduğundan, üzerinde de çalıştırılabilir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Bildirimi](../deployment/clickonce-deployment-manifest.md)
