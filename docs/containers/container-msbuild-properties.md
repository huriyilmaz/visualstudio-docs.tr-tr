---
title: Visual Studio Konteyner Araçları özellikleri oluşturmak
author: ghogen
description: Konteyner Araçları oluşturma sürecine genel bakış
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950692"
---
# <a name="container-tools-build-properties"></a>Konteyner Araçları özellikleri oluşturmak

MSBuild'in projenizi oluşturmak için kullandığı özellikleri ayarlayarak Visual Studio'nun konteyner projelerinizi nasıl oluşturduğunu özelleştirebilirsiniz. Örneğin, Dockerfile'ın adını değiştirebilir, resimleriniz için etiket ve etiketler belirtebilir, Docker komutlarına geçirilen ek bağımsız değişkenler sağlayabilir ve Visual Studio'nun bina dışında bina gibi belirli performans optimizasyonları yapıp etmediğini kontrol edebilirsiniz. konteyner ortamı. Ayrıca, başlatılabilen yürütülebilir adı ve sağlamak için komut satırı bağımsız değişkenleri gibi hata ayıklama özellikleri ayarlayabilirsiniz.

Bir özelliğin değerini ayarlamak için proje dosyasını edin. Örneğin, Dockerfile'ınızın adının *MyDockerfile*olduğunu varsayalım. Proje dosyasındaki `DockerfileFile` özelliği aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Özellik ayarını varolan `PropertyGroup` bir öğeye ekleyebilirsiniz veya yoksa yeni `PropertyGroup` bir öğe oluşturabilirsiniz.

Aşağıdaki tablo, kapsayıcı projeleri için kullanılabilir MSBuild özelliklerini gösterir. NuGet paketi sürümü [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)için geçerlidir.

| Özellik adı | Açıklama | Varsayılan değer  | NuGet paket sürümü|
|---------------|-------------|----------------|----------------------|
| Konteyner Geliştirme Modu | "Ev sahibi" optimizasyonu ("Hızlı Mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler **Hızlı** ve **Düzenli'dir.** | Hızlı |1.0.1872750 veya daha yeni|
| KonteynerVsDbgPath | VSDBG hata ayıklama için yol. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 veya daha yeni|
| DockerDebuggeeArguments | Hata ayıklama, hata ayıklama başlatılmış yürütülebilir bu bağımsız değişkenleri geçmek için talimat verilir. | ASP.NET .NET Framework projeleri için geçerli değildir |1.7.8 veya daha yeni|
| DockerDebuggeeProgram | Hata ayıklama yaparken, hata ayıklayanbu yürütülebilir başlatmak için talimat verilir. | .NET Core projeleri için: dotnet, ASP.NET .NET Framework projeleri: Geçerli değil (IIS her zaman kullanılır) |1.7.8 veya daha yeni|
| DockerDebuggeeKillProgram | Bu komut, bir kapsayıcıda çalışan işlemi öldürmek için kullanılır. | ASP.NET .NET Framework projeleri için geçerli değildir |1.7.8 veya daha yeni|
| DockerDebuggeeWorkingDirectory | Hata ayıklama yaparken hata ayıklayanın bu yolu çalışma dizini olarak kullanması talimatı verilir. | C:\app (Windows) veya /app (Linux) |1.7.8 veya daha yeni|
| DockerDefaultTargetOS | Docker görüntüsünü oluştururken kullanılan varsayılan hedef işletim sistemi. | Visual Studio tarafından ayarlanır. |1.0.1985401 veya daha yeni|
| DockerImageEtiketler | Docker görüntüsüne uygulanan varsayılan etiket kümesi. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 veya daha yeni|
| DockerFastModeProjectMountDirectory|**Hızlı**Mod'da, bu özellik, proje çıktı dizininin çalışan kapsayıcıya hacim olarak monte edildiği denetimi denetler.|C:\app (Windows) veya /app (Linux)|1.9.2 veya daha yeni|
| DockerfileBuildArguments | Docker yapı komutuna ek bağımsız değişkenler geçti. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileContext | Docker görüntüsünü oluştururken kullanılan varsayılan bağlam. | Visual Studio tarafından ayarlanır. |1.0.1872750 veya daha yeni|
| DockerfileFastModeStage | Görüntü hata ayıklama modunda oluştururken kullanılacak Dockerfile aşaması (yani hedef). | Dockerfile'da bulunan ilk aşama (taban) |
| DockerfileDosya | Proje için kapsayıcıyı oluşturmak/çalıştırmak için kullanılacak varsayılan Dockerdosyasını açıklar. Bu da bir yol olabilir. | Dockerdosyası |1.0.1872750 veya daha yeni|
| DockerfileRunArguments | Docker çalıştır komutuna ek bağımsız değişkenler geçti. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileRunEnvironmentFiles | Docker çalışması sırasında uygulanan ortam dosyalarının yarı sütunlu sınırlı listesi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileTag | Docker görüntüsünü oluştururken kullanılacak etiket. Hata ayıklamada, etikete bir ":dev" eklenir. | Alfasayısal olmayan karakterleri aşağıdaki kurallarla sıyırdıktan sonra derleme adı: <br/> Elde edilen etiket tamamen sayısalsa, önek olarak "resim" eklenir (örneğin, image2314) <br/> Ortaya çıkan etiket boş bir dize ise, etiket olarak "resim" kullanılır. |1.0.1872750 veya daha yeni|

## <a name="next-steps"></a>Sonraki adımlar

Genel olarak MSBuild özellikleri hakkında bilgi için [MSBuild Özellikleri'ne](../msbuild/msbuild-properties.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

[Docker Oluşturma yapı özellikleri](docker-compose-properties.md)

[Konteyner Araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve iyi bilinen özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
