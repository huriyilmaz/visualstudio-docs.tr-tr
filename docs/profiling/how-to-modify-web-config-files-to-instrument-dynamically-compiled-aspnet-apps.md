---
title: Web.Config dosya gereci & profili dinamik derlenmiş ASP.NET Web uygulaması
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 8ed2d8e8cc62d26f9d63a8a675301c78fc35c51a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331503"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl yapılır: dinamik olarak derlenen ASP.NET Web uygulamalarını işaretlemek ve profil haline getirmek için web.config dosyalarını değiştirme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Dinamik olarak derlenen Web uygulamalarından ayrıntılı zamanlama verileri, .net bellek ayırma verileri ve .NET nesne yaşam süresi verilerini toplamak için profil oluşturma araçları izleme yöntemini kullanabilirsiniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Bu konuda, Web uygulamalarının izleme ve profil oluşturma özelliğini etkinleştirmek için *web.config* yapılandırma dosyasının nasıl değiştirileceği açıklanmaktadır [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

> [!NOTE]
> Örnekleme profil oluşturma yöntemini kullanırken veya önceden derlenmiş bir modülü işaretlemek istediğinizde *web.config* dosyasını değiştirmeniz gerekli değildir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 *web.config* bir dosyanın kökü **yapılandırma** öğesidir. Dinamik olarak derlenen bir Web uygulamasını işaretlemek ve profil haline getirmek için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aşağıdaki öğeleri eklemeniz veya değiştirmeniz gerekir:

- Profil oluşturmayı denetleyen Microsoft. VisualStudio. Enterprise. ASPNetHelper derlemesini tanımlayan bir **yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly** öğesi. **DependentAssembly** öğesi iki alt öğe Içeriyor: **assemblyIdentity** ve **kod temeli**.

- Hedef derleme için profil oluşturucu işlem sonrası derleme adımını tanımlayan bir **Configuration/System. Web/Compilation** öğesi.

- Profil Oluşturma Araçları araçlarının konumunu tanımlayan iki **ekleme** öğesi **Configuration/appSettings** bölümüne eklenir.

  Uygulamanın yapılandırmasını geri yüklemek için kullanabileceğiniz özgün *web.config* dosyasının bir kopyasını oluşturmanızı öneririz.

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
   |**Sürüm**|**10.0.0.0**|
   |**değerini**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll dosya URL 'sidir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Varsayılan konumda yüklüyse, **href** değeri şu şekilde olmalıdır`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

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
   | **deeri** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. **AppSettings** öğesinin alt öğesi olarak başka bir **Add** öğesi ekleyin.

5. Aşağıdaki öznitelik adlarını ve değerlerini bu **ekleme** öğesine ekleyin:

   |Öznitelik adı|Öznitelik değeri|
   |--------------------|---------------------|
   |**anahtar**|**Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrTools**|
   |**deeri**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` , profil oluşturucu yürütülebilir dosyalarının yoludur. Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

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
 Aşağıda, dinamik olarak derlenen Web uygulamalarının izleme ve profil oluşturmayı sağlayan bir bütün *web.config* dosyası verilmiştir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Bu örnek, değişiklik yapmadan önce dosyada başka bir ayar olmadığını varsayar.

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
