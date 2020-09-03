---
title: '&lt;AssemblyIdentity &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155722"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity &gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanın birincil derlemesini tanımlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `assemblyIdentity`Öğe gereklidir. Alt öğesi içermez ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gereklidir. Bilgilendirici amaçlar için dağıtımın okunabilir adını tanımlar.<br /><br /> `name`Tek veya çift tırnak gibi özel karakterler içeriyorsa, uygulama etkinleştiremeyebilir.|  
|`version`|Gereklidir. Derlemenin sürüm numarasını şu biçimde belirtir: `major.minor.build.revision` .<br /><br /> Bu değer, bir uygulama güncelleştirmesinin tetiklenmesi için güncelleştirilmiş bir bildirimde arttırılmalıdır.|  
|`publicKeyToken`|Gereklidir. Dağıtım bildiriminin imzalandığı, ortak anahtarın SHA-1 karma değerinin son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir. İmzalamak için kullanılan ortak anahtar 2048 bit veya daha büyük olmalıdır.<br /><br /> Bir derlemeyi imzalamak önerilse ancak isteğe bağlı olsa da, bu öznitelik gereklidir. Bir bütünleştirilmiş kod imzasız ise, kendinden imzalı bir derlemeden bir değer kopyalamanız veya tümü sıfırlardan oluşan bir "kukla" değeri kullanmanız gerekir.|  
|`processorArchitecture`|Gereklidir. İşlemciyi belirtir. Geçerli değerler `msil` tüm işlemciler için `x86` 32 bit windows, `IA64` 64 bit Windows için ve `Itanium` Intel 64 bit Itanium işlemcilere yöneliktir.|  
|`type`|Gereklidir. Windows yan yana yükleme teknolojisiyle uyumluluk için. İzin verilen tek değer `win32` .|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir `assemblyIdentity` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bu kod örneği, [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> Dosyalarında](../deployment/assemblyidentity-element-clickonce-application.md)
