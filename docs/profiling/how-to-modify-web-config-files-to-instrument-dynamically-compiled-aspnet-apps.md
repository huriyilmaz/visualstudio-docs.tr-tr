---
title: Web.Config dosyası - & profili dinamik ASP.NET uygulama
description: Dinamik olarak derlenmiş bir web Visual Studio Profil Oluşturma Araçları zamanlama ve bellek etkinliği verilerini toplamak için ASP.NET öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 92b8acd828a89e1f120a8dc35fa3bc001193f4f4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038805"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl kullanılır: Web web.config dinamik olarak derlenmiş dosyaları ve profillerini ASP.NET değiştirme
Dinamik olarak derlenmiş Web uygulamalarından ayrıntılı zamanlama verileri, .NET bellek ayırma verileri ve .NET nesne yaşam süresi verilerini toplamak için Profil Oluşturma Araçları ölçüm ölçümleme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yöntemini kullanabilirsiniz.

 Bu konu başlığında, Web *uygulamalarınınweb.config* ve profil oluşturmayı etkinleştirmek için uygulama yapılandırma dosyasında nasıl değişiklik [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] olduğu açıklanmıştır.

> [!NOTE]
> Örnekleme profil oluşturma yöntemini *web.config* veya önceden derlenmiş bir modülü takip etmek istediğiniz zaman dosyada değişiklik yapmak zorunda [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] değildir.

 Bir dosyanın *web.config* yapılandırma **öğesidir.** Dinamik olarak derlenmiş bir web uygulamasını takip etmek ve profilini oluşturmak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için aşağıdaki öğeleri eklemeniz veya değiştirmeniz gerekir:

- Microsoft.VisualStudio'yu tanımlayan **bir configuration/runtime/assemblyBinding/dependentAssembly** öğesi. Enterprise. Profil oluşturmayı kontrol eden ASPNetHelper derlemesi. **dependentAssembly öğesi** iki alt öğe içerir: **assemblyIdentity** ve **codeBase.**

- Hedef derleme için işlem sonrası derleme adımını tanımlayan **bir configuration/system.web/compilation** öğesi.

- **yapılandırma/appSettings** bölümüne Profil Oluşturma Araçları araçlarının konumunu belirleyen iki ek öğe eklenir. 

  Uygulamanın yapılandırmasını geri yüklemek için *web.config* dosyanın bir kopyasını oluşturmanızı öneririz.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>ASPNetHelper derlemesini yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly öğesi olarak eklemek için

1. Gerekirse, çalışma **zamanı öğesini** yapılandırma öğesinin alt öğesi **olarak** ekleyin; aksi takdirde, sonraki adıma gidin.

    Çalışma **zamanı** öğesinin özniteliği yoktur. Yapılandırma **öğesinin** yalnızca bir çalışma zamanı **alt** öğesi olabilir.

2. Gerekirse **assemblyBinding öğesini çalışma** zamanı öğesinin alt öğesi **olarak** ekleyin; aksi takdirde, sonraki adıma gidin.

    Çalışma **zamanı** öğesinde yalnızca bir **assemblyBinding öğesi** olabilir.

3. **AssemblyBinding** öğesine aşağıdaki öznitelik adını ve değerini ekleyin:

   | Öznitelik Adı | Öznitelik Değeri |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schemas-microsoft-com:asm.v1** |

4. assemblyBinding öğesinin alt öğesi olarak **dependentAssembly öğesi** ekleyin. 

    **dependentAssembly öğesinin** özniteliği yoktur.

5. **dependentAssembly** öğesinin alt öğesi olarak **assemblyIdentity** öğesi ekleyin.

6. **AssemblyIdentity** öğesine aşağıdaki öznitelik adlarını ve değerlerini ekleyin:

   | Öznitelik Adı | Öznitelik Değeri |
   |--------------------| - |
   | **Adı** | **Microsoft.VisualStudio. Enterprise. ASPNetHelper** |
   | **Publickeytoken** | **b03f5f7f11d50a3a** |
   | **Kültür** | **Nötr** |

7. **dependentAssembly** öğesinin alt öğesi olarak **bir codeBase** öğesi ekleyin.

8. CodeBase öğesine aşağıdaki öznitelik adlarını ve **değerlerini** ekleyin:

   |Öznitelik Adı|Öznitelik Değeri|
   |--------------------|---------------------|
   |**Sürüm**|**10.0.0.0**|
   |**Href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` , dosya url'si Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Varsayılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] konumda yüklüyse **href** değeri şu şekildedir: `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>İşlem sonrası profil oluşturma adımını configuration/system.web/compilation öğesine eklemek için

1. Gerekirse **system.web öğesini** yapılandırma öğesinin alt öğesi **olarak ekleyin;** aksi takdirde, sonraki adıma gidin.

     **system.web öğesinin** özniteliği yoktur. Yapılandırma **öğesinde** yalnızca bir **system.web alt** öğesi olabilir.

2. Gerekirse, derleme **öğesini** **system.web** öğesinin alt öğesi olarak ekleyin; aksi takdirde, sonraki adıma gidin.

     **system.web öğesinin** yalnızca bir derleme **alt** öğesi olabilir.

3. Derleme öğesinden mevcut öznitelikleri **kaldırın** ve aşağıdaki öznitelik adını ve değerini ekleyin:

    |Öznitelik Adı|Öznitelik Değeri|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio. Enterprise. Common.AspPerformanceInstrumenter, Microsoft.VisualStudio. Enterprise. ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
    <configuration>
```

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>configuration/appSettings öğesine profil oluşturma konumu ayarları eklemek için

1. Gerekirse **appSettings öğesini** yapılandırma öğesinin alt öğesi **olarak** ekleyin; aksi takdirde, sonraki adıma gidin.

    **appSettings öğesinin** özniteliği yoktur. Yapılandırma **öğesinde** yalnızca bir **appSettings alt** öğesi olabilir.

2. **appSettings** **öğesinin** alt öğesi olarak bir add öğesi ekleyin.

3. Add öğesine aşağıdaki öznitelik adlarını ve **değerlerini** ekleyin:

   | Öznitelik Adı | Öznitelik Değeri |
   |----------------| - |
   | **Anahtar** | **Microsoft.VisualStudio. Enterprise. AspNetHelper.VsInstrLocation** |
   | **değer** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. **appSettings** **öğesinin** alt öğesi olarak başka bir add öğesi ekleyin.

5. Bu add öğesine aşağıdaki öznitelik adlarını ve **değerlerini** ekleyin:

   |Öznitelik Adı|Öznitelik Değeri|
   |--------------------|---------------------|
   |**Anahtar**|**Microsoft.VisualStudio. Enterprise. AspNetHelper.VsInstrTools**|
   |**değer**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` , profil işleyici yürütülebilir dosyalarının yoludur. Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        . . .
        <system.web>
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Örnek
 Aşağıda, dinamik olarak *derlenmiş Webweb.config* ve profil oluşturma işlemini sağlayan eksiksiz bir derleme dosyası [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] velanmıştır. Bu örnekte, değişiklik öncesinde dosyada başka ayar olmadığını varsayabilirsiniz.

```xml
<?xml version="1.0"?>
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral,
                    PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Dinamik olarak derlenmiş bir ASP.NET uygulamanın ölçümlerini ve ayrıntılı zamanlama verilerini toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Nasıl kullanılır: Dinamik olarak derlenmiş bir ASP.NET uygulamanın ölçümlerini ve bellek verilerini toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
