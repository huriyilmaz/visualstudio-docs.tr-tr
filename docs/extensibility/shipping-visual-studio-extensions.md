---
title: Visual Studio uzantılarını aktarma | Microsoft Docs
description: . vsix dosyaları, yayımlama, yerelleştirme ve güncelleştirme dahil olmak üzere Visual Studio SDK uzantınızı yayımlamayı ve bakımını yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 55362ac1aa8aa5c04eb2631b689f70cc2ef98e1100b65ef0fcc63da1bf5b8e5b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305132"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio Uzantıları Gönderme
uzantınızı geliştirmeyi bitirdikten sonra, diğer makinelere yükleyebilir, arkadaşlarınızla ve iş arkadaşlarınızla paylaşabilir veya Visual Studio market 'te yayımlayabilirsiniz. Bu bölümde, uzantınızı yayımlamak ve sürdürmek için ihtiyacınız olan tüm şeyleri açıkladık:. vsix dosyaları, yayımlama, yerelleştirme ve güncelleştirme ile çalışma.

## <a name="working-with-vsix-extensions"></a>VSıX Uzantılarıyla çalışma
 boş bir vsıx Project oluşturup daha sonra buna farklı öğe şablonları ekleyerek vsıx uzantıları oluşturabilirsiniz. daha fazla bilgi için bkz. [vsıx Project şablonu](../extensibility/vsix-project-template.md).

 proje şablonları, öğe şablonları, vspackages, Managed Extensibility Framework (MEF) bileşenleri, **araç kutusu** denetimleri, derlemeler ve özel türleri paketlemek için vsıx biçimini kullanabilirsiniz (buna Visual Studio 2017 için özel başlangıç sayfaları dahildir). VSıX biçimi dosya tabanlı dağıtım kullanır. VSıX paketleri hakkında daha fazla bilgi için bkz. [BIR VSIX paketinin Anatomı](../extensibility/anatomy-of-a-vsix-package.md).

 VSıX biçimi, kod parçacıklarının yüklenmesini desteklemez. Ayrıca, genel derleme önbelleği 'ne (GAC) veya sistem kayıt defterine yazma gibi bazı diğer senaryoları da desteklemez. yüklemede GAC veya kayıt defterine yazmanız gerekiyorsa Windows Installer kullanmanız gerekir. daha fazla bilgi için bkz. [Windows Installer dağıtım için uzantıları hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>uzantınızı Visual Studio marketi 'nde yayımlama
 Uzantınızı diğer kişilere,. vsix dosyasını postayla göndererek veya sunucuya yerleştirerek dağıtabilirsiniz. ancak, kodunuzu çok sayıda kişinin elsinden elde etmenin en iyi yolu, [Visual Studio market](https://marketplace.visualstudio.com/vs)'e yerleştirkullanmaktır. Visual Studio market uzantıları, **uzantılar ve güncelleştirmeler** aracılığıyla Visual Studio kullanıcılar tarafından kullanılabilir. daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md).

 Visual Studio market 'e uzantı yükleme işleminin nasıl yapılacağını gösteren tam bir örnek için bkz. [izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Özel Galeriler
 Denetimleri, şablonları ve araçları geliştirirken, bunları intranetinizdeki özel bir galeri 'ye göndererek kuruluşunuzla paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel galeriler](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Uzantınızı yerelleştirme
 Uzantınızı farklı yerel ayarlarda serbest bırakmayı planlıyorsanız, bunu yerelleştirmelisiniz. Nelerin ilgili olduğuna ilişkin bir açıklama için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Uzantınızı güncelleştirme ve sürümü oluşturma
 Uzantınızı yayımladıktan sonra, güncelleştirmeniz gerektiğinde bir zaman görüntülenir. Visual Studio marketi 'nde yayımlanmış olan bir uzantıyı güncelleştirme hakkında bilgi edinmek için bkz. [nasıl yapılır: uzantı güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md).

 Uzantınızı, Visual Studio birden çok sürümünü destekleyecek şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio birden çok sürümünü destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[VSIX Proje Şablonunu Kullanmaya Başlama](../extensibility/getting-started-with-the-vsix-project-template.md)|Özel bir proje şablonu yüklemek için VSıX proje şablonunun nasıl kullanılacağını açıklar.|
|[Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSıX paketinin bileşenlerini açıklar.|
|[VSIX Proje Şablonu](../extensibility/vsix-project-template.md)|Uzantı paketleme ve yayımlama hakkında adım adım yönergeler sağlar.|
|[VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)|Uzantı. valtlangpack dosyalarını kullanarak yükleme işlemi için yerelleştirilmiş metnin nasıl sağlanacağını açıklar.|
|[Nasıl Yapılır: Uzantı Güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md)|sisteminizde bir uzantının nasıl güncelleştirileceğini ve mevcut bir Visual Studio uzantısına bir güncelleştirmenin nasıl dağıtılacağını açıklar.|
|[Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSıX dağıtım paketlerine başvuruların nasıl ekleneceğini açıklar.|
|[Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|uzantınızı Windows Installer ile dağıtmayı açıklar.|
|[VSIX Paketlerini İmzalama](../extensibility/signing-vsix-packages.md)|VSıX paketlerinin nasıl imzalanacağı açıklanmaktadır.|
|[Özel Galeriler](../extensibility/private-galleries.md)|Uzantılar için özel galerinin nasıl oluşturulacağını açıklar.|
|[Visual Studio'nun Birden Çok Sürümünü Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Uzantınızın Visual Studio birden çok sürümünü nasıl desteklediğini gösterir.|
|[Visual Studio'yu Bulma](locating-visual-studio.md)|özel uzantı dağıtımı için Visual Studio örneklerinin nasıl bulunacağını açıklar.|
