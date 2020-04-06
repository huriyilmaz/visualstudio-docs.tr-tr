---
title: Proje Türü (C#) için Yönetilen Paket Çerçevesini Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704115"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Yönetilen Paket Çerçevesini Kullanarak Proje Türü Uygulama (C#)
Yönetilen Paket Çerçevesi (MPF), kendi proje türlerinizi uygulamak için kullanabileceğiniz veya devralabileceğiniz C# sınıfları sağlar. MPF, Visual Studio'nun bir proje türünün sağlamasını beklediği arabirimlerin çoğunu uygular ve proje türünün belirli uygulamalarını serbest bırakır.

## <a name="using-the-mpf-project-source-code"></a>MPF Proje Kaynak Kodunu Kullanma
 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. MPF'deki diğer sınıfların aksine, proje sınıfları Visual Studio ile gönderilen derlemelere dahil edilmez. Bunun yerine, proje sınıfları [Projeler 2013 için MPF'de](https://github.com/tunnelvisionlabs/MPFProj10)kaynak kodu olarak sağlanır.

 Bu projeyi VSPackage çözümünüze eklemek için aşağıdakileri yapın:

1. MPFProj dosyalarını *MPFProjectDir'e*indirin.

2. *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.filesinde aşağıdaki bloğu değiştirin:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Bir VSPackage projesi oluşturun.

2. VSPackage projesini boşaltın.

3. VsPackage .csproj dosyasını diğer `<Import>` bloklardan önce aşağıdaki bloğu ekleyerek düzenleme:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Projeyi kaydet.

2. VSPackage çözümlerini kapatın ve yeniden açın.

3. VSPackage projesini yeniden açın. ProjectBase adında yeni bir dizin görmeniz gerekir.

4. VSPackage projesine aşağıdaki başvuruyu ekleyin:

     Microsoft.Build.Tasks.4.0

5. Projeyi derleyin.

## <a name="hierarchy-classes"></a>Hiyerarşi Sınıfları
 Aşağıdaki tablo, MPFProj'da proje hiyerarşilerini destekleyen sınıfları özetleyilmiştir. Daha fazla bilgi için [Hiyerarşiler ve Seçim'e](../../extensibility/internals/hierarchies-and-selection.md)bakın.

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

## <a name="document-handling-classes"></a>Belge İşleme Sınıfları
 Aşağıdaki tabloda, MPF'de belge işlemeyi destekleyen sınıflar listeleneb.)'de. Daha fazla bilgi için [bkz.](../../extensibility/internals/opening-and-saving-project-items.md)

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Yapılandırma ve Çıktı Sınıfları
 Aşağıdaki tablo, MPF'de proje türlerinin hata ayıklama ve sürüm gibi birden çok yapılandırmayı desteklemesine ve proje çıktısı koleksiyonlarını desteklemesine izin veren sınıfları listeler. Daha fazla bilgi için yapılandırma [seçeneklerini yönetme'ye](../../extensibility/internals/managing-configuration-options.md)bakın.

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Otomasyon-Destek Sınıfları
 Aşağıdaki tablo, Proje türünün kullanıcılarının eklenti yazabilmesi için MPF'de otomasyonu destekleyen sınıfları listeler.

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Özellikler Sınıfları
 Aşağıdaki tablo, MPF'de proje türlerinin kullanıcıların bir özellik tarayıcısında göz atabileceği ve değiştirebileceği özellikler eklemesine izin veren sınıfları listeler.

|Sınıf adı|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
