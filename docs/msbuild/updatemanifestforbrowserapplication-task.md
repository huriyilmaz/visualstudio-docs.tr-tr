---
title: UpdateManifestForBrowserApplication görevi | Microsoft Docs
description: MSBuild 'in, uygulama bildirimine HostInBrowser öğesini eklemek için UpdateManifestForBrowserApplication görevinin nasıl çalıştığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e71e11988d4dd853b0f97c745b6d720a45adcdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961553"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication görevi

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> **\<hostInBrowser />** Bir XAML tarayıcı UYGULAMASı (XBAP) projesi yapılandırıldığında, görev, uygulama bildirimine (*\<projectname> . exe. manifest*) eklemek için çalıştırılır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationManifest`|Gerekli **ıtaskitem []** parametresi.<br /><br /> Öğesini eklemek istediğiniz uygulama bildirim dosyasının yolunu ve adını belirtir `<hostInBrowser />` .|
|`HostInBrowser`|Gerekli **Boolean** parametresi.<br /><br /> Uygulama bildiriminin öğesini dahil etmek için değiştirip değiştirmeyeceğinizi belirtir **\<hostInBrowser />** . **True** ise, öğesine yeni bir **\<hostInBrowser />** öğesi dahil edilir **\<entryPoint />** . Öğe içerme birikimlidir: bir **\<hostInBrowser />** öğe zaten varsa, kaldırılmaz veya üzerine yazılmaz. Bunun yerine, ek bir **\<hostInBrowser />** öğe oluşturulur. **False** ise, uygulama bildirimi değiştirilmez.|

## <a name="remarks"></a>Açıklamalar

 XBAP 'ler ClickOnce dağıtımı kullanılarak çalıştırılır, bu nedenle destekleyici dağıtım ve uygulama bildirimleri ile yayımlanmaları gerekir. MSBuild, bir uygulama bildirimi oluşturmak için [GenerateApplicationManifest](generateapplicationmanifest-task.md) görevini kullanır.

 Ardından, bir uygulamayı bir tarayıcıdan barındırılacak şekilde yapılandırmak için, **\<hostInBrowser />** Aşağıdaki örnekte gösterildiği gibi, uygulama bildirimine ek bir öğe eklenmelidir:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Öğe eklemek için BIR XBAP projesi yapılandırıldığında görev çalıştırılır `<hostInBrowser />` .

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `<hostInBrowser />` öğesinin bir uygulama bildirim dosyasına dahil edildiğini nasıl sağlamak gerektiğini gösterir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)