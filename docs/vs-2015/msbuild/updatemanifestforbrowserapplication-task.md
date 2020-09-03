---
title: UpdateManifestForBrowserApplication görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740214"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Görev, **\<hostInBrowser />** bir proje oluşturulduğunda öğeyi uygulama bildirimine (*ProjectName*. exe. manifest) eklemek için çalıştırılır [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] .  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`ApplicationManifest`|Gerekli **ıtaskitem []** parametresi.<br /><br /> Öğesini eklemek istediğiniz uygulama bildirim dosyasının yolunu ve adını belirtir `<hostInBrowser />` .|  
|`HostInBrowser`|Gerekli **Boolean** parametresi.<br /><br /> Uygulama bildiriminin öğesini dahil etmek için değiştirip değiştirmeyeceğinizi belirtir **\<hostInBrowser />** . **True**ise, öğesine yeni bir `<` **hostınbrowser/>** öğesi dahil edilir **\<entryPoint />** . Öğe içerme birikimlidir: bir **\<hostInBrowser />** öğe zaten varsa, kaldırılmaz veya üzerine yazılmaz. Bunun yerine, ek bir **\<hostInBrowser />** öğe oluşturulur. **False**ise, uygulama bildirimi değiştirilmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] , dağıtım kullanılarak çalıştırılır [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] ve bu nedenle, destekleyici dağıtım ve uygulama bildirimleri ile yayımlanmalıdır. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] bir uygulama bildirimi oluşturmak için [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) görevini kullanır.  
  
 Ardından, bir uygulamayı bir tarayıcıdan barındırılacak şekilde yapılandırmak için, **\<hostInBrowser />** Aşağıdaki örnekte gösterildiği gibi, uygulama bildirimine ek bir öğe eklenmelidir:  
  
```  
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
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Görev, [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] öğe eklemek için oluşturulduğunda çalıştırılır `<hostInBrowser />` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<hostInBrowser />` öğesinin bir uygulama bildirim dosyasına dahil edildiğini nasıl güvence altına gösterir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması oluşturma (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
