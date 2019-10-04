---
title: Visual Studio kapsayıcı araçları derleme özellikleri
author: ghogen
description: Kapsayıcı araçları derleme işlemine genel bakış
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950692"
---
# <a name="container-tools-build-properties"></a>Kapsayıcı araçları derleme özellikleri

MSBuild 'in projenizi oluşturmak için kullandığı özellikleri ayarlayarak, Visual Studio 'Nun kapsayıcı projelerinizi nasıl derlemediğini özelleştirebilirsiniz. Örneğin, Dockerfile adını değiştirebilir, görüntüleriniz için Etiketler ve Etiketler belirtebilir, Docker komutlarına geçirilen ek bağımsız değişkenleri sağlayabilir ve Visual Studio 'nun kapsayıcı ortamı. Ayrıca, başlatılacak yürütülebilir dosyanın adı ve sağlanacak komut satırı bağımsız değişkenleri gibi hata ayıklama özelliklerini de ayarlayabilirsiniz.

Bir özelliğin değerini ayarlamak için proje dosyasını düzenleyin. Örneğin, Dockerfile adlı dosyanın *Mydockerfile*olduğunu varsayalım. Proje dosyasında `DockerfileFile` özelliğini aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Özellik ayarını mevcut bir `PropertyGroup` öğesine ekleyebilir veya bir tane yoksa, yeni bir `PropertyGroup` öğesi oluşturun.

Aşağıdaki tabloda kapsayıcı projeleri için kullanılabilen MSBuild özellikleri gösterilmektedir. NuGet paketi sürümü [Microsoft. VisualStudio. Azure. containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)için geçerlidir.

| Özellik adı | Açıklama | Varsayılan değer  | NuGet paket sürümü|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | "Konak oluşturma" iyileştirmesi ("hızlı mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler **hızlı** ve **normal**. | Hızlı |1.0.1872750 veya daha yeni|
| ContainerVsDbgPath | VSDBG hata ayıklayıcısı için yol. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 veya daha yeni|
| DockerDebuggeeArguments | Hata ayıklarken, hata ayıklayıcı, bu bağımsız değişkenleri başlatılan yürütülebilir dosyaya iletmektir. | ASP.NET .NET Framework projelerine uygulanamaz |1.7.8 veya daha yeni|
| DockerDebuggeeProgram | Hata ayıklarken, hata ayıklayıcıda bu çalıştırılabiliri başlatması istendi. | .NET Core projeleri için: DotNet, ASP.NET .NET Framework projeleri: Uygulanamaz (IIS her zaman kullanılır) |1.7.8 veya daha yeni|
| DockerDebuggeeKillProgram | Bu komut, bir kapsayıcıda çalışan işlemi sonlandırmak için kullanılır. | ASP.NET .NET Framework projelerine uygulanamaz |1.7.8 veya daha yeni|
| Dockerdebuggeeworkingdizini | Hata ayıklarken, hata ayıklayıcının bu yolu çalışma dizini olarak kullanması talimatı verilir. | C:\app (Windows) veya/App (Linux) |1.7.8 veya daha yeni|
| DockerDefaultTargetOS | Docker görüntüsü oluşturulurken kullanılan varsayılan hedef işletim sistemi. | Visual Studio tarafından ayarlanır. |1.0.1985401 veya daha yeni|
| Dockerımagelabels | Docker görüntüsüne uygulanan varsayılan etiket kümesi. | com. Microsoft. Created-By = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 veya daha yeni|
| Dockerfastmodeprojectbağlamadizini|**Hızlı modda**, bu özellik proje çıktı dizininin çalışan kapsayıcıya birim bağlı olduğunu denetler.|C:\app (Windows) veya/App (Linux)|1.9.2 veya daha yeni|
| DockerfileBuildArguments | Docker Build komutuna ek bağımsız değişkenler geçirildi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileContext | Docker görüntüsü oluşturulurken kullanılan varsayılan bağlam. | Visual Studio tarafından ayarlanır. |1.0.1872750 veya daha yeni|
| DockerfileFastModeStage | Görüntü hata ayıklama modunda oluşturulurken kullanılacak Dockerfile aşaması (yani, hedef). | Dockerfile 'da bulunan ilk aşama (temel) |
| DockerfileFile | Projenin kapsayıcısını derlemek/çalıştırmak için kullanılacak varsayılan Dockerfile öğesini açıklar. Bu bir yol da olabilir. | Dockerfile |1.0.1872750 veya daha yeni|
| DockerfileRunArguments | Docker Run komutuna ek bağımsız değişkenler geçirildi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileRunEnvironmentFiles | Docker çalıştırması sırasında uygulanan ortam dosyalarının noktalı virgülle ayrılmış listesi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileTag | Docker görüntüsü oluşturulurken kullanılacak etiket. Hata ayıklama sırasında, etikete bir ":d ev" eklenir. | Aşağıdaki kurallarla alfasayısal olmayan karakterleri gerçekleştirdikten sonra bütünleştirilmiş kod adı: <br/> Sonuç etiketi tümü sayısal ise, "görüntü" bir ön ek olarak eklenir (örneğin, image2314) <br/> Sonuç etiketi boş bir dizeyse, etiket olarak "görüntü" kullanılır. |1.0.1872750 veya daha yeni|

## <a name="next-steps"></a>Sonraki adımlar

MSBuild özellikleri hakkında genel bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Docker Compose derleme özellikleri](docker-compose-properties.md)

[Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md)
