---
title: Standart ve özel araç takımı yapılandırması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d08a7eb20c01568b3501f16348eb19afdcaefa2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802645"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve Özel Araç Takımı Yapılandırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild Araç Takımı, bir uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara yönelik başvurular içerir. MSBuild standart bir araç takımı içerir, ancak özel araç kümeleri de oluşturabilirsiniz. Araç takımını belirtme hakkında daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)  

## <a name="standard-toolset-configurations"></a>Standart araç takımı yapılandırması  
 MSBuild 12,0 aşağıdaki standart araç kümelerini içerir:  

| ToolsVersion | Araç takımı yolu (Msbuildaraçları yolu veya MSBuildBinPath derleme özelliğinde belirtilen şekilde) |
|--------------|--------------------------------------------------------------------------------------|
|     2.0      |           *Windows yükleme yolu*\Microsoft.NET\Framework\v2.0.50727\            |
|     3,5      |              *Windows yükleme yolu*\Microsoft.NET\Framework\v3.5\               |
|     4.0      |           *Windows yükleme yolu*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *% ProgramFiles%* \Msbuild\12.0\Bin                           |

 `ToolsVersion`Değer, Visual Studio 'nun oluşturduğu bir proje tarafından kullanılan araç takımını belirler. [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]Varsayılan değer olan "12,0" (proje dosyasında belirtilen sürüm ne olduğuna bakılmaksızın), ancak komut isteminde **/araçları sürüm** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmek için diğer yollar hakkında daha fazla bilgi için `ToolsVersion` bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).  

 `ToolsVersion`Belirtilmezse, kayıt defteri anahtarı **HKEY_LOCAL_MACHINE \software\microsoft\msbuild \\<sürüm numarası \> \defaulttools\version** , `ToolsVersion` her zaman 2,0 olan öğesini tanımlar.  

 Aşağıdaki kayıt defteri anahtarları MSBuild.exe yükleme yolunu belirtir.  

|Kayıt Defteri Anahtarı|Anahtar adı|Dize anahtarı değeri|  
|------------------|--------------|----------------------|  
|\ HKEY_LOCAL_MACHINE \Software\microsoft\msbuild\tools\versions\2.0 \| msbuildaraçları yolu|.NET Framework 2,0 yüklemesi yolu|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\3.5 \| msbuildaraçları yolu|.NET Framework 3,5 yüklemesi yolu|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\4.0 \| msbuildaraçları yolu|.NET Framework 4 yüklemesi yolu|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\12.0 \| msbuildaraçları yolu|MSBuild yüklemesi yolu|  

### <a name="sub-toolsets"></a>Alt araç kümeleri  
 Önceki tablodaki kayıt defteri anahtarının bir alt anahtarı varsa, MSBuild bunu bir alt araç takımının yolunu belirlemede ana araç takımının yolunu geçersiz kılabilir. Aşağıdaki alt anahtar bir örnektir:  

 \ HKEY_LOCAL_MACHINE \Software\microsoft\msbuild\tools\versions\12.0\12.0  

 Hem temel araç takımı hem de seçili alt araç takımı 'nda herhangi bir özellik tanımlanırsa, alt araç takımının özellik tanımları kullanılır. Örneğin, MSBuild 4,0 araç takımı `SDK40ToolsPath` 7.0 a SDK 'sını işaret etmek üzere tanımlar, ancak MSBuild 4.0 \ 11.0 araç takımı, 8.0 'ı BIR SDK 'ya işaret etmek için aynı özelliği tanımlar. `VisualStudioVersion`Ayarı ayarlanmamışsa, `SDK40ToolsPath` 7.0 a 'ya işaret edecektir, ancak `VisualStudioVersion` 11,0 olarak ayarlanırsa, özellik 8.0 a 'ya işaret edecektir.  

 `VisualStudioVersion`Build özelliği bir alt araç takımının etkin olup olmadığını gösterir. Örneğin, `VisualStudioVersion` "12,0" değeri MSBuild 12,0 alt araç takımını belirtir. Daha fazla bilgi için araç kümesi 'nin [(Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.  

> [!NOTE]
> Bu ayarları değiştirmekten kaçınmanızı öneririz. Bununla birlikte, sonraki bölümde açıklandığı gibi kendi ayarlarınızı ekleyebilir ve bilgisayar genelindeki özel araç takımı tanımlarını tanımlayabilirsiniz.  

## <a name="custom-toolset-definitions"></a>Özel araç takımı tanımları  
 Standart bir araç takımı derleme gereksinimlerinizi yerine getirmiyorsa, özel bir araç takımı oluşturabilirsiniz. Örneğin, proje derlemek için ayrı bir sisteme sahip olmanız gereken bir derleme Laboratuvarı senaryonuz olabilir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] . Özel bir araç kümesi kullanarak, `ToolsVersion` proje oluştururken veya MSBuild.exe çalıştırdığınızda özniteliğe özel değerler atayabilirsiniz. Bunu yaparak, bu özelliği, bu `$(MSBuildToolsPath)` dizindeki. targets dosyalarını içeri aktarmak ve bu araç takımını kullanan herhangi bir proje için kullanılabilecek kendi özel araç takımı özelliklerinizi tanımlamak için de kullanabilirsiniz.  

 MSBuild.exe yapılandırma dosyasında (veya kullanıyorsanız, MSBuild altyapısını barındıran özel araç için) özel bir araç kümesi belirtin. Örneğin, MSBuild.exe yapılandırma dosyası, araçları sürüm 12,0 ' nin varsayılan davranışını geçersiz kılmak üzere kullandıysanız aşağıdaki araç kümesi tanımını içerebilir.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` Ayrıca yapılandırma dosyasında aşağıdaki gibi tanımlanmalıdır.  

```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  

> [!NOTE]
> Doğru okunalmak için, `<configSections>` bölümündeki ilk alt bölüm olmalıdır `<configuration>` .  

 `ToolsetConfigurationSection` , özel yapılandırma için herhangi bir MSBuild ana bilgisayarı tarafından kullanılabilen özel bir yapılandırma bölümüdür. Özel bir araç kümesi kullanıyorsanız, yapılandırma dosyası girdilerini sağlama dışında bir konağın derleme altyapısını başlatmak için bir şey yapması gerekmez. Kayıt defterindeki girişleri tanımlayarak, MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve tüm MSBuild konakları için geçerli olan bilgisayar genelindeki araç kümelerini belirtebilirsiniz.  

> [!NOTE]
> Bir yapılandırma dosyası, `ToolsVersion` kayıt defterinde önceden tanımlanmış olan ayarları tanımlıyorsa, iki tanım birleştirilmez. Yapılandırma dosyasındaki tanım öncelik kazanır ve kayıt defterindeki ayarlar `ToolsVersion` yoksayılır.  

 Aşağıdaki özellikler, `ToolsVersion` projelerde kullanılan değerine özgüdür:  

- **$ (MSBuildBinPath)** , `ToolsPath` kayıt defterinde veya tanımlanan yapılandırma dosyasında belirtilen değere ayarlanır `ToolsVersion` . `$(MSBuildToolsPath)`Kayıt defterindeki veya yapılandırma dosyasındaki ayar, çekirdek görevlerinin ve hedeflerin konumunu belirtir. Proje dosyasında, bu $ (MSBuildBinPath) özelliğine ve ayrıca $ (Msbuildaraçları yolu) özelliğine eşlenir.  

- `$(MSBuildToolsPath)` , yapılandırma dosyasında belirtilen Msbuildaraçları yol özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik yerini alır `$(MSBuildBinPath)` . Ancak, `$(MSBuildBinPath)` uyumluluk için ileriye doğru yürütülür.) Özel bir araç takımı, her `$(MSBuildToolsPath)` `$(MSBuildBinPath)` ikisi de aynı değere sahip olmadıkları takdirde, ya da öğesini tanımlamalıdır.  

  Ayrıca, Msbuildaraçları Path özelliğini eklemek için kullandığınız söz dizimini kullanarak yapılandırma dosyasına özel, araçları sürümüne özel özellikler ekleyebilirsiniz. Bu özel özellikleri proje dosyası için kullanılabilir hale getirmek için, yapılandırma dosyasında belirtilen değerin adı ile aynı adı kullanın. Yapılandırma dosyasında araç kümelerini tanımlayabilir, ancak alt araç kümelerini tanımlayabilirsiniz.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
