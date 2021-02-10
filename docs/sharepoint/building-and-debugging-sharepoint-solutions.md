---
title: SharePoint çözümlerini derleme ve hata ayıklama | Microsoft Docs
description: SharePoint çözümlerini derlemeyi ve hata ayıklamayı öğrenin ve Visual Studio 'da diğer proje türlerini oluşturma ve hata ayıklamanın nasıl farklı olduğunu anlayın.
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
ms.workload:
- office
ms.openlocfilehash: c16414e6a49d727cf6b2113184c507feb7a73569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955800"
---
# <a name="build-and-debug-sharepoint-solutions"></a>SharePoint çözümlerini derleme ve hata ayıklama
  Genel olarak, SharePoint çözümlerini derleme ve hata ayıklama, içindeki diğer proje türlerini derleme ve hata ayıklama ile aynıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu bölümdeki konular, var olan farkları açıklamaktadır.

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint çözümleri için proje çıktısı
 SharePoint çözümleri oluşturma, derlemeler ve bir çözüm paketi (*. wsp*) dosyası oluşturur. Aşağıdaki tabloda, bir derleme sırasında bu dosyaların konumları gösterilmektedir.

|Derleme öğesi|Çıkış klasörü|
|----------------|-------------------|
|Derleme, program veritabanı (*. pdb*) ve *. wsp* dosyaları.|*\<ProjectName> \Bin\Debug* veya *\<ProjectName> \bin\Release*|
|SharePoint proje öğesi dosyaları.|*\<ProjectName> \pkg\debug* veya *\<ProjectName> \pkg\release*|
|Ara dosyalar oluşturun.|*\<ProjectName> \obj\debug* veya *\<ProjectName> \obj\release*|
|Paket ara dosyaları.|*\<ProjectName> \pkgobj\debug* veya *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>SharePoint çözümleri oluşturma
 SharePoint çözümleri oluşturmak için, geliştirme bilgisayarında SharePoint Server 'ın doğru sürümünün yüklü olması gerekir. Aksi halde, SharePoint çözümlerini derleme ' de diğer proje türlerini oluşturma ile aynıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri derleme](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>SharePoint çözümlerini hata ayıklama ve test etme
 Hata ayıklamadan önce, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] *. wsp* paketini SharePoint sunucusuna kopyalar, siteyi ve Web kapsamlı özellikleri etkinleştirir ve bazı durumlarda projeyi başlatır. Diğer durumlarda, projeyi el ile açmanız gerekebilir. Daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md) ve [SharePoint çözümlerini hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Azure DevOps Services özelliklerini kullanarak SharePoint çözümlerini hata ayıklama ve doğrulama
 Birim testi ve IntelliTrace gibi Azure DevOps Services özellikler, SharePoint çözümlerinizde sorunları daha doğru bir şekilde belirlemenize olanak sağlar. Profil oluşturma, SharePoint çözümlerinizde performans sorunu alanını bulmanıza ve tanımlamanızı sağlar. Daha fazla bilgi için bkz. [SharePoint kodunu doğrulama ve hata ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md) ve [SharePoint uygulamalarının performansını profil oluşturma](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Oluşturma işlemi sırasında güvenlik
 SharePoint çözümlerini paketlemek veya dağıtmak için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint sunucusuna dosya kopyalama izninizin olması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yükseltilmiş bir işlem olarak çalıştırmalısınız ve Kullanıcı hesabınızın SharePoint sunucusunda bir site koleksiyonları Yöneticisi olması gerekir. Ayrıca, projenizin korumalı bir çözüm mi yoksa Grup çözümü mi olduğunu belirtmeniz gerekir. Daha fazla bilgi için bkz. [korumalı ve Grup çözümleri arasındaki farklılıklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Clean komutunu kullanma
 Hata ayıklama için bir SharePoint sunucusuna SharePoint çözümü yüklendiğinde, **Temizleme** komutu çözümü kaldırmaz. Bunun yerine, SharePoint yapılandırması aracılığıyla özellikleri devre dışı bırakmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
