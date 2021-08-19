---
title: '&lt;dependency &gt; Öğesi (ClickOnce Application) | Microsoft Docs'
description: Bağımlılık öğesi, uygulama için gerekli olan bir platform veya derleme bağımlılığını tanımlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6dc3d0ad29597e801f4f28cc2b80335cab7240b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160887"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dependency &gt; öğesi (ClickOnce uygulama)
Uygulama için gereken bir platform veya derleme bağımlılığını tanımlar.

## <a name="syntax"></a>Syntax

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `dependency`öğesi gereklidir. Aynı uygulama bildiriminde birden `dependency` çok örneği olabilir.

 öğesinin `dependency` özniteliği yoktur ve aşağıdaki alt öğeleri içerir.

### <a name="dependentos"></a>dependentOS
 İsteğe bağlı. öğesini `osVersionInfo` içerir. ve öğeleri birbirini dışlar: bir öğe için bir veya diğerinin mevcut olması `dependentOS` `dependentAssembly` `dependency` gerekir, ancak her ikisi için de mevcut değildir.

 `dependentOS` aşağıdaki öznitelikleri destekler.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`supportUrl`|İsteğe bağlı. Bağımlı platform için bir destek URL'si belirtir. Gerekli platform bulunursa bu URL kullanıcıya gösterilir.|
|`description`|İsteğe bağlı. öğesi tarafından açıklanan işletim sistemini insan tarafından okunabilir bir şekilde `dependentOS` açıklar.|

### <a name="osversioninfo"></a>osVersionInfo
 Gereklidir. Bu öğe, öğesinin alt `dependentOS` öğesidir ve öğesini `os` içerir. Bu öğenin özniteliği yoktur.

### <a name="os"></a>os
 Gereklidir. Bu öğe, öğesinin alt `osVersionInfo` öğesidir. Bu öğe aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`majorVersion`|Gereklidir. Işletim sistemi ana sürüm numarasını belirtir.|
|`minorVersion`|Gereklidir. Işletim sistemi alt sürüm numarasını belirtir.|
|`buildNumber`|Gereklidir. Işletim sistemi derleme numarasını belirtir.|
|`servicePackMajor`|Gereklidir. Hizmet paketinin işletim sistemi ana sayısını belirtir.|
|`servicePackMinor`|İsteğe bağlı. Hizmet paketi ikincil işletim sistemi numarasını belirtir.|
|`productType`|İsteğe bağlı. Ürün türü değerini tanımlar. Geçerli değerler `server` : , ve `workstation` `domainController` . Örneğin, 2000 Windows 2000 Professional, bu öznitelik `workstation` değeridir.|
|`suiteType`|İsteğe bağlı. Sistemde veya sistemin yapılandırma türünde kullanılabilen bir ürün paketini tanımlar. Geçerli değerler `backoffice` : , , , , , , , ve `blade` `datacenter` `enterprise` `home` `professional` `smallbusiness` `smallbusinessRestricted` `terminal` . Örneğin, 2000 Windows 2000 Professional, bu öznitelik `professional` değeridir.|

### <a name="dependentassembly"></a>Dependentassembly
 İsteğe bağlı. öğesini `assemblyIdentity` içerir. ve öğeleri birbirini dışlar: bir öğe için bir veya diğerinin mevcut olması `dependentOS` `dependentAssembly` `dependency` gerekir, ancak her ikisi için de mevcut değildir.

 `dependentAssembly` aşağıdaki özniteliklere sahip.

| Öznitelik | Açıklama |
|-----------------------| - |
| `dependencyType` | Gereklidir. Bağımlılık türünü belirtir. Geçerli değerler ve `preprequisite` `install` değerleridir. `install`Derleme, uygulamanın bir parçası olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklenir. Uygulamanın `prerequisite` yüklenmeden önce genel derleme önbelleğinde (GAC) bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] derleme olması gerekir. |
| `allowDelayedBinding` | Gereklidir. Derlemenin çalışma zamanında program aracılığıyla yüklenemiyor olup olmadığını belirtir. |
| `group` | İsteğe bağlı. özniteliği `dependencyType` olarak `install` ayarlanırsa, yalnızca isteğe bağlı olarak yükleme yapılan adlandırılmış bir derleme grubu olarak ayarlanır. Daha fazla bilgi için, [bkz. Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> olarak `framework` ayarlanırsa ve `dependencyType` özniteliği olarak `prerequisite` ayarlanırsa, derlemeyi derlemenin bir parçası olarak .NET Framework. Genel assemby önbelleği (GAC), 4 ve sonraki sürümlere yüklerken bu .NET Framework denetlenmez. |
| `codeBase` | Özniteliği olarak `dependencyType` ayarlanırken `install` gereklidir. Bağımlı derlemenin yolu. Mutlak bir yol veya bildirimin kod tabanına göre bir yol olabilir. Derleme bildiriminin geçerli olması için bu yol geçerli bir URI olmalıdır. |
| `size` | Özniteliği olarak `dependencyType` ayarlanırken `install` gereklidir. Bağımlı derlemenin bayt cinsinden boyutu. |

### <a name="assemblyidentity"></a>Assemblyıdentity
 Gereklidir. Bu öğe, öğesinin alt `dependentAssembly` öğesidir ve aşağıdaki özniteliklere sahip olur.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Uygulamanın adını tanımlar.|
|`version`|Gereklidir. Uygulamanın sürüm numarasını aşağıdaki biçimde belirtir: `major.minor.build.revision`|
|`publicKeyToken`|İsteğe bağlı. Uygulamanın veya derlemenin imza altında olduğu ortak anahtarın karma değerinin son 8 baytı temsil eden 16 karakterlik onaltılık `SHA-1` dizeyi belirtir. Kataloğu imzalamak için kullanılan ortak anahtar 2048 bit veya daha fazla olabilir.|
|`processorArchitecture`|İsteğe bağlı. İşlemciyi belirtir. Geçerli değerler `x86` 32 bitlik Windows `I64` ve 64 bit Windows.|
|`language`|İsteğe bağlı. Derlemenin EN-US gibi iki bölüm dil kodunu tanımlar.|

### <a name="hash"></a>hash
 öğesi, `hash` öğesinin isteğe bağlı bir alt `assemblyIdentity` öğesidir. öğesinin `hash` özniteliği yoktur.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , dağıtımdan sonra dosyalardan hiçbirinin değişmediğini sağlamak için güvenlik denetimi olarak bir uygulamanın tüm dosyalarının algoritma karması kullanır. Öğe `hash` dahil yoksa, bu denetim gerçekleştirlanmaz. Bu nedenle, `hash` öğesinin yok kullanılması önerilmez.

### <a name="dsigtransforms"></a>dsig:Transforms
 `dsig:Transforms`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesinin `dsig:Transforms` özniteliği yoktur.

### <a name="dsigtransform"></a>dsig:Transform
 `dsig:Transform`öğesi, öğesinin gerekli bir alt `dsig:Transforms` öğesidir. öğesi `dsig:Transform` aşağıdaki özniteliklere sahip.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosyanın özetini hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` değeridir. |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesi `dsig:DigestMethod` aşağıdaki özniteliklere sahip.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosyanın özetini hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` değeridir. |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesinin `dsig:DigestValue` özniteliği yoktur. Metin değeri, belirtilen dosya için hesaplanan karmadır.

## <a name="remarks"></a>Açıklamalar
 Uygulamanız tarafından kullanılan tüm derlemelerin karşılık gelen bir öğesi `dependency` olması gerekir. Bağımlı derlemeler, platform derlemeleri olarak genel derleme önbelleğine önceden yüklenmiş olması gereken derlemeleri içermez.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir `dependency` uygulama bildiriminde öğeleri [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gösterir. Bu kod örneği, uygulama uygulama bildirimi konusu için sağlanan [daha ClickOnce bir örnektir.](../deployment/clickonce-application-manifest.md)

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [\<dependency> Öğe](../deployment/dependency-element-clickonce-deployment.md)