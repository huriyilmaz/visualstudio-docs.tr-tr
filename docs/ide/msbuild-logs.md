---
title: Sorun giderme ve günlük oluşturma MSBuild oluşturma
description: Visual Studio projenizin derleme sorunlarını tanılamayı öğrenin ve gerekirse araştırma için Microsoft'a göndermek için bir günlük oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/08/2021
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: efa2ba6a298c4e3326b8a43d3fe6e8ecef0fb214beba6e1b0aaaa26643b982ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413021"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Sorun giderme ve günlük oluşturma MSBuild oluşturma

Aşağıdaki yordamlar, Visual Studio projenizin derleme sorunlarını tanılamanıza ve gerekirse araştırma için Microsoft'a göndermek için bir günlük oluşturmanıza yardımcı olabilir.

## <a name="a-property-value-is-ignored"></a>Özellik değeri yoksayılır

Bir proje özelliği belirli bir değere ayarlanmış gibi görünüyorsa ama derleme üzerinde hiçbir etkisi yoksa şu adımları izleyin:

1. Visual Studio Geliştirici Komut İstemi sürümünüze karşılık gelen Visual Studio.
1. Çözüm yolunuz, yapılandırmanız ve proje adınız için değerleri verdikten sonra aşağıdaki komutu çalıştırın:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Bu komut bir "önceden işlenmemiş" msbuild proje dosyası (out.xml). Tanımlandığı yeri görmek için bu dosyada belirli bir özelliği arayabilirsiniz.

Bir özelliğin son tanımı, derlemenin tükettiğidir. Özellik iki kez ayarlanırsa ikinci değer ilk değerin üzerine yazmaktadır. Ayrıca, MSBuild birkaç geçişle projeyi değerlendirir:

- PropertyGroups ve İçeri Aktarmalar
- ItemDefinitionGroups
- ItemGroups
- Targets

Bu nedenle, aşağıdaki sırayla:

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

Derleme sırasında "MyFile.txt" öğesi için "MyMetadata" değeri "B" olarak değerlendirilir (boş değil)

## <a name="incremental-build-is-building-more-than-it-should"></a>Artımlı derleme olması gerekenden daha fazla derleme

Bir MSBuild proje veya proje öğesini gereksiz yere yeniden oluşturuyorsa, ayrıntılı veya ikili derleme günlüğü oluşturun. Günlükte gereksiz yere derlenmiş veya derlenmiş olan dosyayı arayabilirsiniz. Çıkış aşağıdakine benzer:

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

Visual Studio IDE'de (ayrıntılı çıkış penceresi ayrıntılılığıyla) Çıkış Penceresi,  her projenin güncel olmadığının nedenini görüntüler:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log-at-the-command-prompt"></a>Komut isteminde MSBuild ikili dosya dosyası oluşturma

1. Geliştirici Komut İstemi sürümünüz için Visual Studio

1. Komut isteminde aşağıdaki komutlardan birini çalıştırın. (Gerçek projenizi ve yapılandırma değerlerinizi kullanmayı unutmayın.):

   ```cmd
   Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
   ```

   veya

   ```cmd
   Msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
   ```

Bir *msbuild.binlog* dosyası, bu dosyadan oluşturduğunuz dizinde MSBuild oluşturulur.

## <a name="create-a-binary-msbuild-log-by-using-the-project-system-tools-extension"></a>Project System Tools uzantısını kullanarak ikili MSBuild günlük oluşturma

1. Project System [Tools uzantısını indirip yükleyin.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)

1. Uzantı yüklendikten sonra, Diğer Öğeleri Görüntüle menüsünde **bazı**  >  **yeni öğeler Windows** görünür.

   ![Diğer Windows menüsü](../ide/media/view-menu.png)

1. Derleme **Günlüğü penceresini**  >  **Windows** görüntülemek için  >  **Diğer** Günlük Kaydı'Visual Studio.  Proje sisteminde hem normal hem de tasarım zamanı derlemelerini kaydetmeye başlamak için ilk araç çubuğu simgesini seçin.

   ![Derleme günlüğü penceresi](../ide/media/build-logging-click-to-record.png)

1. Derleme kaydedildiktan sonra Derleme Günlüğü penceresinde görünür. Öğeye sağ tıklayın ve bağlam **menüsünde Günlükleri** Kaydet'i seçerek *.binlog dosyanızı* kaydedin.

   ![Derleme günlüğü bağlam menüsü](../ide/media/build-logging-context-menu.png)

*.binlog* dosyalarınızı görüntülemek ve aramak için yapılandırılmış MSBuild [Görüntüleyicisi'ni kullanarak.](http://www.msbuildlog.com/)

## <a name="create-a-detailed-log"></a>Ayrıntılı günlük oluşturma

1. Ana menüden Visual Studio Seçenekler Projeleri ve **Çözümleri**  >  **Derleme**  >  **ve Çalıştırma'ya**  > **gidin.**
1. Msbuild **proje derleme ayrıntılılığı'nın her iki** birleşik giriş kutusuna **da** Ayrıntılı olarak ayarlayın. İlk denetim, **Çıkış Penceresi** içinde ayrıntılılık, ikinci denetim ise derleme sırasında her projenin Ara dizininde oluşturulan .log dosyasında ayrıntılılık \<projectname\> sağlar.
2. Bir Visual Studio komut isteminde, şu komutlardan birini girin ve asıl yol ve yapılandırma değerlerinizi yerine yazın:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    veya

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    msbuild'i oluşturduğunuz dizinde bir Msbuild.log dosyası oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
