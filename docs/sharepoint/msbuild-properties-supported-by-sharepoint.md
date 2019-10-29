---
title: SharePoint tarafından desteklenen MSBuild özellikleri | Microsoft Docs
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
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985174"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint tarafından desteklenen MsBuild özellikleri
  Microsoft. VisualStudio. SharePoint. targets dosyasında, proje dosyasında veya proje Kullanıcı dosyasında tanımlanan herhangi bir [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] özelliği, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projelerinde kullanılabilir. SharePoint, projenin sağladığı ortak [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] özelliklerine ek olarak SharePoint projelerine özgü ek özellikler tanımlar.

 Ortak [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] özelliklerinin bir listesi için bkz. [Ortak MSBuild proje özellikleri](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Programlama diliniz tarafından desteklenen özelliklerin tam listesi için *. targets* dosyasına, proje dosyasına ( *. csproj* veya *. vbproj*) veya proje Kullanıcı dosyasına (*csproj. User* veya *. vbproj. User*) bakın.

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint 'e özgü MsBuild özellikleri
 Aşağıdaki tabloda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]özel olarak SharePoint projelerine uygulanan [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] özellikleri listelenmektedir. Diğer özellikler mevcuttur, ancak bunlar iç kullanım içindir.

|Özellik adı|Açıklama|
|-------------------|-----------------|
|SharePointSiteUrl|SharePoint sitesinin [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] temsil eden bir dize.|
|SandboxedSolution|Çözümün korumalı bir çözüm olup olmadığını gösteren bir Boole değeri.|
|ActiveDeploymentConfiguration|Etkin dağıtım yapılandırması.|
|Includeassemblınpackage|Derlemenin paket dosyasına dahil edilip edilmeyeceğini belirten bir Boole değeri.|
|PreDeploymentCommand|Dağıtım öncesi komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|PostDeploymentCommand|Dağıtım sonrası komut adımında yürütülecek komutu temsil eden bir dize değeri.|
|CustomBeforeSharePointTargets|[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] hedef dosyasının yolunu temsil eden bir dize. Hedef dosya varsa ve tanımlanmışsa, SharePoint hedefi verilerinden önce içeri aktarılır. Bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmeden paketlemeyle ilgili özelliklerini önceden tanımlayarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası tüm SharePoint projeleri için geçerli olmaya devam eder.|
|CustomAfterSharePointTargets|[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] hedef dosyasının yolunu temsil eden bir dize. Hedef dosya varsa ve tanımlanmışsa, tüm SharePoint hedefi verilerinden sonra içeri aktarılır. Bu özellik, sevk edilen SharePoint hedefleri dosyasını değiştirmek zorunda kalmadan paketlemeyle ilgili özellikleri ve hedefleri geçersiz kılarak paket işlemini özelleştirmenize olanak tanır, ancak hedefler dosyası tüm SharePoint projeleri için geçerli olmaya devam eder.|
|LayoutPath|Paketlenebilecek her bir dosyanın *. wsp* dosyasına eklenmeden önce geçici olarak yerleştirildiği kök dizini temsil eden bir dize. Bu yol, *. wsp* dosyasının içeriğini değiştirmek için kullanabileceğiniz dosyaları eklemek, kaldırmak veya değiştirmek için BeforeLayout ve AfterLayout hedeflerini geçersiz kıldığınızda bilmeniz yararlı olabilir.|
|BasePackagePath|Paketin yerleştirildiği klasörü temsil eden bir dize. Bu değer, projenin çıkış dizinini (örneğin, Bin\debug) kullanır.|
|PackageExtension|Pakete eklenecek dosya adı uzantısını temsil eden bir dize. Varsayılan değer wsp ' dir.|
|AssemblyDeploymentTarget|SharePoint sunucusunda proje derlemesinin dağıtıldığı konumu temsil eden bir dize. Değeri GlobalAssemblyCache (varsayılan) ya da WebApplication ' dir. Bu özellik Özellikler penceresi de ayarlanabilir.|
|PackageWithValidation|Paketlemeden önce doğrulamanın gerçekleştirilip gerçekleştirilmeyeceğini belirten bir Boole değeri. Bu özellik, paket oluştururken doğrulama hatalarını yoksaymanıza olanak sağlar.|
|Validatepackagebağımlıdson|ValidatePackage hedefinden önce yürütülecek ek hedefleri tanımlayan bir dize.|
|TokenReplacementFileExensions|Paketleme sırasında belirteçleri bulunan dosyaları tanımlayan bir dize.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Özellikler sayfasında MsBuild özelliklerini kullanın
 Esneklik için, SharePoint Özellikler sayfasında **dağıtım öncesi komut satırı** ve **dağıtım sonrası komut satırı** kutularında sabit kodlanmış dizeler kullanmak yerine, SharePoint özelliklerini bağımsız değişkenler olarak kullanabilirsiniz. Örneğin, SharePoint sitesi için belirli bir [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dizesi belirtmek yerine `$(SharePointSiteUrl)`kullanabilirsiniz.

> [!NOTE]
> Bir özellik belirtmek için `$(`*propertyname*`)` [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] değişken sözdizimini veya ortam değişkeni sözdizimini `%`*PropertyName*`%` kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild Başvurusu](../msbuild/msbuild-reference.md)