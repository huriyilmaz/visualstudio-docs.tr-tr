---
title: Araçları sürüm ayarlarını geçersiz kılma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 468561a627a3ad7eb477328b5afef794c7acf2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199942"
---
# <a name="overriding-toolsversion-settings"></a>ToolsVersion Ayarlarını Geçersiz Kılma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje ve çözümlerin araç takımını üç şekilde değiştirebilirsiniz:  
  
1. bir `/ToolsVersion` `/tv` komut satırından proje veya çözüm oluştururken anahtarı (veya kısaca) kullanarak  
  
2. `ToolsVersion`MSBuild görevinde parametresini ayarlayarak  
  
3. `$(ProjectToolsVersion)`bir çözüm içindeki bir projede özelliğini ayarlayarak. Bu, diğer projelerden farklı bir araç takımı sürümüne sahip bir çözümde proje oluşturmanıza olanak sağlar.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Komut satırı derlemelerindeki projelerin ve çözümlerin araçları sürüm ayarlarını geçersiz kılın  
 Visual Studio projeleri genellikle proje dosyasında belirtilen araçları sürümü ile derlense de, `/ToolsVersion` `/tv` Bu değeri geçersiz kılmak ve projeleri ve proje-proje bağımlılıklarını farklı bir araç kümesiyle derlemek için komut satırındaki (veya) anahtarını kullanabilirsiniz. Örneğin:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 Bu örnekte, tüm projeler, araçları sürüm 12,0 kullanılarak oluşturulmuştur. (Ancak, bu konunun devamındaki "öncelik sırası" bölümüne bakın.)  
  
 `/tv`Komut satırında anahtarı kullanırken, isteğe bağlı olarak bu `$(ProjectToolsVersion)` özelliği, çözümdeki diğer projelerden farklı bir bir bir bir  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild Görevinin ToolsVersion Parametresini Kullanarak ToolsVersion Ayarlarını Geçersiz Kılma  
 MSBuild görevi, bir projenin başka bir proje oluşturması için birincil anlamına gelir. MSBuild görevini, projede belirtilenden farklı bir araçları sürümüne sahip bir proje oluşturmak üzere etkinleştirmek için, adlı isteğe bağlı bir görev parametresi sağlar `ToolsVersion` . Aşağıdaki örnek, bu parametrenin nasıl kullanılacağını gösterir:  
  
1. `projectA.proj`Aşağıdaki kodu içeren ve adlı bir dosya oluşturun:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2. Aşağıdaki kodu içeren ve adlı başka bir dosya oluşturun `projectB.proj` :  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3. Komut istemine aşağıdaki komutu girin:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4. Aşağıdaki çıktı görüntülenir. İçin `projectA` , `/toolsversion:3.5` komut satırındaki ayarı `ToolsVersion=12.0` etiketindeki ayarı geçersiz kılar `Project` .  
  
     `ProjectB` , içinde bir görev tarafından çağırılır `projectA` . Bu görev `ToolsVersion=2.0` , için diğer ayarları geçersiz kılar `ToolsVersion` `projectB` .  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Öncelik Sırası  
 Öncelik sırası, en yüksekten en düşüğe, şu olduğunu tespit etmek için kullanılır `ToolsVersion` :  
  
1. `ToolsVersion`MSBuild görevinde, varsa projeyi oluşturmak için kullanılan öznitelik.  
  
2. `/toolsversion` `/tv` Varsa, msbuild.exe komutunda kullanılan (veya) anahtarı.  
  
3. Ortam değişkeni `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlandıysa, geçerli öğesini kullanın `ToolsVersion` .  
  
4. Ortam değişkeni `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ayarlandıysa ve `ToolsVersion` Proje dosyasında tanımlı değeri geçerli olandan büyükse `ToolsVersion` , geçerli ' i kullanın `ToolsVersion` .  
  
5. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlandıysa veya `ToolsVersion` ayarlanmamışsa, aşağıdaki adımlar kullanılır:  
  
    1. `ToolsVersion`Proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinin özniteliği. Bu öznitelik yoksa, geçerli sürüm olduğu varsayılır.  
  
    2. MSBuild.exe.config dosyasındaki varsayılan Araçlar sürümü.  
  
    3. Kayıt defterindeki varsayılan Araçlar sürümü. Daha fazla bilgi için bkz. [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmamışsa, aşağıdaki adımlar kullanılır:  
  
    1. Ortam değişkeni `MSBUILDDEFAULTTOOLSVERSION` bir `ToolsVersion` varsa, bunu kullanın.  
  
    2. `DefaultOverrideToolsVersion`MSBuild.exe.config ' de ayarlanırsa, onu kullanın.  
  
    3. `DefaultOverrideToolsVersion`Kayıt defterinde ayarlandıysa, onu kullanın.  
  
    4. Aksi takdirde, geçerli öğesini kullanın `ToolsVersion` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Araç Takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)
