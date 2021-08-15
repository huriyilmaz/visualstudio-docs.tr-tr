---
title: Çözüm Çözümleri SharePoint Ve Hata Ayıklama | Microsoft Docs
description: Çözüm oluşturma ve SharePoint ayıklama hakkında bilgi edinmek ve bu çözümlerde diğer proje türlerini derlemek ve hata ayıklamaktan ne Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 38a82d6b5eba33bd3c832e0c028054087db17e107e1b93d2c1b173657d4a6bb4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244582"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Çözüm oluşturma ve SharePoint ayıklama
  Genel olarak, çözümlerini SharePoint ve hata ayıklaması, 'de diğer proje türlerine yönelik olarak yapı ve hata ayıklama ile [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aynıdır. Bu bölümdeki konular, var olan farkları açıklar.

## <a name="project-output-for-sharepoint-solutions"></a>Project çözümleri için SharePoint çıkış
 Derleme SharePoint derlemeler ve bir çözüm paketi (*.wsp*) dosyası oluşturur. Aşağıdaki tabloda, bir derleme sırasında bu dosyaların konumları gösterir.

|Derleme öğesi|Çıkış klasörü|
|----------------|-------------------|
|Derleme, program veritabanı (*.pdb*) ve *.wsp* dosyaları.|*\<ProjectName> \bin\debug* veya *\<ProjectName> \bin\release*|
|SharePoint öğesi dosyalarını seçin.|*\<ProjectName> \pkg\debug* veya *\<ProjectName> \pkg\release*|
|Ara dosyalar derleme.|*\<ProjectName> \obj\debug* veya *\<ProjectName> \obj\release*|
|Ara dosyaları paketle.|*\<ProjectName> \pkgobj\debug* veya *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Yeni SharePoint oluşturma
 Bu SharePoint oluşturmak için, geliştirme bilgisayarın doğru SharePoint yüklü olmalıdır. Aksi takdirde, SharePoint çözümlerinin inşası, içinde diğer proje türleriyle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aynıdır. Daha fazla bilgi için [bkz. Nasıl SharePoint.](../sharepoint/how-to-build-sharepoint-solutions.md)

## <a name="debug-and-test-sharepoint-solutions"></a>Hata ayıklama ve SharePoint test
 Hata ayıklamadan [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] önce *, .wsp* paketini SharePoint sunucusuna kopyalar, Site ve Web kapsamlı Özellikleri etkinleştirir ve bazı durumlarda projeyi başlatır. Diğer durumlarda projeyi el ile açmanız gerekebilir. Daha fazla bilgi için [bkz. SharePoint sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-solutions.md) ve [hata ayıklama SharePoint çözümleri.](../sharepoint/debugging-sharepoint-solutions.md)

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Azure DevOps Services kullanarak SharePoint çözümlerini ayıklama ve doğrulama
 Azure DevOps Services testi ve IntelliTrace gibi farklı özellikler sayesinde sorunları daha doğru bir şekilde tespit SharePoint sağlar. Profil oluşturma, uygulama çözümlerinizin performans sorunu alanlarını bulmanızı ve SharePoint sağlar. Daha fazla bilgi için, [bkz. Verifying and Debugging SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) [and Profiling the Performance of SharePoint Applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Derleme işlemi sırasında güvenlik
 Farklı çözümleri SharePoint dağıtmak için, dosyaları SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sunucusuna kopyalama iznine sahip olması gerekir. Yükseltilmiş bir işlem olarak çalıştırmanız ve kullanıcı hesabınız, SharePoint sunucusunda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Site Koleksiyonları Yöneticisi olması gerekir. Ayrıca, projenizin korumalı alan çözümü veya grup çözümü olduğunu belirtmeniz gerekir. Daha fazla bilgi için [bkz. Korumalı Alan ve Grup Çözümleri Arasındaki Farklar.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)

## <a name="using-the-clean-command"></a>Clean komutunu kullanma
 Hata SharePoint için bir SharePoint sunucusuna bir çözüm yüklenirken, **Clean** komutu çözümü kaldırmaz. Bunun yerine, Özellikler'i SharePoint devre dışı bırakmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint kullanarak bağlantılara göz Sunucu Gezgini](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
