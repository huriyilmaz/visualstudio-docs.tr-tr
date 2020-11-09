---
title: '&lt;Dependency &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
description: Dependency öğesi, uygulama için gerekli olan platformu veya derleme bağımlılığını tanımlar.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7896fa2d39bafc793c5fd74f66f4991cf5e8461
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382955"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency &gt; öğesi (ClickOnce uygulaması)
Uygulama için gerekli olan platformu veya derleme bağımlılığını tanımlar.

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
 `dependency`Öğe gereklidir. Aynı uygulama bildiriminde birden çok örneği olabilir `dependency` .

 `dependency`Öğesi özniteliklere sahip değildir ve aşağıdaki alt öğeleri içerir.

### <a name="dependentos"></a>Bağımlılık TOS
 İsteğe bağlı. Öğesini içerir `osVersionInfo` . `dependentOS`Ve `dependentAssembly` öğeleri birbirini dışlıyor: bir veya diğeri bir öğe için bulunmalıdır `dependency` , ancak her ikisine birden değil.

 `dependentOS` Aşağıdaki öznitelikleri destekler.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`supportUrl`|İsteğe bağlı. Bağımlı platform için bir destek URL 'SI belirtir. Gerekli platform bulunursa, bu URL kullanıcıya gösterilir.|
|`description`|İsteğe bağlı. Öğesi tarafından tanımlanan işletim sistemini, insan tarafından okunabilen biçimde açıklar `dependentOS` .|

### <a name="osversioninfo"></a>osVersionInfo
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `dependentOS` ve `os` öğesi içerir. Bu öğenin öznitelikleri yok.

### <a name="os"></a>os
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `osVersionInfo` . Bu öğe aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`majorVersion`|Gereklidir. İşletim sisteminin ana sürüm numarasını belirtir.|
|`minorVersion`|Gereklidir. İşletim sisteminin ikincil sürüm numarasını belirtir.|
|`buildNumber`|Gereklidir. İşletim sisteminin yapı numarasını belirtir.|
|`servicePackMajor`|Gereklidir. İşletim sisteminin hizmet paketi ana numarasını belirtir.|
|`servicePackMinor`|İsteğe bağlı. İşletim sisteminin hizmet paketi ikincil numarasını belirtir.|
|`productType`|İsteğe bağlı. Ürün türü değerini tanımlar. Geçerli değerler `server` , `workstation` , ve `domainController` . Örneğin, Windows 2000 Professional için bu öznitelik değeri ' dir `workstation` .|
|`suiteType`|İsteğe bağlı. Sistemde veya sistemin yapılandırma türünde bulunan bir ürün paketini tanımlar. Geçerli değerler şunlardır,,,,,,, `backoffice` `blade` `datacenter` `enterprise` `home` `professional` `smallbusiness` `smallbusinessRestricted` ve `terminal` . Örneğin, Windows 2000 Professional için bu öznitelik değeri ' dir `professional` .|

### <a name="dependentassembly"></a>dependentAssembly
 İsteğe bağlı. Öğesini içerir `assemblyIdentity` . `dependentOS`Ve `dependentAssembly` öğeleri birbirini dışlıyor: bir veya diğeri bir öğe için bulunmalıdır `dependency` , ancak her ikisine birden değil.

 `dependentAssembly` Aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|-----------------------| - |
| `dependencyType` | Gereklidir. Bağımlılık türünü belirtir. Geçerli değerler `preprequisite` ve ' dir `install` . `install`Derleme, uygulamanın bir parçası olarak yüklenir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . `prerequisite`Uygulamanın yüklenebilmesi için önce bir derlemenin genel derleme önbelleğinde (GAC) mevcut olması gerekir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . |
| `allowDelayedBinding` | Gereklidir. Derlemenin çalışma zamanında programlı bir şekilde yüklenip yüklenemeyeceğini belirtir. |
| `group` | İsteğe bağlı. `dependencyType`Özniteliği olarak ayarlandıysa `install` , yalnızca istek üzerine yüklenen bir adlandırılmış derleme grubunu belirtir. Daha fazla bilgi için bkz. [Izlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'si Ile isteğe bağlı derlemeleri indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Olarak ayarlıysa `framework` ve özniteliği olarak `dependencyType` ayarlanırsa `prerequisite` , derlemeyi .NET Framework bir parçası olarak belirler. Bu derleme için genel assemby Cache (GAC), .NET Framework 4 ve sonraki sürümlere yüklenirken denetlenmez. |
| `codeBase` | `dependencyType`Özniteliği olarak ayarlandığında gereklidir `install` . Bağımlı derlemenin yolu. Mutlak bir yol veya bildirimin kod tabanına göreli bir yol olabilir. Bu yol, Derleme bildiriminin geçerli olması için geçerli bir URI olmalıdır. |
| `size` | `dependencyType`Özniteliği olarak ayarlandığında gereklidir `install` . Bağımlı derlemenin bayt cinsinden boyutu. |

### <a name="assemblyidentity"></a>AssemblyIdentity
 Gereklidir. Bu öğe, öğesinin bir alt öğesidir `dependentAssembly` ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Uygulamanın adını tanımlar.|
|`version`|Gereklidir. Uygulamanın sürüm numarasını aşağıdaki biçimde belirtir: `major.minor.build.revision`|
|`publicKeyToken`|İsteğe bağlı. `SHA-1`Uygulamanın veya derlemenin imzalandığı ortak anahtarın karma değerinin son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir. Kataloğu imzalamak için kullanılan ortak anahtar 2048 bit veya daha fazla olmalıdır.|
|`processorArchitecture`|İsteğe bağlı. İşlemciyi belirtir. Geçerli değerler `x86` 32 bitlik Windows ve `I64` 64 bit Windows içindir.|
|`language`|İsteğe bağlı. Derlemenin EN-US gibi iki bölüm dil kodunu tanımlar.|

### <a name="hash"></a>hash
 `hash`Öğesi, öğesinin isteğe bağlı bir alt öğesidir `assemblyIdentity` . `hash`Öğesinde hiç öznitelik yok.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] herhangi bir dosyanın dağıtımdan sonra değişmediğinden emin olmak için, bir uygulamadaki tüm dosyaların bir güvenlik denetimi olarak algoritmik karmasını kullanır. `hash`Öğe dahil değilse, bu denetim gerçekleştirilmez. Bu nedenle, `hash` öğesinin atlanması önerilmez.

### <a name="dsigtransforms"></a>dsig: dönüşümler
 `dsig:Transforms`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:Transforms`Öğesinde hiç öznitelik yok.

### <a name="dsigtransform"></a>dsig: dönüştürme
 `dsig:Transform`Öğesi, öğesinin gerekli bir alt öğesidir `dsig:Transforms` . `dsig:Transform`Öğesi aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig: DigestMethod
 `dsig:DigestMethod`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:DigestMethod`Öğesi aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig: DigestValue
 `dsig:DigestValue`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:DigestValue`Öğesinde hiç öznitelik yok. Metin değeri, belirtilen dosya için hesaplanan karmadır.

## <a name="remarks"></a>Açıklamalar
 Uygulamanız tarafından kullanılan tüm derlemeler karşılık gelen bir öğeye sahip olmalıdır `dependency` . Bağımlı derlemeler, genel derleme önbelleğinde platform derlemeleri olarak önceden yüklenmiş olması gereken derlemeleri içermez.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `dependency` bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimindeki öğeleri gösterir. Bu kod örneği, [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.

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
- [\<dependency> dosyalarında](../deployment/dependency-element-clickonce-deployment.md)