---
title: SharePoint tarafından desteklenen MSBuild özellikleri | Microsoft Docs
description: Tarafından desteklenen ve SharePoint 'e özgü MSBuild özellik adlarının ve açıklamalarının listesini okuyun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1eab3832121f1e0c926257797ddbc79695546a5
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305142"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint tarafından desteklenen MsBuild özellikleri
  [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft. VisualStudio. SharePoint. targets dosyasında, proje dosyasında veya Project User dosyasında tanımlanan herhangi bir özellik [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projelerinde kullanılabilir. [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]SharePoint, projenin sağladığı ortak özelliklere ek olarak SharePoint projelerine özgü ek özellikler tanımlar.

 Ortak özelliklerin listesi için [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] bkz. [Ortak MSBuild proje özellikleri](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Programlama diliniz tarafından desteklenen özelliklerin tam listesi için *. targets* dosyasına, proje dosyasına (*. csproj* veya *. vbproj*) veya proje Kullanıcı dosyasına (*csproj. User* veya *. vbproj. User*) bakın.

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 'e özgü MsBuild özellikleri
 Aşağıdaki tabloda, [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] ' de SharePoint projelerine özel olarak uygulanan özellikler listelenmiştir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Diğer özellikler mevcuttur, ancak bunlar iç kullanım içindir.

|Özellik Adı|Description|
|-------------------|-----------------|
|SharePointSiteUrl|SharePoint sitesini temsil eden bir dize [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] .|
|SandboxedSolution|Çözümün korumalı bir çözüm olup olmadığını gösteren bir Boole değeri.|
|ActiveDeploymentConfiguration|Etkin dağıtım yapılandırması.|
|Includeassemblınpackage|Derlemenin paket dosyasına dahil edilip edilmeyeceğini belirten bir Boole değeri.|
|PreDeploymentCommand|Dağıtım öncesi komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|PostDeploymentCommand|Dağıtım sonrası komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|CustomBeforeSharePointTargets|Bir hedef dosyanın yolunu temsil eden bir dize [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . Hedef dosya varsa ve tanımlanmışsa, SharePoint hedefi verilerinden önce içeri aktarılır. Bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmeden paketlemeyle ilgili özelliklerini önceden tanımlayarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası tüm SharePoint projeleri için geçerli olmaya devam eder.|
|CustomAfterSharePointTargets|Bir hedef dosyanın yolunu temsil eden bir dize [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . Hedef dosya varsa ve tanımlanmışsa, tüm SharePoint hedefi verilerinden sonra içeri aktarılır. Bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmek zorunda kalmadan paketlemeyle ilgili özellikleri ve hedefleri geçersiz kılarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası tüm SharePoint projeleri için geçerli olmaya devam eder.|
|LayoutPath|Paketlenebilecek her bir dosyanın *. wsp* dosyasına eklenmeden önce geçici olarak yerleştirildiği kök dizini temsil eden bir dize. Bu yol, *. wsp* dosyasının içeriğini değiştirmek için kullanabileceğiniz dosyaları eklemek, kaldırmak veya değiştirmek için BeforeLayout ve AfterLayout hedeflerini geçersiz kıldığınızda bilmeniz yararlı olabilir.|
|BasePackagePath|Paketin yerleştirildiği klasörü temsil eden bir dize. Bu değer, projenin çıkış dizinini (örneğin, Bin\debug) kullanır.|
|PackageExtension|Pakete eklenecek dosya adı uzantısını temsil eden bir dize. Varsayılan değer wsp ' dir.|
|AssemblyDeploymentTarget|SharePoint sunucusunda proje derlemesinin dağıtıldığı konumu temsil eden bir dize. Değeri GlobalAssemblyCache (varsayılan) ya da WebApplication ' dir. Bu özellik Özellikler penceresi de ayarlanabilir.|
|PackageWithValidation|Paketlemeden önce doğrulamanın gerçekleştirilip gerçekleştirilmeyeceğini belirten bir Boole değeri. Bu özellik, paket oluştururken doğrulama hatalarını yoksaymanıza olanak sağlar.|
|Validatepackagebağımlıdson|ValidatePackage hedefinden önce yürütülecek ek hedefleri tanımlayan bir dize.|
|TokenReplacementFileExensions|Paketleme sırasında belirteçleri bulunan dosyaları tanımlayan bir dize.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Özellikler sayfasında MsBuild özelliklerini kullanın
 Esneklik için, SharePoint Özellikler sayfasında **dağıtım öncesi komut satırı** ve **dağıtım sonrası komut satırı** kutularında sabit kodlanmış dizeler kullanmak yerine, SharePoint özelliklerini bağımsız değişkenler olarak kullanabilirsiniz. Örneğin, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint sitesi için belirli bir dize belirtmek yerine, ' yi kullanabilirsiniz `$(SharePointSiteUrl)` .

> [!NOTE]
> [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(` *propertyName* `)` `%` *propertyName* `%` Bir özellik belirtmek için, değişken sözdizimi PropertyName veya ortam değişkeni sözdizimi PropertyName ' i kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)