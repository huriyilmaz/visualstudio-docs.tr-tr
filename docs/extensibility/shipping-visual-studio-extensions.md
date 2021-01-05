---
title: Visual Studio uzantılarını aktarma | Microsoft Docs
description: Visual Studio SDK uzantınızı yayımlama ve bakımını yapma hakkında bilgi edinin. VSIX dosyaları, yayımlama, yerelleştirme ve güncelleştirme gibi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 812fc4f4e2f8dcf54876e2764f0c091f16348496
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716009"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio Uzantıları Gönderme
Uzantınızı geliştirmeyi bitirdikten sonra, diğer makinelere yükleyebilir, arkadaşlarınızla ve iş arkadaşlarınızla paylaşabilir veya Visual Studio Market yayımlayabilirsiniz. Bu bölümde, uzantınızı yayımlamak ve sürdürmek için ihtiyacınız olan tüm şeyleri açıkladık:. vsix dosyaları, yayımlama, yerelleştirme ve güncelleştirme ile çalışma.

## <a name="working-with-vsix-extensions"></a>VSıX Uzantılarıyla çalışma
 Boş bir VSıX projesi oluşturup buna farklı öğe şablonları ekleyerek VSıX uzantıları oluşturabilirsiniz. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

 Proje şablonları, öğe şablonları, VSPackages, Managed Extensibility Framework (MEF) bileşenleri, **araç kutusu** denetimleri, derlemeler ve özel türleri PAKETLEMEK için VSIX biçimini kullanabilirsiniz (Bu, Visual Studio 2017 Için özel başlangıç sayfalarını içerir). VSıX biçimi dosya tabanlı dağıtım kullanır. VSıX paketleri hakkında daha fazla bilgi için bkz. [BIR VSIX paketinin Anatomı](../extensibility/anatomy-of-a-vsix-package.md).

 VSıX biçimi, kod parçacıklarının yüklenmesini desteklemez. Ayrıca, genel derleme önbelleği 'ne (GAC) veya sistem kayıt defterine yazma gibi bazı diğer senaryoları da desteklemez. Yüklemede GAC veya kayıt defterine yazmanız gerekiyorsa Windows Installer kullanmanız gerekir. Daha fazla bilgi için bkz. [Windows Installer dağıtım Için uzantıları hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Uzantınızı Visual Studio Market Yayımlama
 Uzantınızı diğer kişilere,. vsix dosyasını postayla göndererek veya sunucuya yerleştirerek dağıtabilirsiniz. Ancak, kodunuzu çok sayıda kişinin elsinden elde etmenin en iyi yolu, [Visual Studio Market](https://marketplace.visualstudio.com/vs). Visual Studio Market uzantıları, **Uzantılar ve güncelleştirmeler** aracılığıyla Visual Studio kullanıcıları tarafından kullanılabilir. Daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md).

 Bir uzantının Visual Studio Market nasıl yükleneceğini gösteren tam bir örnek için bkz. [Izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Özel Galeriler
 Denetimleri, şablonları ve araçları geliştirirken, bunları intranetinizdeki özel bir galeri 'ye göndererek kuruluşunuzla paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel galeriler](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Uzantınızı yerelleştirme
 Uzantınızı farklı yerel ayarlarda serbest bırakmayı planlıyorsanız, bunu yerelleştirmelisiniz. Nelerin ilgili olduğuna ilişkin bir açıklama için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Uzantınızı güncelleştirme ve sürümü oluşturma
 Uzantınızı yayımladıktan sonra, güncelleştirmeniz gerektiğinde bir zaman görüntülenir. Visual Studio Market yayımlanmış bir uzantıyı güncelleştirme hakkında bilgi edinmek için bkz. [nasıl yapılır: uzantıyı güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md).

 Uzantınızı, Visual Studio 'nun birden çok sürümünü destekleyecek şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Nun birden çok sürümünü destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[VSIX Proje Şablonunu Kullanmaya Başlama](../extensibility/getting-started-with-the-vsix-project-template.md)|Özel bir proje şablonu yüklemek için VSıX proje şablonunun nasıl kullanılacağını açıklar.|
|[Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSıX paketinin bileşenlerini açıklar.|
|[VSIX Proje Şablonu](../extensibility/vsix-project-template.md)|Uzantı paketleme ve yayımlama hakkında adım adım yönergeler sağlar.|
|[VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)|Uzantı. valtlangpack dosyalarını kullanarak yükleme işlemi için yerelleştirilmiş metnin nasıl sağlanacağını açıklar.|
|[Nasıl Yapılır: Uzantı Güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md)|Sisteminizde bir uzantının nasıl güncelleştirileceğini ve var olan bir Visual Studio uzantısına bir güncelleştirmenin nasıl dağıtılacağını açıklar.|
|[Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSıX dağıtım paketlerine başvuruların nasıl ekleneceğini açıklar.|
|[Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Uzantınızı Windows Installer ile dağıtmayı açıklar.|
|[VSIX Paketlerini İmzalama](../extensibility/signing-vsix-packages.md)|VSıX paketlerinin nasıl imzalanacağı açıklanmaktadır.|
|[Özel Galeriler](../extensibility/private-galleries.md)|Uzantılar için özel galerinin nasıl oluşturulacağını açıklar.|
|[Visual Studio'nun Birden Çok Sürümünü Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Uzantınızın Visual Studio 'nun birden çok sürümünü nasıl desteklemesi gerektiğini gösterir.|
|[Visual Studio'yu Bulma](locating-visual-studio.md)|Özel uzantı dağıtımı için Visual Studio örneklerinin nasıl bulunacağını açıklar.|
