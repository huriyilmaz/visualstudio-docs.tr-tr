---
title: Standart ve Özel Araç Seti Yapılandırmaları | Microsoft Dokümanlar
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fef5a84285afdaa429606937f3e537863b060ec8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632167"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve özel Araç Seti yapılandırmaları

MSBuild Araç Kümesi, bir uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara başvurular içerir. MSBuild standart bir Araç Seti içerir, ancak özel Araç Setleri de oluşturabilirsiniz. Araç Kümesi'nin nasıl belirtilen hakkında bilgi için [Bkz. Araç Seti (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standart Araç Seti yapılandırmaları

::: moniker range=">=vs-2019"
 MSBuild 16.0 aşağıdaki standart Araç kümelerini içerir:

|Toolsversion|Araç seti yolu (MSBuildToolsPath veya MSBuildBinPath yapı özelliğinde belirtildiği gibi)|
|------------------| - |
|2,0|*\<Windows yükleme yolu>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows yükleme yolu>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows yükleme yolu>\Microsoft.NET\Framework\v4.0.30319\\*|
|Geçerli|*\<Visual Studio yükleme yolu>\MSBuild\Current\bin*|

 Değer, Visual Studio'nun `ToolsVersion` oluşturduğu bir proje tarafından hangi Araç Kümesi'nin kullanılacağını belirler. Visual Studio 2019'da varsayılan değer "Geçerli" (proje dosyasında belirtilen sürüm ne olursa olsun), ancak komut isteminde **/toolsversion** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve diğer yolları belirtmek `ToolsVersion`için bilgi için, [Bkz. Geçersiz Kılma AraçlarıSürüm ayarları.](../msbuild/overriding-toolsversion-settings.md)

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15.0 aşağıdaki standart Araç kümelerini içerir:

|Toolsversion|Araç seti yolu (MSBuildToolsPath veya MSBuildBinPath yapı özelliğinde belirtildiği gibi)|
|------------------| - |
|2,0|*\<Windows yükleme yolu>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows yükleme yolu>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows yükleme yolu>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Visual Studio yükleme yolu>\MSBuild\15.0\bin*|

 Değer, Visual Studio'nun `ToolsVersion` oluşturduğu bir proje tarafından hangi Araç Kümesi'nin kullanılacağını belirler. Visual Studio 2017'de varsayılan değer "15.0" (proje dosyasında belirtilen sürüm ne olursa olsun) olur, ancak komut isteminde **/toolsversion** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve diğer yolları belirtmek `ToolsVersion`için bilgi için, [Bkz. Geçersiz Kılma AraçlarıSürüm ayarları.](../msbuild/overriding-toolsversion-settings.md)
 ::: moniker-end

Visual Studio 2017 ve sonraki sürümlerde MSBuild yolu için bir kayıt defteri anahtarı kullanılmaz. Visual Studio 2017 ile yüklenen 15.0'dan önceki MSBuild sürümlerinde, aşağıdaki kayıt defteri anahtarları MSBuild.exe'nin yükleme yolunu belirtir.

|Kayıt defteri anahtarı|Anahtar adı|String anahtar değeri|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**.NET Framework 2.0 Yükleme Yolu**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**.NET Framework 3.5 Yükleme Yolu**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**.NET Framework 4 Yükleme Yolu**|

### <a name="sub-toolsets"></a>Alt araç kümeleri

 Önceki tablodaki kayıt defteri anahtarının bir alt anahtarı varsa, MSBuild bunu üst Araç kümesindeki yolu geçersiz kılan bir alt araç kümesinin yolunu belirlemek için kullanır. Aşağıdaki alt anahtar bir örnektir:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Hem temel Araç kümesinde hem de seçili alt araç kümesinde herhangi bir özellik tanımlanırsa, alt araç kümesindeki özellik tanımları kullanılır. Örneğin, MSBuild 4.0 Araç Kümesi `SDK40ToolsPath` 7,0A SDK'yı işaret etmek için tanımlar, ancak MSBuild 4.0\11.0 Araç Kümesi 8,0A SDK'yı işaret etmek için aynı özelliği tanımlar. `VisualStudioVersion` Ayarlanmamışsa, `SDK40ToolsPath` 7.0A'ya işaret `VisualStudioVersion` eder, ancak 11.0 olarak ayarlanırsa, özellik bunun yerine 8,0A'ya işaret eder.

 Yapı `VisualStudioVersion` özelliği, bir alt araç kümesinin etkin olup olmadığını gösterir. Örneğin, "12.0" `VisualStudioVersion` değeri MSBuild 12.0 alt araç kümesini belirtir. Daha fazla bilgi [için, Araç Kümesi 'nin (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.

> [!NOTE]
> Bu ayarları değiştirmekten kaçınmanızı öneririz. Bununla birlikte, bir sonraki bölümde açıklandığı gibi, kendi ayarlarınızı ekleyebilir ve bilgisayar genelinde özel Araç Seti tanımlarını tanımlayabilirsiniz.

## <a name="custom-toolset-definitions"></a>Özel Araç Seti tanımları

 Standart bir Araç Seti yapı gereksinimlerinizi karşılamazsa, özel bir Araç Kümesi oluşturabilirsiniz. Örneğin, C++ projeleri oluşturmak için ayrı bir sisteminiz olması gereken bir yapı laboratuarı senaryonuz olabilir. Özel bir Araç Kümesi kullanarak, projeler oluştururken `ToolsVersion` veya *MSBuild.exe*çalıştırdığınızda özniteliğe özel değerler atayabilirsiniz. Bunu yaparak, `$(MSBuildToolsPath)` özelliği, bu dizinden *.targets* dosyalarını almak ve bu Araç Kümesi'ni kullanan herhangi bir proje için kullanılabilecek kendi özel Araç Kümesi özelliklerinizi tanımlamak için de kullanabilirsiniz.

 *MSBuild.exe* için yapılandırma dosyasında özel bir Araç Kümesi belirtin (veya kullandığınız buysa MSBuild motorını barındıran özel araç için). Örneğin, *MyCustomToolset*adlı bir araç kümesi tanımlamak istiyorsanız *MSBuild.exe* için yapılandırma dosyası aşağıdaki Araç Seti tanımı içerebilir.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>`yapılandırma dosyasında da aşağıdaki gibi tanımlanmalıdır.

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
> Doğru okunabilmesi için, `<configSections>` `<configuration>` bölümdeki ilk alt bölüm olmalıdır.

 `ToolsetConfigurationSection`özel yapılandırma için herhangi bir MSBuild ana bilgisayar tarafından kullanılabilecek özel bir yapılandırma bölümüdür. Özel bir Araç Kümesi kullanıyorsanız, ana bilgisayar yapılandırma dosyası girişlerini sağlamak dışında yapı altyapısını başlatmaya çalışmak zorunda değildir. Kayıt defterindeki girişleri tanımlayarak, *MSBuild.exe,* Visual Studio ve MSBuild'in tüm ana bilgisayarları için geçerli olan bilgisayar genelindeki Araç kümelerini belirtebilirsiniz.

> [!NOTE]
> Bir yapılandırma dosyası, kayıt `ToolsVersion` defterinde zaten tanımlanmış bir dosyanın ayarlarını tanımlıyorsa, iki tanım birleştirilmeyecektir. Yapılandırma dosyasındaki tanım önceliklidir ve bunun `ToolsVersion` için kayıt defterindeki ayarlar yoksayılır.

 Aşağıdaki özellikler projelerde kullanılan `ToolsVersion` değerine özgüdür:

- **$(MSBuildBinPath)** kayıt defterinde veya tanımlandığı yapılandırma dosyasında `ToolsPath` `ToolsVersion` belirtilen değere ayarlanır. Kayıt `$(MSBuildToolsPath)` defterindeki veya yapılandırma dosyasındaki ayar, temel görevlerin ve hedeflerin konumunu belirtir. Proje dosyasında, $(MSBuildBinPath) özelliğine ve $(MSBuildToolsPath) özelliğine bu haritalar.

- `$(MSBuildToolsPath)`yapılandırma dosyasında belirtilen MSBuildToolsPath özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik `$(MSBuildBinPath)`değiştirir. Ancak, `$(MSBuildBinPath)` uyumluluk için ileriye taşınır.) Özel bir Araç Kümesi, `$(MSBuildBinPath)` her ikisi de aynı değere sahip olmadıkça, her ikisini de `$(MSBuildToolsPath)` tanımlamalıdır.

  Ayrıca, MSBuildToolsPath özelliğini eklemek için kullandığınız sözdizimini kullanarak yapılandırma dosyasına özel, ToolsVersion'e özgü özellikler ekleyebilirsiniz. Bu özel özellikleri proje dosyasında kullanılabilir hale getirmek için, yapılandırma dosyasında belirtilen değerin adı ile aynı adı kullanın. Araç Kümelerini tanımlayabilirsiniz, ancak yapılandırma dosyasında alt araç kümelerini tanımlayamaabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
