---
title: 'Web. config dosyası: Gereç & profili dinamik derlenmiş ASP.NET Web uygulaması'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 6fb67a5b0da186bd87b9e5c39204e3acccc0529f
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775418"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl yapılır: dinamik olarak derlenen ASP.NET Web uygulamalarını işaretlemek ve profil haline getirmek için Web. config dosyalarını değiştirme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları izleme yöntemini kullanarak, dinamik olarak derlenen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarından ayrıntılı zamanlama verileri, .NET bellek ayırma verileri ve .NET nesne yaşam süresi verileri toplayabilirsiniz.

 Bu konu, Web *. config* yapılandırma dosyasının [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarının izleme ve profil oluşturmayı etkinleştirmek için nasıl değiştirileceğini açıklamaktadır.

> [!NOTE]
> Örnekleme profil oluşturma yöntemini kullanırken veya önceden derlenmiş bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] modülünü işaretlemek istediğinizde, *Web. config* dosyasını değiştirmeniz gerekli değildir.

 Bir *Web. config* dosyasının kökü **yapılandırma** öğesidir. Dinamik olarak derlenen bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını işaretlemek ve profil haline getirmek için aşağıdaki öğeleri eklemeniz veya değiştirmeniz gerekir:

- Profil oluşturmayı denetleyen Microsoft. VisualStudio. Enterprise. ASPNetHelper derlemesini tanımlayan bir **yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly** öğesi. **DependentAssembly** öğesi iki alt öğe Içeriyor: **assemblyIdentity** ve **kod temeli**.

- Hedef derleme için profil oluşturucu işlem sonrası derleme adımını tanımlayan bir **Configuration/System. Web/Compilation** öğesi.

- Profil Oluşturma Araçları araçlarının konumunu tanımlayan iki **ekleme** öğesi **Configuration/appSettings** bölümüne eklenir.

  Uygulamanın yapılandırmasını geri yüklemek için kullanabileceğiniz özgün *Web. config* dosyasının bir kopyasını oluşturmanızı öneririz.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>ASPNetHelper derlemesini bir Configuration/runtime/assemblyBinding/dependentAssembly öğesi olarak eklemek için

1. Gerekirse, **çalışma zamanı** öğesini **yapılandırma** öğesinin bir alt öğesi olarak ekleyin; Aksi halde, bir sonraki adıma gidin.

    **Çalışma zamanı** öğesinin öznitelikleri yok. **Yapılandırma** öğesinde yalnızca bir **çalışma zamanı** alt öğesi olabilir.

2. Gerekirse, **assemblyBinding** öğesini **Runtime** öğesinin bir alt öğesi olarak ekleyin; Aksi halde, bir sonraki adıma gidin.

    **Çalışma zamanı** öğesi yalnızca bir **assemblyBinding** öğesine sahip olabilir.

3. **AssemblyBinding** öğesine aşağıdaki öznitelik adını ve değerini ekleyin:

   | Öznitelik adı | Öznitelik değeri |
   |----------------|--------------------------------------|
   | **Özniteliði** | **urn: schemas-microsoft-com: asm. v1** |

4. **AssemblyBinding** öğesinin alt öğesi olarak bir **dependentAssembly** öğesi ekleyin.

    **DependentAssembly** öğesinin hiç özniteliği yok.

5. **DependentAssembly** öğesinin alt öğesi olarak bir **assemblyIdentity** öğesi ekleyin.

6. Aşağıdaki öznitelik adlarını ve değerlerini **assemblyIdentity** öğesine ekleyin:

   | Öznitelik adı | Öznitelik değeri |
   |--------------------| - |
   | **ada** | **Microsoft. VisualStudio. Enterprise. ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **ayarı** | **Kültür** |

7. **DependentAssembly** öğesinin alt öğesi olarak bir **CODEBASE** öğesi ekleyin.

8. Aşağıdaki öznitelik adlarını ve değerlerini **CODEBASE** öğesine ekleyin:

   |Öznitelik adı|Öznitelik değeri|
   |--------------------|---------------------|
   |**version**|**10.0.0.0**|
   |**değerini**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll`, Microsoft. VisualStudio. Enterprise. ASPNetHelper. dll dosyasının URL 'sidir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılan konumda yüklüyse, **href** değeri `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL` olmalıdır

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

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Profil Oluşturucu işlem sonrası adımını Configuration/System. Web/Compilation öğesine eklemek için

1. Gerekirse, **System. Web** öğesini **yapılandırma** öğesinin bir alt öğesi olarak ekleyin; Aksi halde, bir sonraki adıma gidin.

     **System. Web** öğesinin hiç özniteliği yok. **Yapılandırma** öğesinde yalnızca bir **System. Web** alt öğesi olabilir.

2. Gerekirse, **derleme** öğesini **System. Web** öğesinin bir alt öğesi olarak ekleyin; Aksi halde, bir sonraki adıma gidin.

     **System. Web** öğesinde yalnızca bir **derleme** alt öğesi olabilir.

3. Tüm mevcut öznitelikleri **derleme** öğesinden kaldırın ve aşağıdaki öznitelik adını ve değerini ekleyin:

    |Öznitelik adı|Öznitelik değeri|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft. VisualStudio. Enterprise. Common. Aspperformanceınstrumenter, Microsoft. VisualStudio. Enterprise. ASPNetHelper, Version = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|

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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Profil Oluşturucu konum ayarlarını yapılandırma/appSettings öğesine eklemek için

1. Gerekirse, **appSettings** öğesini **yapılandırma** öğesinin bir alt öğesi olarak ekleyin; Aksi halde, bir sonraki adıma gidin.

    **AppSettings** öğesinin hiç özniteliği yok. **Yapılandırma** öğesinde yalnızca bir **appSettings** alt öğesi olabilir.

2. Bir **Add** öğesini **appSettings** öğesinin alt öğesi olarak ekleyin.

3. **Add** öğesine aşağıdaki öznitelik adlarını ve değerleri ekleyin:

   | Öznitelik adı | Öznitelik değeri |
   |----------------| - |
   | **anahtar** | **Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\Vsınstr.exe** |

4. **AppSettings** öğesinin alt öğesi olarak başka bir **Add** öğesi ekleyin.

5. Aşağıdaki öznitelik adlarını ve değerlerini bu **ekleme** öğesine ekleyin:

   |Öznitelik adı|Öznitelik değeri|
   |--------------------|---------------------|
   |**anahtar**|**Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrTools**|
   |**value**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` profil oluşturucu yürütülebilir dosyalarının yoludur. Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

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
 Aşağıda, dinamik olarak derlenen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarının izleme ve profil oluşturma işlemini sağlayan bir *Web. config* dosyası verilmiştir. Bu örnek, değişiklik yapmadan önce dosyada başka bir ayar olmadığını varsayar.

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
- [Nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve bellek verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
