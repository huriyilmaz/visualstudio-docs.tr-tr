---
title: Standart ve özel araç takımı yapılandırması | Microsoft Docs
description: Bir uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara başvurular içeren standart ve özel MSBuild Araç kümeleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70b0d85ea161a3f938013c01702dd2ccce73a31d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956106"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve özel araç takımı yapılandırması

MSBuild Araç Takımı, bir uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara yönelik başvurular içerir. MSBuild standart bir araç takımı içerir, ancak özel araç kümeleri de oluşturabilirsiniz. Araç takımını belirtme hakkında daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standart araç takımı yapılandırması

::: moniker range=">=vs-2019"
 MSBuild 16,0 aşağıdaki standart araç kümelerini içerir:

|ToolsVersion|Araç takımı yolu (Msbuildaraçları yolu veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|Geçerli|*\<Visual Studio installation path>\MSBuild\Current\bin*|

 `ToolsVersion`Değer, Visual Studio 'nun oluşturduğu bir proje tarafından kullanılan araç takımını belirler. Visual Studio 2019 ' de, varsayılan değer "geçerli" (proje dosyasında belirtilen sürüm değildir), ancak komut isteminde **/, sürüm** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmek için diğer yollar hakkında daha fazla bilgi için `ToolsVersion` bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15,0 aşağıdaki standart araç kümelerini içerir:

|ToolsVersion|Araç takımı yolu (Msbuildaraçları yolu veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Visual Studio installation path>\MSBuild\15.0\bin*|

 `ToolsVersion`Değer, Visual Studio 'nun oluşturduğu bir proje tarafından kullanılan araç takımını belirler. Visual Studio 2017 ' de, varsayılan değer "15,0" ' dir (proje dosyasında belirtilen sürümden bağımsız olarak), ancak komut isteminde **/araçları sürüm** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmek için diğer yollar hakkında daha fazla bilgi için `ToolsVersion` bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Visual Studio 2017 ve sonraki sürümleri, MSBuild yolu için bir kayıt defteri anahtarı kullanmaz. Visual Studio 2017 ile yüklenen 15,0 ' den önceki MSBuild sürümleri için aşağıdaki kayıt defteri anahtarları MSBuild.exe yükleme yolunu belirtir.

|Kayıt defteri anahtarı|Anahtar adı|Dize anahtarı değeri|
|------------------|--------------|----------------------|
|**\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Msbuild\tools\versions\2.0\\** |**Msbuildaraçları yolu**|**.NET Framework 2,0 yüklemesi yolu**|
|**\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Msbuild\tools\versions\3.5\\** |**Msbuildaraçları yolu**|**.NET Framework 3,5 yüklemesi yolu**|
|**\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Msbuild\tools\versions\4.0\\** |**Msbuildaraçları yolu**|**.NET Framework 4 yüklemesi yolu**|

### <a name="sub-toolsets"></a>Alt araç kümeleri

 Önceki tablodaki kayıt defteri anahtarının bir alt anahtarı varsa, MSBuild bunu üst araç takımından yolu geçersiz kılan bir alt araç takımının yolunu belirlemede kullanır. Aşağıdaki alt anahtar bir örnektir:

 **\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Hem temel araç takımı hem de seçili alt araç takımı 'nda herhangi bir özellik tanımlanırsa, alt araç takımının özellik tanımları kullanılır. Örneğin, MSBuild 4,0 araç takımı `SDK40ToolsPath` 7.0 a SDK 'sını işaret etmek üzere tanımlar, ancak MSBuild 4.0 \ 11.0 araç takımı, 8.0 'ı BIR SDK 'ya işaret etmek için aynı özelliği tanımlar. `VisualStudioVersion`Ayarı ayarlanmamışsa, `SDK40ToolsPath` 7.0 a 'ya işaret edecektir, ancak `VisualStudioVersion` 11,0 olarak ayarlanırsa, özellik 8.0 a 'ya işaret edecektir.

 `VisualStudioVersion`Build özelliği bir alt araç takımının etkin olup olmadığını gösterir. Örneğin, `VisualStudioVersion` "12,0" değeri MSBuild 12,0 alt araç takımını belirtir. Daha fazla bilgi için araç kümesi 'nin [(Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.

> [!NOTE]
> Bu ayarları değiştirmekten kaçınmanızı öneririz. Bununla birlikte, sonraki bölümde açıklandığı gibi kendi ayarlarınızı ekleyebilir ve bilgisayar genelindeki özel araç takımı tanımlarını tanımlayabilirsiniz.

## <a name="custom-toolset-definitions"></a>Özel araç takımı tanımları

 Standart bir araç takımı derleme gereksinimlerinizi yerine getirmiyorsa, özel bir araç takımı oluşturabilirsiniz. Örneğin, C++ projeleri oluşturmak için ayrı bir sisteme sahip olmanız gereken bir derleme Laboratuvarı senaryonuz olabilir. Özel bir araç kümesi kullanarak, `ToolsVersion` proje oluştururken veya *MSBuild.exe* çalıştırdığınızda özniteliğe özel değerler atayabilirsiniz. Bunu yaparak, bu özelliği, bu `$(MSBuildToolsPath)` dizindeki *. targets* dosyalarını içeri aktarmak ve bu araç takımını kullanan herhangi bir proje için kullanılabilecek kendi özel araç takımı özelliklerinizi tanımlamak için de kullanabilirsiniz.

 *MSBuild.exe* yapılandırma dosyasında (veya kullanıyorsanız, MSBuild altyapısını barındıran özel araç için) özel bir araç kümesi belirtin. Örneğin, *MSBuild.exe* yapılandırma dosyası, *mycustomaraç* kümesi adlı bir araç takımını tanımlamak üzere kullandıysanız aşağıdaki araç kümesi tanımını içerebilir.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>` Ayrıca yapılandırma dosyasında aşağıdaki gibi tanımlanmalıdır.

```xml
<configSections>
   <section name="msbuildToolsets"
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a"
   </section>
</configSections>
```

> [!NOTE]
> Doğru okunalmak için, `<configSections>` bölümündeki ilk alt bölüm olmalıdır `<configuration>` .

 `ToolsetConfigurationSection` , özel yapılandırma için herhangi bir MSBuild ana bilgisayarı tarafından kullanılabilen özel bir yapılandırma bölümüdür. Özel bir araç kümesi kullanıyorsanız, yapılandırma dosyası girdilerini sağlama dışında bir konağın derleme altyapısını başlatmak için bir şey yapması gerekmez.

 Aşağıdaki özellikler, `ToolsVersion` projelerde kullanılan değerine özgüdür:

- **$ (MSBuildBinPath)** , `ToolsPath` kayıt defterinde veya tanımlanan yapılandırma dosyasında belirtilen değere ayarlanır `ToolsVersion` . `$(MSBuildToolsPath)`Kayıt defterindeki veya yapılandırma dosyasındaki ayar, çekirdek görevlerinin ve hedeflerin konumunu belirtir. Proje dosyasında, bu $ (MSBuildBinPath) özelliğine ve ayrıca $ (Msbuildaraçları yolu) özelliğine eşlenir.

- `$(MSBuildToolsPath)` , yapılandırma dosyasında belirtilen Msbuildaraçları yol özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik yerini alır `$(MSBuildBinPath)` . Ancak, `$(MSBuildBinPath)` uyumluluk için ileriye doğru yürütülür.) Özel bir araç takımı, her `$(MSBuildToolsPath)` `$(MSBuildBinPath)` ikisi de aynı değere sahip olmadıkları takdirde, ya da öğesini tanımlamalıdır.

  Ayrıca, Msbuildaraçları Path özelliğini eklemek için kullandığınız söz dizimini kullanarak yapılandırma dosyasına özel, araçları sürümüne özel özellikler ekleyebilirsiniz. Bu özel özellikleri proje dosyası için kullanılabilir hale getirmek için, yapılandırma dosyasında belirtilen değerin adı ile aynı adı kullanın. Yapılandırma dosyasında araç kümelerini tanımlayabilir, ancak alt araç kümelerini tanımlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
