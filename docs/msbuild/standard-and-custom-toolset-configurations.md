---
title: Standart ve özel araç takımı yapılandırması | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632167"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standart ve özel araç takımı yapılandırması

MSBuild Araç Takımı, bir uygulama projesi oluşturmak için kullanabileceğiniz görevlere, hedeflere ve araçlara yönelik başvurular içerir. MSBuild standart bir araç takımı içerir, ancak özel araç kümeleri de oluşturabilirsiniz. Araç takımını belirtme hakkında daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standart araç takımı yapılandırması

::: moniker range=">=vs-2019"
 MSBuild 16,0 aşağıdaki standart araç kümelerini içerir:

|ToolsVersion|Araç takımı yolu (Msbuildaraçları yolu veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2,0|*\<Windows yükleme yolu > \Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v4.0.30319\\*|
|Geçerli|*\<Visual Studio yükleme yolu > \MSBuild\Current\bin*|

 `ToolsVersion` değeri, Visual Studio 'Nun oluşturduğu bir proje tarafından hangi araç takımının kullanıldığını belirler. Visual Studio 2019 ' de, varsayılan değer "geçerli" (proje dosyasında belirtilen sürüm değildir), ancak komut isteminde **/, sürüm** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve `ToolsVersion`belirtmek için diğer yollar hakkında daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15,0 aşağıdaki standart araç kümelerini içerir:

|ToolsVersion|Araç takımı yolu (Msbuildaraçları yolu veya MSBuildBinPath derleme özelliğinde belirtilen şekilde)|
|------------------| - |
|2,0|*\<Windows yükleme yolu > \Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Windows yükleme yolu > \Microsoft.NET\Framework\v4.0.30319\\*|
|15,0|*\<Visual Studio yükleme yolu > \MSBuild\15.0\bin*|

 `ToolsVersion` değeri, Visual Studio 'Nun oluşturduğu bir proje tarafından hangi araç takımının kullanıldığını belirler. Visual Studio 2017 ' de, varsayılan değer "15,0" ' dir (proje dosyasında belirtilen sürümden bağımsız olarak), ancak komut isteminde **/araçları sürüm** anahtarını kullanarak bu özniteliği geçersiz kılabilirsiniz. Bu öznitelik ve `ToolsVersion`belirtmek için diğer yollar hakkında daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Visual Studio 2017 ve sonraki sürümleri, MSBuild yolu için bir kayıt defteri anahtarı kullanmaz. Visual Studio 2017 ile yüklenen 15,0 ' den önceki MSBuild sürümleri için aşağıdaki kayıt defteri anahtarları, MSBuild. exe ' nin yükleme yolunu belirtir.

|Kayıt defteri anahtarı|Anahtar adı|Dize anahtarı değeri|
|------------------|--------------|----------------------|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\2,0\\** |**Msbuildaraçları yolu**|**.NET Framework 2,0 yüklemesi yolu**|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\3.5\\** |**Msbuildaraçları yolu**|**.NET Framework 3,5 yüklemesi yolu**|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ Msbuild\tools\versions\4.0\\** |**Msbuildaraçları yolu**|**.NET Framework 4 yüklemesi yolu**|

### <a name="sub-toolsets"></a>Alt araç kümeleri

 Önceki tablodaki kayıt defteri anahtarının bir alt anahtarı varsa, MSBuild bunu üst araç takımından yolu geçersiz kılan bir alt araç takımının yolunu belirlemede kullanır. Aşağıdaki alt anahtar bir örnektir:

 **\ HKEY_LOCAL_MACHINE \Software\microsoft\msbuild\tools\versions\12.0\12.0**

 Hem temel araç takımı hem de seçili alt araç takımı 'nda herhangi bir özellik tanımlanırsa, alt araç takımının özellik tanımları kullanılır. Örneğin, MSBuild 4,0 araç takımı, 7.0 A SDK 'sını işaret etmek için `SDK40ToolsPath` tanımlar, ancak MSBuild 4.0 \ 11.0 araç takımı, 8.0 'ı bir SDK 'ya işaret etmek için aynı özelliği tanımlar. `VisualStudioVersion` ayarlanmamışsa, `SDK40ToolsPath` 7.0 A 'ya işaret edecektir, ancak `VisualStudioVersion` 11,0 olarak ayarlandıysa, özellik 8.0 A 'ya işaret edecektir.

 `VisualStudioVersion` Build özelliği bir alt araç takımının etkin olup olmadığını gösterir. Örneğin, bir `VisualStudioVersion` değeri "12,0" MSBuild 12,0 alt araç takımını belirtir. Daha fazla bilgi için araç kümesi 'nin [(Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.

> [!NOTE]
> Bu ayarları değiştirmekten kaçınmanızı öneririz. Bununla birlikte, sonraki bölümde açıklandığı gibi kendi ayarlarınızı ekleyebilir ve bilgisayar genelindeki özel araç takımı tanımlarını tanımlayabilirsiniz.

## <a name="custom-toolset-definitions"></a>Özel araç takımı tanımları

 Standart bir araç takımı derleme gereksinimlerinizi yerine getirmiyorsa, özel bir araç takımı oluşturabilirsiniz. Örneğin, proje derlemek C++ için ayrı bir sisteme sahip olmanız gereken bir derleme Laboratuvarı senaryonuz olabilir. Özel bir araç kümesi kullanarak, proje oluştururken veya *MSBuild. exe*' yi çalıştırdığınızda `ToolsVersion` özniteliğine özel değerler atayabilirsiniz. Bunu yaparak, bu dizindeki *. targets* dosyalarını içeri aktarmak için `$(MSBuildToolsPath)` özelliğini ve bu araç takımını kullanan herhangi bir proje için kullanılabilecek kendi özel araç takımı özelliklerinizi tanımlamayı de kullanabilirsiniz.

 *MSBuild. exe* için yapılandırma dosyasında özel bir araç kümesi belirtin (veya kullanıyorsanız, MSBuild altyapısını barındıran özel araç için). Örneğin, *MSBuild. exe* için yapılandırma dosyası, *mycustomaraç*kümesi adlı bir araç takımını tanımlamak üzere kullandıysanız aşağıdaki araç kümesi tanımını içerebilir.

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
> Doğru okunalmak için, `<configuration>` bölümündeki ilk alt bölüm olmalıdır `<configSections>`.

 `ToolsetConfigurationSection`, özel yapılandırma için herhangi bir MSBuild ana bilgisayarı tarafından kullanılabilen özel bir yapılandırma bölümüdür. Özel bir araç kümesi kullanıyorsanız, yapılandırma dosyası girdilerini sağlama dışında bir konağın derleme altyapısını başlatmak için bir şey yapması gerekmez. Kayıt defterindeki girişleri tanımlayarak, *MSBuild. exe*, Visual Studio ve MSBuild 'in tüm konakları için geçerli olan bilgisayar genelindeki araç kümelerini belirtebilirsiniz.

> [!NOTE]
> Bir yapılandırma dosyası, kayıt defterinde zaten tanımlanmış olan bir `ToolsVersion` ayarlarını tanımlıyorsa, iki tanım birleştirilmez. Yapılandırma dosyasındaki tanım önceliklidir ve bu `ToolsVersion` kayıt defterindeki ayarlar yoksayılır.

 Aşağıdaki özellikler, projelerde kullanılan `ToolsVersion` değerine özgüdür:

- **$ (MSBuildBinPath)** , kayıt defterinde ya da `ToolsVersion` tanımlı yapılandırma dosyasında belirtilen `ToolsPath` değerine ayarlanır. Kayıt defterindeki `$(MSBuildToolsPath)` ayarı veya yapılandırma dosyası, çekirdek görevlerinin ve hedeflerin konumunu belirtir. Proje dosyasında, bu $ (MSBuildBinPath) özelliğine ve ayrıca $ (Msbuildaraçları yolu) özelliğine eşlenir.

- `$(MSBuildToolsPath)`, yapılandırma dosyasında belirtilen Msbuildaraçları yol özelliği tarafından sağlanan ayrılmış bir özelliktir. (Bu özellik `$(MSBuildBinPath)`yerini alır. Ancak, `$(MSBuildBinPath)` uyumluluk için ileriye doğru yürütülür.) Özel bir araç takımı, her ikisi de aynı değere sahip olmadıkları müddetçe `$(MSBuildToolsPath)` ya da `$(MSBuildBinPath)` tanımlamalıdır.

  Ayrıca, Msbuildaraçları Path özelliğini eklemek için kullandığınız söz dizimini kullanarak yapılandırma dosyasına özel, araçları sürümüne özel özellikler ekleyebilirsiniz. Bu özel özellikleri proje dosyası için kullanılabilir hale getirmek için, yapılandırma dosyasında belirtilen değerin adı ile aynı adı kullanın. Yapılandırma dosyasında araç kümelerini tanımlayabilir, ancak alt araç kümelerini tanımlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
