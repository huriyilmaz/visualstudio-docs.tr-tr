---
title: MSBuild SharePoint tarafından desteklenen özellikler | Microsoft Docs
description: tarafından desteklenen ve SharePoint özgü MSBuild özellik adları ve açıklamaları listesini okuyun.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 66024105ac41c6c72d7eec019d507183fdd7479a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115557"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint tarafından desteklenen MsBuild özellikleri
  [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft. VisualStudio. SharePoint. targets dosyasında, proje dosyasında veya proje kullanıcı dosyasında tanımlanan herhangi bir özellik [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projelerinde kullanılabilir. [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]projenin sağladığı ortak özelliklere ek olarak, SharePoint SharePoint projelerine özgü ek özellikler tanımlar.

 ortak özelliklerin listesi için [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] bkz. [ortak MSBuild Project özellikleri](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Programlama diliniz tarafından desteklenen özelliklerin tam listesi için *. targets* dosyasına, proje dosyasına (*. csproj* veya *. vbproj*) veya proje Kullanıcı dosyasına (*csproj. User* veya *. vbproj. User*) bakın.

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint özgü MsBuild özellikleri
 aşağıdaki tabloda, [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] içindeki SharePoint projelerine özel olarak uygulanan özellikler listelenmiştir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Diğer özellikler mevcuttur, ancak bunlar iç kullanım içindir.

|Özellik Adı|Açıklama|
|-------------------|-----------------|
|SharePointSiteUrl|SharePoint sitesine temsil eden bir dize [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] .|
|SandboxedSolution|Çözümün korumalı bir çözüm olup olmadığını gösteren bir Boole değeri.|
|ActiveDeploymentConfiguration|Etkin dağıtım yapılandırması.|
|Includeassemblınpackage|Derlemenin paket dosyasına dahil edilip edilmeyeceğini belirten bir Boole değeri.|
|PreDeploymentCommand|Dağıtım öncesi komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|PostDeploymentCommand|Dağıtım sonrası komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|CustomBeforeSharePointTargets|Bir hedef dosyanın yolunu temsil eden bir dize [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . hedef dosya varsa ve tanımlanmışsa, hiçbir SharePoint verileri hedeflemesinden önce içeri aktarılır. bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmeden paketlemeyle ilgili özellikleri tanımlayarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası hala tüm SharePoint projelerine uygulanır.|
|CustomAfterSharePointTargets|Bir hedef dosyanın yolunu temsil eden bir dize [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . hedef dosya varsa ve tanımlanmışsa, tüm SharePoint verileri hedefledikten sonra içeri aktarılır. bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmek zorunda kalmadan paketlemeyle ilgili özellikleri ve hedefleri geçersiz kılarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası yine de tüm SharePoint projelerine uygulanır.|
|LayoutPath|Paketlenebilecek her bir dosyanın *. wsp* dosyasına eklenmeden önce geçici olarak yerleştirildiği kök dizini temsil eden bir dize. Bu yol, *. wsp* dosyasının içeriğini değiştirmek için kullanabileceğiniz dosyaları eklemek, kaldırmak veya değiştirmek için BeforeLayout ve AfterLayout hedeflerini geçersiz kıldığınızda bilmeniz yararlı olabilir.|
|BasePackagePath|Paketin yerleştirildiği klasörü temsil eden bir dize. Bu değer, projenin çıkış dizinini (örneğin, Bin\debug) kullanır.|
|PackageExtension|Pakete eklenecek dosya adı uzantısını temsil eden bir dize. Varsayılan değer wsp ' dir.|
|AssemblyDeploymentTarget|SharePoint sunucuda proje derlemesinin dağıtıldığı konumu temsil eden bir dize. Değeri GlobalAssemblyCache (varsayılan) ya da WebApplication ' dir. Bu özellik Özellikler penceresi de ayarlanabilir.|
|PackageWithValidation|Paketlemeden önce doğrulamanın gerçekleştirilip gerçekleştirilmeyeceğini belirten bir Boole değeri. Bu özellik, paket oluştururken doğrulama hatalarını yoksaymanıza olanak sağlar.|
|Validatepackagebağımlıdson|ValidatePackage hedefinden önce yürütülecek ek hedefleri tanımlayan bir dize.|
|TokenReplacementFileExensions|Paketleme sırasında belirteçleri bulunan dosyaları tanımlayan bir dize.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Özellikler sayfasında MsBuild özelliklerini kullanın
 esneklik için, SharePoint özellikler sayfasında **dağıtım öncesi komut satırı** ve **dağıtım sonrası komut satırı** kutularında sabit kodlanmış dizeler kullanmak yerine, SharePoint özelliklerini bağımsız değişken olarak kullanabilirsiniz. örneğin, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] SharePoint sitesi için belirli bir dize belirtmek yerine, ' yi kullanabilirsiniz `$(SharePointSiteUrl)` .

> [!NOTE]
> [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`  `)` `%`  `%` Bir özellik belirtmek için, değişken sözdizimi PropertyName veya ortam değişkeni sözdizimi PropertyName ' i kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild Başvurunun](../msbuild/msbuild-reference.md)