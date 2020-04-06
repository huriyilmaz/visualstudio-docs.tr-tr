---
title: Nakliye Görsel Stüdyo Uzantıları | Microsoft Dokümanlar
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
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700119"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio Uzantıları Gönderme
Uzantınızı geliştirmeyi bitirdikten sonra, diğer makinelere yükleyebilir, arkadaşlarınız ve iş arkadaşlarınızla paylaşabilir veya Visual Studio Marketplace'te yayınlayabilirsiniz. Bu bölümde uzantınızı yayımlamak ve korumak için yapmanız gereken her şeyi açıklıyoruz: .vsix dosyalarıyla çalışmak, yayımlamak, yerelleştirmek ve güncelleştirmek.

## <a name="working-with-vsix-extensions"></a>VSIX Uzantıları ile çalışma
 Boş bir VSIX Projesi oluşturup sonra farklı öğe şablonları ekleyerek bir VSIX uzantıları oluşturabilirsiniz. Daha fazla bilgi için [VSIX Proje Şablonu'na](../extensibility/vsix-project-template.md)bakın.

 Proje şablonlarını, madde şablonlarını, VSPackages'ı, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenlerini, **Araç Kutusu** denetimlerini, derlemeleri ve özel türleri (Visual Studio 2017 için özel Başlangıç Sayfalarını içerir) paketlemek için VSIX biçimini kullanabilirsiniz. VSIX biçimi dosya tabanlı dağıtım kullanır. VSIX paketleri hakkında daha fazla bilgi için [vsix paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)bölümüne bakın.

 VSIX biçimi kod parçacıklarının yüklenmesini desteklemez. Ayrıca, Genel Montaj Önbelleğine (GAC) veya sistem kayıt defterine yazma gibi diğer bazı senaryoları da desteklemez. Yüklemedeki GAC'ye veya kayıt defterine yazmanız gerekiyorsa, Windows Yükleyici'yi kullanmanız gerekir. Daha fazla bilgi için Windows [Yükleyici Dağıtımı için Uzantı Hazırlama'ya](../extensibility/preparing-extensions-for-windows-installer-deployment.md)bakın.

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Uzantınızı Visual Studio Marketplace'e Yayınlama
 Uzantınızı sadece .vsix dosyasını postalayarak veya bir sunucuya koyarak diğer kişilere dağıtabilirsiniz. Ama bir çok insanın elinde kod almak için en iyi yolu [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)koymaktır. Visual Studio Marketplace uzantıları **Uzantılar ve Güncellemeler**aracılığıyla Visual Studio kullanıcıları tarafından kullanılabilir. Daha fazla bilgi için Visual [Studio Uzantılarını Bulma ve Kullanma bilgisine](../ide/finding-and-using-visual-studio-extensions.md)bakın.

 Visual Studio Marketplace'e nasıl bir uzantı yükleyin, [bkz.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

## <a name="private-galleries"></a>Özel Galeriler
 Denetimler, şablonlar ve araçlar geliştirirken, bunları intranetinizdeki özel bir galeriye göndererek kuruluşunuzla paylaşabilirsiniz. Daha fazla bilgi için [Bkz. Özel Galeriler.](../extensibility/private-galleries.md)

## <a name="localizing-your-extension"></a>Uzantınızı Yerelleştirme
 Uzantınızı farklı yerel bölgelerde serbest bırakmayı planlıyorsanız, bu uzantınızı yerelleştirmeyi düşünmelisiniz. İşin içinde ne olduğunu açıklamak için [VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)bölümüne bakın.

## <a name="updating-and-versioning-your-extension"></a>Uzantınızı Güncelleme ve Sürümleme
 Uzantınızı yayımladıktan sonra, güncelleştirmeniz gereken bir zaman gelecektir. Visual Studio Marketplace'te yayınlanan bir uzantIyi nasıl güncelleştirebilirsiniz öğrenmek [için bkz.](../extensibility/how-to-update-a-visual-studio-extension.md)

 Uzantınızı Visual Studio'nun birden çok sürümüne destek olacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için Visual [Studio'nun Birden Çok Sürümlerini Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)bölümüne bakın.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[VSIX Proje Şablonunu Kullanmaya Başlama](../extensibility/getting-started-with-the-vsix-project-template.md)|Özel bir proje şablonu yüklemek için VSIX proje şablonu nasıl kullanılacağını açıklar.|
|[Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSIX paketinin bileşenlerini açıklar.|
|[VSIX Proje Şablonu](../extensibility/vsix-project-template.md)|Bir uzantını nasıl paketleyip yayımlayacağı hakkında adım adım yönergeler sağlar.|
|[VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)|Extension.vsixlangpack dosyalarını kullanarak yükleme işlemi için yerelleştirilmiş metin nasıl sağlandığını açıklar.|
|[Nasıl Yapılır: Uzantı Güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md)|Sisteminizdeki bir uzantıyı nasıl güncelleştirip varolan bir Visual Studio uzantısına nasıl dağıtılanın açıklar.|
|[Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX dağıtım paketlerine başvuruların nasıl ekleyeceğini açıklar.|
|[Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Uzantınızın Windows Installer ile nasıl dağıtılangerektiğini açıklar.|
|[VSIX Paketlerini İmzalama](../extensibility/signing-vsix-packages.md)|VSIX paketlerinin nasıl imzalayacağını açıklar.|
|[Özel Galeriler](../extensibility/private-galleries.md)|Uzantılar için özel galerilerin nasıl oluşturulurulur açıklar.|
|[Visual Studio'nun Birden Çok Sürümünü Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Uzantınızın Visual Studio'nun birden fazla sürümüne nasıl destek gösteriş yapılacağını gösterir.|
|[Visual Studio'yu Bulma](locating-visual-studio.md)|Özel uzantı dağıtımı için Visual Studio örneklerini nasıl bulup bulalır açıklar.|
