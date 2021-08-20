---
title: UpdateManifestForBrowserApplication Görev | Microsoft Docs
description: HostInBrowser MSBuild uygulama bildirimine eklemek için UpdateManifestForBrowserApplication görevini nasıl çalıştırabilirsiniz?
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2bedda1d9d923a7c01cde21ae4404038e956f9e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142591"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> bir XAML Tarayıcı Uygulaması (XBAP) projesi yerleşik olduğunda öğesini uygulama bildirimine **\<hostInBrowser />** (*\<projectname>.exe.manifest)* eklemek için çalışır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationManifest`|Gerekli **ITaskItem[]** parametresi.<br /><br /> Öğesini eklemek istediğiniz uygulama bildirim dosyasının yolunu ve adını `<hostInBrowser />` belirtir.|
|`HostInBrowser`|Gerekli **Boole parametresi.**<br /><br /> Uygulama bildiriminin öğesini içerecek şekilde değiştirip değiştirilene olmadığını **\<hostInBrowser />** belirtir. true **ise,** öğesine **\<hostInBrowser />** yeni bir öğe dahil **\<entryPoint />** edilir. Öğe ekleme kümülatiftir: **\<hostInBrowser />** Bir öğe zaten varsa, öğenin kaldırılması veya üzerine yazılmaz. Bunun yerine, ek **\<hostInBrowser />** bir öğe oluşturulur. False **ise,** uygulama bildirimi değiştirilmez.|

## <a name="remarks"></a>Açıklamalar

 XBAP'ler, ClickOnce dağıtım kullanılarak çalıştırıldık, bu nedenle desteklenen dağıtım ve uygulama bildirimleriyle yayımlanırlar. MSBuild bir uygulama [bildirimi oluşturmak için GenerateApplicationManifest](generateapplicationmanifest-task.md) görevini kullanır.

 Ardından, bir uygulamayı tarayıcıdan barındırılan bir uygulamayı yapılandırmak için, aşağıdaki örnekte gösterildiği gibi uygulama bildirimine **\<hostInBrowser />** ek bir öğe eklenmiştir:

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

 Görevi, <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> öğesi eklemek için bir XBAP projesi yerleşik olduğunda `<hostInBrowser />` çalıştır.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, öğesinin bir uygulama bildirim `<hostInBrowser />` dosyasına dahil olduğundan nasıl emin olunarak ilgili bilgiler ve bilgiler yer almaktadır.

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