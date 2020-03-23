---
title: MSBuild sorunları için sorun giderme ve günlükoluşturma
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 07b2c5e941d31ab1be853f9a89af94462329bdf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278801"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>MSBuild sorunları için sorun giderme ve günlükoluşturma

Aşağıdaki yordamlar Visual Studio projenizde sorun oluşturmatanısına ve gerekirse, araştırma için Microsoft'a gönderilecek bir günlük oluşturmanıza yardımcı olabilir.

## <a name="a-property-value-is-ignored"></a>Özellik değeri yoksayılır

Bir proje özelliği belirli bir değere ayarlanmış gibi görünüyorsa, ancak yapı üzerinde hiçbir etkisi yoksa, aşağıdaki adımları izleyin:

1. Open the Visual Studio Developer Command Prompt that corresponds to your version of Visual Studio.
1. Çözüm yolunuz, yapılandırmanız ve proje adınız için değerleri yerine geçtikten sonra aşağıdaki komutu çalıştırın:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Bu komut bir "önceden işlenmiş" msbuild proje dosyası (out.xml) üretir. Bu dosyanın tanımlandığı yeri görmek için belirli bir özelliği arayabilirsiniz.

Bir özelliğin son tanımı, yapının tükettiği şeydir. Özellik iki kez ayarlanırsa, ikinci değer ilkinin üzerine yazar. Ayrıca, MSBuild projeyi birkaç geçişte değerlendirir:

- PropertyGroups ve İthalat
- ItemDefinitionGroups
- Öğe Grupları
- Hedefler

Bu nedenle, aşağıdaki sırayla verilir:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

"MyFile.txt" öğesi için "MyMetadata" değeri yapı sırasında "B" olarak değerlendirilecektir ("A" değil ve boş değil)

## <a name="incremental-build-is-building-more-than-it-should"></a>Artımlı yapı olması gerekenden daha fazla inşa ediyor

MSBuild gereksiz yere bir proje veya proje öğesi yeniden oluşturuyorsa, ayrıntılı veya ikili bir yapı günlüğü oluşturun. Yapılan veya gereksiz yere derlenen dosya için günlük arama yapabilirsiniz. Çıktı şuna benzer:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Visual Studio IDE'de (ayrıntılı çıkış penceresi ayrıntılı olarak yapılı) bina oluşturuyorsanız, **Çıkış Penceresi** her projenin neden güncel olmadığını gösterir:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>İkili msbuild günlüğü oluşturma

1. Visual Studio sürümünüz için Geliştirici Komut Komut Ustem'ini açın
1. Komut isteminden aşağıdaki komutlardan birini çalıştırın. (Gerçek proje ve yapılandırma değerlerinizi kullanmayı unutmayın.):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

MSBuild'i çalıştırdığınız dizinde bir Msbuild.binlog dosyası oluşturulur. [Msbuild Yapılandırılmış Günlük Görüntüleyici'yi](http://www.msbuildlog.com/)kullanarak görüntüleyebilir ve arayabilirsiniz.

## <a name="create-a-detailed-log"></a>Ayrıntılı bir günlük oluşturma

1. Visual Studio ana menüsünden, **Araçlar** > **Seçenekleri** > **Projeler ve Çözümleri** >**Oluştur ve Çalıştır'a**gidin.
1. Her iki açılan kutuda **ayrıntılı** **olarak Msbuild proje oluşturma ayrıntılı** ayarlayın. **Üstteki, Çıkış Penceresinde** yapı ayrıntılılığını denetler ve ikincisi proje adı \<\>.log dosyasında yapı özbosity oluşturur.
2. Visual Studio geliştirici komut isteminden, gerçek yol ve yapılandırma değerlerinizi yerine bu komutlardan birini girin:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Msbuild'i çalıştırdığınız dizinde bir Msbuild.log dosyası oluşturulur.
