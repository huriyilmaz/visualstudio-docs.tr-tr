---
title: GüncellemeManifestForBrowserApplication Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631334"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication görevi

Bir <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> XAML Tarayıcı Uygulaması (XBAP) projesi oluşturulurken, görev ** \<hostInBrowser />** öğesini uygulama bildirimine*\<(projeadı>.exe.manifest)* eklemek için çalıştırılır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationManifest`|Gerekli **ITaskItem[]** parametresi.<br /><br /> `<hostInBrowser />` Öğeyi eklemek istediğiniz uygulama bildirimi dosyasının yolunu ve adını belirtir.|
|`HostInBrowser`|Gerekli **Boolean** parametresi.<br /><br /> Uygulama bildiriminin ** \<hostInBrowser />** öğesini içerecek şekilde değiştirilip değiştirilemeyeceğini belirtir. **Doğruysa,** ** \<entryPoint />** öğesine yeni ** \<bir hostInBrowser />** öğesi dahildir. Öğe ekleme kümülatif: bir ** \<hostInBrowser />** öğesi zaten varsa, kaldırılmaz veya üzerine yazılmamıştır. Bunun yerine, ek ** \<bir hostInBrowser />** öğesi oluşturulur. **Yanlışsa,** uygulama bildirimi değiştirilmez.|

## <a name="remarks"></a>Açıklamalar

 XBAP'lar ClickOnce dağıtımı kullanılarak çalıştırılır, bu nedenle dağıtım ve uygulama bildirimlerini destekleyen şekilde yayımlanmalıdır. MSBuild, bir uygulama bildirimi oluşturmak için [GenerateApplicationManifest](generateapplicationmanifest-task.md) görevini kullanır.

 Daha sonra, bir tarayıcıdan barındırılacak bir uygulamayı yapılandırmak için, aşağıdaki örnekte gösterildiği gibi uygulama bildirimine ek ** \<bir hostInBrowser />** öğesi eklenmelidir:

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

 Öğeyi <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> eklemek `<hostInBrowser />` için bir XBAP projesi oluşturulduğunda görev çalıştırılır.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğenin bir `<hostInBrowser />` uygulama bildirimi dosyasına nasıl dahil edildiğinden nasıl emin olunan gösterilmektedir.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)