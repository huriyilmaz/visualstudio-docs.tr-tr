---
title: Sevkiyat Visual Studio Uzantıları | Microsoft Docs
description: .vsix dosyalarıyla çalışma, yayımlama, yerelleştirme ve güncelleştirme dahil olmak üzere Visual Studio SDK uzantınızı yayımlamayı ve korumayı öğrenin.
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
ms.openlocfilehash: a57cb6732c1b1cb5fa74381ab7c8bdf8208be08d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028637"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio Uzantıları Gönderme
Uzantınızı geliştirmeyi bitirdikten sonra diğer makinelere yükleyebilir, arkadaşlarınızla ve iş arkadaşlarınızla paylaşabilir veya Visual Studio Market'te yayımlayın. Bu bölümde uzantınızı yayımlamak ve korumak için gereken her şeyi açıklayacağız: .vsix dosyalarıyla çalışma, yayımlama, yerelleştirme ve güncelleştirme.

## <a name="working-with-vsix-extensions"></a>VSIX Uzantılarıyla Çalışma
 Boş bir VSIX uzantısı oluşturarak ve ardından Project şablonlarını ekleyerek VSIX uzantıları oluşturabilirsiniz. Daha fazla bilgi için bkz. [VSIX Project Şablonu.](../extensibility/vsix-project-template.md)

 Proje şablonlarını, öğe şablonlarını, VSPackage'ları, Managed Extensibility Framework (MEF) bileşenlerini, **Araç** kutusu denetimlerini, derlemeleri ve özel türleri (bu, Visual Studio 2017 için özel Başlangıç Sayfalarını içerir) paketlemek için VSIX biçimini kullanabilirsiniz. VSIX biçimi, dosya tabanlı dağıtım kullanır. VSIX paketleri hakkında daha fazla bilgi için bkz. [VSIX Paketinin Anatomisi.](../extensibility/anatomy-of-a-vsix-package.md)

 VSIX biçimi, kod parçacıklarının yüklemesini desteklemez. Genel Derleme Önbelleği'ne (GAC) veya sistem kayıt defterine yazma gibi bazı diğer senaryoları da desteklemez. Yüklemede GAC'ye veya kayıt defterine yazmanız gerekirse, Windows Installer'Windows gerekir. Daha fazla bilgi için, [bkz. Preparing Extensions for Windows Installer Deployment](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Uzantınızı Visual Studio Market'te yayımlama
 Uzantınızı diğer kullanıcılara dağıtmak için onlara .vsix dosyasını e-postayla veya bir sunucuya koyarak dağıtabilirsiniz. Ancak kodunuzu birçok kişinin eline almanın en iyi yolu, bunu Market'te Visual Studio [etmektir.](https://marketplace.visualstudio.com/vs) Visual Studio Market uzantıları, uzantılar ve Visual Studio kullanıcılar **tarafından kullanılabilir.** Daha fazla bilgi için, [bkz. Using and Using Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md).

 Visual Studio Market'e bir uzantının nasıl yük Visual Studio gösteren tam bir örnek için bkz. Visual Studio [Yayımlama.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

## <a name="private-galleries"></a>Özel Galeriler
 Denetimler, şablonlar ve araçlar geliştirirken, bunları intraneti üzerinde özel bir galeriye göndererek bunları kuruluşla paylaşabilirsiniz. Daha fazla bilgi için bkz. [Özel Galeriler.](../extensibility/private-galleries.md)

## <a name="localizing-your-extension"></a>Uzantınızı Yerelleştirme
 Uzantınızı farklı yerel olarak serbest bırakmayı planlıyorsanız yerelleştirmeyi göz önünde bulundurarak yapabilirsiniz. Neler olduğu hakkında bir açıklama için bkz. [VSIX Paketlerini Yerelleştirme.](../extensibility/localizing-vsix-packages.md)

## <a name="updating-and-versioning-your-extension"></a>Uzantınızı Güncelleştirme ve Sürüme Ekleme
 Uzantınızı yayımladıktan sonra güncelleştirmeniz gereken bir zaman gelecektir. Visual Studio Market'te yayımlanmış bir uzantının nasıl güncelleştirilmesi hakkında bilgi için [bkz. How to: Update an Extension](../extensibility/how-to-update-a-visual-studio-extension.md).

 Uzantınızı birden çok sürüm sürümünü destekleyecek şekilde Visual Studio. Daha fazla bilgi için, [bkz. Supporting Multiple Versions of Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[VSIX Proje Şablonunu Kullanmaya Başlama](../extensibility/getting-started-with-the-vsix-project-template.md)|VsIX proje şablonunu kullanarak özel bir proje şablonu yüklemeyi açıklar.|
|[Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSIX paketinin bileşenlerini açıklar.|
|[VSIX Proje Şablonu](../extensibility/vsix-project-template.md)|Uzantıyı paketle ve yayımla hakkında adım adım yönergeler sağlar.|
|[VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)|extension.vsixlangpack dosyalarını kullanarak yükleme işlemi için yerelleştirilmiş metin sağlamayı açıklar.|
|[Nasıl Yapılır: Uzantı Güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md)|Sisteminiz üzerinde bir uzantıyı güncelleştirme ve mevcut bir uzantıya güncelleştirme dağıtma Visual Studio açıklar.|
|[Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX dağıtım paketlerine başvuru eklemeyi açıklar.|
|[Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Uzantınızı Windows Yükleyicisi ile dağıtmayı açıklar.|
|[VSIX Paketlerini İmzalama](../extensibility/signing-vsix-packages.md)|VSIX paketlerini imzalamayı açıklar.|
|[Özel Galeriler](../extensibility/private-galleries.md)|Uzantılar için özel galeriler oluşturma açıklandı.|
|[Visual Studio'nun Birden Çok Sürümünü Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Uzantınıza birden çok sürüm desteğinin nasıl Visual Studio.|
|[Visual Studio'yu Bulma](locating-visual-studio.md)|Özel uzantı dağıtımı için Visual Studio örneklerinin nasıl bulun açık olduğunu açıklar.|
