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
ms.openlocfilehash: 1758b671b8151bb851074190c6afcd2468f9f1c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085110"
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
