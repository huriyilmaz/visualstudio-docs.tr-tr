---
title: FileClassifier Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46ed1b1f94cd2ef23ff0704912cb2a2194ba7dab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634194"
---
# <a name="fileclassifier-task"></a>FileClassifier görev

Görev, <xref:Microsoft.Build.Tasks.Windows.FileClassifier> kaynak kaynakları kümesini derlemeye katıştırılmış kaynaklar olarak sınıfa getirir. Bir kaynak yerelleştirilebilir değilse, ana uygulama derlemesine gömülür; aksi takdirde, bir uydu montajı içine gömülüdür.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`CLREmbeddedResource`|Kullanılmıyor.|
|`CLRResourceFiles`|Kullanılmıyor.|
|`CLRSatelliteEmbeddedResource`|Kullanılmıyor.|
|`Culture`|İsteğe bağlı **String** parametresi.<br /><br /> Yapı nın kültürünü belirtir. Yapı yerelleştirilemezse bu değer **null** olabilir. **Null**ise, varsayılan değer **CultureInfo.InvariantCulture** döndürür küçük değerdir.|
|`MainEmbeddedFiles`|İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> Ana derlemeye katıştürülmüş yerelleştirilebilir olmayan kaynakları belirtir.|
|`OutputType`|Gerekli **String** parametresi.<br /><br /> Belirtilen kaynak dosyaları katıştırmak için dosya türünü belirtir. Geçerli değerler **exe,** **winexe**veya **kütüphanedir.**|
|`SatelliteEmbeddedFiles`|İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> **Kültür** parametresi tarafından belirtilen kültür için uydu derlemesine katıştürülmüş yerelleştirilebilir dosyaları belirtir.|
|`SourceFiles`|Gerekli **ITaskItem[]** parametresi.<br /><br /> Sınıflandırmak için dosyaların listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

**Kültür** parametresi ayarlanmamışsa, **Kaynak Dosyaları** parametresi kullanılarak belirtilen tüm kaynaklar yerelleştirilebilir değildir; aksi takdirde, **yanlış**olarak ayarlanmış bir **Yerelleştirilebilir** öznitelik ile ilişkili olmadıkça, yerelleştirilebilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek bir kaynak dosyasını kaynak olarak sınıflandırır ve ardından Fransız-Kanada (fr-CA) kültürü için bir uydu derlemesine katıştırır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <ItemGroup>
    <Resource Include="Resource1.bmp" />
  </ItemGroup>
  <Target Name="FileClassifierTask">
    <FileClassifier
      SourceFiles="Resource1.bmp"
      Culture="fr-CA"
      OutputType="exe" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
