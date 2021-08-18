---
title: Proje türü için Yönetilen Paket Çerçevesi kullanma (C#)
description: Kendi proje türlerinizi uygulamak için kullanabileceğiniz veya 'den devralınabilir .NET sınıfları sağlayan Yönetilen Paket Çerçevesi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a6d229919bf496822a7b5499881af5fd7957a623
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144723"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Yönetilen Paket Çerçevesini Kullanarak Proje Türü Uygulama (C#)
Yönetilen Paket Çerçevesi (MPF), kendi proje türlerinizi uygulamak için kullanabileceğiniz veya 'den devralınabilir C# sınıfları sağlar. MPF, bir proje türünün Visual Studio beklediğiniz arabirimlerin birçoğuna sahiptir ve bu da sizi proje türüne özel olarak odaklanmanızı sağlar.

## <a name="using-the-mpf-project-source-code"></a>MPF'yi Project Kodu Kullanma
 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. MPF'deki diğer sınıfların aksine proje sınıfları, proje sınıfları ile birlikte gönderilen derlemelere dahil Visual Studio. Bunun yerine, proje sınıfları Projeler [2013 için MPF'de kaynak kodu olarak sağlanır.](https://github.com/tunnelvisionlabs/MPFProj10)

 Bu projeyi VSPackage çözümünüze eklemek için şunları yapın:

1. MPFProj dosyalarını *MPFProjectDir'e indirin.*

2. *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file dosyasında aşağıdaki bloğu değiştir:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. VSPackage projesi oluşturun.

2. VSPackage projesini kaldırma.

3. Diğer bloklara önce aşağıdaki bloğu ekleyerek VSPackage .csproj dosyasını `<Import>` düzenleyin:

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

2. VSPackage çözümünü kapatın ve yeniden açın.

3. VSPackage projesini yeniden açın. ProjectBase adlı yeni bir dizin görüyor olun.

4. VSPackage projesine aşağıdaki başvuru ekleyin:

     Microsoft.Build.Tasks.4.0

5. Projeyi derleyin.

## <a name="hierarchy-classes"></a>Hiyerarşi Sınıfları
 Aşağıdaki tabloda, MPFProj'da proje hiyerarşilerini destekleyen sınıflar özetlenmiştir. Daha fazla bilgi için [bkz. Hiyerarşiler ve Seçim](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Document-Handling Sınıfları
 Aşağıdaki tabloda MPF'de belge işlemeyi destekleyen sınıflar listelemektedir. Daha fazla bilgi için [bkz. Öğeleri Açma Project Kaydetme.](../../extensibility/internals/opening-and-saving-project-items.md)

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Yapılandırma ve Çıkış Sınıfları
 Aşağıdaki tabloda, MPF'deki proje türlerinin hata ayıklama ve sürüm gibi birden çok yapılandırmayı ve proje çıktısı koleksiyonlarını desteklemesine izin eden sınıflar listelemektedir. Daha fazla bilgi için [bkz. Yapılandırma Seçeneklerini Yönetme.](../../extensibility/internals/managing-configuration-options.md)

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation-Support Sınıfları
 Aşağıdaki tabloda MPF'de proje türüne sahip kullanıcıların eklentiler yazarak otomasyonu destekleyen sınıfları listelemektedir.

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Özellik Sınıfları
 Aşağıdaki tabloda, MPF'deki proje türlerinin, kullanıcıların özellik tarayıcısında göz atarak değiştirerek özellik ekleyen sınıfları listelemektedir.

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
