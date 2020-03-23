---
title: 'Web.Config dosyası: Web uygulaması ASP.NET derlenen enstrüman & profil dinamiği'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775418"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl yapılır: web.config dosyalarını enstrüman ve profil dinamik olarak derlenmiş ASP.NET web uygulamalarıyla değiştirin
Ayrıntılı zamanlama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verileri, .NET bellek ayırma verileri ve dinamik olarak derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarından .NET nesne yaşam boyu verilerini toplamak için Profil Oluşturma Araçları enstrümantasyon yöntemini kullanabilirsiniz.

 Bu konu, Web uygulamalarının enstrümantasyonunu ve profilini etkinleştirmek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için *web.config* yapılandırma dosyasının nasıl değiştirilebildiğini açıklar.

> [!NOTE]
> Örnekleme profil oluşturma yöntemini kullandığınızda veya önceden derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir modül elet etmek istediğinizde *web.config* dosyasını değiştirmeniz gerekmez.

 Bir *web.config* dosyasının kökü **yapılandırma** öğesidir. Dinamik olarak derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir web uygulamasını enstrüman ve profilleeklemek için aşağıdaki öğeleri eklemeniz veya değiştirmeniz gerekir:

- Profil oluşturmayı denetleyen Microsoft.VisualStudio.Enterprise.ASPNetHelper derlemesini tanımlayan bir **yapılandırma/çalışma zamanı/derlemeBağlayıcı/bağımlıDerleme** öğesi. **BağımlıAssembly** öğesi iki alt öğe içerir: **assemblyIdentity** ve **codeBase**.

- Hedef derleme için profil oluşturucu işlem sonrası derleme adımını tanımlayan bir **configuration/system.web/derleme** öğesi.

- **Yapılandırma/uygulama Ayarları** bölümüne Profil Oluşturma Araçları araçlarının konumunu tanımlayan iki **ekleme** öğesi eklenir.

  Uygulamayapılandırmasını geri yüklemek için kullanabileceğiniz orijinal *web.config* dosyasının bir kopyasını oluşturmanızı öneririz.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>ASPNetHelper derlemesini yapılandırma/çalışma süresi/derlemeBağlama/bağımlıAssembly öğesi olarak eklemek için

1. Gerekirse, çalışma **zamanı** öğesini **yapılandırma** öğesinin alt öğesi olarak ekleyin; aksi takdirde, bir sonraki adıma geçin.

    **Çalışma zamanı** öğesi hiçbir öznitelikleri vardır. **Yapılandırma** öğesi yalnızca bir **çalışma zamanı** alt öğesi olabilir.

2. Gerekirse, **çalışma zamanı** öğesinin alt öğesi olarak **derlemeBağlama** öğesi ekleyin; aksi takdirde, bir sonraki adıma geçin.

    **Çalışma zamanı** öğesi yalnızca bir **derlemeBağlama** öğesi olabilir.

3. **DerlemeBağlayıcı** öğeye aşağıdaki öznitelik adı ve değeri ekleyin:

   | Öznitelik Adı | Öznitelik Değeri |
   |----------------|--------------------------------------|
   | **Xmlns** | **vazo:şema-microsoft-com:asm.v1** |

4. **Bağlama** Bağlama öğesinin alt öğesi olarak **bağımlı BirDerleme** öğesi ekleyin.

    **BağımlıAssembly** öğesi hiçbir öznitelikleri vardır.

5. **Bağlı Assembly** öğesinin alt öğesi olarak bir **assemblyIdentity** öğesi ekleyin.

6. **AssemblyIdentity** öğesine aşağıdaki öznitelik adlarını ve değerlerini ekleyin:

   | Öznitelik Adı | Öznitelik Değeri |
   |--------------------| - |
   | **Adı** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **Publickeytoken** | **b03f5f7f11d50a3a** |
   | **kültür** | **Nötr** |

7. **BağımlıAssembly** öğesinin alt öğesi olarak bir **codeBase** öğesi ekleyin.

8. **CodeBase** öğesine aşağıdaki öznitelik adlarını ve değerlerini ekleyin:

   |Öznitelik Adı|Öznitelik Değeri|
   |--------------------|---------------------|
   |**Sürüm**|**10.0.0.0**|
   |**Href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll`Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll dosyasının URL'sidir. Varsayılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] konuma yüklenmişse, **href** değeri`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

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

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Configuration/system.web/compilation öğesine profil oluşturucu işlem sonrası adımeklemek için

1. Gerekirse, **configuration** öğesinin alt öğesi olarak **system.web** öğesini ekleyin; aksi takdirde, bir sonraki adıma geçin.

     **System.web** öğesinin öznitelikleri yoktur. **Yapılandırma** öğesi yalnızca bir **system.web** alt öğesi olabilir.

2. Gerekirse, **system.web** öğesinin bir alt öğesi olarak **derleme** öğesi ekleyin; aksi takdirde, bir sonraki adıma geçin.

     **System.web** öğesi yalnızca bir **derleme** alt öğesi olabilir.

3. Derleme **öğesinden** varolan öznitelikleri kaldırın ve aşağıdaki öznitelik adı ve değeri ekleyin:

    |Öznitelik Adı|Öznitelik Değeri|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Sürüm=10.0.0.0, Kültür=nötr, PublicKeyToken=b03f5f7f11d50a3a**|

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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Yapılandırma/uygulamaAyarlar öğesine profil oluşturucu konum ayarları eklemek için

1. Gerekirse, **yapılandırma** öğesinin alt öğesi olarak **appAyarlar** öğesini ekleyin; aksi takdirde, bir sonraki adıma geçin.

    **appSettings** öğesinin öznitelikleri yoktur. **Yapılandırma** öğesi yalnızca bir **uygulamaAyarlar** alt öğesi olabilir.

2. **appAyarlar** öğesinin alt öğesi olarak bir **ekleme** öğesi ekleyin.

3. Ekle öğesine aşağıdaki öznitelik adlarını ve değerlerini **ekleyin:**

   | Öznitelik Adı | Öznitelik Değeri |
   |----------------| - |
   | **anahtar** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **Değer** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. **appAyarlar** öğesinin alt öğesi olarak başka bir **ekle** öğesi ekleyin.

5. Bu ekle öğesine aşağıdaki öznitelik adlarını ve değerlerini **ekleyin:**

   |Öznitelik Adı|Öznitelik Değeri|
   |--------------------|---------------------|
   |**anahtar**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**Değer**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder`profilci yürütülebilir dosyaların yoludur. Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz.

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
 Aşağıda, dinamik olarak derlenmiş Web uygulamalarının enstrümantasyonunu ve profilini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oluşturmayı sağlayan eksiksiz bir *web.config* dosyası ve bu dosya yer alıyor. Bu örnek, değişiklikten önce dosyada başka ayar olmadığını varsayar.

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
- [Nasıl yapılır: Dinamik olarak derlenmiş bir ASP.NET uygulama ve ayrıntılı zamanlama verileri toplamak enstrüman](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Nasıl yapılır: Dinamik olarak derlenmiş bir ASP.NET uygulama ve bellek verileri toplamak enstrüman](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
