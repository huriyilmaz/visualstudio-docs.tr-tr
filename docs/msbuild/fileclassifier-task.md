---
title: Filesınıflandırıcı görevi | Microsoft Docs
description: bir derlemeye eklenecek kaynak kaynakları kümesini sınıflandırmak için MSBuild filesınıflandırıcı görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: df4d07364f0f1b707ed4f4f95aca9a90de484f0da40eab9a369fc28cde398090
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428074"
---
# <a name="fileclassifier-task"></a>FileClassifier görevi

<xref:Microsoft.Build.Tasks.Windows.FileClassifier>Görev bir kaynak kaynakları kümesini bir derlemeye katıştırılacak şekilde sınıflandırır. Bir kaynak yerelleştirilebilir değilse, ana uygulama derlemesine katıştırılır; Aksi halde, bir uydu derlemesine katıştırılır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`CLREmbeddedResource`|Kullanılmıyor.|
|`CLRResourceFiles`|Kullanılmıyor.|
|`CLRSatelliteEmbeddedResource`|Kullanılmıyor.|
|`Culture`|İsteğe bağlı **dize** parametresi.<br /><br /> Derleme için kültürü belirtir. Bu değer, derleme yerelleştirilemeyen ise **null** olabilir. **Null** ise, varsayılan değer, **CultureInfo. InvariantCulture** işlevinin döndürdüğü küçük harfli değerdir.|
|`MainEmbeddedFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Ana derlemeye eklenmiş olan yerelleştirilemeyen kaynakları belirtir.|
|`OutputType`|Gerekli **dize** parametresi.<br /><br /> Belirtilen kaynak dosyaların içine gömüleceği dosya türünü belirtir. Geçerli değerler **exe**, **winexe** veya **Library**.|
|`SatelliteEmbeddedFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> **Kültür** parametresi tarafından belirtilen kültürün uydu derlemesine gömülü olan yerelleştirilebilir dosyaları belirtir.|
|`SourceFiles`|Gerekli **ıtaskitem []** parametresi.<br /><br /> Sınıflandırılacağı dosyaların listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

**Kültür** parametresi ayarlanmamışsa **SourceFiles** parametresi kullanılarak belirtilen tüm kaynaklar yerelleştirilemeyen; Aksi takdirde, **yanlış** olarak ayarlanmış bir **yerelleştirilebilir** özniteliğiyle ilişkilendirilmedikleri müddetçe bunlar yerelleştirilebilir olur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek bir kaynak dosyayı kaynak olarak sınıflandırır ve sonra French-Canadian (fr-CA) kültürü için bir uydu derlemesine katıştırır.

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
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
