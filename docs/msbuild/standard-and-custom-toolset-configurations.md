---
title: Standart ve Özel Araç Kümesi Yapılandırmaları | Microsoft Docs
description: Uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara başvurular içeren standart ve özel MSBuild Araç Kümeleri hakkında bilgi edinebilirsiniz.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d8ad327c41816d6a506e52c28cc50891ba9756c6
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132879738"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve özel Araç Kümesi yapılandırmaları

Bir MSBuild Araç Kümesi, uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara başvurular içerir. MSBuild araç kümesi içerir, ancak özel Araç Kümeleri de oluşturabilirsiniz. Araç Kümesi belirtme hakkında bilgi için bkz. Araç [Kümesi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standart Araç Seti yapılandırmaları

::: moniker range=">=vs-2022"
 MSBuild 17.0 aşağıdaki standart Araç Takımlarını içerir:

|Toolsversion|Araç seti yolu (MSBuildToolsPath veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|Geçerli|*\<Visual Studio installation path>\MSBuild\Current\Bin*|

 değeri, `ToolsVersion` bir proje tarafından hangi Araç Seti'nin Visual Studio belirler. 2022 Visual Studio de varsayılan değer "Geçerli" (proje dosyasında belirtilen sürüm ne olursa olsun) olur, ancak komut isteminde **/toolsversion** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmenin diğer yolları hakkında bilgi için `ToolsVersion` bkz. [ToolsVersion ayarlarını Geçersiz Kılma.](../msbuild/overriding-toolsversion-settings.md)

 ::: moniker-end


::: moniker range="vs-2019"
 MSBuild 16.0 aşağıdaki standart Araç Takımlarını içerir:

|Toolsversion|Araç seti yolu (MSBuildToolsPath veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|Geçerli|*\<Visual Studio installation path>\MSBuild\Current\bin*|

 değeri, `ToolsVersion` bir proje tarafından hangi Araç Seti'nin Visual Studio belirler. Visual Studio 2019'da varsayılan değer "Current" (proje dosyasında belirtilen sürüm ne olursa olsun) şeklindedir ancak komut isteminde **/toolsversion** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmenin diğer yolları hakkında bilgi için `ToolsVersion` bkz. [ToolsVersion ayarlarını Geçersiz Kılma.](../msbuild/overriding-toolsversion-settings.md)

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15.0 aşağıdaki standart Araç Takımlarını içerir:

|Toolsversion|Araç seti yolu (MSBuildToolsPath veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2.0|*\<Windows installation path>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows installation path>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows installation path>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Visual Studio installation path>\MSBuild\15.0\bin*|

 değeri, `ToolsVersion` bir proje tarafından hangi Araç Seti'nin Visual Studio belirler. Visual Studio 2017'de varsayılan değer "15.0" (proje dosyasında belirtilen sürüm ne olursa olsun) şeklindedir, ancak komut isteminde **/toolsversion** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve belirtmenin diğer yolları hakkında bilgi için `ToolsVersion` bkz. [ToolsVersion ayarlarını Geçersiz Kılma.](../msbuild/overriding-toolsversion-settings.md)
 ::: moniker-end

Visual Studio 2017 ve sonraki sürümlerde kayıt defteri anahtarı, 2017'ye MSBuild. Visual Studio 2017 ile yüklenmiş olan 15.0'dan önceki MSBuild sürümleri için, aşağıdaki kayıt defteri anahtarları MSBuild.exe.

|Kayıt defteri anahtarı|Anahtar adı|Dize anahtarı değeri|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**.NET Framework 2.0 Yükleme Yolu**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**.NET Framework 3.5 Yükleme Yolu**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**.NET Framework 4 Yükleme Yolu**|

### <a name="sub-toolsets"></a>Alt araç kümeleri

 Önceki tablodaki kayıt defteri anahtarı bir alt anahtara sahipse MSBuild araç takımı yolunu geçersiz kılmak için bu anahtarı kullanır. Aşağıdaki alt anahtar bir örnektir:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Hem temel Araç Kümesinde hem de seçili alt araç kümesinde herhangi bir özellik tanımlanmışsa, alt araç kümesinde özellik tanımları kullanılır. Örneğin, MSBuild 4.0 Araç Seti 7.0A SDK'yı işaret etmek için tanımlar, ancak `SDK40ToolsPath` MSBuild 4.0\11.0 Araç Seti aynı özelliği 8.0A SDK'sı işaret etmek için tanımlar. `VisualStudioVersion`ayarlanmamışsa `SDK40ToolsPath` 7.0A'ya işaret, ancak 11.0 olarak ayarlanırsa özellik bunun yerine `VisualStudioVersion` 8.0A'ya işaret etti.

 Build `VisualStudioVersion` özelliği, alt araç kümesi etkin duruma gelir. Örneğin, `VisualStudioVersion` "12.0" değeri, 12.0 MSBuild araç kümesi değerini belirtir. Daha fazla bilgi için Araç Seti'nin [(ToolsVersion) Alt araç kümeleri bölümüne bakın.](../msbuild/msbuild-toolset-toolsversion.md)

> [!NOTE]
> Bu ayarları değiştirmekten kaçınmayı öneririz. Yine de, kendi ayarlarınızı ekleyebilir ve sonraki bölümde açıkladığınız gibi bilgisayar genelindeki özel Araç Seti tanımlarını tanımlayabilirsiniz.

## <a name="custom-toolset-definitions"></a>Özel Araç Seti tanımları

 Standart bir Araç Seti derleme gereksinimlerinizi karşılamazsa özel bir `Toolset` oluşturabilirsiniz. Örneğin, C++ projeleri oluşturmak için ayrı bir sisteminiz olması gereken bir derleme laboratuvarı senaryoya sahip olabilirsiniz. Özel bir kullanarak, komut satırı anahtarını kullanarak özel değerleriMSBuild.exe`Toolset` `ToolsVersion`  `/toolsVersion` özniteliğine atabilirsiniz. Proje dosyasında `ToolsVersion` özniteliğini belirtirsiniz, yoksayılır.

 Bunu yaparak, bu dizinden .targets dosyalarını içeri aktarmanın yanı sıra bu Araç Kümesi'nin kullandığı herhangi bir proje için kullanılan kendi özel Araç Kümesi özelliklerinizi tanımlamak için özelliğini `$(MSBuildToolsPath)` de kullanabilirsiniz. 

 *MSBuild.exe* yapılandırma dosyasında (veya MSBuild altyapıyı barındıran özel araç için) özel bir Araç Kümesi belirtin. Örneğin,  `Toolset` *MyCustomToolset* adlı bir araçMSBuild.exeiçin yapılandırma dosyası aşağıdaki tanımı içerebilir.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>` yapılandırma dosyasında da aşağıdaki gibi tanımlanmalıdır.

```xml
<configSections>
   <section name="msbuildToolsets"
       type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a">
   </section>
</configSections>
```

> [!NOTE]
> Doğru okunsun diye `<configSections>` bölümün ilk alt bölümü `<configuration>` olması gerekir.

 `ToolsetConfigurationSection`, özel yapılandırma için herhangi bir konak tarafından MSBuild özel bir yapılandırma bölümüdir. Özel bir Araç Seti kullanıyorsanız, yapılandırma dosyası girdilerini sağlamak dışında bir ana bilgisayar derleme altyapısını başlatmak için herhangi bir şey yapmak zorunda değildir.

 Aşağıdaki özellikler, projelerde `ToolsVersion` kullanılan değerine özeldir:

- **$(MSBuildBinPath),** kayıt defterinde veya tanımlandığı yapılandırma dosyasında `ToolsPath` belirtilen değere `ToolsVersion` ayarlanır. Kayıt `$(MSBuildToolsPath)` defterindeki veya yapılandırma dosyasındaki ayarı, temel görevlerin ve hedeflerin konumunu belirtir. Proje dosyasında bu, $(MSBuildBinPath) özelliğine ve $(MSBuildToolsPath) özelliğine eşler.

- `$(MSBuildToolsPath)` , yapılandırma dosyasında belirtilen MSBuildToolsPath özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik yerini `$(MSBuildBinPath)` almaktadır. Ancak, `$(MSBuildBinPath)` uyumluluk için ileriye doğru ilerler.) Özel bir Araç Kümesi, aynı `$(MSBuildToolsPath)` değere sahip olmadığı sürece her ikisini de tanımlamalı veya `$(MSBuildBinPath)` tanımlamaz.

  MsBuildToolsPath özelliğini eklemek için kullanılan söz dizimini kullanarak yapılandırma dosyasına özel, ToolsVersion'a özgü özellikler de ebilirsiniz. Bu özel özellikleri proje dosyası için kullanılabilir yapmak için, yapılandırma dosyasında belirtilen değerin adıyla aynı adı kullanın. Araç kümeleri tanımlayabilirsiniz ancak yapılandırma dosyasında alt araç kümeleri tanımlanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
