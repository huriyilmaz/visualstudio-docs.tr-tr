---
title: Bir proje türü (C#) uygulamak Için yönetilen paket çerçevesini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066695c6d94603d0a0474243ed05dece4cc0bd1f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300371"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Yönetilen Paket Çerçevesini Kullanarak Proje Türü Uygulama (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yönetilen paket çerçevesi (MPF), kendi C# proje türlerinizi uygulamak için kullanabileceğiniz veya buradan devralma sınıfları sağlar. MPF, Visual Studio 'nun sağlaması için bir proje türünün sağlamasını beklediği ve proje türünün bununla uygulama üzerinde yoğunlaşmaya odaklanmanızı sağlayan birçok arabirimi uygular.  
  
## <a name="using-the-mpf-project-source-code"></a>MPF proje kaynak kodunu kullanma  
 Projeler için yönetilen paket çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. MPF içindeki diğer sınıfların aksine proje sınıfları, Visual Studio ile gönderilen derlemelere dahil edilmez. Bunun yerine, proje sınıfları [2013 projeleri Için MPF](https://archive.codeplex.com/?p=mpfproj12)'de kaynak kodu olarak sağlanır.  
  
 Bu projeyi VSPackage çözümünüze eklemek için aşağıdakileri yapın:  
  
1. MPFProj dosyalarını *MPFProjectDir*öğesine indirin.  
  
2. *MPFProjectDir*\Dev10\src\csharp\projectbase.exe dosyasında aşağıdaki bloğu değiştirin:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1. VSPackage projesi oluşturun.  
  
2. VSPackage projesini kaldırın.  
  
3. Diğer `<Import>` bloğundan önce aşağıdaki bloğu ekleyerek VSPackage. csproj dosyasını düzenleyin:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1. Projeyi kaydedin.  
  
2. VSPackage çözümünü kapatıp yeniden açın.  
  
3. VSPackage projesini yeniden açın. ProjectBase adlı yeni bir dizin görmeniz gerekir.  
  
4. VSPackage projesine aşağıdaki başvuruyu ekleyin:  
  
     Microsoft. Build. Tasks. 4.0  
  
5. Projeyi oluşturun.  
  
## <a name="hierarchy-classes"></a>Hiyerarşi sınıfları  
 Aşağıdaki tabloda, MPFProj içindeki proje hiyerarşilerini destekleyen sınıflar özetlenmektedir. Daha fazla bilgi için bkz. [hiyerarşiler ve seçim](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Belge Işleme sınıfları  
 Aşağıdaki tabloda, MPF 'de belge işlemeyi destekleyen sınıflar listelenmektedir. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Yapılandırma ve çıkış sınıfları  
 Aşağıdaki tabloda, MPF içindeki sınıflar, proje türlerinin hata ayıklama ve yayın gibi birden çok yapılandırmayı ve proje çıkışı koleksiyonlarını desteklemesini sağlar. Daha fazla bilgi için bkz. [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Otomasyon-destek sınıfları  
 Aşağıdaki tabloda, proje türü kullanıcıların eklentiler yazabilmesi için otomasyonu destekleyen MPF içindeki sınıflar listelenmektedir.  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Özellikler sınıfları  
 Aşağıdaki tabloda, MPF içindeki sınıflar listelenir. Bu, proje türlerine kullanıcıların bir özellik tarayıcısına gözatabilmesine ve değiştiremeyeceğiniz özellikler eklemesine olanak tanır.  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
